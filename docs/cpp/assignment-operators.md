---
title: Operátory přiřazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- cpp-language
ms.topic: language-reference
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
- '&&='
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], C++
- '&= operator'
- '&&= operator'
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd26c8b9fd044c9f6372ef0a680fbc770620e43d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408584"
---
# <a name="assignment-operators"></a>Operátory přiřazení
## <a name="syntax"></a>Syntaxe  
  
```  
expression assignment-operator expression   
assignment-operator : one of  
   =   *=   /=   %=   +=   -=   <<=   >>=   &=   ^=   |=  &&=
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory přiřazení ukládají hodnotu v objektu určeném levým operandem. Existují tři typy operací přiřazení: 

1. jednoduché přiřazení, ve kterém je hodnota druhého operandu uložena v objektu určeném prvním operandem. 1. složené přiřazení, ve kterém aritmetický, posunu nebo bitová operace provádí před uložením výsledku.
1. které prostředky jsou přeneseny bez kopírování přesuňte přiřazení (pro typy tříd).


Všechny operátory přiřazení v následující tabulce s výjimkou = a & & = složené operátory přiřazení jsou operátory.  
  
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
|**&&=**| Operátor přiřazení přesunutí (třída pouze pro typy). Pokud je druhý operand je typu rvalue, jeho prostředky přesunout do prvního operandu (bez kopírování). Zobrazit [konstruktory přesunutí a operátory přiřazení přesunutí](move-constructors-and-move-assignment-operators-cpp.md) Další informace.|
  
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
 Operátor jednoduchého přiřazení (=) způsobí, že je hodnota druhého operandu uložena v objektu, který je zadán prvním operandem. Jsou-li oba objekty aritmetickými typy, je pravý operand před uložením hodnoty převeden na typ levého operandu.  
  
 Objekty typů const a volatile lze přiřadit l-hodnotám typů, které jsou pouze typu volatile nebo typům, které jsou const, nikoli však volatile.  
  
 Přiřazení k objektům typu třídy (typy struct, union a class) je prováděno pomocí funkce operátoru pojmenování =. Výchozí chování této funkce operátoru je provedení bitového kopírování. Toto chování lze však změnit pomocí přetížených operátorů. (Viz [přetížené operátory](../cpp/operator-overloading.md) Další informace.)  
  
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
  
-   Pro `UserType2` je třeba zavolat funkční operátor =, který je součástí argumentu `UserType1`.  
  
-   Bude-li taková funkce existovat, je třeba zavolat funkci explicitního převodu `UserType1::operator UserType2`.  
  
-   Dále je třeba zavolat konstruktor `UserType2::UserType2` za předpokladu, že takový konstruktor existuje a přebírá argument `UserType1` a zkopíruje výsledek.  
  
## <a name="compound-assignment"></a>Složené přiřazení  
 Operátory složeného přiřazení, uvedené v tabulce v [operátory přiřazení](../cpp/assignment-operators.md), jsou uvedeny ve tvaru *e1* `op` =  *e2*, kde *e1* je upravitelná l hodnota nekonstantního typu a *e2* je jedním z následujících akcí:  
  
-   Aritmetický typ  
  
-   Ukazatel, pokud `op` je + nebo -  
  
 *E1* `op` =  *e2* formulář chovat jako *e1* *= e1* `op` *e2*, ale *e1* se vyhodnotí pouze jednou.  
  
 Složené přiřazení výčtového typu vygeneruje chybovou zprávu. Je-li levý operand typu ukazatele, pravý operand musí být typu ukazatele nebo musí být konstantním výrazem vyhodnoceným na hodnotu 0. Je-li levý operand celočíselný typ, nesmí být pravý operand typu ukazatele.  
  
## <a name="result-of-assignment-operators"></a>Výsledek operátorů přiřazení  
 Operátory přiřazení vrací hodnotu objektu určeném levým operandem po přiřazení. Výsledný typ je typ levého operandu. Výsledek výrazu přiřazení je vždy l hodnotou. Tyto operátory mají asociativitu zprava doleva. Levý operand musí být upravitelná l hodnota.  
  
 Ve standardu ANSI C výsledek výrazu přiřazení není l hodnotou. Proto platný výraz jazyka C++ `(a += b) += c` je neplatné. v jazyce C.  
  
## <a name="see-also"></a>Viz také:  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)