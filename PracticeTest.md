# Practice Test

 Return the product of the arguments 
```powershell
function q1($var1,$var2,$var3,$var4) { 
   $var1 * $var2 * $var3 * $var4
}
```
Search the 2 dimensional array for the first occurance of key at column index 0
       and return the value at column index 9 of the same row.
       Return -1 if the key is not found.
```powershell
   function q2($arr,$rows,$cols,$key) {
   $x = 0 
      foreach($i in $arr)
      {
        if($arr[$x][0] -eq $key){
        return $arr[$x][9]}
      $x = $x + 1 
      }
      return -1
      }
   ```
In a loop, prompt the user to enter positive integers one at time.
       Stop when the user enters a -1. Return the maximum positive
       value that was entered."
```powershell
function q3 {
      $wee = 0
      $yolo = @()
        while ( $wee -ne -1 ) {
        $wee = Read-Host "Positive Number: "
          $yolo += $wee
        }
          $yolo | Measure-Object -Maximum | select -ExpandProperty Maximum
}
```
Return the line of text from the file given by the $filename
	   argument that corresponds to the line number given by $whichline.
	   The first line in the file corresponds to line number 0."
```powershell
function q4($filename,$whichline) {
    (Get-Content $filename)[$whichline]
}
```
Return the child items from the given path sorted
       ascending by their Name
```powershell
function q5($path) {
        Get-ChildItem $path | sort
}
```
Return the sum of all elements provided on the pipeline
```powershell
function q6 {
    $sum = 0
    $input | foreach { $sum += $_ }
    $sum 
}
```
Return only those commands whose noun is process
```powershell
function q7 {
    Get-Command -noun process
}
```
Return the string 'PowerShell is ' followed by the adjective given
	   by the $adjective argument
```powershell
function q8($adjective) {
    "Powershell is $adjective"
}
```
Return `$true when the given argument is a valid IPv4 address,
	   otherwise return `$false. For the purpose of this function, regard
	   addresses where all octets are in the range 0-255 inclusive to
	   be valid.
```powershell
function q9($addr) {
        if ( $addr -as [IPAddress] ) { return $true }
        else {
        return $false }
}
```
Return $true if the contents of the file given in the
       $filepath argument have changed since $lasthash was
       computed. $lasthash is the previously computed SHA256
       hash (as a string) of the contents of the file.
```powershell
function q10 ($filepath,$lasthash) {
       $memes = (Get-Filehash $filepath | Select-Object -ExpandProperty hash)
       if ( $memes -eq $lasthash )
       { return $false }
       else
       { return $true }
       
}
```
