# 1. In words, list 3 reasons why structs are different from resources.


Structs are simply containers of data.  Resources are similar in that they are also containers, 
however they are differnt than structs in that they are 
 - more secure 
 - impossible to copy 
 - cannot be lost 
 - and cannot be created outside of a contract

# 2. Describe a situation where a resource might be better to use than a struct.

When the resource that you created is meant to be unique and secure, like when creating non fungible tokens.

# 3. What is the keyword to make a new resource?

<- Create

# 4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

No, Resources can only be created inside of a contract.

# 5. What is the type of the resource below?

@Jacob

# 6. I Spy 4 things wrong with this code. Please fix them.

```cadence
pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): Jacob { // there is 1 here   || @Jacob
        let myJacob = Jacob() // there are 2 here       || <- create Jacob()
        return myJacob // there is 1 here               || return <- myJacob
    }
}
```
