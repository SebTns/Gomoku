

### AC-04-01: Spelaren väljer färg före partistart

**Relaterade krav:** FR-04.1, FR-04.2, FR-04.3, FR-04.7

**Given** att spelaren befinner sig i konfigurationsvyn för ett nytt parti  
**And** partiet ännu inte har startat

**When** spelaren väljer svart eller vit

**Then** ska systemet tilldela spelaren den valda färgen  
**And** tilldela motståndaren den andra färgen  
**And** visa spelarens tilldelade färg innan det första draget kan göras  
**And** den spelare som har svart ska göra det första draget.


### AC-04-02: Ingen färg väljs före partistart

**Relaterade krav:** FR-04.2, FR-04.4, FR-04.7

**Given** att spelaren befinner sig i konfigurationsvyn för ett nytt parti  
**And** spelaren inte har valt någon färg

**When** spelaren startar partiet

**Then** ska systemet slumpmässigt tilldela spelaren svart eller vit  
**And** tilldela motståndaren den andra färgen  
**And** visa spelarens tilldelade färg innan det första draget görs.


### AC-04-03: Färgval i ett parti mot en vän

**Relaterade krav:** FR-04.2, FR-04.5

**Given** att ett parti mot en vän konfigureras  
**And** båda spelarna ännu inte har fått sina färger

**When** inbjudaren väljer svart eller vit

**Then** ska systemet tilldela inbjudaren den valda färgen  
**And** automatiskt tilldela motspelaren den andra färgen  
**And** båda spelarna ska ha olika färger.


### AC-04-04: Spelaren försöker ändra färg efter partistart

**Relaterade krav:** FR-04.6

**Given** att partiet har startat  
**And** spelaren redan har fått en färg

**When** spelaren försöker ändra sin färg

**Then** ska systemet förhindra ändringen  
**And** spelarens tilldelade färg ska förbli oförändrad.
