---
title: for – příkaz (C++)
description: Odkaz na standardní C++ pro příkaz v Microsoft Visual Studio C++.
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 92f7ae4b1f2fbaaf710cd5a8739b78cb98a0accb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375387"
---
# <a name="for-statement-c"></a>for – příkaz (C++)

Spustí příkaz opakovaně, dokud podmínka nebude nepravda. Informace o příkazu pro příkaz založený na rozsahu naleznete v [tématu Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).

## <a name="syntax"></a>Syntaxe

> **`for (`***init-expression* **`;`** *cond-expression* **`;`** *loop-expression***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_Prohlášení_**`;`**

## <a name="remarks"></a>Poznámky

Pomocí příkazu **for** vytvořte smyčky, které musí provést zadaný počet opakování.

Příkaz **for** se skládá ze tří volitelných částí, jak je znázorněno v následující tabulce.

### <a name="for-loop-elements"></a>Prvky smyčky for

|Název syntaxe|Při provedení|Popis|
|-----------------|-------------------|-----------------|
|`init-expression`|Před jakýkoli jiný **for** prvek for `init-expression` prohlášení, je proveden pouze jednou. Ovládací prvek `cond-expression`pak předá .|Často se používá k inicializaci indexů smyčky. Může obsahovat výrazy nebo deklarace.|
|`cond-expression`|Před spuštěním každé `statement`iterace , včetně první iterace. `statement`je spuštěna `cond-expression` pouze v případě, že je vyhodnocena jako true (nenulová).|Výraz, jehož výsledkem je integrální typ nebo typ třídy, která má jednoznačný převod na integrální typ. Obvykle se používá k testování kritérií pro ukončení smyčky.|
|`loop-expression`|Na konci každé iterace `statement`. Po `loop-expression` provedení `cond-expression` je vyhodnocen.|Obvykle se používá pro zvýšení indexu smyčky.|

Následující příklady ukazují různé způsoby použití **příkazu for.**

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

`init-expression`a `loop-expression` může obsahovat více příkazů oddělených čárkami. Příklad:

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

`loop-expression`může být zbydžené nebo snížené nebo upravené jinými způsoby.

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

A **for** smyčky ukončí, když [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md) (na `statement` popisek příkazmimo **for** smyčky) uvnitř je proveden. Příkaz [continue](../cpp/continue-statement-cpp.md) ve smyčce **for** ukončí pouze aktuální iteraci.

Pokud `cond-expression` je vynechán, je `true`považován za a **for** smyčky nebude ukončena bez **přestávky**, **návrat**, nebo **goto** v . `statement`

Přestože tři pole **for** prohlášení se obvykle používají pro inicializaci, testování pro ukončení a zvýšení, nejsou omezeny na tato použití. Následující kód například tiskne čísla 0 až 4. V tomto `statement` případě je null prohlášení:

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

Standard C++ říká, že proměnná deklarovaná ve smyčce **for** musí po ukončení **smyčky for** vyřadit z rozsahu. Příklad:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

Ve výchozím nastavení v části [/Ze](../build/reference/za-ze-disable-language-extensions.md)zůstává proměnná deklarovaná ve smyčce **for** v oboru, dokud neskončí ohraničující obor **smyčky for.**

[/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) umožňuje standardní chování proměnných deklarovaných v `/Za`for loops bez nutnosti specifikovat .

Je také možné použít oborové rozdíly **for** smyčky znovu deklarovat `/Ze` proměnné v následujícím:

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

Toto chování více napodobuje standardní chování proměnné deklarované ve smyčce **for,** která vyžaduje proměnné deklarované ve smyčce **for,** aby po dokončení smyčky přešely mimo rozsah. Když je proměnná deklarována ve smyčce **for,** kompilátor ji interně povýší na místní proměnnou v oboru uzavření **smyčky for.** Je povýšen, i když již existuje místní proměnná se stejným názvem.

## <a name="see-also"></a>Viz také

[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[while Statement (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while příkaz (C++)](../cpp/do-while-statement-cpp.md)<br/>
[Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)
