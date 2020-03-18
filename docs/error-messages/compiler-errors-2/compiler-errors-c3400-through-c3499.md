---
title: Chyby kompilátoru C3400 až C3499
ms.date: 04/21/2019
f1_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
helpviewer_keywords:
- C3401
- C3402
- C3403
- C3404
- C3405
- C3406
- C3407
- C3410
- C3411
- C3416
- C3419
- C3422
- C3424
- C3425
- C3426
- C3427
- C3428
- C3429
- C3430
- C3431
- C3432
- C3433
- C3434
- C3435
- C3436
- C3437
- C3438
- C3439
- C3440
- C3441
- C3442
- C3443
- C3444
- C3471
- C3472
- C3473
- C3474
- C3475
- C3476
- C3477
- C3478
- C3479
- C3486
- C3494
- C3497
ms.assetid: a5651dfb-c402-4e01-b3ae-28f371e51d6a
ms.openlocfilehash: f4aff80178033d34cf051a14d89736b2b8347dd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446845"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Chyby kompilátoru C3400 až C3499

Články v této části dokumentace vysvětlují podmnožinu chybových zpráv generovaných kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C3400](compiler-error-c3400.md)|cyklická závislost omezení zahrnující '*Constraint1*' a '*constraint2*'|
|Chyba kompilátoru C3401|'*specifikátor*': Neplatný specifikátor přístupu k sestavení – pro šablony tříd je povolen pouze typ Private.|
|Chyba kompilátoru C3402|'*Function*': přetížení nelze vyřešit s výjimkou v aktuálním oboru|
|Chyba kompilátoru C3403|thread_local nelze použít s možností/CLR: pure nebo/CLR: safe.|
|Chyba kompilátoru C3404|'*CONSTRUCT*': Neočekávaná chyba syntaxe|
|Chyba kompilátoru C3405|'*Function*': metodu Overload nelze vyřešit bez deskriptoru Complete|
|Chyba kompilátoru C3406|*klíčové slovo*: nejde použít ve specifikátoru propracovaného typu.|
|Chyba kompilátoru C3407|klíčové slovo*Type*se v tomto kontextu nedá použít.|
|[Chyba kompilátoru C3408](compiler-error-c3408.md)|'*attribute*': atribut není v definicích šablon povolen|
|[Chyba kompilátoru C3409](compiler-error-c3409.md)|prázdný blok atributu není povolený.|
|Chyba kompilátoru C3410|'*Identifier*': typ explicitního vytvoření instance '*Type*' neodpovídá typu proměnné šablony '*Type*'|
|Chyba kompilátoru C3411|*typ*není platný jako velikost pole, protože se nejedná o celočíselný typ.|
|[Chyba kompilátoru C3412](compiler-error-c3412.md)|*specializace*: nejde specializovat šablonu v aktuálním oboru.|
|[Chyba kompilátoru C3413](compiler-error-c3413.md)|'*template*': neplatné explicitní vytváření instancí|
|[Chyba kompilátoru C3414](compiler-error-c3414.md)|'*Function*': nelze definovat importovanou členskou funkci|
|[Chyba kompilátoru C3415](compiler-error-c3415.md)|našlo se víc oddílů*Section*s různými atributy (0x*Value*).|
|Chyba kompilátoru C3416|Zastaralé.|
|[Chyba kompilátoru C3417](compiler-error-c3417.md)|'*deklarátor*': typy hodnot nemohou obsahovat speciální členské funkce definované uživatelem|
|[Chyba kompilátoru C3418](compiler-error-c3418.md)|specifikátor přístupu '*specifikátor*' není podporován.|
|Chyba kompilátoru C3419|Zastaralé.|
|[Chyba kompilátoru C3420](compiler-error-c3420.md)|'*Function*': finalizační metoda nemůže být virtuální.|
|[Chyba kompilátoru C3421](compiler-error-c3421.md)|'*Function*': nemůžete volat finalizační metodu pro tuto třídu, protože je buď nedostupná, nebo neexistuje.|
|Chyba kompilátoru C3422|'*Declaration*': neodpovídající typy '*Type*' a '*Type*'|
|Chyba kompilátoru C3423|Zastaralé.|
|Chyba kompilátoru C3424|*typ*: přetypování Function-Style na typ pole není povolené.|
|Chyba kompilátoru C3425|nejde vyvolat ukazatel na objekt neúplného typu*typu*.|
|Chyba kompilátoru C3426|nejde vyvolat objekt*typu*nekompletního typu.|
|Chyba kompilátoru C3427|'*Context*':*klíčové slovo*nelze použít s layout_version (*Number*)|
|Chyba kompilátoru C3428|*Context*:*klíčové slovo*se dá použít jedině pro deklarace nebo definice tříd.|
|Chyba kompilátoru C3429|'*Context*':*klíčové slovo*nelze použít pro sjednocení.|
|Chyba kompilátoru C3430|výčet s vymezeným oborem musí mít název.|
|Chyba kompilátoru C3431|'*Identifier*': *typ1* nelze deklarovat jako *typ2*|
|Chyba kompilátoru C3432|'*Identifier*': Dopředná deklarace výčtu bez oboru musí mít podkladový typ.|
|Chyba kompilátoru C3433|'*Identifier*': všechny deklarace výčtu musí mít stejný podkladový typ, byl '*typ1*' nyní '*typ2*'|
|Chyba kompilátoru C3434|'*Context*': hodnota enumerátoru '*Number*' nemůže být reprezentována jako*typ ' Type*', hodnota je '*Number*'|
|Chyba kompilátoru C3435|znaková sada*Name*není podporována.|
|Chyba kompilátoru C3436|#pragma setlocale není podporován, je-li zadán parametr/source-charset,/Execution-charset nebo/UTF-8.|
|Chyba kompilátoru C3437|#pragma execution_character_set není podporován, pokud byla zadána podpora/source-charset,/Execution-charset nebo/UTF-8.|
|Chyba kompilátoru C3438|klíčové slovo*Context*:*Value*se nedá použít u třídy Managed/WinRT.|
|Chyba kompilátoru C3439|layout_version (*číslo*): neplatné číslo verze|
|Chyba kompilátoru C3440|*deklarace*: layout_version (*číslo*) není kompatibilní s předchozí deklarací.|
|Chyba kompilátoru C3441|*deklarace ' Declaration*':*klíčové slovo*nelze použít po definování třídy.|
|Chyba kompilátoru C3442|Inicializuje se víc členů sjednocení:*člen1*a*member2*.|
|Chyba kompilátoru C3443|Výchozí inicializátor členu pro*Class*je rekurzivní.|
|Chyba kompilátoru C3444|Prázdná agregovaná třída*Class*musí být inicializovaná pomocí{}.|
|[Chyba kompilátoru C3445](compiler-error-c3445.md)|Inicializace kopírování seznamu*typu*nemůže používat explicitní konstruktor.|
|[Chyba kompilátoru C3446](compiler-error-c3446.md)|*Class*: výchozí inicializátor členů není povolený pro člena hodnotové třídy.|
|Chyba kompilátoru C3447|Zastaralé.|
|Chyba kompilátoru C3448|Zastaralé.|
|Chyba kompilátoru C3449|Zastaralé.|
|[Chyba kompilátoru C3450](compiler-error-c3450.md)|'*Type*': není atribut; nelze zadat [System:: AttributeUsageAttribute]/[Windows:: Foundation:: metadata:: AttributeUsageAttribute].|
|[Chyba kompilátoru C3451](compiler-error-c3451.md)|'*attribute*': nespravovaný atribut nelze použít pro*typ*'|
|[Chyba kompilátoru C3452](compiler-error-c3452.md)|člen argumentu seznamu není konstanta.|
|[Chyba kompilátoru C3453](compiler-error-c3453.md)|*atribut*: atribut se nepoužil, protože se neshodoval*kvalifikátor kvalifikátoru*.|
|[Chyba kompilátoru C3454](compiler-error-c3454.md)|[Attribute] není povolený pro deklaraci třídy.|
|[Chyba kompilátoru C3455](compiler-error-c3455.md)|'*attribute*': žádný z konstruktorů atributu neodpovídá argumentům|
|[Chyba kompilátoru C3456](compiler-error-c3456.md)|[zdroj\_annotation_attribute] není povolený pro deklaraci třídy Managed/WinRT.|
|[Chyba kompilátoru C3457](compiler-error-c3457.md)|'*attribute*': atribut nepodporuje nepojmenované argumenty|
|[Chyba kompilátoru C3458](compiler-error-c3458.md)|' [*atribut*] ': atribut ' [*atribut*] ' je již určen pro '*identifikátor*'|
|[Chyba kompilátoru C3459](compiler-error-c3459.md)|[*attribute*]: atribut je povolený jedině pro indexer tříd (výchozí indexovaná vlastnost).|
|[Chyba kompilátoru C3460](compiler-error-c3460.md)|'*Type*': je možné přeslat pouze uživatelsky definovaný typ.|
|[Chyba kompilátoru C3461](compiler-error-c3461.md)|'*Type*': lze přesměrovat pouze typ spravovaného/WinRT|
|[Chyba kompilátoru C3462](compiler-error-c3462.md)|'*Type*': je možné přeslat pouze importovaný typ.|
|[Chyba kompilátoru C3463](compiler-error-c3463.md)|*Type*: typ není povolený v atributech Implements.|
|[Chyba kompilátoru C3464](compiler-error-c3464.md)|*typ*vnořeného typu nemůže být předán.|
|[Chyba kompilátoru C3465](compiler-error-c3465.md)|Pokud chcete použít typ*Type,* musíte odkazovat na sestavení*Assembly*.|
|[Chyba kompilátoru C3466](compiler-error-c3466.md)|'*Type*': specializace obecné třídy nemůže být předána|
|[Chyba kompilátoru C3467](compiler-error-c3467.md)|*typ*: Tento typ už je předaný.|
|[Chyba kompilátoru C3468](compiler-error-c3468.md)|'*Type*': typ lze přeslat pouze do sestavení: '*identifikátor*' není sestavení|
|[Chyba kompilátoru C3469](compiler-error-c3469.md)|'*Type*': obecnou třídu nelze přesměrováním|
|[Chyba kompilátoru C3470](compiler-error-c3470.md)|'*Class*': třída nemůže mít jak indexer (výchozí indexovanou vlastnost), tak i operator []|
|Chyba kompilátoru C3471|*název nového modulu (nastavený* v příkazovém řádku) je v konfliktu s *názvem* předchozího názvu.|
|Chyba kompilátoru C3472|název souboru nového výstupního *souboru (nastavený* v příkazovém řádku) je v konfliktu s *názvem souboru* předchozí.|
|Chyba kompilátoru C3473|není zadaná žádná cesta k výstupu ani název modulu.|
|Chyba kompilátoru C3474|nejde otevřít výstupní soubor*filename*.|
|Chyba kompilátoru C3475|Chyba syntaxe ve vstupním souboru*filename*|
|Chyba kompilátoru C3476|Nepovedlo se otevřít soubor*filename*pro vstup.|
|Chyba kompilátoru C3477|výraz lambda se nemůže vyskytovat v nehodnoceném kontextu.|
|Chyba kompilátoru C3478|'*Identifier*': pole nemůže být zachyceno kopií|
|Chyba kompilátoru C3479|Poznámky SAL pro výrazy lambda nejsou podporované.|
|[Chyba kompilátoru C3480](compiler-error-c3480.md)|'*Variable*': proměnná zachycení lambda musí být z oboru ohraničující funkce|
|[Chyba kompilátoru C3481](compiler-error-c3481.md)|'*Identifier*': nebyla nalezena proměnná zachycení lambda|
|[Chyba kompilátoru C3482](compiler-error-c3482.md)|klíčové slovo this se dá použít jedině jako zachycení lambdy v rámci nestatické členské funkce.|
|[Chyba kompilátoru C3483](compiler-error-c3483.md)|'*Identifier*' už je součástí seznamu zachycení lambdy.|
|[Chyba kompilátoru C3484](compiler-error-c3484.md)|Chyba syntaxe: před návratovým typem se očekávala hodnota->.|
|[Chyba kompilátoru C3485](compiler-error-c3485.md)|definice lambda nemůže mít žádné kvalifikátory cv.|
|Chyba kompilátoru C3486|Zastaralé.|
|[Chyba kompilátoru C3487](compiler-error-c3487.md)|*typ*: všechny návratové výrazy se musí odvozovat na stejný typ: dřív to bylo*Type*.|
|[Chyba kompilátoru C3488](compiler-error-c3488.md)|&*identifikátor*není povolený, pokud je výchozí režim sběru podle odkazu.|
|[Chyba kompilátoru C3489](compiler-error-c3489.md)|Pokud je výchozí režim sběru na základě kopie, vyžaduje se &*identifikátor*.|
|[Chyba kompilátoru C3490](compiler-error-c3490.md)|*identifikátor*nejde změnit, protože se k němu přistupoval prostřednictvím objektu const.|
|[Chyba kompilátoru C3491](compiler-error-c3491.md)|'*Identifier*': zachycení po kopírování nemůže být upraveno v neproměnlivém výrazu lambda|
|[Chyba kompilátoru C3492](compiler-error-c3492.md)|*identifikátor*: nejde zachytit člen anonymního sjednocení.|
|[Chyba kompilátoru C3493](compiler-error-c3493.md)|*identifikátor*nejde implicitně zachytit, protože není zadaný žádný výchozí režim zachycení.|
|Chyba kompilátoru C3494|klíčové slovo this nejde zachytit explicitně, protože režim zachycení, který ho obklopuje, to nepovoluje.|
|[Chyba kompilátoru C3495](compiler-error-c3495.md)|'*Identifier*': identifikátor v zachycení musí být proměnná s automatickou dobou trvání úložiště deklarovanou v oboru dosažení výrazu lambda|
|[Chyba kompilátoru C3496](compiler-error-c3496.md)|klíčové slovo this je vždycky zachycené hodnotou: & se ignoruje.|
|Chyba kompilátoru C3497|Nemůžete vytvořit instanci výrazu lambda.|
|[Chyba kompilátoru C3498](compiler-error-c3498.md)|'*Identifier*': nelze zachytit proměnnou, která má typ spravovaného/WinRT|
|[Chyba kompilátoru C3499](compiler-error-c3499.md)|lambda, která je zadaná tak, aby měla návratový typ void, nemůže vracet hodnotu.|

## <a name="see-also"></a>Viz také

[Chyby aC++ upozornění pro nástroje C/kompilátor a Build](../compiler-errors-1/c-cpp-build-errors.md) a \
[Chyby kompilátoru c2000 – C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
