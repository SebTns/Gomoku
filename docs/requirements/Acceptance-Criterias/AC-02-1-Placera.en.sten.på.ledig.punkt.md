Given att ett parti pågår, det är spelarens tur och brädet visar det
When en spelare väljer en ledig punkt
Then Placeras spelarens sten på punkten
And den senast placerade stenen  markeras
And draget registreras med position, färg och nummer
And totala dragen ökas med ett
And återkopplingen sker inom 0,33 sekunder
