## Úvod
1. Co je známo?
    1. Diskrétní prostor, omezený počet stavů, co si představit pod pojmem klasická karetní hra
    1. Knihovny pro reprezentaci karet, stolních her, karetních her s nedostatečnou strukturou ~ umožním ti spustit hru která je stolní a bude mít karty.. ale kde jsou karty a tak, vps celé to okénko si nadefinuj sám pořádně. Stejně tak ochranu před podváděním, atp.
1. Cíl práce
    1. Knihovna pro návrh klasických karetních her
    1. Aplikace pro spouštění
    1. Rozšíření pro server a databázi
    1. Umělá inteligence, Q-Learning
1. Proč je to důležité
    1. Jednoduší vývoj, přímo spajtý s námi poskytnutou databází uživatelů - představa hraní her jako aplikace s pluginy
    1. Zpřístupnění méně známých her více hráčům a doplnění hráčské komunity o umělé inteligence
1. Volba metody
    1. Diskrétní prostor - tabulková reprezentace (nezměním to přecijen ještě? Například na nějaké jednoduché spojité rozdělení prostoru na sekce)
    1. Server - mediator - úspora času a místa
    1. Nebezpečí hrozí u:
        1. tahů umělé inteligence, kterou asi nebudu pouštět na všech strojích (možná kontrola, pokud budu mít 2 stejně silné stroje a pustím stejný seed) - uživatel by jí mohl upravit, aby hrála tak, jak se mu hodí
        1. Nahlížení do karet, pokud uživatel napíše vlastního klienta
    1. Q-Learning. Proč Q a vztah k ostatním umělým inteligencím a vztah k naším cílům (2.4.)

___
Veškeré karetní hry 
