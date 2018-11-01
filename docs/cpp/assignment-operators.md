---
title: Operátory přiřazení
ms.date: 03/05/2018
f1_keywords:
- =
- '*='
- /=
- '%='
- +=
- -=
- <<=
- '>>='
- '&='
- ^=
- '|='
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- ^= operator
- += operator
- '>>= operator'
- '|= operator'
- operator>>=
- '*= operator'
- '%= operator'
- ^= operator
- operator >>=
- = operator
- -= operator
- /= operator
- <<= operator
ms.assetid: b028cf35-2ff1-4f14-9027-fd53ebec8aa0
ms.openlocfilehash: d435ea051610f9ffa496f41f364ffc1c81694b61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617396"
---
# <a name="assignment-operators"></a>Operátory přiřazení

## <a name="syntax"></a>Syntaxe

*výraz* *operátor přiřazení* *výraz*

*operátor přiřazení* : jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>= * =, / = % =, +=,-= \< \<= >> = & = ^ =   \|=</strong>

## <a name="remarks"></a>Poznámky

Operátory přiřazení ukládají hodnotu v objektu určeném levým operandem. Existují dva typy operací přiřazení:

1. *jednoduché přiřazení*, ve které je uložený hodnotu druhého operandu v objektu určeném prvním operandem.

1. *složené přiřazení*, ve kterém aritmetický, posunu nebo bitová operace provádí před uložením výsledku.

Všechny operátory přiřazení v následující tabulce, s výjimkou operátoru =, jsou operátory složeného přiřazení.

### <a name="assignment-operators"></a>Operátory přiřazení

|Operátor|Význam|
|--------------|-------------|
|**=**|Uloží hodnotu druhého operandu v objektu určeném prvním operandem (jednoduché přiřazení).|
|**\*=**|Vynásobí hodnotu prvního operandu hodnotou druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**/=**|Vydělí hodnotu prvního operandu hodnotou druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**%=**|Vezme numerický zbytek prvního operandu určený hodnotou druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**+=**|Přičte hodnotu druhého operandu k hodnotě prvního operandu a uloží výsledek v objektu určeném prvním operandem.|
|**-=**|Odečte hodnotu druhého operandu od hodnoty prvního operandu a uloží výsledek v objektu určeném prvním operandem.|
|**<\<=**|Posune hodnotu prvního operandu vlevo o počet bitů určený hodnotou druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**>>=**|Posune hodnotu prvního operandu vpravo o počet bitů určený hodnotou druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**&=**|Získá bitový AND prvního a druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**^=**|Získá bitový exkluzivní OR prvního a druhého operandu a uloží výsledek v objektu určeném prvním operandem.|
|**\|=**|Získá bitový inkluzivní OR prvního a druhého operandu a uloží výsledek v objektu určeném prvním operandem.|

**Klíčová slova operátorů**

Tři operátory složeného přiřazení mají textové ekvivalenty. Možnosti jsou následující:

|Operátor|Ekvivalent|
|--------------|----------------|
|**&=**|`and_eq`|
|**\|=**|`or_eq`|
|**^=**|`xor_eq`|

Existují dva způsoby přístupu k těmto klíčovým slovům operátorů v programech: zahrnutím souboru hlaviček `iso646.h`, nebo kompilací s [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru (zakázání jazykových rozšíření).

## <a name="example"></a>Příklad

```cpp
// expre_Assignment_Operators.cpp
// compile with: /EHsc
// Demonstrate assignment operators
#include <iostream>
using namespace std;
int main() {
   int a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555;

   a += b;      // a is 9
   b %= a;      // b is 6
   c >>= 1;      // c is 5
   d |= e;      // Bitwise--d is 0xFFFF

   cout  << "a = 3, b = 6, c = 10, d = 0xAAAA, e = 0x5555" << endl
         << "a += b yields " << a << endl
         << "b %= a yields " << b << endl
         << "c >>= 1 yields " << c << endl
         << "d |= e yields " << hex << d << endl;
}
```

## <a name="simple-assignment"></a>Jednoduché přiřazení

Operátor jednoduchého přiřazení (**=**) způsobí, že hodnota druhého operandu uložena v objektu určeném prvním operandem. Jsou-li oba objekty aritmetickými typy, je pravý operand před uložením hodnoty převeden na typ levého operandu.

Objekty **const** a **volatile** typy je možné přiřadit l-hodnotám typů, které jsou právě **volatile** nebo ani jeden **const** ani **volatile**.

Přiřazení k objektům typu třídy (struct, union a typy tříd) se provádí pomocí funkce s názvem `operator=`. Výchozí chování této funkce operátoru je provedení bitového kopírování. Toto chování lze však změnit pomocí přetížených operátorů. Zobrazit [přetížení operátoru](../cpp/operator-overloading.md) Další informace. Kromě toho může mít typy tříd *zkopírujte přiřazení* a *přesunutí přiřazení* operátory. Další informace najdete v tématu [kopírovací konstruktory a operátory přiřazení pro kopírování](copy-constructors-and-copy-assignment-operators-cpp.md) a [konstruktory přesunutí a operátory přiřazení přesunutí](move-constructors-and-move-assignment-operators-cpp.md).

Objekt libovolné jednoznačně odvozené třídy z dané základní třídy lze přiřadit k objektu základní třídy. Opačně to neplatí, protože mezi odvozenou třídou a základní třídou existuje explicitní převod, který však neexistuje mezi základní a odvozenou třídou. Příklad:

```cpp
// expre_SimpleAssignment.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
class ABase
{
public:
    ABase() { cout << "constructing ABase\n"; }
};

class ADerived : public ABase
{
public:
    ADerived() { cout << "constructing ADerived\n"; }
};

int main()
{
    ABase aBase;
    ADerived aDerived;

    aBase = aDerived; // OK
    aDerived = aBase; // C2679
}
```

Přiřazení typů odkazů se chovají, jako by byla přiřazení k objektu, na nějž reference odkazuje, právě vytvořena.

U objektů typu třídy se přiřazení liší od inicializace. Pro ilustraci různých přiřazení a inicializací uvažujme následující kód

```cpp
UserType1 A;
UserType2 B = A;
```

Předchozí kód zobrazí inicializátor. Zavolá konstruktor `UserType2`, který přebírá argument typu `UserType1`. Vzhledem ke kódu

```cpp
UserType1 A;
UserType2 B;

B = A;
```

může příkaz přiřazení

```cpp
B = A;
```

mít jednu z následujících funkcí:

- Volání funkce `operator=` pro `UserType2`, k dispozici `operator=` je součástí služby `UserType1` argument.

- Bude-li taková funkce existovat, je třeba zavolat funkci explicitního převodu `UserType1::operator UserType2`.

- Dále je třeba zavolat konstruktor `UserType2::UserType2` za předpokladu, že takový konstruktor existuje a přebírá argument `UserType1` a zkopíruje výsledek.

## <a name="compound-assignment"></a>Složené přiřazení

Operátory složeného přiřazení, uvedené v tabulce v [operátory přiřazení](#assignment-operators), jsou uvedeny ve tvaru *e1* *op*= *e2*, kde *e1* je upravitelná l hodnota není **const** typ a *e2* je jedním z následujících akcí:

- Aritmetický typ

- Ukazatel, pokud *op* je **+** nebo **-**

*E1* *op*= *e2* formulář chovat jako *e1* **=** *e1* *op* *e2*, ale *e1* se vyhodnotí pouze jednou.

Složené přiřazení výčtového typu vygeneruje chybovou zprávu. Je-li levý operand typu ukazatele, pravý operand musí být typu ukazatele nebo musí být konstantním výrazem vyhodnoceným na hodnotu 0. Je-li levý operand celočíselný typ, nesmí být pravý operand typu ukazatele.

## <a name="result-of-assignment-operators"></a>Výsledek operátorů přiřazení

Operátory přiřazení vrací hodnotu objektu určeném levým operandem po přiřazení. Výsledný typ je typ levého operandu. Výsledek výrazu přiřazení je vždy l hodnotou. Tyto operátory mají asociativitu zprava doleva. Levý operand musí být upravitelná l hodnota.

Ve standardu ANSI C výsledek výrazu přiřazení není l hodnotou. Proto platný výraz jazyka C++ `(a += b) += c` je neplatné. v jazyce C.

## <a name="see-also"></a>Viz také:

[Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)<br/>
[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)
