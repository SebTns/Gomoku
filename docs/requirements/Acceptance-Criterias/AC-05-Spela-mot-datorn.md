Given att spelaren är på startsidan
When spelaren väljer "Spela mot datorn" och en svårighetsgrad
Then startas ett parti mot datorn
And gör datorn sitt drag inom 3 sekunder
And turas spelaren och datorn om att göra drag
And kontrollerar efter varje drag om någon har fem i rad
And avslutas partiet när någon får fem i rad eller brädet blir fullt
And visas resultatet
