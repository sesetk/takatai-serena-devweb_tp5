# TP5 - Serveur HTTP et Express (Node.js)

# Partie 1 : serveur HTTP natif

# Question 1.1
Les en-têtes de la réponse HTTP renvoyée par le serveur sont :

Connection: keep-alive
Date: Mon, 21 Sep 2026 04:07:45 GMT
Keep-Alive: timeout=5
Transfer-Encoding: chunked


# Question 1.2
Les en-têtes de la réponse HTTP renvoyée par le serveur après avoir remplacer la fonction requestListener() : 

Connection: keep-alive
Content-length: 20
Content-type: application/json
Date: Mon, 21 Sep 2026 04:15:24 GMT
Keep-alive: timeout=5

Par rapport à la question 1.1 deux en-têtes sont apparu, "Content-type: application/json" est apparu qui signifie que le serveur indique au navigateur que le contenu de la réponse est du JSON et "Content-Length: 20". Et "transfert encoding" a disparu.

# Question 1.3
La page localhost met du temps à charger et le terminal renvoie cette réponse :

  errno: -4058,
  code: 'ENOENT',
  syscall: 'open',
  path: 'C:\\Users\\TAKATAI\\Desktop\\serena\\dev_web\\devweb-tp5\\index.html'

# Question 1.4
Le code de l'erreur affichée par la console est 'ENOENT'.
Cette erreur indique qu'un composant du chemin d'accès spécifié n'existe pas, ici le fichier index.html n'est pas encore créé.

# QSuestion 1.5
async function requestListener(_request, response) {
  try {
    const contents = await fs.readFile("index.html", "utf8");
    response.setHeader("Content-Type", "text/html");
    response.writeHead(200);
    return response.end(contents);
  } catch (error) {
    console.error(error);
    response.writeHead(500);
    return response.end("<html><p>ERROR : 50</p></html>");
  }
}

# Question 1.6
Ces commandes ont rajoutées le dossier "node_modules", le fichier "package-lock.json" et "depencies" dans mon fichier package.json.

# Question 1.7
La différence entre http-dev et http-prod est déjà le programme qui lance le serveur, -dev utilise nodemon et -prod utilise node et ensuite -dev redémarre automatiquement dès qu'on modifie le code alors -prod non.

# Question 1.8
http://localhost:8000/index.html le code renvoyé pour cette route est 200, la page affiche le contenu de index.html.

http://localhost:8000/random.html le code renvoyé pour cette route est 200 la page affiche 64.

http://localhost:8000/ le code renvoyé pour cette route est 404 la page affiche l'erreur 404: not found.

http://localhost:8000/dont-exist le code renvoyé pour cette route est 404 la page affiche l'erreur 404: not found.



# Partie 2 : Express

# Question 2.1
express : https://expressjs.com/
http-errors : https://github.com/jshttp/http-errors
loglevel : https://github.com/pimterry/loglevel
morgan : https://github.com/expressjs/morgan

# Question 2.2/2.3
Les 3 routes fonctionnent.

http://localhost:8000/ affiche la page index.html son status code est 304 et l'en-tête de la réponse http renvoie :
    accept-ranges: bytes
    cache-control: public, max-age=0
    connection: keep-alive
    date:   Mon, 21 Sep 2026 06:40:32 GMT
    etag: W/"3ac-1a0c277e8e4"
    keep-alive: timeout=5
    last-modified: Mon, 21 Sep 2026 05:37:13 GMT
    x-powered-by: Express

http://localhost:8000/index.html affiche également la page index.html son status code est 304 et renvoie :
    accept-ranges: bytes
    cache-control: public, max-age=0
    connection: keep-alive
    date: Mon, 21 Sep 2026 06:40:50 GMT
    etag: W/"3ac-1a0c277e8e4"
    keep-alive: timeout=5
    last-modified: Mon, 21 Sep 2026 05:37:13 GMT
    x-powered-by: Express

http://localhost:8000/random/5 affiche une page avec une liste de  5 nombres son status code est 200 et renvoie :
    connection: keep-alive
    content-length: 80
    content-type: text/html; charset=utf-8
    date: Mon, 21 Sep 2026 06:41:09 GMT
    etag: W/"50-C1mjaTCXfI7/+GRNbM0Tb65q5lI"
    keep-alive: timeout=5
    x-powered-by: Express


Les nouvelles en-têtes des réponses fournies par Express qui sont nouvelles par rapport au serveur HTTP sont :
- X-Powered By: Express
- ETag : W/50-...
- Content-type: text/html; charset=utf-8
- Content-Length: 80

# Question 2.4
L'événement listening se déclenche quand le serveur a fini de s'installer à l'emplacement précis qu'on lui a donné et qu'il est maintenant ouvert pour recevoir les connexions des utilisateurs.

# Question 2.5
L'option qui redirige / vers /index.html est "index".

# Question 2.6 
Les codes HTTP sur le fichier style.css sont : 
- 304 avant de forcer le rafrîchissement
- 200 après avoir forcer le rafraîchissement

# Question 2.7
Oui l'affichage change bien entre le mode -dev et -prod.