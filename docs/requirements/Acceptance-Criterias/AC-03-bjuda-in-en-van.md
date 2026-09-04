Given att spelaren är på startsidan och har ett synligt spelarnamn
When spelaren väljer Spela mot vän
Then skapas en inbjudningslänk inom 1 sekund
And visas länken med möjlighet att kopiera eller dela den
And visas ett väntläge för spelaren
And när motståndaren öppnar länken startar partiet med båda spelarna anslutna
And visas båda spelarnas namn för varandra
And syns ett drag hos motståndaren inom 0,5 sekunder
