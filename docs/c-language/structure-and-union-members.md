---
title: Členové struktury a sjednocení
ms.date: 11/04/2016
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
ms.openlocfilehash: b22f5a29a4dc088ea4f3db863d635badee048d2c
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825688"
---
# <a name="structure-and-union-members"></a>Členové struktury a sjednocení

„Výraz výběru členů“ odkazuje na členy struktury a sjednocení. Takový výraz má hodnotu a typ vybraného členu.

> *výraz přípony* **.** *RID*\
> *identifikátor* *výrazu přípony* **->**

Seznam popisuje dva typy výrazů výběru členů:

1. V prvním formuláři představuje *příponový výraz* hodnotu **struktury** nebo typu **sjednocení** a názvy *identifikátorů* člena zadané struktury nebo sjednocení. Hodnotou operace je *identifikátor* a je l-hodnotou, pokud je *příponový výraz* l-hodnotou. Další informace naleznete v tématu [výrazy L-Value a R-Value](../c-language/l-value-and-r-value-expressions.md) .

1. Ve druhém formuláři představuje *příponový výraz* ukazatel na strukturu nebo sjednocení a názvy *identifikátorů* člena zadané struktury nebo sjednocení. Hodnota je *identifikátor* a je l-hodnotou.

Oba typy výrazů výběru členů mají podobné funkce.

Ve skutečnosti je výraz zahrnující operátor výběru členů (**->**) zkráceným zněním výrazu za použití tečky (**.**), pokud se výraz před tečkou skládá z operátoru dereference (<strong>\*</strong>), který je použit na hodnotu ukazatele. Proto:

```cpp
expression->identifier
```

je ekvivalentem

```cpp
(*expression).identifier
```

je-li *výraz* hodnotou ukazatele.

## <a name="examples"></a>Příklady

Následující příklady odkazují na tuto deklaraci struktury. Informace o operátoru dereference (<strong>\*</strong>), který se používá v těchto příkladech, naleznete v tématu [operátory dereference a Address-of](../c-language/indirection-and-address-of-operators.md).

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

V tomto příkladu je výraz `item.sp` ukazatele použit s operátorem výběru členů (**->**) pro přiřazení hodnoty členu. `a`

```
list[8].b = 12;
```

Tento příkaz ukazuje, jak vybrat jednotlivý člen struktury z pole struktur.

## <a name="see-also"></a>Viz také

[Operátory přístupu členů: . a ->](../cpp/member-access-operators-dot-and.md)
