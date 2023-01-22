<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <form onsubmit="savelocal(event)"
    <label>Name</label>
    <input type="text" name="username" required/>
    <label>Email</label>
    <input type="email" name="emailId" required/>
    <label>Phone no</label>
    <input type="tel" name="phonenumber" required/>
    <button> Submit </button>
    <input type="button" v="delete">
</form>
<ul id='listofitems'></ul>
<script>
    function savelocal(event) {
        event.preventDefault();
        const name = event.target.username.value;
        const email = event.target.emailId.value;  
        const phonenumber = event.target.phonenumber.value;
        const obj = {
            name:name,
            email:email, 
            phonenumber:phonenumber

        }
        localStorage.setItem(obj.email, JSON.stringify(obj))
        showUserOnScreen(obj)
    }
        function showUserOnScreen(obj) {
            const parentElem = document.getElementById("listofitems")
            const childElement = document.createElement("li") 
            childElement.textContent =   obj.name + '-' + obj.email + '-' + obj.phonenumber
            parentElem.appendChild(childElement)
   
   const deleteButton= document.createElement('input')
   deleteButton.type = "button"
   deleteButton.value = "delete"
   deleteButton.oneclick = () => {
    localStorage.removeItem(obj.email)
    parentElem.removeChild(childElement)
   }
   childElement.appendChild(deleteButton)
   parentElem.appendChild(childElement)

   }
</script>
    </body>
</body>