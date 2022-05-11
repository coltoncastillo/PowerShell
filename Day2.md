# Day 2 💀 😆 🤑
in powershell, parenthesis means "do this first"
```powershell
get-item c:\windows\system32\cmd.exe | select-object -property name 
#gets the name 
#or, with parenthesis
(get-item C:\windows\system32\cmd.exe).name
```
output 1: 
```
Name
---
cmd.exe
```
output 2:
```
cmd.exe
```
---
hash table: powershell's version of a dictionary

```powershell
$hashtable = @{}
#declaring a hash table
#powershell automatically sorts hashtables or somem shit
$hashtable = [ordered]@{}
#this makes it so that it doesnt automatically sort, keeps the values in the order you put them in
$orderedhashtable = [ordered]@{}
$notorderedhastable = @{ Game = "Minecraft ; Publisher = "Mojang" }
#calling on $notorderedhashtable will result in a name column and a value column, with game and publisher being name and
$notorderedhashtable["Game"]
#output would display Minecraft
$notorderedhashtable.name or $notorderedhashtable.values
#will print name or value 
$notorderedhashtable.cost = "'$26.95"
#will add a value in the hash table for cost that = 26.95
$notorderedhashtable["Cost"]=""'$1,000"
#this changes this value of cost to 1,000 
#or
$notorderedhashtable.cost="'$1,000"
#which is a lot easier
```
<p align="center">
<img src="https://i.kym-cdn.com/entries/icons/mobile/000/029/963/inside_you_there_are_two_wolves.jpg" alt="drawing" width="400"/>
</p>

```powershell
get-PSProvider
#idk this shows providers which tells powershell what kind of data to use or something 
```
## Activities
### ACTIVITY: Reverse Arrays
- Create an array containing a range with a random starting and stopping point. 
    - The starting point will be a random number from -10 through 0. The ending point will be a random number from 1 through 20.
```powershell
$start = Get-Random -Minimum -10 Maximum 1
$stop = Get-Random -Minimum 1 -Maximum 20
$array = $start..$stop
$array
#or
$array = (Get-Random -Minimum -10 -Maximum 1)..(Get-Random -Minimum 1 -Maximum 20)
```
- Create a variable that contains the contents of the array in reverse
```powershell 
$reversed = $array[($array.length-1)..0]
$reversed
```

### ACTIVITY: Arrays & Hash Tables
Create two empty hash tables with the following names:
  1. employee1
  2. employee2
```powershell
$employee1 = [ordered]@{}
$employee1.First = "Mary"
$employee1["Last"] = "Hopper
$employee1.ID = "001"
$employee1["Job"] = "Software Developer"

$employee2 = @{Same shit as first employee}
```
 - Now add a new key called Username which holds a contraction of the employee’s first initial then last name then ID. (i.e. mhopper001)
 ```powershell
 [
 ```
  - Mary got promoted to "Software Lead" so the job key for Mary needs to be changed to "Software Lead"
 ```powershell
 $employee1.Job = "Software Lead"
 ```
  - Create a new hash table called "employee3" that contains the following values with the respective keys.
 ```powershell
 $employee3 = [ordered]@{same shit}
 ```
  - Add a new key called "Status" that holds the values:
```powershell
$employee1.Status = "Management"
same shit
same shit 
```

<p align="center">
<img src="https://i.kym-cdn.com/photos/images/newsfeed/001/500/667/619.jpg" alt="drawing" width="400"/>
</p>
---

#### Pipeline
```powershell
function fruit-output {
  Write-Output "Apple"
  Write-Output "Orange"
  Write-Output "Banana"
  Write-Output "Pear"
  }
  #doing fruit-output will return apple orange banana pear with newlines separating
  ```
```powershell
$myblock = { Get-Service | Format-Table Name, Status }
#to run the scriptblock 
& myblock
```
```powershell
$a = 1
$b = { 1 + 1 }
$a += &$b
#or
$a += invoke-command $b
```
```powershell
Get-Service | sort-object -property status
#gets all services sorted by the property of "status" (running, stopped, etc)
```
```powershell
Get-Process | Sort-Object StartTime | Select-Object -Last 10 | Format-Table ProcessName, StartTime
#lists 10 longest running processes
#will throw an error, since "idle" does not have a start time. To filter it out:
Get-Process | where-object processname -ne "idle" | Sort-Object StartTime | Select-Object -Last 10 | Format-Table ProcessName, StartTime
```
```powershell
#measure the sum of elements in an array using ForEach-Object
#$array = 1, 2, 3, 4, 5
$sum = 0
$array | ForEach-Object { $sum +=; $sum }
$sum
```
```powershell 
#using Get-Unique 
1,2,3,1,2,3,1,2,3,1,2,3 | Get-Unique
#using Measure-Object 
Get-ChildItem | Measure-Object Length -Average -Maximum -Minimum -Sum
```
<p align="center">
<img src="https://memegenerator.net/img/instances/76959275.jpg" alt="drawing" width="400"/>
</p>

```powershell
#create test file and snapshot of directory
'What is the answer to lif, the universe, and everything?' > test.txt
$before = Get-ChildItem
#modify test file and new snapshot 
'42' > test.txt
$after = Get-ChildItem
#use comapare-object $before $after -Property Length, Name
```

## Activity
### The Pipeline Activity
  1. Display the start time of the earliest and latest running processes
    
  ```powershell
  Get-Process | Where-Object{$_.StartTime} | `
  Measure-Object -Property StartTime -Minimum -Maximum | `
  Select-Object -Property Minimum, Maximum
  ```
  2. Identify a cmdlet that returns the current date and time then using this cmdlet and Select-object, display only the current day of the week
```powershell
Get-Date | Select-Object DayofWeek
```
  3. Identify a cmdlet that displays a list of installed hotfixes.
```powershell
Get-Hotfix
```
  4. Extend the expression to sort the list by install date, and display only the install date and hotfix ID.
```powershell
Get-Hotfix | sort-object InstalledOn | Select-Object HotfixID, InstalledOn
```
  5. Extend the expression further, but this time sort by description, include description, hotfix ID, and install Date.
```powershell
Get-Hotfix | Sort-Object Description | Select-Object Description, HotFixID, InstalledOn
```
<p align="center">
<img src="https://media.makeameme.org/created/activity-time-great.jpg" alt="drawing" width="300"/>
</p>

---
```powershell
$my_car = New-Object Object
Add-Member -MemberType NoteProperty -Name Color -Value 'Green-Blue Camo' -InputObject $my_car
Add-Member -Me NoteProperty -in $my_car -Na Make -Value Jeep 
Add-Member -InputObject $my_car NoteProperty Model "Renegade"
$my_car | Add-Member NoteProperty Cab "45 seats"
Add-Member -in $my_car -me ScriptMethod -na TreeWheelDrive -value {"Upside-Down, Backwards, and on Fire..."}
Add-Member -in $my_car -me ScriptMethod -na GiveMeSpeech -value {"I'm sorry, mom."}
Add-Member -in $my_car -me ScriptMethod -na MakeItSnow -value {"WWIIIIII Era? Nice try, sack of fucking horse shit bitch cunt."}
```
## Activity
### Custom Object Activity

  1. Create a custom object that contains information about the host system using the following 
      - Win32_ComputerSystem
      - Win32_BIOS
      - Win32_OperatingSystem
      - Win32_LogicalDisk
 ```powershell
$pp = New-Object Object
Add-Member -MemberType NoteProperty -Name ComputerName -Value "WIN-OPS" -InputObject $pp
Add-Member -MemberType NoteProperty -Name OperatingSystem -Value "Windows" -InputObject $pp
Add-Member -MemberType NoteProperty -Name Version -Value "10.0.19041" -InputObject $pp
Add-Member -MemberType NoteProperty -Name Manufacturer -Value "SeaBIOS" -InputObject $pp
Add-Member -MemberType NoteProperty -Name Disks -Value "C:" -InputObject $pp
#Could have done it like 
$computerinfovariable = Get-WmiObject Win32_ComputerSystem 
osinfovariable = asdaf
etc
etc
etc
$myobject | add-member -membertype noteproperty -name computername -value $computerinfovariable.Name
$myobject | add-member -membertype noteproperty -name operatingsystem -value $osinfovariable.caption
same thing for version
same thing for manufacturer
same thing for Disks $.__path
```
Use the cmdlet ***Get-WmiObject*** to obtain the needed information

---

```powershell
$text = "Your account username is ACE4495"
$pattern = '([A-F]){3}(\d{4})'
$text -match $pattern
```

```powershell
#display only the services wwith the status of 'running
Get-Service | Where-Object{$_.Status -eq 'running'}
Get-Service | Where-Object{$_.Status -like 'runn'}
Get-Service | Where-Object{$_.Status -match 'run'}
```
```powershell
#show text files with sizes greater than 100
Get-ChildItem *.txt | Where-Object{$_.Length -gt 100}
```
```powershell
#Display all processes whose company begins with 'micro'
Get-Process | Where-Object{$_.Company -like 'micro*'} | Format-Table Name, Description, Company
```

## Activity
### Comparison and Condition Activity
  1. Find and extract the model number from the provided lines of text. 
      - If there isn’t a model number then display to the user that a model number wasn’t found
  2. Check both lines for model numbers and report individually the line and model number if found.
  3. Use the following variables for your script
      - $line1 = "Do you have model number: MT5437 for john.doe@sharklasers.com?"
      - $line2 = "What model number for john.doe@sharklasers.com?"
```powershell
$line1 = "Do you have model number: MT5437 for john.doe@sharklasers.com?"
$line2 = "What model number for john.doe@sharklasers.com?"
$pattern = '([A-Z]){2}(\d{4})'
switch ($pattern) {
  { $line1 -match $_ } {
      $line1 -match $pattern | out-null
      $model = $matches[0]
      "yes the model number is $model" }
  { $line2 -match $_ } {
      $line2 -match $pattern | out-null
      $model = $matches[0]
      "yes the model number is $model" }
  { $line1 -notmatch $_ } {
      "There is no model number in line1" }
   { $line2 -notmatch $_ } {
      "There is no model number in line2" }
 }
#or
$line1,$line2 | foreach-object { if($_ -match "[A-Z]{2}[0-9]{4}") {$Matches.Values } else { 'Model not found' } }

```
---
## Activity 
### RETARDED ACTIVITY: Looping & Iteration
1. Part 1
  - Use an array to iterate and open the following
    - Notepad
    - MS Edge
    - MSpaint
  - Query the processes
  - Kill the processes from PowerShell
2. Part 2
  - Use an array to iterate and open the following
    - Notepad
    - MS Edge
    - MSpaint
  - Query the processes
  - Save the processIDs to a text file called procs.txt
  - Iterate through ProcessIDs in the text file and kill them
3. Part 3
  - Use an array to iterate and open the following
    - Notepad
    - MS Edge
    - MSpaint
  - Query the processes and display only the following information in order by process ID
    - Process ID
    - Process Name
    - The time the process started
    - The amount of time the process has spent on the processor
    - The amount of memory assigned to the process

```powershell
#This is about to be retarded








```
