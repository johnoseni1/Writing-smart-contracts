# How to write smart contracts


- ## write Comments in Solidity?

You can write single line comments and multi-line comments in solidity using // and /** ... */

samples like 

``` 
    // Single Line comment in solidity

    /* 
    Multi-line comment in solidity
    */
```

> A single-line comment is terminated by any unicode line terminator (LF, VF, FF, CR, NEL, LS or PS) in utf8 encoding. The terminator is still part of the source code after the comment, so if it is not an ascii symbol (these are NEL, LS and PS), it will lead to a parser error.


- ## what are NatSpec Comments in solidity?

Solidity contracts can have a special form of comments that form the basis of the Ethereum Natural Language Specification Format, also known as Natspec. Natspec is developed and promoted by Ethereum itself.

The Natspec commenting format follows the Doxygen notation style:

> - Single line commenting, with the use of three slashes ///
> - Multi-line commenting, with the use of double asterisk block /** ... */
> - Comments are included above library, interface, function , contract , function and constructor.

and this are how they look like : 

``` 
///  Natspec single line commenting

/**
Natspec multi-line
commenting
*/
```
## so let us get started and write at least a page of code

- Create a new directory and go inside it : ``$ mkdir Natspec-comms && cd Natspec-comms``

- Create a new Solidity file :`` $ nano natspec.sol``

- Paste the smart contract code below: : 

```pragma solidity ^0.5.0;
/// @title A sample contract to learn
/// @author John Oseni
/// @notice you can use this contract to learn alone
/// @dev Contract under development to enable floating point
contract Geometry {
    
    struct Triangle {
        uint side_a;
        uint side_b;
        uint hypothenuse;
    }
    
    /// @notice Math function to calculate square root
    /// @dev Not working with decimal numbers
    /// @param x The number to calculate the square root of
    /// @return y The square root of x
    function sqrt(uint x) internal pure returns (uint y) {
            uint z = (x + 1) / 2;
            y = x;
            while (z < y) {
                y = z;
                z = (x / z + z) / 2;
            }
        }
    
    /// @notice Calculate the hypothenuse length based on x and y
    /// @dev Not working as it returns integers and not float
    /// @param _a Side 1
    /// @param _b Side 2
    /// @return uint the hypothenuse length
    function calculateHypothenuse(uint _a, uint _b) public pure returns (uint) {
        return sqrt((_a * _a) + (_b * _b));
    }
    
    Triangle public my_triangle;
    
    /// @author John oseni
    /// @notice Enter the two legs of your right angle triangle
    /// @dev This function modifies the state of the variable `my_triangle` and use `calculateHypothenuse()` function
    /// @param _a Side 1
    /// @param _b Side 2
    /// @return string return to user a custom success message
    function createTriangle(uint _a, uint _b) public returns (string memory) {
        my_triangle = Triangle ({
            side_a: _a,
            side_b: _b,
            hypothenuse: calculateHypothenuse(_a, _b)
        });
        return "new triangle created";
    }
    
    
}
```

## ABI outputting

- Run the following command on the CLI of your editor: 

`` solc — devdoc natspec.sol ``

You should obtain the following output down here : 

``` 

{
  "author" : "John Oseni",
  "details" : "All function calls are currently implemented without side effects",
  "methods" :
  {
    "calculateHypothenuse(uint256,uint256)" :
    {
      "details" : "Not working as it returns integers and not float",
      "params" :
      {
        "_a" : "Side 1",
        "_b" : "Side 2"
      },
      "return" : "uint the hypothenuse length"
    },
    "createTriangle(uint256,uint256)" :
    {
      "author" : "John Oseni",
      "details" : "This function modifies the state of the variable `my_triangle` and use `calculateHypothenuse()` function",
      "params" :
      {
        "_a" : "Side 1",
        "_b" : "Side 2"
      },
      "return" : "string return to user a custom success message"
    }
  },
  "title" : "A sample contract to learn"
} 
```
