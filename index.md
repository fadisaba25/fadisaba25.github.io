<!doctype html> <html lang="de"> <head> <meta charset="utf-8"> <title>Serienbrief Intake</title> <style> body { font-family: sans-serif; margin: 2rem; } form { max-width: 640px; display: grid; grid-template-columns: max-content 1fr; gap: 0.5rem 1rem; align-items: center; } label { font-weight: 600; } input, textarea, select { width: 100%; padding: 0.4rem; font-size: 1rem; } button { grid-column: span 2; padding: 0.4rem; background-color: #e4e4e4; border: 1px solid #ccc; cursor: pointer; } table { margin-top: 2rem; border-collapse: collapse; width: 100%; } th, td { border: 1px solid #ccc; padding: 0.5rem; font-size: 0.9rem; } th { background: #f5f5f5; font-weight: bold; text-align: left; } .downloads { margin-top: 2rem; } </style> </head> <body> <h1>Serienbrief-Daten erfassen</h1> <form method="post"> <!-- Fehlermeldungen/Erfolgsnachrichten --> <div class="messages"> {% with flashes = get_flashed_messages(with_categories=true) %} {% if flashes %} {% for category, message in flashes %} <div class="msg {{ category }}">{{ message }}</div> {% endfor %} {% endif %} {% endwith %} </div>

<label for="platz">Platz</label>
<input type="text" id="platz" name="platz" required>

<label for="name_des_besitzers">Name des Besitzers</label>
<input type="text" id="name_des_besitzers" name="name_des_besitzers" required>

<label for="bootsnummer">Bootsnummer</label>
<input type="text" id="bootsnummer" name="bootsnummer" required>

<label for="adresse">Adresse</label>
<input type="text" id="adresse" name="adresse" required>

<label for="mail">Mail</label>
<input type="email" id="mail" name="mail" required>

<label for="telefonnummer">Telefonnummer</label>
<input type="text" id="telefonnummer" name="telefonnummer" required>

<label for="versichertes_oder_nicht">Versichertes oder nicht</label>
<input type="text" id="versichertes_oder_nicht" name="versichertes_oder_nicht" required>

<button type="submit">Eintrag speichern</button>

</form> <div class="downloads"> <h2>Downloads</h2> <ul> <li><a href="/download/ods">Seriendruck-Daten (ODS)</a></li> <li><a href="/download/xlsx">Daten als XLSX</a></li> <li><a href="/download/template">Serienbrief-Vorlage</a></li> </ul> </div> <table> <thead> <tr> <th>#</th> <th>Erfasst am</th> <th>Platz</th> <th>Name des Besitzers</th> <th>Bootsnummer</th> <th>Adresse</th> <th>Mail</th> <th>Telefonnummer</th> <th>Versichertes oder nicht</th> </tr> </thead> <tbody> {% for row in entries %} <tr> <td>{{ loop.index }}</td> <td>{{ row.erfasst_am }}</td> <td>{{ row.platz }}</td> <td>{{ row.name_des_besitzers }}</td> <td>{{ row.bootsnummer }}</td> <td>{{ row.adresse }}</td> <td>{{ row.mail }}</td> <td>{{ row.telefonnummer }}</td> <td>{{ row.versichertes_oder_nicht }}</td> </tr> {% else %} <tr> <td colspan="9">Noch keine Einträge</td> </tr> {% endfor %} </tbody> </table> </body> </html>
