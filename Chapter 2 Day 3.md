# 1. In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.
```cadence
pub fun main(){
    var favPeeps: [String] = ["Bam", "snomobeels", "JcubKittycat"]
    log(favPeeps) 
}
```
![image](https://user-images.githubusercontent.com/104528601/173406682-21225116-a667-4832-9b7a-31ed51bcd508.png)


# 2. In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!
```cadence
pub fun main() {
    var socials: {String: UInt64} = {"Facebook": 2 , "Instagram": 3, "Twitter": 5, "YouTube": 4, "Reddit": 0, "LinkedIn": 1}
}
```

# 3. Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type).
It gets rid of the optional type. If the value is nil, the program will panic, otherwise it will work just fine.
```cadence
pub fun main(): String { 
    var socials: {String: UInt64} = {"Facebook": 2 , "Instagram": 3, "Twitter": 5, "YouTube": 4, "Reddit": 0, "LinkedIn": 1}
    var favInstructor: {Int: String} = {1: "Bam", 2: "snomobeels", 3: "JcubKittyCat=8o)"}
    return favInstructor [1]!
}
```
![image](https://user-images.githubusercontent.com/104528601/173408876-2d4e5c25-f628-4cf3-9891-4bfd385f2cc2.png)

# 4. Using this picture below, explain...

  * What the error message means - the funtion returned a different type than it was expecting
  * Why we're getting this error - dictionaries return optional values, the function expected to return String type, not the optional String? type
  * How to fix it -  it can be fixed by either adding an optional operator - ```pub fun main(): String?{``` or a force unwrap operator - ```return thing[0x03]!```

