Tasmota auf Zeitzone Berlin/Deutschland konfigurieren

<code>TimeSTD 0, 0, 10, 1, 3, 60
TimeDST 0, 0, 3, 1, 2, 120
timezone 99
time</code>


oder als praktischer Web Request für Massenkonfig aus der Shell:
<code>
curl http:///cm?cmnd=Backlog%20TimeSTD%200%2C%200%2C%2010%2C%201%2C%203%2C%2060%3B%20
TimeDST%200%2C%200%2C%203%2C%201%2C%202%2C%20120%3B%20timezone%2099%3B%20Latitude%2052.
31%3B%20Longitude%2013.24%3B%20time</code>
