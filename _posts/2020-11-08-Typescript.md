2020-11-08-Typescript



Basic types



Addition types(the types Javascript don't have):

#### tuple

let x :[array with same or different types]

#### enum

a set of datatypes, you can name a list of numeric value with enum.

Q: which means 

enum Color {  Red = 1,  Green = 2,  Blue = 4,  } Can Black also be 2??? since Color[2] means "Grean", I guess not...



#### unknown & never & void & any



#### as 

type assertion, 

fnA(b as number)/(<number>b) means b is a number





ps: Number, String etc. is not the same with number, string... and better not to use them as a type...