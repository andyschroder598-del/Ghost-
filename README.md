# Ghost (Sprachsteuerung für Spotify + TikTok-Chat vorlesen)

Ghost antwortet per Stimme (Knopf "Stimme" schaltet das an/aus). Auf manchen Handys wird das Mikrofon beim Sprechen kurz stumm, dann ist der nächste Befehl erst nach der Antwort möglich.

Das Logo (public/logo.jpg) leuchtet beim Zuhören, blitzt bei jeder Antwort auf und glüht, während der Chat vorgelesen wird.

Web-App fürs Handy. Du sprichst Befehle, die App steuert Spotify und liest dir den Chat deines TikTok-Lives vor.

## Was geht
- Spotify: Pause, Weiter, Nächstes/Voriges Lied, Lauter/Leiser, "Lautstärke 40", "Spiel Layla", "Spiel Playlist Workout"
- TikTok-Live: Chat vorlesen an/aus ("Chat vorlesen", "Chat aus")
- TikTok-Live selbst (starten, beenden usw.) lässt sich NICHT steuern, dafür gibt es keine offizielle Schnittstelle.

## Voraussetzungen
- Spotify Premium (Spotify erlaubt Fernsteuerung nur damit)
- Chrome (Android) oder Safari (iPhone). Mikrofon erlauben.
- Die Spotify-App muss auf dem Handy geöffnet sein, mindestens einmal einen Song gespielt haben.

## Einrichtung
1. **Spotify-App anlegen:** https://developer.spotify.com/dashboard → "Create app". Als Redirect-URI trägst du später die https-Adresse deiner Seite ein (Schritt 3). Notiere die Client-ID.
2. **Hosten (kostenlos reicht):** Lade den Ordner bei einem Node-Hoster hoch, z. B. Render, Railway oder Fly.io. Start-Befehl: `npm start`. Build-Befehl: `npm install tiktok-live-connector`. Du bekommst eine https-Adresse wie `https://meine-app.onrender.com/`.
3. **Redirect-URI:** Trage genau diese Adresse (mit `/` am Ende) im Spotify-Dashboard ein.
4. **Optional, empfohlen:** Setze die Umgebungsvariable `ACCESS_KEY` auf ein eigenes Passwort, damit Fremde den Chat-Anschluss nicht benutzen.
5. **Auf dem Handy:** Seite öffnen → Einstellungen → Client-ID, TikTok-Name (und Schlüssel) eintragen → Speichern → "Mit Spotify verbinden".
6. **Live starten**, dann in der App "TikTok-Chat verbinden" und "Chat vorlesen" sagen.

## Lokal testen (am PC)
```
npm install tiktok-live-connector
node server.js
```
Dann http://127.0.0.1:3000/ öffnen. Als Redirect-URI im Spotify-Dashboard `http://127.0.0.1:3000/` eintragen.

## Hinweise
- Die TikTok-Anbindung nutzt eine inoffizielle Bibliothek. Sie kann jederzeit nicht mehr funktionieren, und TikTok erlaubt solche Zugriffe nicht ausdrücklich. Nutzung auf eigene Verantwortung.
- Während die App vorliest, ignoriert sie das Mikrofon, damit sie sich nicht selbst Befehle gibt.
- Das Zuhören läuft nur, solange die Seite im Vordergrund offen ist und der Bildschirm an bleibt.
