# covid-cases
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css"
    integrity="sha384-xOolHFLEh07PJGoPkLv1IbcEPTNtaed2xpHsD9ESMhqIYd0nLMwNLD69Npy4HI+N" crossorigin="anonymous">
<link rel="stylesheet" href="index.css">
</head>
<body>
    <div>
        <h4>COVID-19 UPDATES</h4>
        <script src="script.js"></script>
    </div>
    <script src="script.js"></script>
</body>
</html>


script.js

var div = document.createElement("div")
div.style.textAlign = "center";

var input = document.createElement("input");
input.setAttribute("type", "text");
input.setAttribute("id", "country");

var button = document.createElement("button");
button.setAttribute("type", "button");
button.innerHTML = "Search";
button.addEventListener("click",foo);

let active = document.createElement("div");
active.setAttribute("Id", "Active");
let Recovered = document.createElement("div");
Recovered.setAttribute("Id", "Recover");
let Deaths = document.createElement("div");
Deaths.setAttribute("Id", "Deaths");

div.append(input,button,active,Recovered,Deaths);
document.body.append(div);

async function foo() {

    let res = document.getElementById("country").value;
    var url = `https://api.covid19api.com/dayone/country/${res}`;

    let result = await fetch(url);
    let result1 = await result.json();
    let index = result1.length-1;
    console.log(result1[index].Active);
    active.innerHTML =`total Active Cases:${result1[index].Active}`;

    console.log(result1[index].Recovered);
    Recovered.innerHTML =`total Recovered Cases:${result1[index].Recovered}`;

    console.log(result1[index].Deaths);
    Deaths.innerHTML =`total Deaths Cases:${result1[index].Deaths}`;







}








index.css



div{
    size: 40px;
    text-align: center;
background-color: cornflowerblue;

}
button{
    background-color: rgb(227, 62, 227);
    color: brown;
    padding-left: 2px;

    
}
h4{

    font-size: 60px;
    font-weight: 100;
    color: rgba(24, 63, 69, 0.427);
    font-style: italic;
    font-feature-settings: "c2pc";
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    background-color: rgb(239, 230, 182);
}



div#Active{
    font-size: 40px;
color: red;
}
div#Recover{
    font-size: 30px;
    color: chartreuse;
}
div#Deaths{
    font-size: 20px;
    color: orange;
}
