---
description: 'Hello world, goodbye world, and more...'
---

# Build a chatbot with Watson Assistant

### 

### Working in the Assistant UI

* Quick overview
* Example Customer Care skill
* Intents
* Entities
* Dialog
* Try it!

### Add an intent

* Examine some from the content catalog
* TODO: an insurance example that is not from the catalog to add

### Add an entity

### Varied responses

* Serialize or randomize responses to be less predictable
* Chatbot says:  Hello, My name is {different every time}

### Using context to remember state

* Use context to retain state
* Demo:
  * Select a random name the first time \(per session\)
  * Keep the same name when asked again \(same session\)
* Demo 2:
  * Remember the users name

### Use "slots" to gather information

* Add a slots example for insurance claim \(or use current examples of pizza or rent-a-car\)

### Digression

* What happens if user says "what is your name?" in the middle of the filling those slots?
* Enable digression to return to slots.  E.g:
  * Bot: What size?
  * User: large
  * Bot: What kind of crust?
  * User: What is your name?
  * Bot: My name is Mario.  What kind of crust?
  * User:  Cauliflower crust
  * Bot: Um. Okay.  What kind of sauce...



## NOTES:

* The Assistant doc has a getting started tutorial which is a really good start for a hello world bot.
* Our watson-assistant-learning-path also has a lot of this covered. Might be nice to sync the learning path \(needs updates\) and a workshop
* As you see above, there are many little things like digression, slots, context, varied responses, and on and on that can be quick examples and exercises.  Would be nice to collect these in a good format.  They are sometimes hidden in our code patterns.









