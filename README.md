<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="icon" href="https://i.pinimg.com/736x/4b/74/60/4b74602ca256953f4007a791056bb795.jpg" class="lin">
    <title>Book A Trip</title>

    <style>

body{
    margin:0;
    padding:0;
    min-height:100vh;
    background-image:url("https://i.pinimg.com/1200x/a8/98/c5/a898c50c82d729d3d9877b27a5d62c79.jpg");
    background-size:cover;
    background-position:center;
    background-repeat:no-repeat;
    background-attachment:fixed;
    font-family:'Franklin Gothic Medium','Arial Narrow',Arial,sans-serif;
}
.lin{
    width: 10px;
    height: 10px;
}
form{
    position:absolute;
    left:50px;
    top:40px;

    width:90%;
    max-width:400px;

    padding:20px;
    background:rgba(255,255,255,0.67);
    border-radius:20px;
}

input,
button{
    width:100%;
}

input{
    background-color:rgb(190,231,241);
}

button{
    background-color:rgb(114,203,238);
}

input,
button{
    border-radius:40px;
    width:300px;
    height:10px;
    margin:10px 0;
    margin-left:30px;
    padding:10px;
}

table{
    width:100%;
    margin-top:15px;
    border-collapse:collapse;
    background: none;
}

.colo{
    color:rgb(54,54,54);
}

td,
th{
    border-bottom:1px solid #ccc;
    padding:6px;
}

th{
    text-align:left;
}

    </style>

<script>

function save() {

    let cou = document.getElementById("cou").value;
    let date = document.getElementById("date").value;
    let detail = document.getElementById("detail").value;

    if (cou === "" || date === "" || detail === "") {
        alert("Please enter all information");
        return;
    }

    localStorage.setItem("country", cou);
    localStorage.setItem("date", date);
    localStorage.setItem("detail", detail);

    displayTable();

    document.getElementById("cou").value = "";
    document.getElementById("date").value = "";
    document.getElementById("detail").value = "";
}

function displayTable() {

    let table = document.getElementById("mytable");

    let country = localStorage.getItem("country");
    let date = localStorage.getItem("date");
    let detail = localStorage.getItem("detail");

    if (!country) {

        table.innerHTML = `
        <tr>
            <td>No Data</td>
            <td>No Data</td>
            <td>No Data</td>
        </tr>
        `;

        return;
    }

    table.innerHTML = `
    <tr>
        <th>The Country</th>
        <th>Date Of Trip</th>
        <th>Details</th>
    </tr>

    <tr>
        <td>${country}</td>
        <td>${date}</td>
        <td>${detail}</td>
    </tr>
    `;
}

function suprime() {

    localStorage.clear();

    document.getElementById("mytable").innerHTML = `
    <tr>
        <td>No Data</td>
        <td>No Data</td>
        <td>No Data</td>
    </tr>
    `;
}

window.onload = displayTable;

</script>

</head>

<body>

<form>

<h2 class="colo">Book A Trip</h2>

<label>The Country</label><br>

<input
type="text"
id="cou"
placeholder="Enter The Country..."
><br>

<label>The Date</label><br>

<input
type="text"
id="date"
placeholder="Date On..."
><br>

<label>Details</label><br>

<input
type="text"
id="detail"
placeholder="The Details..."
><br>

<input
type="button"
value="Save"
onclick="save()"
><br>

<input
type="button"
value="Clear All"
onclick="suprime()"
><br>

<h3>Book A Trip</h3>

<table id="mytable">

<tr>
<td>No Data</td>
<td>No Data</td>
<td>No Data</td>
</tr>

</table>

</form>

</body>

</html>
