---
title: Deferenční operátory a operátory adresy | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75afd44b8c0a31d9f3731a4c6f9fb86c15de4328
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389417"
---
# <a name="indirection-and-address-of-operators"></a>Deferenční operátory a operátory adresy

Deferenční operátor unární (__&#42;__) přistupuje hodnotu nepřímo prostřednictvím ukazatele. Operand musí být typu ukazatele. Výsledkem operace je hodnota adresovaná operandem, tedy hodnota na adrese, na kterou operand ukazuje. Typ výsledku je typ adresovaný operandem.

Výsledkem deferenční operátor je *typ* Pokud operand typu *ukazatel na typ*. Ukazuje-li operand na funkci, je výsledkem označení funkce. Odkazuje na objekt, výsledkem je lvalue, který určuje objekt.

Pokud je hodnota ukazatele je neplatná, není definován výsledek deferenční operátor. Toto jsou některé z nejběžnějších podmínky, které zneplatnit hodnota ukazatele:

- Ukazatel je nulový.

- Ukazatele určuje adresu objektu po konci životnosti (například objekt, který je mimo rozsah nebo který je navrácena) v době odkaz.

- Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.

- Ukazatel určuje adresu, která není používána spuštěným programem.

Operátor unární adresy (**&**) poskytuje adresu jeho operand. Operand musí být buď lvalue, který určuje objekt, který není deklarovaný __zaregistrovat__ a není bitové pole nebo výsledek unární operátor __&#42;__ dereference – operátor nebo pole (__&#91; &#93;__) operátor nebo označení funkce. Výsledkem je typu *ukazatel na typ* pro operand typu *typu*.

Pokud je výsledkem unární operátor operand __&#42;__ operátor, ani operátor je vyhodnocena a výsledkem je, jako kdyby byly vynechání obě. Výsledek není lvalue a omezení u operátory platit stále. Pokud je výsledkem operand __&#91; &#93;__ operátor, ani __&__ operátor ani unární __&#42;__ implikované __&#91; &#93;__ vyhodnotí operátor. Výsledek obsahuje stejného efektu jako odebrání __&__ operátor a změna __&#91; &#93;__ operátor a __+__ operátor. Výsledkem je, jinak hodnota ukazatele na objekt nebo funkce, které jsou určené operandem.


## <a name="examples"></a>Příklady

Následující příklady použijte tyto společné deklarace:

```C
int *pa, x;
int a[20];
double d;
```

Tento příkaz používá address-of – operátor (**&**) provést adresu šesté elementu pole `a`. Výsledek je uložen v proměnné ukazatele `pa`:

```C  
pa = &a[5];
```

Deferenční operátor (__&#42;__) se v tomto příkladu používá pro přístup `int` hodnotu na adrese uložené v `pa`. Hodnota je přiřazena k proměnné celé číslo `x`:

```C
x = *pa;
```

Tento příklad ukazuje, který výsledek použití deferenční operátor na adresu `x` je stejný jako `x`:

```C
assert( x == *&x );
```

Tento příklad ukazuje ekvivalentní způsoby deklarování ukazatel na funkci:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```  

Po deklaraci funkce `roundup` jsou na tuto funkci `roundup` deklarovány a inicializovány dva ukazatele. První ukazatel `proundup` je inicializován pouze pomocí názvu funkce, zatímco druhý ukazatel `pround` v inicializaci používá operátor adresa. Tyto inicializace jsou ekvivalentní.

## <a name="see-also"></a>Viz také

[Deferenční operátor:&#42;](../cpp/indirection-operator-star.md)  
[Operátor address-of: &](../cpp/address-of-operator-amp.md)  
