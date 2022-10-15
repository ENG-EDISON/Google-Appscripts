# Google-Appscripts
This repository has very important App scripts to manipulate data in google sheets

onEdit(e) - runs when a user changes a value in a spreadsheet.

Create a function "function Addtimestamp(e)" thats takes the object e.

Create a variable **range_modified** to hold the range of object e.

const range_modified=e.range


**Print the A1 notation of the "range_modified" to the console**


console.log("A1 notation",range_modified.getA1Notation())

**print the name of the edited sheet on the console**


console.log("Sheet Name",range_modified.getSheet().getName())

**print the column of the edited sheet on the console**




console.log("Column NUmber",range_modified.getColumn())

**print the row of the edited sheet on the console**



console.log("Row Number",range_modified.getRow())

**test if the cell value was deleted(blank) then remove the time stamp**



  if(range_modified.getValue() == ""){
    range_modified.offset(0,1).setValue("")
    return}
    
    

**The change must be in column 3 so that we can add timestamp to the next column**


  if(range_modified.getColumn() !== 3)return
  
  
  
  **The change must occur in the "Inbound sheet only"**
  
  
  if(range_modified.getSheet().getName()!== "Inbound")return
  
  
  **Dont add the timestamp in row 1 since it contains the headers of the data**
  
  
  if(range_modified.getRow() < 2) return
  
  
  
  **Offset() is used to move from the current cell in steps define in the function**
  
  
  **offset(0,1) means move 0 step in row axis and 1 step in column axis**
  
  
  range_modified.offset(0,1).setValue(new Date())
 
