# Write your own smart contract that contains 
  - two state variables: 
  - an array of resources, and a dictionary of resources. 
  - Add functions to remove and add to each of them. They must be different from the examples above.

```cadence
pub contract HardLesson {

  pub var arrayOfDifficulties: @[Difficulties]
  pub var dictionaryOfItems: @{Int:Description}

  pub resource Difficulties {
    pub let scale : Int
    init(){
      self.scale = 8
    }
  }

  pub resource Description {
    pub let listing : Int
    init () {
      self.listing = 1
    }
  }

  pub fun addDifficulty (difficulty: @Difficulties) {
    self.arrayOfDifficulties.append(<- difficulty) 
  }

  pub fun removeDifficulty (index: Int): @Difficulties {
    return <- self.arrayOfDifficulties.remove(at: index)
  }

  pub fun addItem (item : @Description) {
    let key = item.listing                          // why do we not need an access modifier here? //
    self.dictionaryOfItems[key] <-! item
  }

  pub fun removeItem (key: Int): @Description {
    let listing <- self.dictionaryOfItems.remove(key:key) ?? panic("There isn't an item here")
    return <- listing 
  }
  


  init(){
  self.arrayOfDifficulties <- []
  self.dictionaryOfItems <- {}
  }

}
```

