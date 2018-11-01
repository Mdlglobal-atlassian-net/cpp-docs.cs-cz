---
title: Chyby kompilátoru C3400 až C3499
ms.date: 11/17/2017
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
- C3445
- C3446
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
- C3445
- C3446
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
ms.openlocfilehash: 24915a52bffb6826599e4d64d60a3ece6bee7675
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576719"
---
# <a name="compiler-errors-c3400-through-c3499"></a>Chyby kompilátoru C3400 až C3499

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C3400](compiler-error-c3400.md)|Cyklické omezení týkajících se závislostí '*constraint1*"a"*constraint2*.|
|C3401 chyby kompilátoru|"*specifikátor*': sestavení Neplatný specifikátor přístupu - jedině možnost private' je povolen u šablon třídy|
|C3402 chyby kompilátoru|"*funkce*': nelze přetížení jde vyřešit jedině v aktuálním rozsahu.|
|C3403 chyby kompilátoru|možnost thread_local nejde používat s parametrem/CLR: pure nebo/CLR: safe|
|C3404 chyby kompilátoru|"*vytvořit*': Neočekávaná chyba syntaxe|
|C3405 chyby kompilátoru|"*funkce*': přetížení nejde vyřešit bez deskriptoru complete|
|C3406 chyby kompilátoru|"*– klíčové slovo*': nelze použít ve vysvětlujícím specifikátoru typu|
|C3407 chyby kompilátoru|"*typ*" v tomto kontextu nelze použít|
|[Chyba kompilátoru C3408](compiler-error-c3408.md)|"*atribut*': atribut není povolený pro definice šablon|
|[Chyba kompilátoru C3409](compiler-error-c3409.md)|prázdný atribut block není povolený.|
|C3410 chyby kompilátoru|"*identifikátor*': typ explicitního vytvoření instance"*typ*"neodpovídá typu variabilní šablony"*typ*"|
|C3411 chyby kompilátoru|"*typ*' není platný jako velikost pole, protože není typu integer|
|[Chyba kompilátoru C3412](compiler-error-c3412.md)|"*specializace*': nejde specializovat šablonu v aktuálním rozsahu.|
|[Chyba kompilátoru C3413](compiler-error-c3413.md)|"*šablony*': neplatné explicitní vytváření instancí|
|[Chyba kompilátoru C3414](compiler-error-c3414.md)|"*funkce*': nejde definovat importovanou členskou funkci|
|[Chyba kompilátoru C3415](compiler-error-c3415.md)|více "*části*" našlo oddílů s rozdílnými atributy (0 x*hodnotu*")|
|C3416 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3417](compiler-error-c3417.md)|"*deklarátor*': hodnotové typy nemůžou obsahovat speciální členské funkce definované uživatele|
|[Chyba kompilátoru C3418](compiler-error-c3418.md)|přístup k specifikátor "*specifikátor*' není podporován|
|C3419 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3420](compiler-error-c3420.md)|"*funkce*': finalizační metoda nemůže být virtuální|
|[Chyba kompilátoru C3421](compiler-error-c3421.md)|"*funkce*': nelze volat finalizační metodu pro tuto třídu, protože je buď nedostupné nebo neexistuje|
|C3422 chyby kompilátoru|"*deklarace*': Neshoda typů*typ*"a"*typ*.|
|C3423 chyby kompilátoru|Zastaralé.|
|C3424 chyby kompilátoru|"*typ*': function-style přetypovat na typ array není povolené.|
|C3425 chyby kompilátoru|nejde aktivovat ukazatel na objekt neúplného typu "*typ*.|
|C3426 chyby kompilátoru|nejde aktivovat objekt s neúplným typem "*typ*.|
|C3427 chyby kompilátoru|"*kontextu*": "*– klíčové slovo*' nelze použít s layout_version (*číslo*)|
|C3428 chyby kompilátoru|"*kontextu*": "*– klíčové slovo*se dá používat jedině pro definice nebo deklarace tříd|
|C3429 chyby kompilátoru|"*kontextu*": "*– klíčové slovo*' nejde použít u sjednocení|
|C3430 chyby kompilátoru|Výčet s oborem musí mít název|
|C3431 chyby kompilátoru|"*identifikátor*': *type1* nejde deklarovat jako *typ2*|
|C3432 chyby kompilátoru|"*identifikátor*': Dopředná deklarace výčtu bez oboru musí mít podkladový typ.|
|C3433 chyby kompilátoru|"*identifikátor*': všechny deklarace výčtu musí mít stejný základní typ., byl"*type1*'now'*type2*.|
|C3434 chyby kompilátoru|"*kontextu*': hodnota výčtu '*číslo*"nemůže být reprezentovaná jako"*typ*', hodnota je'*číslo*"|
|C3435 chyby kompilátoru|Znaková sada "*název*' není podporován|
|C3436 chyby kompilátoru|#pragma setlocale není podporovaný, pokud má jste zadali/Source-Charset, / Execution-Charset nebo/UTF-8|
|C3437 chyby kompilátoru|#pragma execution_character_set není podporovaný, pokud má jste zadali/Source-Charset, / Execution-Charset nebo/UTF-8|
|C3438 chyby kompilátoru|"*kontextu*": "*hodnotu*' nelze použít pro třídu spravované/WinRT|
|C3439 chyby kompilátoru|layout_version (*číslo*): Neplatné číslo verze|
|C3440 chyby kompilátoru|"*deklarace*': layout_version (*číslo*) nekompatibilní s předchozí deklarací.|
|C3441 chyby kompilátoru|"*deklarace*": "*– klíčové slovo*' nelze použít po definování třídy|
|C3442 chyby kompilátoru|Inicializace několika členů sjednocení: "*member1*"a"*člen2*.|
|C3443 chyby kompilátoru|Výchozí inicializátor členu pro "*třídy*" je rekurzivní|
|C3444 chyby kompilátoru|Prázdná agregovaná třída*třídy*"je nutné inicializovat s"{}.|
|[Chyba kompilátoru C3445](compiler-error-c3445.md)|kopírování Inicializace seznamu z "*typ*' nelze použít explicitní konstruktor|
|[Chyba kompilátoru C3446](compiler-error-c3446.md)|"*třídy*': výchozí inicializátor členu není povolený pro člena hodnotové třídy.|
|C3447 chyby kompilátoru|Zastaralé.|
|C3448 chyby kompilátoru|Zastaralé.|
|C3449 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3450](compiler-error-c3450.md)|"*typ*': nejde o atribut; nejde zadat [System::AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute]|
|[Chyba kompilátoru C3451](compiler-error-c3451.md)|"*atribut*': nejde použít nespravovaný atribut na"*typ*.|
|[Chyba kompilátoru C3452](compiler-error-c3452.md)|člen argumentu seznamu není konstanta.|
|[Chyba kompilátoru C3453](compiler-error-c3453.md)|"*atribut*': atribut se nepoužil, protože kvalifikátor '*kvalifikátor*' neodpovídá|
|[Chyba kompilátoru C3454](compiler-error-c3454.md)|[attribute] není povolený u deklarace třídy|
|[Chyba kompilátoru C3455](compiler-error-c3455.md)|"*atribut*': žádný z konstruktů atributů argumentům neodpovídá|
|[Chyba kompilátoru C3456](compiler-error-c3456.md)|[zdroj\_annotation_attribute] není povolený u deklarace třídy spravované/WinRT|
|[Chyba kompilátoru C3457](compiler-error-c3457.md)|"*atribut*': atribut nepodporuje nepojmenované argumenty|
|[Chyba kompilátoru C3458](compiler-error-c3458.md)|"[*atribut*]": atribut ' [*atribut*]' již zadán pro "*identifikátor*"|
|[Chyba kompilátoru C3459](compiler-error-c3459.md)|"[*atribut*]': atribut je povolený jedině pro indexer tříd (výchozí indexovanou vlastnost)|
|[Chyba kompilátoru C3460](compiler-error-c3460.md)|"*typ*': předávat dál se dají jenom typ definovaný uživatelem|
|[Chyba kompilátoru C3461](compiler-error-c3461.md)|"*typ*': předávat dál se dají jenom typu spravované/WinRT|
|[Chyba kompilátoru C3462](compiler-error-c3462.md)|"*typ*': předávat dál se dají jenom importované typy|
|[Chyba kompilátoru C3463](compiler-error-c3463.md)|"*typ*': typ není povolený v atributu 'implements'|
|[Chyba kompilátoru C3464](compiler-error-c3464.md)|"*typ*" vnořený typ nelze předat dál|
|[Chyba kompilátoru C3465](compiler-error-c3465.md)|použití typu "*typ*'musí odkazovat na sestavení'*sestavení*.|
|[Chyba kompilátoru C3466](compiler-error-c3466.md)|"*typ*': specializace obecné třídy nejde předat dál|
|[Chyba kompilátoru C3467](compiler-error-c3467.md)|"*typ*': Tento typ už je předaný|
|[Chyba kompilátoru C3468](compiler-error-c3468.md)|"*typ*': Typ může předávat pouze na sestavení:"*identifikátor*' není sestavení.|
|[Chyba kompilátoru C3469](compiler-error-c3469.md)|"*typ*': Obecné třídy nejde předat dál|
|[Chyba kompilátoru C3470](compiler-error-c3470.md)|"*třídy*': třída nemůže mít jak indexer (výchozí indexovanou vlastnost) a taky operator]|
|C3471 chyby kompilátoru|nový název modulu *název* (sada na příkazovém řádku) je v konfliktu s předchozím názvem *název*|
|C3472 chyby kompilátoru|nový název výstupního souboru *filename* (sada na příkazovém řádku) je v konfliktu s předchozím názvem souboru *název souboru*|
|C3473 chyby kompilátoru|Výstupní cesta nebo modul zadán žádný název.|
|C3474 chyby kompilátoru|Nelze otevřít výstupní soubor '*filename*.|
|C3475 chyby kompilátoru|Chyba syntaxe ve vstupním souboru "*filename*.|
|C3476 chyby kompilátoru|nepovedlo se otevřít soubor "*filename*" pro vstup|
|C3477 chyby kompilátoru|výraz lambda se nemůže vyskytovat v nevyhodnoceném kontextu.|
|C3478 chyby kompilátoru|"*identifikátor*': pole se nemůže zachycovat na základě kopie|
|C3479 chyby kompilátoru|Poznámky SAL pro výrazy lambda nejsou podporovány.|
|[Chyba kompilátoru C3480](compiler-error-c3480.md)|"*proměnnou*': proměnná zachycení lambda musí být z nadřazeného oboru – funkce|
|[Chyba kompilátoru C3481](compiler-error-c3481.md)|"*identifikátor*': proměnná zachycení lambda nebyl nalezen|
|[Chyba kompilátoru C3482](compiler-error-c3482.md)|"this" jde použít jenom jako zachycení lambdy v rámci funkce nestatického člena|
|[Chyba kompilátoru C3483](compiler-error-c3483.md)|"*identifikátor*" je již součástí seznamu zachycení lambdy|
|[Chyba kompilátoru C3484](compiler-error-c3484.md)|Chyba syntaxe: očekávalo: ->"před návratový typ|
|[Chyba kompilátoru C3485](compiler-error-c3485.md)|definice lambdy nemůže mít cv Qualifier|
|C3486 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3487](compiler-error-c3487.md)|"*typ*': všechny návratové výrazy se musí odvozovat na stejný typ: dřív to bylo"*typ*.|
|[Chyba kompilátoru C3488](compiler-error-c3488.md)|"&*identifikátor*" není povolený, pokud výchozí režim sběru je podle odkazu|
|[Chyba kompilátoru C3489](compiler-error-c3489.md)|"&*identifikátor*" je potřeba po výchozí režim sběru dat na základě kopie|
|[Chyba kompilátoru C3490](compiler-error-c3490.md)|"*identifikátor*" nejde upravit, protože se přistupuje prostřednictvím objektu const.|
|[Chyba kompilátoru C3491](compiler-error-c3491.md)|"*identifikátor*': na základě kopie zachycení nelze upravit ve neměnitelnou výrazu lambda.|
|[Chyba kompilátoru C3492](compiler-error-c3492.md)|"*identifikátor*': nejde zachytit člen anonymního sjednocení|
|[Chyba kompilátoru C3493](compiler-error-c3493.md)|"*identifikátor*" nejde implicitně zachytit, protože nebyl zadán žádný výchozí režim sběru dat|
|C3494 chyby kompilátoru|"this" nejde zachytit explicitně, protože nadřazené režim sběru je nepovoluje|
|[Chyba kompilátoru C3495](compiler-error-c3495.md)|"*identifikátor*': identifikátor v zachycení musí být proměnná s automatickým trváním úložiště deklarovány v oboru dosahu lambdy|
|[Chyba kompilátoru C3496](compiler-error-c3496.md)|"this" se vždycky zachycuje na základě hodnoty: & Ignorovat|
|C3497 chyby kompilátoru|Nelze vytvořit konstruktor instance lambdy|
|[Chyba kompilátoru C3498](compiler-error-c3498.md)|"*identifikátor*': nejde zachytit proměnnou, která má typ spravovaného/WinRT|
|[Chyba kompilátoru C3499](compiler-error-c3499.md)|výraz lambda, který byl zadán mít návratový typ void nemůže vracet hodnotu.|

