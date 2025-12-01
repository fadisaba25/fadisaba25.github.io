<div class="messages">
  {% with flashes = get_flashed_messages(with_categories=true) %}
    {% if flashes %}
      {% for category, message in flashes %}
        <div class="msg {{ category }}">{{ message }}</div>
      {% endfor %}
    {% endif %}
  {% endwith %}
</div>

<form method="post">
  {% for label, key in field_order %}
    <div>
      <label for="{{ key }}">{{ label }}</label>
      <input id="{{ key }}" name="{{ key }}" value="{{ request.form.get(key, '') }}" required>
    </div>
  {% endfor %}
  <button type="submit">Eintrag speichern</button>
</form>

<div class="downloads">
  <h2>Downloads</h2>
  <ul>
    <li><a href="{{ url_for('download_file', filename='Serienbrief_Daten.ods') }}">Seriendruck-Daten (ODS)</a></li>
    <li><a href="{{ url_for('download_file', filename='Serienbrief_Daten.xlsx') }}">Daten als XLSX</a></li>
    <li><a href="{{ url_for('download_file', filename='serienbriefKUNDEN-züblinMArina.odt') }}">Serienbrief-Vorlage</a></li>
  </ul>
</div>

<table>
  <thead>
    <tr>
      <th>#</th>
      <th>Erfasst am</th>
      {% for label, _ in field_order %}
        <th>{{ label }}</th>
      {% endfor %}
    </tr>
  </thead>
  <tbody>
    {% for entry in entries %}
      <tr>
        <td>{{ entry['id'] }}</td>
        <td>{{ entry['created_at'] }}</td>
        {% for _, key in field_order %}
          <td>{{ entry[key] }}</td>
        {% endfor %}
      </tr>
    {% else %}
      <tr>
        <td colspan="{{ 2 + field_order|length }}">Noch keine Einträge</td>
      </tr>
    {% endfor %}
  </tbody>
</table>
