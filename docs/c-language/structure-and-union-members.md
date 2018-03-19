---
title: "Členové struktury a sjednocení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2183aead53ee02f36bc982e4f33ad174346da5f2
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="structure-and-union-members"></a>Členové struktury a sjednocení
„Výraz výběru členů“ odkazuje na členy struktury a sjednocení. Takový výraz má hodnotu a typ vybraného členu.  
  
```  
  
postfix-expression  
.  
identifier  
postfix-expression  
->  
identifier  
  
```  
  
 Seznam popisuje dva typy výrazů výběru členů:  
  
1.  Ve formuláři první *operátory výraz* představuje hodnotu `struct` nebo **sjednocení** typ, a *identifikátor* názvy členem zadané struktury nebo union. Hodnota operace je u *identifikátor* a pokud je hodnotou l *operátory výraz* je l hodnota. V tématu [L-Value a R-Value výrazy](../c-language/l-value-and-r-value-expressions.md) Další informace.  
  
2.  Ve formuláři druhý *operátory výraz* představuje ukazatel na strukturu nebo union, a *identifikátor* názvy členem zadané struktury nebo union. Hodnota je u *identifikátor* a je l hodnota.  
  
 Oba typy výrazů výběru členů mají podobné funkce.  
  
 Ve skutečnosti výraz zahrnující operátor výběru členů (**->**) je verze sdruženou výraz používající období (**.**) Pokud výraz před doby se skládá z indirection – operátor (**\****) projeví na hodnotě ukazatele. Proto  
  
```  
  
expression  
->  
identifier  
  
```  
  
 je ekvivalentem  
  
```  
  
(*  
expression  
) .  
identifier  
  
```  
  
 Když *výraz* je hodnota ukazatele.  
  
## <a name="examples"></a>Příklady  
 Následující příklady odkazují na tuto deklaraci struktury. Informace o deferenční operátor (**\****) používané v těchto příkladech, najdete v části [Deferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md).  
  
```  
struct pair   
{  
    int a;  
    int b;  
    struct pair *sp;  
} item, list[10];  
```  
  
 Výraz výběru členů struktury `item` vypadá takto:  
  
```  
item.sp = &item;  
```  
  
 V příkladu uvedeném výše je adresa struktury `item` přiřazena členu struktury `sp`. To znamená, že struktura `item` obsahuje ukazatel sám na sebe.  
  
```  
(item.sp)->a = 24;  
```  
  
 V tomto příkladu výraz ukazatel `item.sp` se používá s operátorem výběru členů (**->**) se členem přiřadit hodnotu `a`.  
  
```  
list[8].b = 12;  
```  
  
 Tento příkaz ukazuje, jak vybrat jednotlivý člen struktury z pole struktur.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přístupu členů: . a ->](../cpp/member-access-operators-dot-and.md)