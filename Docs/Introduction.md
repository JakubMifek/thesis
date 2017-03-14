## Úvod
1. Co je známo?
    1. [X] Diskrétní prostor, omezený počet stavů, co si představit pod pojmem klasická karetní hra
    1. [X] Knihovny pro reprezentaci karet, stolních her, karetních her s nedostatečnou strukturou ~ umožním ti spustit hru která je stolní a bude mít karty.. ale kde jsou karty a tak, vps celé to okénko si nadefinuj sám pořádně. Stejně tak ochranu před podváděním, atp.
1. Cíl práce
    1. [X] Knihovna pro návrh klasických karetních her
    1. [X] Aplikace pro spouštění
    1. [X] Rozšíření pro server a databázi
    1. [ ] Umělá inteligence, Q-Learning
1. Proč je to důležité
    1. [ ] Jednoduší vývoj, přímo spajtý s námi poskytnutou databází uživatelů - představa hraní her jako aplikace s pluginy
    1. [ ] Zpřístupnění méně známých her více hráčům a doplnění hráčské komunity o umělé inteligence
1. Volba metody
    1. [ ] Diskrétní prostor - tabulková reprezentace (nezměním to přecijen ještě? Například na nějaké jednoduché spojité rozdělení prostoru na sekce)
    1. [ ] Server - mediator - úspora času a místa
    1. [ ] Nebezpečí hrozí u:
        1. Tahů umělé inteligence, kterou asi nebudu pouštět na všech strojích (možná kontrola, pokud budu mít 2 stejně silné stroje a pustím stejný seed) - uživatel by jí mohl upravit, aby hrála tak, jak se mu hodí
        1. Nahlížení do karet, pokud uživatel napíše vlastního klienta
    1. [ ] Q-Learning. Proč Q a vztah k ostatním umělým inteligencím a vztah k naším cílům (2.4.)

___
###### Co je známo?
Jednou z hlavních částí naší práce je návrh knihovny pro tvorbu klasických karetních her. Klasické karetní hry mají spoustu společných vlastností, které v naší knihovně můžeme reprezentovat. Odehrávají se v diskrétním prostoru (karetní stůl), mají pouze omezený počet předem známých karet, omezený počet hráčů. Každý klasický karetní stůl je složen ze základních elementů jako například karetní míst (cardspot). Každá klasická karta má svou hodnotu a barvu. Každá klasická karetní hra je složena z dílčích fází. Každá fáze může ovlivnit jak vypadá karetní stůl nebo například skóre hráčů. A také ji je možno spustit a zastavit. Hlavní charakteristikou fází je, že na jejich žádost hráč vybírá možnost z množiny stavů, pomocí které určí další průběh hry. Typicky se jedná o volbu karty, přetažení karty nebo o licitační hlášku. Každý hráč klasické karetní hry vlastní svůj profil, má přiřazenou probíhající karetní hru, své balíčky karet a je schopen na žádost hry zvolit akci, kterou chce provést.

Pokusy o reprezentaci karetních her již samozřejmě proběhly ve větším množství. Existují knihovny pro podporu reprezentace karet a balíčků karet. Ale to je nedostačující. Klasické karetní hry mají mnohem více společných rysů. Existují knihovny pro podporu stolních her, avšak ty jsou moc obecné. Uživatel si musí dodefinovat velké množství charakteristik, které se často pro karetní hry opakují. Avšak najdou se i knihovny, které spojují oboje charakteristiky a jsou poměrně blízko k nami požadovanému výsledku. Avšak ani jeden z těchto návrhů nedokázal vyřešit problém reprezentace stolu, licitací, her po síti, a nebo opatření proti podvádění.

###### Cíl práce
Vzhledem k nedostatkům ostatních knihoven jsme se rozhodli naimplementovat knihovnu vlastní. Ta bude schopna jednoduše reprezentovat libovolnou klasickou hru a to jak její logickou strukturu, tak grafický vzhled hry. Umožní tak jednoduchou distribuci karetních her mezi uživateli. Dále pro ověření univerzálnosti knihovny naimplementujeme pět typově rozdílných her za pomoci naší knihovny. Konkrétně Mariáš (týmová hra s licitací), Texas Hold'Em Poker (hra založená na principu peněz a přetvářky) a Lóru (Kladenská karetní hra, která je složena celkem ze sedmi podher, obsahující mimo jiné klasické hry typu prší, vykládací hru a hru, jejíž pravidla jsou určeny až za průběhu). Dále pro ověření univerzálnosti reprezentace naprogramujeme aplikaci schopnou spuštění libovolné klasické karetní hry. Zároveň s tím naprogramujeme databázi a server za účelem propojení uživtelů a možnosti hry online. V rámci serveru bude implementovaný i žebříček hráčů pro každou oficiální hru (oficiální hry budou nabízeny distributorem klient-server aplikace). Dále vytvoříme pravidlové umělé inteligence pro ukázkové hry a umělou inteligenci schopnou naučit se libovolnou z těchto her. K tvorbě samoučící se umělé inteligence využijeme techonologii Q-Learning.
