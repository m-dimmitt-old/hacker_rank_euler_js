### [Challenge Name: Project Euler #1: Multiples of 3 and 5](/contests/projecteuler/challenges/euler001)


<sub>This problem is a programming version of [Problem 1](https://projecteuler.net/problem=1) from [projecteuler.net](https://projecteuler.net/)</sub>

If we list all the natural numbers below $10$ that are multiples of $3$ or $5$, we get $3, 5, 6$ and $9$. The sum of these multiples is $23$.

Find the sum of all the multiples of $3$ or $5$ below $N$.   

solution1 constant function but still fails test case 2 and 3:
this is because the input is too large and crashes javascript. 
```javascript
function solve(n, scalor){
  const result =  
    scalor * ( 
      Math.floor( n / scalor ) * 
     (Math.floor( n / scalor ) +1)
    ) /2 
  return result 
}

function main() {
  var t = parseInt(readLine());
  for(var a0 = 0; a0 < t; a0++){
    var n = parseInt(readLine());
    let result = solve(n-1, 3) + solve(n-1, 5) - solve(n-1, 15)
    console.log(result)
  }
}
```

solution2 accepted for all answers: 
```javascript
var BigNumber = require('bignumber.js');
function main() {
  const t = parseInt(readLine());    
  for(var a0 = 0; a0 < t; a0++){ 
    const bigAnswer = calc(BigNumber(readLine()))
    console.log(bigAnswer.toString());
  }
}
function summation(targetValue, scalar){
  const  baseValue = BigNumber( Math.floor( ( targetValue.minus(1) ).dividedBy(scalar) ).toString() )
  const result = scalar
    .times(baseValue)
    .times(baseValue.plus(1))
    .dividedBy(2)
}
  
function calc(big_num){
  return summation(big_num, 3).plus(summation(big_num, 5)).minus(summation(big_num, 15))
}
```
