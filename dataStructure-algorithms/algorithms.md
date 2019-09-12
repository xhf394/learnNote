# Algorithms

#### isPalindrome?

```javascript
function isPalindrome(string) {
  //split string 
  let stringArr = string.toLowerCase().split('');
  let alphabetArr = 'abcdefghijklmnopqrstyvwxyz'.split('');
  
  //filter non letter
  let wordStringArr = stringArr.filter(word =>{
    return alphabetArr.indexOf(word) >= 0; 
  });

  //compare and return boolean result
  return wordStringArr.join('') === wordStringArr.reverse().join('');
}

isPalindrome("Madam, I'm Adam");
```

1. lower case all the letters;
2. filter unnecessary contents;
3. compare and return boolean.

#### CaesarCipher

```javascript
function caesarCipher(str, num) {
  //deal with num with mudul operator
  let numToPass = num % 26;
  
  //to lower case all the string text
  let strArr = str.toLowerCase().split('');
  let alphabet = 'abcdefghijklmnopqrstuvwxyz'.split('');
  
  //define new str
  let newStr = '';

  //locate index of each letter

  for( let i = 0; i < strArr.length; i++ ) {
    //deal with space;
    let char = strArr[i];
    if( char === ' '){
      newStr += char;
      continue;
    }
      //get current index
    let currentIndex = alphabet.indexOf(char);
    //get new index
    let newIndex = currentIndex + numToPass;
    if( newIndex > 25 ) newIndex = newIndex - 26;
    if( newIndex < 0 ) newIndex = 26 + newIndex;
    //if upper case
    //update to new str
    if(str[i] === str[i].toUpperCase()) {
      newStr += alphabet[newIndex].toUpperCase();
    }
    else {
      newStr += alphabet[newIndex];
    }
    console.log(i);
    
  }
  return newStr; 
}

caesarCipher('Zoo Keeper', 2);
```

1. cannot use forEach//for(let i of items), need to locate index of letter in str
2. need to deal with:  [***a. num > 26; b. newIndex > 26; c. space ; d. upper case letter***]()

