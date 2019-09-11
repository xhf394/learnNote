# Algorithms

isPalindrome?

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



