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






# Partie 2 : Express

# Question 2.1

(ta réponse)