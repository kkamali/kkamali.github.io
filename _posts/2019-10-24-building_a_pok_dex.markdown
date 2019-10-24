---
layout: post
title:      "Building a Pokédex"
date:       2019-10-24 16:40:27 +0000
permalink:  building_a_pok_dex
---

Pokémon Sword and Shield is coming out soon. Unfortunately, I'm probably not going to be able to afford it when it does.. But I'm in the Pokémon mood! Since I can't get the 'mons out of my head, I guess I'll just write a Pokédex CLI application.  

Instead of scraping all of Bulbapedia, there's an API. And luckily I've used the PokéAPI before, it's straightforward and well-built. Also, it has a Ruby  wrapper!  

So an easy step 1 --  add  the PokéAPI gem to the gemfile. 
```
gem "poke-api-v2"

group :development do
  gem "pry"
end
```

Pry is going to help with figuring out how to maniuplate what we get back from PokéAPI. Speaking of, what information do we want our Pokédex to provide? In the game, you only get entries for Pokémon you actually catch but let's assume we're the best trainers, like no one ever was. Height, weight, type and flavor-text is probably all we need to start. Since this is a CLI app we won't need anything like cries or sprites. 

I assumed a simple base case that you have a name of a 'Mon and want more information on it. So I  created a simple method to wrap around what we get from the PokéAPI gem. This will all take place in a Pokédex class. 

```
def get_pokemon(pokemon)
   mon = PokeAPI.get(pokemon: pokemon) 
	 #you can then do things like 
	 height = mon.height 
end
```

There were a couple of things I noticed while building out this method. A) The height and weight are in decimetres and hectograms. For now, I just normalized them into meters and kilos. B) What if we called this method on a Pokémon that doesn't actually exist? You need to rescue your program like so... 

```
def get_pokemon(pokemon)
    begin
      mon = PokeApi.get(pokemon: pokemon)
    rescue JSON::ParserError
      return "No such Pokemon!"
    end
		#then feel free to get your PokéInfo
end
```

PokéAPI has a lot of other methods you can use to look up abilities, locations, etc. But for now we have a good base. Why don't we try creating the CLI app itself before adding more functionality? I'm going to create a PokédexController. 

What's important to consider about a CLI app, is that it takes user input until the user exits. So, in a method called run I can just create a loop that goes *until* a user inputs "exit". Until will be the loop chosen. I love the way Ruby handles loops. So you'll end up with something like this... 

```
def run
  puts "Some instructions here..." 
	user_input = gets.chomp
	until user_input == "exit" 
	  #output stuff about chosen pokemon here! 
		user_input = gets.chomp #don't forget this or you'll end up in an infinite loop dimension... 
	end
end
```

Once we build out an executable in our bin folder we'll have an MVP. This is a very very simple Pokédex, and as we can see the API has a lot of information we can use to add even cooler functionality. You can add features to your hearts content! And maybe it can distract you while all of your friends are playing the new game :) 
