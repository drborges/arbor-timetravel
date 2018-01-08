# Arbor Time Travel

Provides time traveling functionality to [Arbor](https://github.com/drborges/arbor-store) stores.

# Getting Started

A simple Counter APP...

```js
import Arbor from "arbor-store"
import timetravel from "arbor-timetravel"

const store = timetravel(new Arbor({
  todos: []
}))

// retrieves the current time cursor value
store.timeline.cursor

// goes back one time unit
store.timeline.travel.step(-1)

// move forward one time unit
store.timeline.travel.step(1)

// travels to a specific point in time
store.timeline.travel.to(5)

// goes back to the beginning of time
store.timeline.travel.origin()

// travels to the last state change (present)
store.timeline.travel.present()
```

# State Tree Time Travel

Arbor leverages Structural Sharing in order to perform state mutations. A new
state tree is always created by applying the minimum amount of operations
necessary to generate the new state. With this, a series of state snapshots may
be recorded. This packages leverages that behavior in order to provide time
traveling features for Arbor based stores. Checkout [this proof of concept app](https://drborges.github.io/arbor-react-app) for more insights:

![2017-12-14 20 51 16](https://user-images.githubusercontent.com/508128/34018352-9d031a56-e110-11e7-9e3f-9f30a3c2e8ad.gif)
