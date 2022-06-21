# 1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

```cadence
pub contract Decisions {

    pub var dictionaryOfDecisions: @{String: Decision}

    pub resource Decision {
        pub let subject: String 
        init(_subject: String) {
            self.subject = _subject 
        }
    }

    pub fun getReference(key: String): &Decision {
        return (&self.dictionaryOfDecisions[key] as &Decision?)!
    }

    init() {
    self.dictionaryOfDecisions <- {
        "Bad": <- create Decision(_subject: "Go to work"),
        "Good": <- create Decision(_subject: "Learn Cadence")
        }
    }
}
```

# 2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

```cadence
import Decisions from 0x01

pub fun main(): String {
  let ref = Decisions.getReference(key: "Bad")
  return ref.subject 
}
```
![image](https://user-images.githubusercontent.com/104528601/174896891-70285411-ca17-497d-bb84-817dfacf793e.png)


# 3. Explain, in your own words, why references can be useful in Cadence.

Since Cadence is a resource oriented language, references help to add clarity and efficiency.  The code could get pretty hefty if it was mostly filled with moving resources around in order to return, access, or update it's fields.
