## Úvod
1. Co je známo?
    1. [X] Diskrétní prostor, omezený počet stavů, co si představit pod pojmem klasická karetní hra
    1. [X] Knihovny pro reprezentaci karet, stolních her, karetních her s nedostatečnou strukturou ~ umožním ti spustit hru která je stolní a bude mít karty.. ale kde jsou karty a tak, vps celé to okénko si nadefinuj sám pořádně. Stejně tak ochranu před podváděním, atp.
1. Cíl práce
    1. [X] Knihovna pro návrh klasických karetních her
    1. [X] Aplikace pro spouštění
    1. [X] Rozšíření pro server a databázi
    1. [X] Umělá inteligence, Q-Learning
1. Proč je to důležité
    1. [X] Jednoduší vývoj, přímo spajtý s námi poskytnutou databází uživatelů - představa hraní her jako aplikace s pluginy
    1. [X] Zpřístupnění méně známých her více hráčům a doplnění hráčské komunity o umělé inteligence
1. Volba metody
    1. [ ] Diskrétní prostor - tabulková reprezentace (nezměním to přecijen ještě? Například na nějaké jednoduché spojité rozdělení prostoru na sekce)
    1. [ ] Server - mediator - úspora času a místa
    1. [ ] Nebezpečí hrozí u:
        1. Tahů umělé inteligence, kterou asi nebudu pouštět na všech strojích (možná kontrola, pokud budu mít 2 stejně silné stroje a pustím stejný seed) - uživatel by jí mohl upravit, aby hrála tak, jak se mu hodí
        1. Nahlížení do karet, pokud uživatel napíše vlastního klienta
    1. [ ] Q-Learning. Proč Q a vztah k ostatním umělým inteligencím a vztah k naším cílům (2.4.)

___
###### Co je známo?
Jednou z hlavních částí naší práce je návrh knihovny pro tvorbu klasických karetních her (CCGs). CCGs mají spoustu společných vlastností, které v naší knihovně můžeme reprezentovat. Odehrávají se v diskrétním prostoru (karetní stůl), mají pouze omezený počet předem známých karet, omezený počet hráčů. Každý klasický karetní stůl je složen ze základních elementů jako například karetní míst (cardspot). Každá klasická karta má svou hodnotu a barvu. Každá CCG je složena z dílčích fází. Každá fáze může ovlivnit jak vypadá karetní stůl nebo například skóre hráčů. A také ji je možno spustit a zastavit. Hlavní charakteristikou fází je, že na jejich žádost hráč vybírá možnost z množiny stavů, pomocí které určí další průběh hry. Typicky se jedná o volbu karty, přetažení karty nebo o licitační hlášku. Každý hráč CCG vlastní svůj profil, má přiřazenou probíhající karetní hru, své balíčky karet a je schopen na žádost hry zvolit akci, kterou chce provést.

Pokusy o reprezentaci karetních her již samozřejmě proběhly ve větším množství. Existují knihovny pro podporu reprezentace karet a balíčků karet. Ale to je nedostačující. CCGs mají mnohem více společných rysů. Existují knihovny pro podporu stolních her, avšak ty jsou moc obecné. Uživatel si musí dodefinovat velké množství charakteristik, které se často pro CCGs opakují. Avšak najdou se i knihovny, které spojují oboje charakteristiky a jsou poměrně blízko k nami požadovanému výsledku. Avšak ani jeden z těchto návrhů nedokázal vyřešit problém reprezentace stolu, licitací, her po síti, a nebo opatření proti podvádění.

###### Cíl práce
Vzhledem k nedostatkům ostatních knihoven jsme se rozhodli naimplementovat knihovnu vlastní. Ta bude schopna jednoduše reprezentovat libovolnou CCG a to jak její logickou strukturu, tak grafický vzhled hry. Dále pro ověření univerzálnosti knihovny naimplementujeme pět typově rozdílných her za pomoci naší knihovny. Konkrétně hry Mariáš (týmová hra s licitací), Texas Hold'Em Poker (hra založená na principu peněz a přetvářky) a Lóru (Kladenská karetní hra, která je složena celkem ze sedmi podher, obsahující mimo jiné klasické hry typu prší, vykládací hru a hru, jejíž pravidla jsou určeny až za průběhu).

Pro ověření univerzálnosti reprezentace her naprogramujeme aplikaci schopnou spuštění libovolné CCG. Její funkčnost ověříme pomocí ukázkových her. Zároveň s tím naprogramujeme databázi a server za účelem propojení uživtelů a možnosti hry více hráčů. V rámci serveru bude implementovaný i inteligentní žebříček hráčů pro každou oficiální hru (oficiální hry budou nabízeny distributorem klient-server aplikace).

Nakonec vytvoříme jednoduché pravidlové AI (AIs) pro ukázkové hry a AI schopnou naučit se libovolnou z těchto her. Tato samoučící se AI bude vytrénována na hrách proti pravidlovým AIs a měla by být schopna je ve většině případů porazit.

###### Proč je to důležité?
Náš koncept by měl ulehčit práci programátorům karetních her. Díky návrhu aplikace a serveru by měl zjednodušit dristribuci CCGs mezi uživateli. Hráčům bude možno nabídnout karetní hry jako doplňující soubory naprogramované aplikace. Také by měl zpřístupnit málo známé karetní hry větší hráčské komunitě a umožnit tak uživatelům jejich hraní i při nedostatku dalších hráčů. A to hlavně za pomoci AIs.

###### Volba metody
K grafické reprezentaci stolu jsme zvolili diskrétní rozdělení na 2D tabulku s překrývajícími se políčky. Součástí práce bude 'Builder' struktura pro zjednodušení tvorby stolu.  
Pro komunikaci přes server jsme se rozhodli pro metodu 'Mediator'. Server slouží pouze pro zápis do databáze, nebo přeposlání událostí hráče k ostatním hráčům. Vlastní hra běží v aplikaci každého z hráčů a nezatěžuje tak server.  
K implementaci AI použijeme metodu Q-Learning. 
