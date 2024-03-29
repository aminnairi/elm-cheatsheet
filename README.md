# elm-cheatsheet

## Requirements

- [Node](https://nodejs.org/en/)
- [NPM](https://nodejs.org/en/)
- [NPX](https://nodejs.org/en/)

## Command-line

```bash
# Install Elm locally
npm install --save-dev elm

# initialize a new Elm folder
npx elm init

# Interactive Elm Shell
npx elm repl

# Development server
npx elm reactor

# Development server listening to a wanted port
npx elm reactor --port 8000

# Compile to index.html (with JavaScript)
npx elm make src/Main.elm

# Compile to index.html for development environments
npx elm make --debug src/Main.elm

# Compile to index.html for production environments
npx elm make --optimize src/Main.elm

# Compile to JavaScript
npx elm make --output index.js src/Main.elm

# Compile to HTML (with JavaScript)
npx elm make --output elm.html src/Main.elm

# Install a package from https://package.elm-lang.org/
npx elm install elm/parser
```

## Syntax

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


-- Integer


123


-- Signed integer


-456


-- Hexadecimal integer lower case notation


0xab12


-- Hexadecimal integer upper case notation


0xAB12


-- Exponential integer notation


1e10


-- Signed exponential integer notation


-2e8


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


-- Float


12.34


-- Signed float


-7.69


-- Exponential float notation


1.2e3


-- Signed exponential float notation


-4.2e5


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
  
  
-- Record value access

  
user =
  { name = "John"
  , age = 42
  }
  
userAge =
  user.age

userName =
  user.name
  
  
-- Record value access alternative

  
user =
  { name = "John"
  , age = 42
  }
  
userAge =
  .age user

userName =
  .name user
  

-- Function definition


greetings name =
  "Greetings, " ++ name ++ "!"
  
getRectangleArea height width =
  height * width
  
join first second third =
  first ++ ", " ++ second ++ ", " ++ third
  
  
-- Function call


greetings "You" -- "Greetings, You!"

getRectangleArea 3 4 -- 12
  
join "Red" "Green" "Blue" -- "Red, Green, Blue"


-- Anonymous function definition


greetings =
  \name -> "Greetings, " ++ name ++ "!"
  
getRectangleArea =
  \height width -> height * width
  
join =
  \first second third -> first ++ ", " ++ second ++ ", " ++ third


-- Functions ignored arguments


greet _ =
  "Hello, everyone!"
  
greet "John" -- "Hello, everyone!"
  
greeter _ _ =
  "Hello, you!"
  
greeter "John" "DOE" -- "Hello, you!"


-- Function multiple instruction


doubleSum first second =
  let
    doubledFirst =
      first * 2
    
    doubledSecond =
      second * 2
  in
    doubledFirst + doubledSecond 
    
    
doubleSum 2 4 -- 12


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
  { firstname = "John"
  , lastname = "DOE",
  , email = "johndoe@domain.com"
  }

updatedUser =
  { user | firstname = "Jane" }
  
-- { firstname = "Jane", lastname = "DOE", email = "johndoe@gmail.com" }


-- Record multiple fields update


user =
  { firstname = "John"
  , lastname = "DOE",
  , email = "johndoe@domain.com"
  }

updatedUser =
  { user
    | firstname = "Jane"
    , email = "janedoe@domain.com"
  }
  
-- { firstname = "Jane", lastname = "DOE", email = "janedoe@gmail.com" }
  

-- Record Access


.firstname { firstname = "John" } -- "John"

.age { firstname = "John", age = 42 } -- 42


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
    
    
-- Explicit type


name : String
name =
  "John"
  
  
greet : String -> String
greet name =
  "Hello, " ++ name
  
  
welcome : String -> String -> String
welcome firstname lastname =
  "Welcome, " ++ firstname ++ " " ++ lastname
  
  
-- Function partial application


add : Int -> Int -> Int
add first second =
  first + second
  
increment : Int -> Int
increment value =
  add 1 value
  
inc : Int -> Int
inc =
  add 1
  
firstResult : Int
firstResult =
  increment 2 -- 3
  
secondResult : Int
secondResult =
  inc 2 -- 3
  
  
-- Type alias  


type alias User =
  { firstname : String
  , lastname : String
  , age : Int
  }
  
myUser : User
myUser =
  { firstname = "John"
  , lastname = "DOE"
  , age = 42
  }
  
getLastname : User -> String
getLastname { lastname } =
  lastname
  
getLastname myUser -- "DOE"
  
  
-- Custom type


type UserState = WaitingConfirmation | Confirmed | Deleted | Banned

type alias User =
  { email : String
  , state : UserState
  }

getWelcomeMessage : User
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
      
myRegistredUser : User
myRegistredUser =
  { email = "john@doe.com"
  , state = Confirmed
  }
  
getWelcomeMessage myRegistredUser -- "Connected!"
  
myUnregistredUser : User
myUnregistredUser =
  { email = "jane@doe.com"
  , state = WaitingConfirmation
  }
  
getWelcomeMessage myUnregistredUser -- "Please, confirm your email before signin"
  
myBannedUser : User
myBannedUser =
  { email = "jane@doe.com"
  , state = Banned
  }
  
getWelcomeMessage myBannedUser -- "This account has been banned"
  
myDeletedUser : User
myDeletedUser =
  { email = "jane@doe.com"
  , state = Deleted
  }
      
getWelcomeMessage myDeletedUser -- "Account not found"

      
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
      "Deleted because " ++ reason
      
    Banned reason ->
      "Banned because " ++ reason
      
myRegistredUser : User
myRegistredUser =
  { email = "john@doe.com"
  , state = Confirmed
  }
  
getWelcomeMessage myRegistredUser -- "Connected!"
  
myUnregistredUser : User
myUnregistredUser =
  { email = "jane@doe.com"
  , state = WaitingConfirmation
  }
  
getWelcomeMessage myUnregistredUser -- "Please, confirm your email before signin"
  
myBannedUser : User
myBannedUser =
  { email = "jane@doe.com"
  , state = Banned "Bad behavior in chat"
  }
  
getWelcomeMessage myBannedUser -- "Banned because Bad behavior in chat"
  
myDeletedUser : User
myDeletedUser =
  { email = "jane@doe.com"
  , state = Deleted "Account timeout registration exceeded"
  }
      
getWelcomeMessage myDeletedUser -- "Deleted because Account timeout registration exceeded"
      
      
-- Generic types


type Cart a =
  | Empty
  | Filled a
  
type alias Hat =
  { color : String
  , name : String
  , price : Float
  }
  
getHatCartMessage : Cart Hat -> String
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

getJeanCartMessage : Cart Jean -> String
getJeanCartMessage jeanCart =
  case jeanCart of
    Empty ->
      "There are no jeans in your cart"
      
    Filled jeans ->
      "There are some jeans in your cart"
      
      
-- Error handling


safeDivide : Float -> Float -> Maybe Float
safeDivide numerator denominator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
firstResult : Maybe Float
firstResult =
  safeDivide 1 2 -- Just 0.5

secondResult : Maybe Float
secondResult =
  safeDivide 1 0 -- Nothing
  
  
-- Error handling pattern matching


safeDivideBy : Float -> Float -> Maybe Float
safeDivideBy denominator numerator =
  if denominator == 0 then
    Nothing
    
  else
    Just (numerator / denominator)
    
message : String
message =
  case safeDivideBy 1 0 of
    Just result ->
      "There is a result"
      
    Nothing ->
      "Result is undefined"
    
    
-- Error handling with reason


safeDivideBy : Float -> Float -> Result String Float
safeDivideBy denominator numerator =
  if denominator == 0 then
    Err "Denominator cannot be equal to zero"
    
  else
    Ok (numerator / denominator)
    
firstResult : Result String Float
firstResult =
  safeDivideBy 1 2 -- Ok 0.5

secondResult : Result String Float
secondResult =
  safeDivideBy 1 0 -- Err "Denominator cannot be equal to zero"


-- Error handling with reason and pattern matching

    
safeDivideBy : Float -> Float -> Result String Float
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

main =
  Html.div [] [ Html.text "Hello, world!" ]


-- Granular import


import Html exposing (div, text)

main =
  div [] [ text "Hello, world!" ]


-- Renamed Import


import Html as H

main =
  H.text "Hello, world!"


-- Import and expose everything


import Html exposing (..)

main =
  div [] [ text "Hello, world!" ]


-- Import from another folder


import Html

import Page.Home      
-- ./src/Page/Home.elm

import Page.NotFound  
-- ./src/Page/NotFound.elm


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


module Page.Home exposing (view)
-- ./src/Page/Home.elm

import Html

view =
  Html.text "Home page"
  
  
-- Core Modules (useless to import)

import Array
-- https://package.elm-lang.org/packages/elm/core/latest/Array

import Basics
-- https://package.elm-lang.org/packages/elm/core/latest/Basics

import Bitwise
-- https://package.elm-lang.org/packages/elm/core/latest/Bitwise

import Char
-- https://package.elm-lang.org/packages/elm/core/latest/Char

import Debug
-- https://package.elm-lang.org/packages/elm/core/latest/Debug

import Dict
-- https://package.elm-lang.org/packages/elm/core/latest/Dict

import List
-- https://package.elm-lang.org/packages/elm/core/latest/List

import Maybe
-- https://package.elm-lang.org/packages/elm/core/latest/Maybe

import Platform
-- https://package.elm-lang.org/packages/elm/core/latest/Platform

import Platform.Cmd
-- https://package.elm-lang.org/packages/elm/core/latest/Platform-Cmd

import Platform.Sub
-- https://package.elm-lang.org/packages/elm/core/latest/Platform-Sub

import Process
-- https://package.elm-lang.org/packages/elm/core/latest/Process

import Result
-- https://package.elm-lang.org/packages/elm/core/latest/Result

import Set
-- https://package.elm-lang.org/packages/elm/core/latest/Set

import String
-- https://package.elm-lang.org/packages/elm/core/latest/String

import Task
-- https://package.elm-lang.org/packages/elm/core/latest/Task

import Tuple
-- https://package.elm-lang.org/packages/elm/core/latest/Tuple
  
  
-- The Elm Architecture


module Main exposing (main)


{-- IMPORTS --}


import Browser
import Html exposing (Html)
import Html.Events


{-- TYPES --}


type alias Model =
    { counter : Int }
    
    
type Message
    = Increment
    | Decrement
    
    
{-- MODEL --}


initialModel : Model
initialModel =
    { counter = 0 }


{-- UPDATE --}


update : Message -> Model -> Model
update message model =
    case message of
        Increment ->
            { model | counter = model.counter + 1 }

        Decrement ->
            { model | counter = model.counter - 1 }
            
            
{-- VIEW --}


viewDecrementButton : Html Message
viewDecrementButton =
  Html.button
    [ Html.Events.onClick Decrement ]
    [ Html.text "Decrement" ]
    
    
viewIncrementButton : Html Message
viewIncrementButton =
  Html.button
    [ Html.Events.onClick Increment ]
    [ Html.text "Increment" ]
    
    
viewCounter : Int -> Html Message
viewCounter counter =
  counter
    |> String.fromInt
    |> Html.text


view : Model -> Html Message
view { counter } =
  Html.div
    []
    [ viewDecrementButton
    , viewCounter counter
    , viewIncrementButton
    ]
    
    
{-- MAIN --}


main : Program () Model Message
main =
    Browser.sandbox
        { init = initialModel
        , view = view
        , update = update
        }
        
        
-- Flags


module Main exposing (main)


import Browser
import Html exposing (Html)


type alias Model =
  { message : String }
  

type Message = None


type alias Flags = String
  

initialModel : Flags -> (Model, Cmd Message)
initialModel flags =
  ( Model flags, Cmd.none )
  
  
  
update : Message -> Model -> (Model, Cmd Message)
update message model =
  (model, Cmd.none)
  
  
view : Model -> Html Message
view { message } =
  Html.text message
  
  
main : Program Flags Model Message
main =
  Browser.element
    { init = initialModel
    , update = update
    , view = view
    , subscriptions = always Sub.none
    }
    
    
-- Outgoing ports


port module Main exposing (main)


import Browser
import Html exposing (Html)
import Html.Events


port vibrate : () -> Cmd message
port copyToClipboard : String -> Cmd message


type alias Model =
  ()
  

type Message
  = Vibrate
  | CopyToClipboard String
  

initialModel : () -> (Model, Cmd Message)
initialModel _ =
  ( (), Cmd.none )
  
  
update : Message -> Model -> (Model, Cmd Message)
update message model =
  case message of
    Vibrate ->
      (model, vibrate ())
      
    CopyToClipboard text ->
      (model, copyToClipboard text)
  

view : Model -> Html Message
view _ =
  Html.div
    []
    [ Html.button
      [ Html.Events.onClick Vibrate ]
      [ Html.text "Vibrate" ]
    , Html.button
      [ Html.Events.onClick (CopyToClipboard "Hello from Elm!") ]
      [ Html.text "Copy" ] 
    ]
    

subscriptions : Model -> Sub Message
subscriptions _ =
    Sub.none
  
main : Program () Model Message
main =
  Browser.element
    { init = initialModel
    , update = update
    , view = view
    , subscriptions = subscriptions
    }


-- Incoming ports


port module Main exposing (main)


import Browser
import Html exposing (Html)


port onWindowResized : (Int -> message) -> Sub message
port onFullScreen : (() -> message) -> Sub message
port onPasteFromClipboard : (String -> message) -> Sub message


type alias Model =
  { message : String }
  

type Message
  = WindowResized Int
  | Paste String
  | FullScreen


initialModel : () -> (Model, Cmd Message)
initialModel _ =
  ( Model "Nothing", Cmd.none )
  
  
update : Message -> Model -> (Model, Cmd Message)
update message model =
  case message of
    FullScreen ->
      ({ model | message = "Fullscreen" }, Cmd.none)
      
    Paste text ->
      ({ model | message = "Copied text " ++ text }, Cmd.none)

    WindowResized size ->
      ({ model | message = "Window size is now " ++ String.fromInt size }, Cmd.none)
  

view : Model -> Html Message
view { message } =
  Html.text message
    

subscriptions : Model -> Sub Message
subscriptions _ =
    Sub.batch
      [ onWindowResized WindowResized
      , onFullScreen (always FullScreen)
      , onPasteFromClipboard Paste
      ]
  
main : Program () Model Message
main =
  Browser.element
    { init = initialModel
    , update = update
    , view = view
    , subscriptions = subscriptions
    }

```

## JavaScript API

```javascript
// Initialization

Elm.Main.init({
  node: document.getElementById("elm")
});

// Flags

Elm.Main.init({
  node: document.getElementById("elm"),
  flags: "Hello, world!"
});

// Elm Outgoing ports

const app = Elm.Main.init({
  node: document.getElementById()
});

app.ports.vibrate.subscribe(() => {
  window.navigator.vibrate(100);
});

app.ports.copyToClipboard.subscribe(text => {
  window.navigator.clipboard.writeText(text).catch(error => {
    console.error(error);
  });
});

// Elm incoming ports

const app = Elm.Main.init({
  node: document.getElementById()
});

window.addEventListener("fullscreenchange", () => {
  if (document.fullscreen) {
    app.ports.onFullScreen.send();
  }
});

window.addEventListener("resize", () => {
  app.ports.onWindowResized.send(window.clientX);
});

window.addEventListener("paste", () => {
  window.navigator.clipboard.readText().then(text => {
    app.ports.onPasteFromClipboard.send(text);
  }).catch(error => {
    console.error(error);
  });
});
```
