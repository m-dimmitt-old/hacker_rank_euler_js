### [Challenge Name: Project Euler #4: Largest palindrome product](/contests/projecteuler/challenges/euler004)


<sub>This problem is a programming version of [Problem 4](https://projecteuler.net/problem=4) from [projecteuler.net](https://projecteuler.net/)</sub>

A palindromic number reads the same both ways. The smallest 6 digit palindrome made from the product of two 3-digit numbers is $101101 = 143 \times 707$.  
<br>
Find the largest palindrome made from the product of two 3-digit numbers which is less than $N$.  

Solution1:
```javascript
/////////////// ignore above this line ////////////////////

function main() {
    var t = parseInt(readLine());
    for(var a0 = 0; a0 < t; a0++){
        var n = parseInt(readLine());
        while(n-- > 0){
            if(isPalindrome(n) && isProduct(n)){
                console.log(n);
                break;
            }
        }
    }

}

const isPalindrome = (n) => (n + "").split("").reverse().join("") === (n + "")

const divisible = (n, i) =>  (n%i == 0) ? true : false 
const largeEnough = (n, i) =>  (n/i > 99) ? true : false 
const smallEnough = (n, i) =>  (n/i < 1000) ? true : false 
const checkOtherFactor = (n, i) => divisible(n, i) && largeEnough(n, i) && smallEnough(n, i) 

const isProduct = (n) =>{
    // set boundary value for a 3-digit number
    let i = 0;
    for(i = 100; i < 1000; i++){
        // check if the other factor is a 3-digit number
        if(checkOtherFactor(n, i)){
            return true;
        }
    }
    return false;
}
```
