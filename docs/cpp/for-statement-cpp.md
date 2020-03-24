---
title: for – příkaz (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: e3dfdb45bdf8a508eca9d29e90b3f7c05e7b147d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179910"
---
# <a name="for-statement-c"></a>for – příkaz (C++)

Spustí příkaz opakovaně, dokud podmínka nebude nepravda. Informace o příkazu for založeném na rozsahu naleznete v tématu [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Syntaxe

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>Poznámky

Použijte příkaz **for** k vytvoření smyček, které musí být spuštěny určeného počtu opakování.

Příkaz **for** se skládá ze tří volitelných částí, jak je znázorněno v následující tabulce.

### <a name="for-loop-elements"></a>Prvky smyčky for

|Název syntaxe|Při provedení|Popis|
|-----------------|-------------------|-----------------|
|`init-expression`|Před jakýmkoli jiným prvkem příkazu **for** je `init-expression` proveden pouze jednou. Řízení pak předá `cond-expression`.|Často se používá k inicializaci indexů smyčky. Může obsahovat výrazy nebo deklarace.|
|`cond-expression`|Před spuštěním každé iterace `statement`, včetně první iterace. `statement` se spustí jenom v případě, že se `cond-expression` vyhodnotí jako true (nenulový).|Výraz, jehož výsledkem je integrální typ nebo typ třídy, která má jednoznačný převod na integrální typ. Obvykle se používá k testování kritérií pro ukončení smyčky.|
|`loop-expression`|Na konci každé iterace `statement`. Po provedení `loop-expression` se vyhodnotí `cond-expression`.|Obvykle se používá pro zvýšení indexu smyčky.|

Následující příklady znázorňují různé způsoby použití příkazu **for** .

```cpp
#include <iostream>
using namespace std;

int main() {
    // The counter variable can be declared in the init-expression.
    for (int i = 0; i < 2; i++ ){
       cout << i;
    }
    // Output: 01
    // The counter variable can be declared outside the for loop.
    int i;
    for (i = 0; i < 2; i++){
        cout << i;
    }
    // Output: 01
    // These for loops are the equivalent of a while loop.
    i = 0;
    while (i < 2){
        cout << i++;
    }
}
    // Output: 012
```

`init-expression` a `loop-expression` mohou obsahovat více příkazů oddělených čárkami. Příklad:

```cpp
#include <iostream>
using namespace std;

int main(){
    int i, j;
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {
        cout << "i + j = " << (i + j) << '\n';
    }
}
    // Output:
    i + j = 15
    i + j = 17
    i + j = 19
```

`loop-expression` lze zvýšit nebo snížit nebo upravit jiným způsobem.

```cpp
#include <iostream>
using namespace std;

int main(){
for (int i = 10; i > 0; i--) {
        cout << i << ' ';
    }
    // Output: 10 9 8 7 6 5 4 3 2 1
    for (int i = 10; i < 20; i = i+2) {
        cout << i << ' ';
    }
    // Output: 10 12 14 16 18
```

Smyčka **for** končí v případě, že je proveden příkaz [Break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md)nebo [goto](../cpp/goto-statement-cpp.md) (na označený příkaz mimo smyčku **for** ) v rámci `statement`. Příkaz [Continue](../cpp/continue-statement-cpp.md) ve smyčce **for** ukončí pouze aktuální iteraci.

Pokud je hodnota `cond-expression` vynechána, je považována za true a smyčka **for** se neukončí bez **přerušení**, **vrácení**nebo **goto** v rámci `statement`.

I když jsou tři pole příkazu **for** obvykle používána pro inicializaci, testování pro ukončení a zvýšení, nejsou omezeny na tato použití. Následující kód například tiskne čísla 0 až 4. V tomto případě je `statement` příkaz null:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for( i = 0; i < 5; cout << i << '\n', i++){
        ;
    }
}
```

## <a name="for-loops-and-the-c-standard"></a>Smyčky for a standard jazyka C++

C++ Standard říká, že Proměnná deklarovaná ve smyčce **for** musí přejít mimo rozsah po ukončení smyčky **for** . Příklad:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Ve výchozím nastavení v části [/ze](../build/reference/za-ze-disable-language-extensions.md)Proměnná deklarovaná ve smyčce **for** zůstává v oboru až do konce ohraničujícího oboru smyčky **for** .

[/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) umožňuje standardní chování proměnných deklarovaných ve smyčkách for, aniž by bylo nutné zadat `/Za`.

Je také možné použít rozdíly v oboru smyčky **for** pro redeklaraci proměnných v rámci `/Ze` následujícím způsobem:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

To přesněji napodobuje standardní chování proměnné deklarované ve smyčce **for** , což vyžaduje, aby proměnné deklarované ve smyčce **for** přešly mimo rozsah po dokončení smyčky. Pokud je proměnná deklarována ve smyčce **for** , kompilátor interně propaguje místní proměnnou v ohraničujícím oboru smyčky **for** , i když již existuje místní proměnná se stejným názvem.

## <a name="see-also"></a>Viz také

[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[while – příkaz (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)
