# Day 1

backtick (`) is escape character

<# creates a comment block #>

quotes mean keep it as a string, no quotes mean interpret how it is, like a number

```powershell
write-host "write the #2"
```
- output: write the #2

regex is only used in single quotes

```powershell
Get-ExecutionPolicy
Set-ExecutionPolicy Unrestricted
Set-ExecutionPolicy Unrestricted -Scope 
```
```powershell
get-help Get-Help -Online
```
- only works in a GUI environment
```powershell
update-help -force 
update-help -force -ErrorAction
get-childitem -Path C:\windows -Filter *.exe -Recurse -Name
```

| Python        | Bash          | PwrSh     |
|:-------------:|:-------------:|:---------:|
| Inst          | var           | $var      |
| Call          | $var          | $var      |

```powershell
$var = 1
$var = 2
$var + $var2
```
output: 3
```powershell
write-host "$var + $var2"
```
output: 1 + 2

```powershell
$env:SystemRoot
```
output : C:\Windows\system32
---
- $$ = variable for last token used 
- $? = if the last command was executed properly
- $_ = the current object in the current pipeline
- $error
- $true
- $false
- $args = all the arguments passed to a function
- $input = the enumeration of all the objects passed to a function
- $null = nothing 
---
typecasting
```powershell
([string]$zero).GetType()
#
.GetType().name
#idk if this right
```

## Activities
### ACTIVITY: Find Cmdlets
0. Update-Help  

1. Which cmdlets deal with the viewing/manipulating of processes?
    - Get-Process, Stop-Process, Wait-Process, Debug-Process, Start-Process
        - Get-WmiObject win32_process, Remove-WmiObject woin32_process, Get-CimInstance win32_process, etc
2. Display a list of services installed on your local computer.
    - Get-Service
3. What cmdlets are used to write or output objects or text to the screen?
    - Write-Host, Write-Debug, Write-Output, Write-Progress, Write-Warning, Out-Default, Out-Host
4. What cmdlets can be used to create, modify, list, and delete variables?
    - Set-Variable, Remove-Variable, Clear-Variable, Get-Variable, New-Variable
5. What cmdlet can be used, other than Get-Help, to find and list other cmdlets?
    - Get-Command
6. Find the cmdlet that is used to prompt the user for input.
    - Read-Host
    
### ACTIVITY: Running Cmdlets

1. Display a list of running processes.
    - Get-Process
2. Display a list of all running processes that start with the letter "s".
    - Get-Process -name s*
3. Find the cmdlet and its purpose for the following aliases:

    - gal: Get

    - dir: Get-ChildItem

    - echo: Write-Output

    - ?: Where-Object

    - %: ForEach-Object

    - ft: Format-Table

4. Display a list of Windows Firewall Rules.
    - Show-NetFireWallRule
5. Create a new alias called "gh" for the cmdlet "Get-Help"
    - Set-Alais gh Get-Help
    

### ACTIVITY: Variables

1. Create a variable called "var1" that holds a random number between 25-50.
    - $var1 = Get-Random -Minimum 25 -Maximum 50 
2. Create a variable called "var2" that holds a random number between 1-10.
    - $var2 = Get-Random -Minimum 1 -Maximum 10 
3. Create a variable called "sum" that holds the sum of var1 and var2.
    - $sum = $var1 + $var2
4. Create a variable called "sub" that holds the difference of var1 and var2.
    - $sub = $var1 - $var2 
5. Create a variable called "prod" that holds the product of var1 and var2.
    - $prod = $var1 * $var2
6. Create a variable called "quo" that holds the quotient of var1 and var2.
    - $quo = $var1 / $var2 
7. Replace the variables in text with their values in the following format:
    
"var1" + "var2" = "sum"

8. Replace the variables in text with their values in the following format:

"var1" - "var2" = "sub"

Replace the variables in text with their values in the following format:

"var1" * "var2" = "prod"

Replace the variables in text with their values in the following format:

"var1" / "var2" = "quo"

---

### Array
- a data type that has multiple values inside 
```powershell
[array]$array1 = "this", "is", '1', "thing"
#declaring array $array1
#output is This is 1 thing with each item on its own line
$arrray3 = @()
#created an empty array
[array]$array4 = ""
#also created an empty array
```

```powershell
get-content path\blah.txt | forEach-Object { if ($_ -as [IPAddress] ) {Write-Host "$_ is valid " )}
#testing IPs or somet shit like that
```
```powershell
$multi [$var1]$var2[$var3] = 2
```
```powershell
$stringArray = 'string' * 20
#output: stringstringstringstringstringstringstringstring (x25)
```
$stringarray= @('string',$null) * 20
#prints 'string' 20 times on a newline each time
[array]$notarray = @('string') * 20 














