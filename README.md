# Darts.sk

Ondrej Šesták

5ZYI31

## Stručný opis projektu
Stránka bude slúžiť ako portál pre hráčov šípiek, budú sa na nej môcť prihlásiť na turnaj, prezerať si výsledky z predošlých turnajov, vidieť svoje štatistiky, alebo štatistiky iných hráčov.  
Ľudia, ktorí organizujú turnaje ich môžu vypísať na stránku a následne zapísať ich priebeh.

## Role v projekte
- Návšteník - môže si pozerať výsledky turnajov, štatistiky hráčov a môže požiadať o registŕaciu.
- Registrovaný používateľ - má svôj vlastný profil, kde sú vidieť jeho štatistiky a turnaje, ktorých sa zúčastnil. Môže sa prihlasovať na nasledujúce turnaje.  
- Organizátor turnaja - môže požiadať o vypísanie turnaja na stránku, následne má právomoc upravovať informácie o turnaji ako dátum, kapacitu atď.. Po ukončení turnaja zapíše jeho priebeh.
- Admin - prijíma/zamieta žiadosti o registráciu alebo vypísanie turnaja. Môže banovať účty, alebo rušit turnaje.

## Prípady použitia podľa rolí
Návštevník si prezerá ukončené turnaje.  
Návštevník požiada o registráciu.  
Používateľ si pozrie svoje štatistiky.  
Používateľ sa prihlási na turnaj.  
Organizátor požiada o vypísanie turnaja.  
Organizátor zmení dátum turnaja.  
Organizátor zapíše pribeh ukončeného turnaja.  
Admin prijme registráciu hráča.  
Admin vypíše turnaj na stránku.

## Plánované entity
- Player - hráč, ktorý sa zúčastnuje turnajov  
Atribúty: Id_player
- Tournament - turnaj, ktorý sa skladá z viacerých zápasov  
Atribúty: Id_tournament
- Tournament_Participation - pomocná entita na prepojenie turnajov a hráčov  
Atribúty: Id_part, Id_player, Id_tournament
- Match - zápas medzi dvoma hráčmi  
Atribúty: Id_match, Id_tournament, Player1, Player2
- Leg - 1 kolo zápasu  
Atribúty: Order, Id_match
- Throw - 1 hod v rámci kola  
Atribúty: Order, Order_leg, Id_player

## Vzťahy medzi entitami
- Player Tournament M:N - Na 1 turnaj sa môže prihlásiť viacero hráčov a 1 hráč sa môže prihlásiť na viacero turnajov 
- Tournament Match 1:N - turnaj pozostáva z viacero zápasov
- Match Leg 1:N - v každom zápase sa hrá niekoľko kôl
- Leg Throw 1:N - v každom kole je odohratých niekoľko hodov

## Hlavné stránky aplikácie
- Registračný formulár - slúži na vypísanie údajov a požiadanie o vytvorenie účtu na stránke
- Profil hráča - slúži na zobrazenie základných štatistík hráča ako priemerný počet bodov na 3 hody, alebo koľko šípiek priemerne potrebuje na ukončenie kola. Pod štatistikami bude zoznam turnajov, ktorých sa hráč zúčastnil a jeho umiestnenie v nich.
- Zoznam aktuálnych turnajov - stránka, na ktorej sa dá prihlásiť na turnaj. Pri turnaji bude vypísané kto ho organizuje, dátum, čas a miesto konania.
- História turnajov - zoznam turnajov, ktoré už boli ukončené 
- Prehľad zápasov v turnaji - pavúkový graf už odohratého turnaja. Bude sa dať prejsť na samostatnú stránku každého zo zápasov.
- Priebeh zápasu - stránka, na ktorej bude vidno každý hod konkrétneho zápasu.

## Rozdelenie funkcionality
Základné funkcie sú prihlasovanie na turnaje, história turnajov, profily hráčov s ich štatistikami.  
Rozširujúce funkcie sú vyhladávanie konkrétneho hráča/turnaja, live stav práve prebiehajúceho turnaja, alebo pridanie nových formátov turnajov.