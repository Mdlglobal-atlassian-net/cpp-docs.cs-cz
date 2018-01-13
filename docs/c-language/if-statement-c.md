---
title: Pokud Statement (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- else
- if
dev_langs: C++
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb0e4929b55d6cfc0ef01ee183b74b2439b85d10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="if-statement-c"></a>if – příkaz (C)
**Pokud** příkaz Ovládací prvky podmíněného větvení. Text **Pokud** je spustit příkaz, pokud je hodnota výrazu nenulové hodnoty. Syntaxe **Pokud** příkaz má dva formuláře.  
  
## <a name="syntax"></a>Syntaxe  
 *Výběr příkaz*:  
 **Pokud (***výraz***)***– příkaz*   
  
 **Pokud (***výraz***)***příkaz***else***– příkaz*   
  
 V obou formy **Pokud** příkaz výrazy, což může mít libovolnou hodnotu kromě strukturu, jsou vyhodnoceny, včetně všech vedlejší účinky.  
  
 Ve formuláři první syntaxe Pokud *výraz* hodnotu true (nenulové hodnoty), *příkaz* se spustí. Pokud *výraz* je nastavena hodnota false, *příkaz* je ignorována. Formulář syntaxe, který používá **else**, druhý *příkaz* se spustí, pokud *výraz* je false. Obě forms kontrolu potom předává z **Pokud** příkaz, který má další příkaz v programu Pokud jeden z příkazy obsahuje **zalomení**, **pokračovat**, nebo `goto`.  
  
 Následují příklady **Pokud** příkaz:  
  
```  
if ( i > 0 )  
    y = x / i;  
else   
{  
    x = i;  
    y = f( x );  
}  
```  
  
 V tomto příkladu příkaz `y = x/i;` se spustí, pokud `i` je větší než 0. Pokud `i` je menší než nebo rovna 0, `i` je přiřazena k `x` a `f( x )` je přiřazena k `y`. Všimněte si, že příkaz, které tvoří **Pokud** klauzule končí středníkem.  
  
 Při vnoření **Pokud** příkazy a **else** klauzule, použít složené závorky k seskupení příkazů a klauzule do složené příkazy, které vysvětlení vašich představ. Pokud nejsou žádné složené závorky, kompilátor řeší tím, že přidružíte každý nejednoznačnosti **else** s nejbližší **Pokud** , chybí **else**.  
  
```  
if ( i > 0 )           /* Without braces */  
    if ( j > i )  
        x = j;  
    else  
        x = i;  
```  
  
 **Else** klauzule souvisí s vnitřní **Pokud** příkaz v tomto příkladu. Pokud `i` je menší než nebo rovna 0, není přiřazena žádná hodnota k `x`.  
  
```  
if ( i > 0 )   
{                      /* With braces */  
    if ( j > i )  
        x = j;  
}  
else  
    x = i;  
```  
  
 Složené závorky, které obaluje vnitřní **Pokud** Zkontrolujte příkaz v tomto příkladu **else** část klauzule vnějšího **Pokud** příkaz. Pokud `i` je menší než nebo rovna 0, `i` je přiřazena k `x`.  
  
## <a name="see-also"></a>Viz také  
 [if-else – příkaz (C++)](../cpp/if-else-statement-cpp.md)