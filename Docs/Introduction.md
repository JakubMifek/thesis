## Úvod
1.	Co je známo?
  1. Knihovny pro reprezentaci karet, stolních her, karetních her s nedostatečnou strukturou ~ umožním ti spustit hru která je stolní a bude mít karty.. ale kde jsou karty a tak, vps celé to okénko si nadefinuj sám pořádně. Stejně tak ochranu před podváděním, atp.
  2. Diskrétní prostor, omezený počet stavů, co si představit pod pojmem klasická karetní hra
2.	Cíl práce
  1. Knihovna pro návrh klasických karetních her
  2. Aplikace pro spouštění
  3. Rozšíření pro server a databázi
  4. Umělá inteligence, Q-Learning
3.	Proč je to důležité
  1. Jednoduší vývoj, přímo spajtý s námi poskytnutou databází uživatelů - představa hraní her jako aplikace s pluginy
  2. Zpřístupnění méně známých her více hráčům a doplnění hráčské komunity o umělé inteligence
4.	Volba metody
  1. Diskrétní prostor - tabulková reprezentace (nezměním to přecijen ještě? Například na nějaké jednoduché spojité rozdělení prostoru na sekce)
  2. Server - mediator - úspora času a místa
  3. Nebezpečí hrozí u:
    1. tahů umělé inteligence, kterou asi nebudu pouštět na všech strojích (možná kontrola, pokud budu mít 2 stejně silné stroje a pustím stejný seed) - uživatel by jí mohl upravit, aby hrála tak, jak se mu hodí
    2. Nahlížení do karet, pokud uživatel napíše vlastního klienta
  4. Q-Learning. Proč Q a vztah k ostatním umělým inteligencím a vztah k naším cílům (2.4.)
