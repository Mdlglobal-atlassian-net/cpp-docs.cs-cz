---
title: 'Relační operátory: &lt;, &gt;, &lt;=, a &gt;= | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- <
- '>'
dev_langs:
- C++
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 393cb0b23ca67877a18d2148af76c8de59d29f30
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465555"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Relační operátory: &lt;, &gt;, &lt;=, a &gt;=
## <a name="syntax"></a>Syntaxe  
  
```  
expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Binární relační operátory určují následující vztahy:  
  
-   Menší než (**\<**)  
  
-   Větší než (**>**)  
  
-   Menší než nebo rovno (**\<=**)  
  
-   Větší než nebo rovno (**>=**)  
  
 Relační operátory mají asociativitu operátorů zleva doprava. Oba operandy relačních operátorů musejí mít aritmetický typ nebo typ ukazatele. Dávají hodnoty typu **bool**. Vrácená hodnota je **false** (0) Pokud je vztah ve výrazu false; v opačném případě je vrácená hodnota **true** (1).  
  
## <a name="example"></a>Příklad  
  
```cpp 
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 Výrazy uvedené v předchozím příkladu musí být uzavřen v závorkách, protože operátor vkládání datového proudu (**<<**) má vyšší prioritu než relační operátory. První výraz bez závorek by tedy byl vyhodnocen jako:  
  
```cpp 
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 Obvyklé aritmetické převody uvedené v [standardní převody](standard-conversions.md) jsou použity na operandy aritmetických typů.  
  
## <a name="comparing-pointers"></a>Porovnání ukazatelů  
 Při porovnání dvou ukazatelů s objekty stejného typu je výsledek určen umístěním objektů, na které je odkazováno v adresním prostoru programu. Ukazatele je také možné porovnat s konstantním výrazem, který se vyhodnotí na hodnotu 0 nebo na ukazatel typu `void *`. Pokud je provedeno porovnání ukazatele s ukazatelem typu `void *`, druhý ukazatel implicitně převeden na typ `void *`. Poté je provedeno porovnání.  
  
 Dva ukazatele na různé typy nelze srovnávat, pokud:  
  
-   jeden typ není typem třídy odvozeným z jiného typu,  
  
-   Nejméně jeden z ukazatelů není explicitně převeden (přetypován) na typ `void *`. (Druhý ukazatel implicitně převeden na typ `void *` pro převod.)  
  
 není zaručeno, že dva odkazy stejného typu, které odkazují na stejný objekt, budou při porovnávání stejné. Pokud jsou porovnány dva ukazatele na nestatické členy objektu, platí následující pravidla:  
  
-   Pokud typ třídy není **sjednocení**, a pokud nejsou dva členy odděleny *access-specifier*, například **veřejné**, **chráněné**, nebo **privátní**, ukazatel na člen deklarovaný jako poslední při porovnání větší než ukazatel na člen deklarovaný dříve.  
  
-   Pokud jsou dva členy odděleny *access-specifier*, nejsou výsledky definovány.  
  
-   Pokud je typ třídy **sjednocení**, ukazatele na různé datové členy v dané **sjednocení** porovnání rovnosti.  
  
 Pokud dva ukazatele odkazují na prvky stejného pole nebo na prvek, který je za koncem tohoto pole, ukazatel na objekt s vyšším dolním indexem bude při porovnávání větší. Porovnání ukazatelů je zaručeno pouze v případě, že ukazatele odkazují na objekty stejného pole nebo na umístění za koncem pole.  
  
## <a name="see-also"></a>Viz také:  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Integrované operátory C++, Priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Relační operátory a operátory rovnosti jazyka C](../c-language/c-relational-and-equality-operators.md)