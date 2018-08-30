---
title: Členové struktury a sjednocení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b497745177bce165277e3a6e4ece2a3c47f20a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194872"
---
# <a name="structure-and-union-members"></a>Členové struktury a sjednocení
„Výraz výběru členů“ odkazuje na členy struktury a sjednocení. Takový výraz má hodnotu a typ vybraného členu.  
  
> *výraz přípony* **.** *identifikátor*  
> *výraz přípony* **->** *identifikátor*
  
Seznam popisuje dva typy výrazů výběru členů:  
  
1.  V prvním *postfix-expression* představuje hodnotu **struktura** nebo **sjednocení** typ, a *identifikátor* pojmenovává člen určené struktury nebo sjednocení. Hodnotu operace má *identifikátor* a je l hodnotou, pokud *postfix-expression* l-hodnotou. Zobrazit [výrazy L-Value a R-Value](../c-language/l-value-and-r-value-expressions.md) Další informace.  
  
2.  Druhý typ *postfix-expression* představuje ukazatel na strukturu nebo sjednocení a *identifikátor* pojmenovává člen určené struktury nebo sjednocení. Hodnota je u *identifikátor* a je l hodnotou.  
  
 Oba typy výrazů výběru členů mají podobné funkce.  
  
 Ve skutečnosti výraz zahrnující operátor výběru členů (**->**) je verze sdruženou výraz používající období (**.**) Pokud výraz před doby se skládá z indirection – operátor (<strong>\**</strong>) projeví na hodnotě ukazatele. Proto  

```cpp
expression->identifier  
```

je ekvivalentem  

```cpp
(*expression).identifier
```

 Když *výraz* hodnotou ukazatele.  
  
## <a name="examples"></a>Příklady  
 Následující příklady odkazují na tuto deklaraci struktury. Informace o deferenční operátor (<strong>\**</strong>) používané v těchto příkladech, najdete v části [Deferenční operátory a operátory adresy](../c-language/indirection-and-address-of-operators.md).  
  
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
  
 V tomto příkladu výraz ukazatele `item.sp` se používá spolu s operátorem výběru členů (**->**) pro přiřazení hodnoty k členu `a`.  
  
```  
list[8].b = 12;  
```  
  
 Tento příkaz ukazuje, jak vybrat jednotlivý člen struktury z pole struktur.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přístupu členů: . a ->](../cpp/member-access-operators-dot-and.md)