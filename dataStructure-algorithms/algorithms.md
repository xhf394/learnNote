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

#### Reversed Word

```javascript
function reverseWords(string){
  //split string to words array
  let wordsArr = string.split(' ');

  //new array to store reversed words
  let reversedWordsArr = [];

  //loop each word, reversed
  wordsArr.forEach( word => {
    let reversedWord = '';
    for( i = word.length - 1; i >=0; i-- ){
      reversedWord += word[i];
    }
    reversedWordsArr.push(reversedWord);
  })
  //return 
  return reversedWordsArr.join(' '); 
}

reverseWords('Coding JavaScript'); //gnidoC tpircSavaJ
```

1. as reversed. ***created reversed word array && reversed single word string***
2. **loop word backwards**
3. push into new array 

#### Reverse Array In Place

```javascript
function reverseArrayInPlace(array) {
  //loop whole array
  for( let i = 0; i < array.length / 2; i++ ) {
    //temporary store i
    let tempItem = array[i];
    //update i to array.length - 1
    array[i] = array[array.length - 1 - i];
    //update array.length - 1 to temporary item
    array[array.length - 1 - i] = tempItem;
  }
  //return reversed array (update on the original one )
  return array;
}

reverseArrayInPlace([1, 2, 3, 4, 5, 6, 7, 8]);
```

**Import Tips**

1. make change based on original array; ==create a temporary store item==
2.  ***==don't forget minus i==*** when get the index of the reverse target
3. deal with the length of the loop



#### Mean, Median, Mode



```javascript
function getMean(array) {
  let sum = 0;
  for( let item of array ) {
    sum += item;
  }
  return sum / array.length;
}

function getMedian(array) {
  //sort array 
  let sortArr = array.sort(function(a, b) { return a - b});
  //get median number
  let midIdx;
  //odd length
  if(array.length % 2 !== 0) {
    midIdx = Math.floor(array.length / 2);
    return sortArr[midIdx];
  }
  //even length
  else {
    let midIdx1 = array.length / 2 - 1;
    let midIdx2 = array.length / 2;
    return (sortArr[midIdx1] + sortArr[midIdx2]) /2;
  }
}

function getMode(array) {
  //calculate frequency
  let numObj = {};
  let numMode = [];

  array.forEach( num => {
    if(!numObj[num]) numObj[num] = 0;
    numObj[num] ++
  })

  //deal with numObj, find out maxfrequency num
  let maxFrequency = 0;
  for( let num in numObj) {
    if(numObj[num] > maxFrequency) {
      numMode = [num];
      maxFrequency = numObj[num];
    }
    else if(numObj[num] === maxFrequency) {
      numMode.push(num);
    }
  }
  //if all numbers are the same frequency
  if(numMode.length === Object.keys(numObj).length) numMode = [];

  return numMode; 

}

function meanMedianMode(array) {
  return {
    mean: getMean(array),
    median: getMedian(array),
    mode: getMode(array)
  }
}
meanMedianMode([9,10,23,10,23,9]);
```

**Import Tips**

