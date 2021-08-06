# Search Photos using Unsplash API

We can get the Images from Unsplash server to our website by calling the unsplash photo search API.

# Steps for calling unsplash Photo Search API 
<ul>
  <li>Go to website <a href="https://unsplash.com/developers">Unsplash Developers</a></li>
  <li>Here click on <b>Register as a Developer</b></li>
  <img src="Images/screen1.png">
  <li>On the new window provide basic details like <b>First name, Last name, Email address, Username</b> and <b>Password</b></li>
  
  
  <img src="Images/screen2.png">
  <li>After clicking on <b>Join</b>, you will have to create one application.</li>
  
  <img src="Images/screen4.png">
  <br>
  
  <li>Accept all the <b>Guidelines</b></li>
  <img src="Images/screen5.png">
  <br>
  
  <li>Provide the application name and what does the application do.</li>
  <img src="Images/screen6.png">
  <br>
  
  <li>Once the creation is done, you will get your <b>Access Key</b> and <b>Secret Key</b>. Copy the <b>Access Key</b>, you will use this as <b>Client Id</b></li>
  
  <img src="Images/screen3.jpg">


<li>Use this URL: "https: //api.unsplash.com /search/photos/?client_id="+ clientId+"&query="+query (Enter the Access key as Client Id)</li>

<li>You can use this Sample Code</li>
</ul>
    
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photo Search</title>
    <link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Lato">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    </head>

    <style>
    body{
    background-position: center;
    background-image: url("");
    min-height: 100%;
    }

    button {
    background-color: Blue;
    color: white;
    padding: 10px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 100%;
    opacity: 0.9;
    border-radius: 4px;
    }

    button:hover {
    background-color: indigo;
    border-radius: 4px;
    opacity: 40;
    }

    input[type=text]{
    width: 100%;
    padding: 15px;
    margin: 5px 0 22px 0;
    display: inline-block;
    border: none;
    background: #f1f1f1;
    border-radius: 4px;
    }

    textarea {
    width: 100%;
    height: 210px;
    padding: 15px;
    box-sizing: border-box;
    border: 2px solid #ccc;
    border-radius: 4px;
    background-color: #f8f8f8;
    font-size: 16px;
    resize: none;
    }

    label {
    color: White;
    font-size: 22px;
    text-align: center;
    text-decoration: none;
    text-transform: uppercase;
    letter-spacing: 2px;
    text-shadow: 2px 2px 5px Blue;
    font-family: Arial, Helvetica, sans-serif;
    }
    </style>

    <body>

        <div class="w3-container w3-content w3-center w3-padding-64" style="max-width:800px" id="Embed-Tool">
        <input type="text" id="search" placeholder="Search Photos">
        <button onclick="SearchPhotos()">Search</button>
        <div class="w3-container w3-black" style="padding:60px 16px" id="result">
        </div>
        </div>
    </body>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script>

    function SearchPhotos() {
        $("#result").empty()

        let clientId = "N6tI4SdOZpxwuDWFC5IGMoR2NulKE_p2e0uiW4Njw6g";

        let query = document.getElementById("search").value;

        let url = "https://api.unsplash.com/search/photos/?client_id="+ clientId+"&query="+query;

        fetch(url)
        .then(function (data) {
        return data.json();
        })
        .then(function (data) {
        console.log(data);
        data.results.forEach(photo => {
        let result = `
        <img width=100% height=auto src="${photo.urls.regular}" >
        <button><a target="_blank" href="${photo.links.download}">Download</a></button><br><br><br>
        `;
        $("#result").append(result);
        });
        })
    }
    </script>



    </html>

The unslash image search API will provide the following output:
<br>
<img src="Images/screen7.png">
