# Day 3 💀💀💀😆
## 💀

Functions in powershell only exist during an individual powershell session/script. obviously

In powershell, calling a function creates its own separate pipeline
  - functions are stored in the 'function' PSDrive
    - since they are a PSDrive we can list what functions are in powershell 

to delcare/create a basic function, the syntax is as follows:
```powershell
function function1 {<function code>}

#here is hello world 
function Hello-World { 'Hello World!!!' }
```
call the function by using the function's name 

to delcare/create a function with a parameter to pass, here's the syntax:
```powershell
function <functionName> ($parameterName) { <function code goes here}
#NOTE - The parameter you would be passing WILL be a variable when passed to the function,
#     therefore we must declare it as a variable when creatig the function
```
Here's an example of a parameter being passed to a function
```powershell
function basic-param ($value) {
  if ($value) {
    Write-Host "The parameter os $value" -ForeGroundColor Green -NoNewLine
  }
  else {
    Write-Host "There is no parameter being passed" -ForegroundColor Red
  }
}
```
`basic-param 42` is how you declare parameter

Parameters must be separated by commas
```powershell
function <functionname> ($,parameter1>, $<parameter2> {function code}
```
To declare a function that contains a switch/parameter, heree's the syntax:
```powershell
function <func name> {
  param(
    [switch]
    $switchparam
  )
  <functioncode>
#A switch parameter operates off boolean logic, either on or off
```
# ACTIVITY
## ACTIVITY 1: Create Functions

Write a function that returns the Ordinal date of the current date.
```powershell 
function ree {
$wee = (Get-Date | Select-Object -ExpandProperty Year) 
$yee = (Get-Date | Select-Object -ExpandProperty Dayofyear)
write-host "$wee-$yee"      
}
```

Create a function that takes a number(n) as an argument and returns the square(n^2) of the number
```powershell
function math ($yut) {
    Write-Host ($yut * $yut)
}
```
Create a function that takes three (3) arguments and returns the product of the arguments.
```powershell
function prod ($ree, $yee, $wee) {
    Write-Host ($ree * $yee * $wee)
}
```
