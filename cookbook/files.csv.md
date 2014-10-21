## CSV  

#### First Example - Client
Original description found here:  
http://stackoverflow.com/questions/14964035/how-to-export-javascript-array-info-to-csv-on-client-side  
````js
var data = [["name1", "city1", "some other info"], ["name2", "city2", "more info"]];
var csvContent = "data:text/csv;charset=utf-8,";
data.forEach(function(infoArray, index){

   dataString = infoArray.join(",");
   csvContent += index < infoArray.length ? dataString+ "\n" : dataString;

}); 


var encodedUri = encodeURI(csvContent);
window.open(encodedUri);


var encodedUri = encodeURI(csvContent);
var link = document.createElement("a");
link.setAttribute("href", encodedUri);
link.setAttribute("download", "my_data.csv");

link.click(); // This will download the data file named "my_data.csv".
````

#### Second Example - Meteor Specific 

````js
    var dataString = "";
    var csvContent = "data:text/csv;charset=utf-8,\n";
    csvContent += "timestamp, text, title\n";

    Posts.find().forEach(function(record, index){
       dataString = record.createdAt.toString() + "," +record.text.toString() + "," + record.title.toString();
       csvContent += index < Posts.find().count() ? dataString + "\n" : dataString;
    });

    var encodedUri = encodeURI(csvContent);
    window.open(encodedUri);
````

#### Third Example - Client  
Original description found here:  
http://stackoverflow.com/questions/17836273/export-javascript-data-to-csv-file-without-server-interaction 
````js
var A = [['n','sqrt(n)']];

for(var j=1; j<10; ++j){ 
    A.push([j, Math.sqrt(j)]);
}

var csvRows = [];

for(var i=0, l=A.length; i<l; ++i){
    csvRows.push(A[i].join(','));
}

var csvString = csvRows.join("%0A");
var a         = document.createElement('a');
a.href        = 'data:attachment/csv,' + csvString;
a.target      = '_blank';
a.download    = 'myFile.csv';

document.body.appendChild(a);
a.click();
````



#### Server  

````js
res.header("Content-Disposition", "attachment;filename="+name+".csv"); 
res.type("text/csv");
res.send(200, csvString);
````

  
