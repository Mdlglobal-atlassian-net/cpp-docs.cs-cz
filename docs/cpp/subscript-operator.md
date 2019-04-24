---
title: Operátor dolního indexu]
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: 2d55c18d2c9faa1a704bea129f2551937e76133c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266891"
---
# <a name="subscript-operator-"></a>Operátor dolního indexu]

## <a name="syntax"></a>Syntaxe

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Poznámky

Výraz přípony (může to také být primární výraz) za nímž následuje operátor dolního indexu **[] č.**, určuje indexování pole.

Informace o spravovaných polí v C++vyhodnocovací, naleznete v tématu [pole](../extensions/arrays-cpp-component-extensions.md).

Obvykle hodnota reprezentovaná *postfix-expression* je hodnota ukazatele, jako je například identifikátor pole a *výraz* je celé číslo (včetně výčtových typů). Všechny možnosti, které je však vyžaduje syntakticky je jeden z výrazů být typu ukazatele a druhý být celočíselného typu. Proto může být celočíselná hodnota v *postfix-expression* pozice a hodnota ukazatele může být v závorkách v *výraz* nebo dolní index pozice. Předpokládejme následující fragment kódu:

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

V předchozím příkladu výraz `nArray[2]` je stejný jako `2[nArray]`. Důvodem je, že výsledek výrazu dolního indexu `e1[e2]` je dán:

`*((e2) + (e1))`

Adresa výsledkem výrazu není *e2* bajtů z adresy *e1*. Místo toho je adresa škálovat na další objekt v poli *e2*. Příklad:

```cpp
double aDbl[2];
```

Adresy `aDb[0]` a `aDb[1]` jsou od sebe 8 bajtů – velikost objektu typu **double**. Škálování podle typu objektu se automaticky stará jazyka C++ a je definován v [operátory součtu](../cpp/additive-operators-plus-and.md) kde je popsána sčítání a odčítání operandy typu ukazatel.

Výraz dolního indexu může mít také více dolních indexů následovně:

*Expression1* **[** *expression2* **] [** *expression3* **]** ...

Výrazy dolního indexu se přiřazují zleva doprava. Úplně vlevo výraz dolního indexu *expression1* **[** *expression2* **]**, je vyhodnocen jako první. Adresa, která je výsledkem přidání *expression1* a *expression2* tvoří výraz ukazatele; potom *expression3* se přidá k tomuto výrazu ukazatele a vytvoří nový výraz ukazatele, a tak dále, dokud se přidala posledního výrazu dolního indexu. Operátor dereference (<strong>\*</strong>) se použijí po vyhodnocení posledního výrazu dolního indexu, pokud hodnota konečné ukazatele odkazuje typ pole.

Výrazy s více dolními indexy odkazují na prvky vícedimenzionální pole. Vícerozměrné pole je pole, jehož prvky jsou pole. Například, první prvek trojrozměrného pole je dvourozměrné pole. Následující příklad deklaruje a inicializuje jednoduché dvourozměrné pole znaků:

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>Kladné a záporné dolní indexy

První prvek pole je prvek 0. Rozsah C++ pole je z *pole*[0] do *pole*[*velikost* - 1]. Jazyk C++ však podporuje kladné a záporné dolní indexy. Záporné dolní indexy musí spadat do hranice pole; Pokud tomu tak není, jsou výsledky nepředvídatelné. Následující kód ukazuje pole kladné a záporné dolní indexy:

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

Záporný subscript na posledním řádku můžete vytvořit chyb za běhu, protože odkazuje na adresu 256 **int** pozice nižší v paměti, než je počátek pole. Ukazatel `midArray` je inicializován ve středu `intArray`; je proto možné (ale) používat oba kladné a záporné pole indexů na něj. Chyby dolního indexu pole negenerují chyby v době kompilace, ale vedou k nepředvídatelným výsledkům.

Operátor dolního indexu je komutativní. Proto výrazy *pole*[*index*] a *index*[*pole*] je zaručeno, že jako ekvivalentní, pokud je to dolního indexu není přetížen operátor (viz [přetížené operátory](../cpp/operator-overloading.md)). První forma je nejběžnějším způsobem kódování, ale funguje kterákoli z nich.

## <a name="see-also"></a>Viz také:

[Výrazy přípony](../cpp/postfix-expressions.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Pole](../cpp/arrays-cpp.md)<br/>
[Jednorozměrná pole](../c-language/one-dimensional-arrays.md)<br/>
[Vícerozměrná pole](../c-language/multidimensional-arrays-c.md)<br/>
