# 1. Explain why we wouldn't call changeGreeting in a script.
We are unable to call changeGreeting in a script because the changeGreeting function was set up to change data.  
A script can only view data, so the changeGreeting function must be utilizied in a transaction.

# 2. What does the AuthAccount mean in the prepare phase of the transaction?
After you sign the transaction, this is the account that data is accessed from.

# 3. What is the difference between the prepare phase and the execute phase in the transaction?
Prepare phase allows you to access the information/data in your account.
Execute phase allows you to call funtions and change data on the blockchain.  
The execute phase isn't needed, as everything can be done in prepare, but it makes the code cleaner when used.

# 4. Additions to contract, transaction and script below
```cadence
pub contract HelloWorld {
    pub var greeting : String  // why not put = "Hello World"  here instead of having to initialize it below?

    pub var myNumber : Int

    pub fun updateMyNumber(newNumber: Int) {
        self.myNumber = newNumber
    }

    pub fun changeGreeting(newGreeting: String) { 
        self.greeting = newGreeting
    }
    
    init(){
        self.greeting = "Hello World"
        self.myNumber = 0
    }

}
```
```cadence
import HelloWorld from 0x01

transaction(newGreetingInput: String) {
  prepare(signer: AuthAccount){
  }
  execute{
    HelloWorld.changeGreeting(newGreeting: newGreetingInput)
  }
}
```
```cadence
import HelloWorld from 0x01

pub fun main() {
    log(HelloWorld.myNumber)
}
```
![image](https://user-images.githubusercontent.com/104528601/173135723-8919ae7a-76d9-45a8-88c4-b1164ccc8726.png)
