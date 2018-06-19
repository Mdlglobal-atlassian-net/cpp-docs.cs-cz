---
title: C3400 chyby kompilátoru prostřednictvím C3499 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
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
dev_langs:
- C++
ms.assetid: a5651dfb-c402-4e01-b3ae-28f371e51d6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc3a06a5c39aff2fea0850879a8d95f757e1b66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285805"
---
# <a name="compiler-errors-c3400-through-c3499"></a>C3400 chyby kompilátoru prostřednictvím C3499

Články v této části dokumentace vysvětlují podmnožinu chybové zprávy, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Chybové zprávy

|Chyba|Zpráva|
|-----------|-------------|
|[Chyba kompilátoru C3400](compiler-error-c3400.md)|omezení cyklické závislosti týkajících se*constraint1*'a'*constraint2*.|
|C3401 chyby kompilátoru|'*specifikátor*': Neplatné sestavení přístup specifikátor - pouze privátní je povolena v šablony třídy|
|C3402 chyby kompilátoru|'*funkce*': nelze vyřešit přetížení kromě v aktuálním oboru|
|C3403 chyby kompilátoru|thread_local nelze použít s/clr: pure nebo/CLR: safe|
|C3404 chyby kompilátoru|'*vytvořit*': Chyba neočekávané syntaxe|
|C3405 chyby kompilátoru|'*funkce*': nelze vyřešit přetížení bez dokončení popisovač|
|C3406 chyby kompilátoru|'*– klíčové slovo*': nelze použít v specifikátor propracována typu|
|C3407 chyby kompilátoru|'*typu*se v tomto kontextu nelze použít|
|[Chyba kompilátoru C3408](compiler-error-c3408.md)|'*atribut*': atributu není povolená na definice šablony|
|[Chyba kompilátoru C3409](compiler-error-c3409.md)|není povolen prázdný atribut bloku|
|C3410 chyby kompilátoru|'*identifikátor*': typ explicitní vytvoření instance '*typ*: neodpovídá typ proměnné šablony'*typ*.|
|C3411 chyby kompilátoru|'*typ*' není platná jako velikost pole, protože se nejedná o typ celé číslo|
|[Chyba kompilátoru C3412](compiler-error-c3412.md)|'*specializace*': nelze specialize šablony v aktuálním oboru|
|[Chyba kompilátoru C3413](compiler-error-c3413.md)|'*šablony*': Neplatný explicitní vytvoření instance|
|[Chyba kompilátoru C3414](compiler-error-c3414.md)|'*funkce*': nemůže být definovaný importované – členská funkce|
|[Chyba kompilátoru C3415](compiler-error-c3415.md)|více '*části*se oddíly s různé atributy nalezen (0 x*hodnotu*')|
|C3416 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3417](compiler-error-c3417.md)|'*deklarátor*': hodnota typy nemohou obsahovat uživatelem definované speciální členské funkce|
|[Chyba kompilátoru C3418](compiler-error-c3418.md)|přístup k specifikátor '*specifikátor*' není podporován|
|C3419 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3420](compiler-error-c3420.md)|'*funkce*': finalizační metody nemůže být virtuální|
|[Chyba kompilátoru C3421](compiler-error-c3421.md)|'*funkce*': finalizační metodu nelze volat pro tuto třídu, jako je buď nedostupné nebo neexistuje|
|C3422 chyby kompilátoru|'*deklarace*': Neshoda typů se*typ*'a'*typ*.|
|C3423 chyby kompilátoru|Zastaralé.|
|C3424 chyby kompilátoru|'*typ*': funkce styl přetypovat na typ pole není povolen.|
|C3425 chyby kompilátoru|Nelze vyvolat ukazatele na objekt neúplné typu '*typu*.|
|C3426 chyby kompilátoru|Nelze vyvolat objekt neúplné typu '*typu*.|
|C3427 chyby kompilátoru|'*kontextu*': '*– klíčové slovo*' nelze použít s layout_version (*číslo*)|
|C3428 chyby kompilátoru|'*kontextu*': '*– klíčové slovo*' lze použít pouze na deklaracích třídy nebo definice|
|C3429 chyby kompilátoru|'*kontextu*': '*– klíčové slovo*' nelze použít ke sjednocení|
|C3430 chyby kompilátoru|vymezená výčtu musí mít název|
|C3431 chyby kompilátoru|'*identifikátor*': *type1* nelze deklarovat jako *type2*|
|C3432 chyby kompilátoru|'*identifikátor*': deklaraci předat dál bez ohledu na obor výčtu musí mít základní typ|
|C3433 chyby kompilátoru|'*identifikátor*': všechny deklarace výčtu musí mít stejnou základní typ, byl '*type1*'nyní'*type2*.|
|C3434 chyby kompilátoru|'*kontextu*': hodnotu výčtu,*číslo*'nemůže být reprezentován jako'*typ*', hodnota je'*číslo*.|
|C3435 chyby kompilátoru|Znaková sada,*název*' není podporován|
|C3436 chyby kompilátoru|setlocale – #pragma není podporováno, když byla zadána /source-charset, /execution-charset nebo /utf-8|
|C3437 chyby kompilátoru|#pragma execution_character_set není podporováno, když byla zadána /source-charset, /execution-charset nebo /utf-8|
|C3438 chyby kompilátoru|'*kontextu*': '*hodnotu*' nelze použít pro třídu spravované nebo WinRT|
|C3439 chyby kompilátoru|layout_version (*číslo*): Neplatné číslo verze|
|C3440 chyby kompilátoru|'*deklarace*': layout_version (*číslo*) není kompatibilní s předchozím prohlášením|
|C3441 chyby kompilátoru|'*deklarace*': '*– klíčové slovo*' nelze použít po definování třídy|
|C3442 chyby kompilátoru|Inicializace více členů sjednocení: '*člen1*'a'*člen2*.|
|C3443 chyby kompilátoru|Výchozí člen inicializátoru pro '*třída*' je rekurzivní|
|C3444 chyby kompilátoru|Prázdný agregační třída *– třída*'musí být inicializován s'{}.|
|[C3445 chyby kompilátoru](compiler-error-c3445.md)|kopie – seznam inicializace '*typ*' nelze použít explicitní konstruktor|
|[Chyba kompilátoru C3446](compiler-error-c3446.md)|'*třída*': inicializátoru výchozí člen není povolen pro člena – hodnotová třída|
|C3447 chyby kompilátoru|Zastaralé.|
|C3448 chyby kompilátoru|Zastaralé.|
|C3449 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3450](compiler-error-c3450.md)|'*typ*': není atribut; nelze zadat [System::AttributeUsageAttribute] nebo [Windows::Foundation::Metadata::AttributeUsageAttribute]|
|[Chyba kompilátoru C3451](compiler-error-c3451.md)|'*atribut*': nelze použít nespravované atribut '*typu*.|
|[Chyba kompilátoru C3452](compiler-error-c3452.md)|Seznam argumentů člen není konstantní|
|[Chyba kompilátoru C3453](compiler-error-c3453.md)|'*atribut*': atribut není použít, protože kvalifikátor '*kvalifikátor*' neodpovídá|
|[Chyba kompilátoru C3454](compiler-error-c3454.md)|[atribut] není povoleno v deklaraci třídy|
|[Chyba kompilátoru C3455](compiler-error-c3455.md)|'*atribut*': žádná z konstruktoru atributu neodpovídala argumenty|
|[Chyba kompilátoru C3456](compiler-error-c3456.md)|[zdroj\_annotation_attribute] nejsou povoleny v deklaraci třídy spravované nebo WinRT|
|[Chyba kompilátoru C3457](compiler-error-c3457.md)|'*atribut*': atribut nepodporuje nepojmenované argumenty|
|[Chyba kompilátoru C3458](compiler-error-c3458.md)|"[*atribut*]': atribut ' [*atribut*]' již zadán pro '*identifikátor*.|
|[Chyba kompilátoru C3459](compiler-error-c3459.md)|"[*atribut*]': atribut povolena pouze v indexeru – třída (Výchozí indexované vlastnosti)|
|[Chyba kompilátoru C3460](compiler-error-c3460.md)|'*typ*': může být přeposílán pouze uživatelsky definovaný typ.|
|[Chyba kompilátoru C3461](compiler-error-c3461.md)|'*typ*': pouze typu spravované nebo WinRT může být přeposílán|
|[Chyba kompilátoru C3462](compiler-error-c3462.md)|'*typ*': pouze typ importované může být přeposílán|
|[Chyba kompilátoru C3463](compiler-error-c3463.md)|'*typ*': typ není povoleno v atribut 'implementuje.|
|[Chyba kompilátoru C3464](compiler-error-c3464.md)|'*typ*' nemůže být předán vnořené typy|
|[Chyba kompilátoru C3465](compiler-error-c3465.md)|Chcete použít typ '*typ*'musí odkazovat sestavení'*sestavení*.|
|[Chyba kompilátoru C3466](compiler-error-c3466.md)|'*typ*': nemůže být předán specializace obecné třídy|
|[Chyba kompilátoru C3467](compiler-error-c3467.md)|'*typ*': Tento typ již byly předány|
|[Chyba kompilátoru C3468](compiler-error-c3468.md)|'*typ*': Typ může předávat jenom k sestavení: '*identifikátor*' není sestavení.|
|[Chyba kompilátoru C3469](compiler-error-c3469.md)|'*typ*': nemůže být předán obecné třídy|
|[Chyba kompilátoru C3470](compiler-error-c3470.md)|'*třída*': třídu nemůže mít obě indexer (Výchozí indexované vlastnosti) a [] – operátor|
|C3471 chyby kompilátoru|nový název modulu *název* (set na příkazovém řádku) je v konfliktu s předchozí název *název*|
|C3472 chyby kompilátoru|nový název výstupního souboru *filename* (set na příkazovém řádku) je v konfliktu s předchozí název souboru *filename*|
|C3473 chyby kompilátoru|Výstupní cesta nebo modul nebyl zadán žádný název.|
|C3474 chyby kompilátoru|Nelze otevřít výstupní soubor '*filename*.|
|C3475 chyby kompilátoru|Chyba syntaxe ve vstupním souboru '*filename*.|
|C3476 chyby kompilátoru|Nelze otevřít soubor "*filename*' pro vstup|
|C3477 chyby kompilátoru|lambda se nemůže vyskytovat v kontextu unevaluated|
|C3478 chyby kompilátoru|'*identifikátor*': pole nemůže být zachyceny kopie|
|C3479 chyby kompilátoru|SAL – poznámky na lambdas nejsou podporovány.|
|[Chyba kompilátoru C3480](compiler-error-c3480.md)|'*proměnná*': zachycená proměnná lambda musí být ze nadřazených oboru – funkce|
|[Chyba kompilátoru C3481](compiler-error-c3481.md)|'*identifikátor*': lambda zachycená proměnná nebyla nalezena|
|[Chyba kompilátoru C3482](compiler-error-c3482.md)|'this' dá použít jenom jako zachycení lambda v rámci nestatické členské funkce|
|[Chyba kompilátoru C3483](compiler-error-c3483.md)|'*identifikátor*' je již součástí seznamu zachycení lambda|
|[Chyba kompilátoru C3484](compiler-error-c3484.md)|Chyba syntaxe: očekáváno '->' než návratový typ|
|[Chyba kompilátoru C3485](compiler-error-c3485.md)|definice lambda nemůže mít žádné kvalifikátory odchylka nákladů|
|C3486 chyby kompilátoru|Zastaralé.|
|[Chyba kompilátoru C3487](compiler-error-c3487.md)|'*typ*': všechny vrátit výrazy musí odvodit do stejného typu: byla dřív '*typu*.|
|[Chyba kompilátoru C3488](compiler-error-c3488.md)|"&*identifikátor*' není povolená, pokud je výchozí režim zachycení odkazem|
|[Chyba kompilátoru C3489](compiler-error-c3489.md)|"&*identifikátor*, je potřeba při kopírování, je výchozí režim zachytávání|
|[Chyba kompilátoru C3490](compiler-error-c3490.md)|'*identifikátor*' nelze upravit, protože je přistupuje prostřednictvím const objektu|
|[Chyba kompilátoru C3491](compiler-error-c3491.md)|'*identifikátor*': podle kopie nemůže být upravena zachycení v neměnitelnou lambda|
|[Chyba kompilátoru C3492](compiler-error-c3492.md)|'*identifikátor*': nemůže zaznamenat členem anonymní sjednocení|
|[Chyba kompilátoru C3493](compiler-error-c3493.md)|'*identifikátor*, nebude možné zaznamenat implicitně, protože nebyl zadán žádný výchozí režim zachytávání|
|C3494 chyby kompilátoru|'this' nebude možné zaznamenat explicitně protože nadřazených režim zachytávání neumožňuje|
|[Chyba kompilátoru C3495](compiler-error-c3495.md)|'*identifikátor*': identifikátor v zachycení musí být proměnná s dobou trvání automatické úložiště deklarované v rozsáhlejší oboru argument lambda|
|[Chyba kompilátoru C3496](compiler-error-c3496.md)|hodnota vždy zachycenou 'this': 'a' ignorovat|
|C3497 chyby kompilátoru|Nelze vytvořit instanci lambda|
|[Chyba kompilátoru C3498](compiler-error-c3498.md)|'*identifikátor*': nemůže zaznamenat proměnnou, která má typ spravované nebo WinRT|
|[Chyba kompilátoru C3499](compiler-error-c3499.md)|lambda, který byl zadaný mít typ vrácené hodnoty void nelze vrátit hodnotu|

