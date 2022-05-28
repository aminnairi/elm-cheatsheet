# elm-cheatsheet

```elm
-- Single line comment

{-- Multiline
    Verbose
    Comment --}


-- Strings


"string"


"Welcome, home!"


-- String concatenation


"Hello, " ++ "world!"

"Triumph " ++ "Street " ++ "Triple"


-- String equality


"Hello" == "World"


-- String inequality


"Linux" /= "Unix"


-- String superiority


"Love" > "Hate"


-- String inferiority


"Hatred" < "Forgiveness"


-- Integers
123


-- Integer addition

1 + 2


-- Integer soustracttion


1 - 2


-- Integer division


1 / 2


-- Integer euclidian division


1 // 2


-- Integer multiplication


1 * 2


-- Integer exponentiation


2 ^ 2


-- Integer equality

1 == 2


-- Integer inequality


1 /= 2


-- Integer superiority

1 > 2


-- Integer inferiotity

1 < 2


-- Floats


12.34

0.5678


-- Float addition


1.2 + 3.4


-- Float subtraction


1.2 - 3.4


-- Float division


1.2 / 3.4


-- Float euclidian division


1.2 / 3.4


-- Float exponentiation


1.2 ^ 3.4


-- Float equality


1.2 == 3.4


-- Float inequality


1.2 /= 3.4


-- Float superiority


1.2 > 3.4


-- Float inferiority


1.2 < 3.4


-- Booleans


True

False


-- Boolean short-circuit


True && False

True || False


-- Lists


[ 1 ]

[ 0.1, 0.2 ]

[ "first"
, "Second"
, "Third"
]


-- List concatenation


[ 1 ] ++ [ 2 ] -- [ 1, 2 ]

[ 3 ] ++ [ 4 ] ++ [ 5 ] -- [ 3, 4, 5 ]


-- List construction


1 :: [] -- [ 1 ]

1 :: 2 :: 3 :: [] -- [ 1, 2, 3 ]


-- List equality


[ 1, 2 ] == [ 2, 3 ]


-- List inequality


[ 1, 2 ] /= [ 2, 3 ]


-- List superiority


[ 1, 2 ] > [ 2, 3 ]


-- List inferiority


[ 1, 2 ] < [ 2, 3 ]


-- Records


{ pet = "Dog" }

{ eur = "Euros", value = 28974 }

{ username = "johndoe"
, age = 42
, administrator = True
}


-- Record equality


{ firstname = "John" } == { firstname = "Jane" }


-- Record inequality


{ firstname = "John" } /= { firstname = "Jane" }


-- Tuple


(1, "John")

("A", 32, False)


-- Tuple equality


(1, "Book") == (2, "Pen")


-- Tuple inequality


(1, "Book") /= (2, "Pen")


-- Tuple superiority


(1, "Book") > (2, "Pen")


-- Tuple inferiority


(1, "Book") < (2, "Pen")


-- Empty tuple


()


-- Constants


name =
  "Rex"
  
  
-- Record constant access

  
user =
  { name = "John"
  , age = 42
  }
  
userAge =
  user.age

userName =
  user.name
  

-- Functions


greetings name =
  "Greetings, " ++ name ++ "!"

greetings "You" -- "Greetings, You!"

hello firstname lastname =
  "Hello, " ++ firstname ++ ", " ++ lastname
  
hello "John" "DOE" -- "Hello, John DOE"


-- Anonymous functions


greetings =
  \firstname -> "Hello, " ++ firstname
    
greetings "John" -- "Hello, John"

welcome =
  \firstname lastname -> "Hello, " ++ firstname ++ " " ++ lastname
    
welcome "John" "DOE" -- "Hello, John DOE"


-- Functions ignored arguments


greet _ =
  "Hello, everyone!"
  
greet "John" -- "Hello, everyone!"
  
greeter _ _ =
  "Hello, you!"
  
greeter "John" "DOE" -- "Hello, you!"


-- Function tuple argument


greet (firstname, lastname) =
  "Hello, " ++ firstname ++ " " ++ lastname
  
  
greet ("John", "DOE") -- "Hello, John DOE"


-- Function record argument


myUser =
  { firstname = "Jane"
  , lastname = "DOE"
  }


greet user =
  "Hello, " ++ user.firstname
  
  
greet { firstname = "John", lastname = "DOE" } -- "Hello, John"

greet myUser -- "Hello, Jane"


-- Function record argument destructuring


greet { firstname } =
  "Hello, " ++ firstname
  
myUser =
  { firstname = "John"
  , lastname = "DOE" 
  }

greet { firstname = "Jane", lastname = "DOE" } -- "Hello, Jane"

greet myUser -- "Hello, John"


-- Record Update


user =
  { firstname = "John" }

updatedUser =
  { user | firstname = "Jane" } -- { user = "Jane" }


-- Record Access


.firstname { firstname = "John" } -- "John"

.age { firstname = "John", age = 42 } -- 42


-- Partial application


add first second =
  first + second
  
add 1 2 -- 3

increment = add 1

increment 2 -- 3


-- Condition


os =
  if kernel == "nt" then
    "Windows"
    
  else if kernel == "linux" then
    "Linux"
    
  else
    "Unix"
    
    
-- Pattern matching


administrator = True

message =
  case administrator of
    True ->
      "Authorized"
      
    False ->
      "Unauthorized"
      
      
-- Pattern matching default case


role = "USER"

message =
  case role of
    "ADMINISTRATOR" ->
      "Authorized"
      
    "USER" ->
      "Unauthorized"
      
    _ ->
      "Forbidden"
      
      
-- List pattern matching


friends = [ "John", "Jane", "Paul" ]

message =
  case friends of
    [] ->
      "No friends commented your article yet"
      
    [ first ] ->
      first ++ " commented your article"
      
    [ first, second ] ->
      first ++ " and " ++ second ++ " commented your article"
      
    first :: second :: others ->
      first ++ ", " ++ second ++ " and  more friends commented your article"
    
    
-- List pattern matching ignored rest


friends = [ "John", "Jane", "Paul" ]

message =
  case friends of
    [] ->
      "No friends commented your article yet"
      
    [ first ] ->
      first ++ " commented your article"
      
    first :: _ ->
      first ++ " and more friends commented your article"
    
    
-- Recursive function


fibonacci value =
  if value <= 1 then
    1
  
  else
    fibonacci (value - 1) + fibonacci (value - 2)
    
    
-- Loops


includedIn items item =
  case items of
    [] ->
      False
      
    current :: others
      if item == current then
        True
        
      else
        includedIn others item
        
        
includedIn ["banana", "apple"] "pear" -- False

includedIn ["banana", "apple"] "banana" -- True


-- Loops with state


countSimilarIn items count item =
  case items of
    [] ->
      count
      
    current :: others ->
      if current == item then
        countSimilarIn others (count + 1) item
        
      else
        countSimilarIn others count item
        
        
countSimilarIn ["a", "b", "c", "b"] 0 "b" -- 2

countSimilarIn ["a", "b", "c", "b"] 0 "a" -- 1

countSimilarIn ["a", "b", "c", "b"] 0 "e" -- 0
    
    
-- Chained functions

add first second =
  first + second
  
multiply first second =
  first * second
  
divide first second =
  first / second
  
toFahrenheit =
  add 32 (multiply 15 (divide 9 5))
  
toFahrenheit 15 -- 59
  
-- Piped functions


add first second =
  first + second
  
multiplyBy second first =
  first * second
  
divideBy second first =
  first / second
  
toFahrenheit celsius =
  celsius |> multiplyBy 9 |> divideBy 5 |> add 32
  
toFahrenheit 15 -- 59
  
  
-- Inverted piped functions
  
  
add first second =
  first + second
  
multiply first second =
  first * second
  
divideBy second first =
  first / second
  
toFahrenheit celsius =
  add 32 <| divideBy 5 <| multiply celsius 9
  
  
toFahrenheit 15 -- 59
  
  
-- Composed functions
  
  
addedBy second first =
  first + second
  
multipliedBy second first =
  first * second
  
divide second first =
  first / second
  
toFahrenheit =
  multipliedBy 9 >> dividedBy 5 >> addedBy 32
  
toFahrenheit 15 -- 59
    
    
-- Explicit typed functions


name : String
name =
  "John"
  
  
greet : String -> String
greet name =
  "Hello, " ++ name
  
  
welcome : String -> String -> String
welcome firstname lastname =
  "Welcome, " ++ firstname ++ " " ++ lastname
  
  
-- Type alias  


type alias User =
  { firstname : String
  , lastname : String
  , age : Int
  }
  
getLastname : User -> String
getLastname { lastname } =
  lastname
  
  
-- Custom type


type UserState = WaitingConfirmation | Confirmed | Deleted | Banned


type alias User =
  { email : String
  , state : UserState
  }


getWelcomeMessage user =
  case user.state of
    WaitingConfirmation ->
      "Please, confirm your email before signin"
      
    Confirmed ->
      "Connected!"
      
    Deleted ->
      "Account not found"
      
    Banned ->
      "This account has been banned"
      
      
-- Custom type with data


type UserState
  = WaitingConfirmation
  | Confirmed
  | Deleted String
  | Banned String


type alias User =
  { email : String
  , state : UserState
  }


getWelcomeMessage user =
  case user.state of
    WaitingConfirmation ->
      "Please, confirm your email before signin"
      
    Confirmed ->
      "Connected!"
      
    Deleted reason ->
      "Account deleted because " ++ reason
      
    Banned reason ->
      "This account has been banned because " ++ reason
      
      
-- Generic types


type Cart a =
  | Empty
  | Filled a
  
type alias Hat =
  { color : String
  , name : String
  , price : Float
  }
  
type alias HatCart =
  Cart Hat
  
getHatCartMessage : HatCat -> String
getHatCartMessage hatCart =
  case hatCart of
    Empty ->
      "No items in your hat cart"
      
    Filled hats ->
      "There are some hats in your cart"
  
type alias Jean =
  { color : String
  , length : Int
  , price : Float
  }

type alias JeanCart =
  Cart Jean
  
getJeanCartMessage : JeanCart -> String
getJeanCartMessage jeanCart =
  case jeanCart of
    Empty ->
      "There are no jeans in your cart"
      
    Filled jeans ->
      "There are some jeans in your cart"
      
      
-- Error handling


divide : Float -> Float -> Float
divide numerator denominator =
  numerator / denominator
  
firstResult : Float
firstResult =
  divide 1 2 -- 0.5
  
secondResult : Float
secondResult =
  divide 1 0 -- Infinity

safeDivide : Float -> Float -> Maybe Float
safeDivide numerator denominator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
thirdResult : Maybe Float
thirdResult =
  divide 1 2 -- Just 0.5

fourthResult : Maybe Float
fourthResult =
  divide 1 0 -- Nothing


-- Error handling default value


safeDivide : Float -> Float -> Maybe Float
safeDivide numerator denominator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
firstResult : Float
firstResult =
  Maybe.withDefault 0 (divide 1 2) -- 0.5
  
secondResult : Float
secondResult =
  Maybe.withDefault 0 (divide 1 0) -- 0


-- Error handling and continuation


safeDivide : Float -> Float -> Maybe Float
safeDivide numerator denominator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
add : Float -> Float -> Float
add first second =
  first + second
    
firstResult : Float
firstResult =
  divide 1 2
    |> Maybe.map (add 1)
    |> Maybe.withDefault 0 -- 1.5
    
secondResult : Float
secondResult =
  divide 1 0
    |> Maybe.map (add 1)
    |> Maybe.withDefault 0 -- 0
  
  
-- Error handling and maybe continuation


safeDivideBy : Float -> Float -> Maybe Float
safeDivideBy denominator numerator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
firstResult : Float
firstResult =
  10
    |> safeDivideBy 2
    |> Maybe.andThen (safeDivideBy 2)
    |> Maybe.withDefault 0 -- 2.5
    
secondResult : Float
secondResult =
  10
    |> safeDivideBy 0
    |> Maybe.andThen (safeDivideBy 2)
    |> Maybe.withDefault 0 -- 0
    
thirdResult : Float
thirdResult =
  10
    |> safeDivideBy 2
    |> Maybe.andThen (safeDivideBy 0)
    |> Maybe.withDefault 0 -- 0
    
    
-- Error handling pattern matching


safeDivideBy : Float -> Float -> Maybe Float
safeDivideBy denominator numerator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
message : String
message =
  case safeDivide 1 0 of
    Just result ->
      "There is a result"
      
    Nothing ->
      "Result is undefined"
    
    
-- Error handling with reason


safeDivideBy : Float -> Float -> Result Float String
safeDivideBy denominator numerator =
  if denominator == 0 then
    Err "Denominator cannot be equal to zero"
    
  else
    Ok (numerator / denominator)
    
message : String
message =
  case safeDivideBy 0 1 of
    Ok result ->
      "There is a result"
      
    Err reason ->
      "No result because " ++ reason
      
      
-- Import


import Html

Html.div [] [ Html.text "Hello, world!" ]


-- Granular import

import Html exposing (div, text)

div [] [ text "Hello, world!" ]


-- Renamed Import


import Html as H

H.text "Hello, world!"


-- Import and expose everything

import Html exposing (..)

div [] [ text "Hello, world!" ]


-- Import from another folder


import Html
import Page.Home      -- ./src/Page/Home.elm
import Page.NotFound  -- ./src/Page/NotFound.elm


-- Export


module Main exposing (main)

import Html


view =
  Html.text "Hello, world!"

main = view
  
  
-- Export everything


module Main exposing (..)

import Html

view =
  Html.text "Hello, world!"

main = view


-- Export from another folder


module Page.Home exposing (view) -- ./src/Page/Home.elm

import Html

view =
  Html.text "Home page"
```
