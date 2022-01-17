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
///  Natspec single line comment

/**
Natspec multi-line
comment 
*/
```


