Given att spelaren är på startsidan, har valt Starta nytt parti och ser konfigurationsvyn
When spelaren bekräftar inställningarna med Starta
Then skapas ett parti med status pågående
And tilldelas färgerna enligt spelarens val
And skapas ett tom bräda av vald storlek inom 3 sekunder
And framgår det att svart gör första draget
