---
title: 'Podmíněný operátor:? : | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '?:'
- '?'
dev_langs:
- C++
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 296ced0754dd12017353469845b3bc4b30e0dc11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="conditional-operator--"></a>Podmíněný operátor:? :
## <a name="syntax"></a>Syntaxe  
  
```  
  
expression ? expression : expression  
```  
  
## <a name="remarks"></a>Poznámky  
 Podmíněný operátor (**?:**) je ternární operátor (má tři operandy). Podmíněný operátor pracuje následujícím způsobem:  
  
-   První operand je implicitně převeden na typ `bool`. Je vyhodnocen a před pokračováním jsou dokončeny všechny vedlejší účinky.  
  
-   Pokud je výsledkem první operand **true** (1), druhý operand vyhodnotí.  
  
-   Pokud je výsledkem první operand **false** (0), vyhodnotí třetí operand.  
  
 Výsledek podmíněného operátoru je určen podle toho, který operand je vyhodnocen, zda druhý nebo třetí. V podmíněném výrazu je vyhodnocen pouze jeden z posledních dvou operandů.  
  
 Podmíněné výrazy mají asociativitu zprava doleva. První operand musí být celočíselného typu nebo typu ukazatele. Pro operandy druhý a třetí platí následující pravidla:  
  
-   Pokud jsou oba operandy stejného typu, výsledkem je daného typu.  
  
-   Pokud jsou oba operandy aritmetické nebo výčtových typů, obvyklé aritmetické převody (popsaná v [standardní převody](standard-conversions.md)) se provádí je převést na stejného typu.  
  
-   Pokud jsou oba operandy typů ukazatele nebo pokud jeden je ukazatel typu a druhá je konstantní výraz, který se vyhodnotí na hodnotu 0, jsou prováděny převody ukazatele je převést na stejného typu.  
  
-   Pokud jsou oba operandy typu odkazů, jsou prováděny převody odkazů je převést na stejného typu.  
  
-   Pokud jsou oba operandy typu void, běžné typ je typ void.  
  
-   Pokud jsou oba operandy stejného typu definovaný uživatelem, je běžné typ typu.  
  
-   Pokud máte operandy různé typy a alespoň jeden z operandy má uživatelsky definovaný typ. jazyk pravidla se používají k určení obecným typem. (Viz níže uvedené upozornění.)  
  
 Jakékoli kombinace druhého a třetího operandu, které nejsou uvedeny v předchozím seznamu, jsou neplatné. Typ výsledku je společný typ a je to l-hodnota, pokud jsou druhý i třetí operand stejného typu a oba jsou l-hodnoty.  
  
> [!WARNING]
>  Pokud nejsou identické typy operandů druhý a třetí, jsou vyvolány pravidel převodu komplexního typu, jak je uvedeno v C++ Standard. Tyto převody může vést k neočekávanému chování, včetně vytváření a odstraňování dočasné objekty. Z tohoto důvodu doporučujeme důrazně vám buď (1) nepoužívejte uživatelem definované typy jako operandy s podmíněný operátor nebo (2) Pokud použijte uživatelem definované typy a potom explicitně přetypovat každý operand stejného typu.  
  
## <a name="example"></a>Příklad  
  
```  
// expre_Expressions_with_the_Conditional_Operator.cpp  
// compile with: /EHsc  
// Demonstrate conditional operator  
#include <iostream>  
using namespace std;  
int main() {  
   int i = 1, j = 2;  
   cout << ( i > j ? i : j ) << " is greater." << endl;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operátor podmíněného výrazu](../c-language/conditional-expression-operator.md)