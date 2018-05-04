---
title: 'Relační operátory: &lt;, &gt;, &lt;=, a &gt;= | Microsoft Docs'
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
ms.openlocfilehash: ea629afbe975e60e9fc4f25e51d757eb3f0f8728
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
  
 Relační operátory mají asociativitu operátorů zleva doprava. Oba operandy relačních operátorů musejí mít aritmetický typ nebo typ ukazatele. Dávají hodnoty typu `bool`. Vrácená hodnota **false** (0) Pokud je vztah ve výrazu false; jinak hodnota, je hodnota vrácená **true** (1).  
  
## <a name="example"></a>Příklad  
  
```  
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
  
 Výrazy v předchozím příkladu musí být uzavřena v závorkách, protože operátor vložení datového proudu (**<<**) má vyšší prioritu než relační operátory. První výraz bez závorek by tedy byl vyhodnocen jako:  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 Obvyklé aritmetické převody zahrnutých v [standardní převody](standard-conversions.md) se použijí pro operandy aritmetické typy.  
  
## <a name="comparing-pointers"></a>Porovnání ukazatelů  
 Při porovnání dvou ukazatelů s objekty stejného typu je výsledek určen umístěním objektů, na které je odkazováno v adresním prostoru programu. Ukazatele je také možné porovnat s konstantním výrazem, který je vyhodnocen na hodnotu 0 nebo na ukazatel typu void *. Pokud se ukazatel je provedeno porovnání proti ukazatel typu void \*, jiné ukazatele je implicitně převést na typ void \*. Poté je provedeno porovnání.  
  
 Dva ukazatele na různé typy nelze srovnávat, pokud:  
  
-   jeden typ není typem třídy odvozeným z jiného typu,  
  
-   alespoň jeden z ukazatelů není explicitně převeden (přetypován) na typ void *, (Další ukazatele je implicitně převést na typ void \* pro převod.)  
  
 není zaručeno, že dva odkazy stejného typu, které odkazují na stejný objekt, budou při porovnávání stejné. Pokud jsou porovnány dva ukazatele na nestatické členy objektu, platí následující pravidla:  
  
-   Pokud není typu třídy sjednocení a pokud nejsou oddělených dva členy *specifikátor přístupu*, jako je například veřejná chráněný, nebo privátní, má ukazatel na člena deklarovaný poslední se porovná větší než ukazatele na člena deklarovaný dříve.  
  
-   Pokud jsou odděleny dva členy *specifikátor přístupu*, výsledky nejsou definovány.  
  
-   Pokud je typ třídy sjednocení, ukazatele na různé datové členy v tomto sjednocení budou při porovnávání stejné.  
  
 Pokud dva ukazatele odkazují na prvky stejného pole nebo na prvek, který je za koncem tohoto pole, ukazatel na objekt s vyšším dolním indexem bude při porovnávání větší. Porovnání ukazatelů je zaručeno pouze v případě, že ukazatele odkazují na objekty stejného pole nebo na umístění za koncem pole.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Relační operátory a operátory rovnosti jazyka C](../c-language/c-relational-and-equality-operators.md)