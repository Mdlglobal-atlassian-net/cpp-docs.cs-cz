---
title: "Operátory přírůstku a snížení přípony: ++ a--| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e1d6c13da3023073f3d8b3e9625fa141253ba2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operátory přírůstku a snížení přípony: ++ a --
## <a name="syntax"></a>Syntaxe  
  
```  
postfix-expression ++  
postfix-expression --  
```  
  
## <a name="remarks"></a>Poznámky  
 Jazyk C++ poskytuje předponové a příponové operátory inkrementace a dekrementace. Tato část popisuje pouze příponové operátory inkrementace a dekrementace. (Další informace najdete v tématu [předpony přírůstku a snížení](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) Rozdíl mezi nimi je, že notaci operátory, zobrazí se operátor po *operátory výraz*, zatímco v zápisu předpony operátor se zobrazuje před *výraz.* Následující příklad ukazuje příponový operátor inkrementace:  
  
```  
i++;  
```  
  
 Účinkem použití příponového operátoru inkrementace (`++`) je zvýšení hodnoty operandu o jednu jednotku příslušného typu. Podobně účinek použití operátor snížení operátory (**--**) je, že je hodnota operand snížila o jednu jednotku příslušného typu.  
  
 Je důležité si uvědomit, že operátory zvýší nebo snížení výraz vyhodnocen jako hodnota výrazu **před** operátoru příslušné aplikace. Přírůstek nebo snížení operace probíhá, **po** operand je vyhodnocena. K tomuto problému dochází pouze v případě výskytu příponové operace inkrementace či dekrementace v kontextu rozsáhlejšího výrazu.  
  
 Je-li příponový operátor použit v argumentu funkce, není zaručeno, že hodnota argumentu bude zvýšena nebo snížena před jeho předáním funkci.  Další informace naleznete v oddílu 1.9.17 standardu jazyka C++.  
  
 Použití operátor přírůstku operátory na ukazatel na pole objektů typu **dlouho** ve skutečnosti přidá čtyři do interního vyjádření ukazatele. To způsobí, že ukazatele, který dříve uvedené  *n* element TD pole, který bude odkazovat na (*n*+ 1) element TD.  
  
 Operandy přípony přírůstek a snížení přípony musí být upravitelnými (ne **const**) hodnoty l aritmetické nebo ukazatel typu. Typ výsledku je stejný jako u *operátory výraz*, ale je už l hodnota.  
  
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand operátory přírůstek nebo snížení operátor nesmí být typu `bool`.
  
 Následující kód znázorňuje příponový operátor inkrementace:  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 Operace následného zvýšení nebo snížení nejsou podporovány pro výčtové typy:  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy přípony](../cpp/postfix-expressions.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operátory inkrementace a dekrementace přípony jazyka C](../c-language/c-postfix-increment-and-decrement-operators.md)