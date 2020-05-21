---
layout: post
title:      "The Suspense is Killing Me"
date:       2020-05-21 16:17:58 -0400
permalink:  the_suspense_is_killing_me
---


![](https://media.tenor.com/images/396316b3becf0784a8a09c4540fcbfdc/tenor.gif)

So, from my [last post](https://kkamali.github.io/befriending_state_with_captain_react_hook) we know that classes in React are going away and it's in with the new. React Hooks! I was definitely excited to use them in my projects I'm working on but then I saw something while trying to use fetch.... Hooks don't use lifecycle methods like the beloved `componentDidMount`.


What do we do instead? We want to use the latest and greatest of course. (Or to be perfectly candid, I just kept my  component class with the note to do more research later). In any case, there is a hook for that! It's `useEffect`. So, it would be something like this... (transforming my old code) 

**Old Code:**
```
class Deck extends Component {
  state = {
    tarotCards: []
  }

  componentDidMount() {
    fetch('http://localhost:3000/cards')
      .then(response => response.json())
      .then(data => {
        this.setState({
          tarotCards: data
        })
      })
  }
```

**To:**
```
const Deck = () => {
  const [deck, setDeck] = useState({})
	
	useEffect(() => {
	  async function fetchData() {
		  const res = await fetch("http://localhost:3000/cards")
			res
			  .json()
				.then(res => setDeck(res))
		}
		fetchData()
	}
```

However, it looks like React is coming out with a new component -- Suspense. 

![](https://media.tenor.com/images/faae6c155cb324a8fde9c47bb5e60613/tenor.gif)


According to the docs it's a new experimental component. 
> [T]hat lets you "wait" for some code to load and declaratively specify a loading state (like a spinner) while we're waiting

But Suspense isn't a replacement for `fetch`! At least, not now. It only works on fetching data with a library that's already integrated with it. So, all in all not very useful for now. Interesting to see how it changes... 

![](https://media1.tenor.com/images/17f638077f347d6ee7c202312e41a106/tenor.gif?itemid=4513227)
