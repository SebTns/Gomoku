Given att spelaren är i konfigurationssidan och partiet inte har startat
When spelaren väljer svart eller vit
Then tilldelas spelaren den valda färgen
And tilldelas motståndaren den andra färgen
And visas båda spelarnas färger i konfigurationssidan
And framgår det att svart gör första draget
And låses färgvalet när partiet startar
And går att skilja åt pjäser på enbart färg
