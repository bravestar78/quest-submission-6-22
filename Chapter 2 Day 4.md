# 1. Deploy a new contract that has a Struct of your choosing inside of it (must be different than Profile).
   * Create a dictionary or array that contains the Struct you defined.
   * Create a function to add to that array/dictionary.

```cadence
pub contract Practice {
  pub var vacation: {String : Details} 

  pub struct Details {
    pub var city: String 
    pub var state: String
    pub var miles: Int 
    pub var activity: String
    
    init(_city: String, _state: String, _miles: Int, _activity: String) {
      self.city = _city
      self.state = _state
      self.miles = _miles
      self.activity = _activity 
    }
  }

  pub fun addSpot(city: String, state: String, miles: Int, activity: String){
    let newSpot = Details(_city: city, _state: state, _miles: miles, _activity: activity)
    self.vacation[city] = newSpot
  }

  init() {
    self.vacation = {}
  }
}
```

# 4. Add a transaction to call that function in step 3.

```cadence
import Practice from 0x02

transaction(city: String, state: String, miles: Int, activity: String) {
  prepare(signer: AuthAccount){}

  execute {
    Practice.addSpot(city: city, state: state, miles: miles, activity: activity)
    log("We're Done")
  }
}
```

# 5. Add a script to read the Struct you defined.

```cadence
import Practice from 0x02

pub fun main (city: String): Practice.Details {
    log (Practice.vacation) 
    return Practice.vacation[city]!
}
```
