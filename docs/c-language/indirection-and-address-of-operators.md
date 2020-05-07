---
title: Deferenční operátory a operátory adresy
ms.date: 02/16/2018
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
ms.openlocfilehash: 146f84c90aa56b5abf6ae5212c1729022cb7e4dc
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343898"
---
# <a name="indirection-and-address-of-operators"></a>Deferenční operátory a operátory adresy

Unární operátor indirekce (__&#42;__) přistupuje k hodnotě nepřímo prostřednictvím ukazatele. Operand musí být typu ukazatel. Výsledkem operace je hodnota adresovaná operandem, tedy hodnota na adrese, na kterou operand ukazuje. Typ výsledku je typ adresovaný operandem.

Výsledek operátoru dereference je *typu* , pokud je operand typu *ukazatel na typ*. Ukazuje-li operand na funkci, je výsledkem označení funkce. Pokud odkazuje na objekt, výsledek je l-hodnota, která určuje objekt.

Pokud hodnota ukazatele není platná, výsledek operátoru dereference není definován. Toto jsou některé z nejběžnějších podmínek, které neověřují hodnotu ukazatele:

- Ukazatel je nulový.

- Ukazatel určuje adresu objektu po skončení své životnosti (například objekt, který je mimo rozsah nebo který byl uvolněn) v okamžiku odkazu.

- Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.

- Ukazatel určuje adresu, která není používána spuštěným programem.

Unární operátor address-of (**&**) poskytuje adresu jeho operandu. Operand musí být buď l-hodnota, který určuje objekt, který není deklarovaný jako __Register__ a není bitové pole, nebo výsledek unárního operátoru __&#42;__ nebo operátoru "vyřazení pole" (__&#91;&#93;__) nebo označení funkce. Výsledek je typu *ukazatel na typ* pro *operand typu typ.*

Pokud je operand výsledkem unárního operátoru __&#42;__ , není vyhodnocen žádný operátor a výsledkem je, že obě byla vynechána. Výsledek není l-hodnota a omezení operátorů jsou stále použita. Pokud je operand výsledkem operátoru __&#91;&#93;__ , není vyhodnocen ani __&__ operátor ani unární __&#42;__ odvozený operátorem __&#91;&#93;__ . Výsledek má stejný účinek jako odebrání __&__ operátoru a Změna operátoru __&#91;&#93;__ na __+__ operátor. V opačném případě je výsledkem ukazatel na objekt nebo funkci určenou operandem.

## <a name="examples"></a>Příklady

Následující příklady používají tyto běžné deklarace:

```C
int *pa, x;
int a[20];
double d;
```

Tento příkaz používá operátor address-of (**&**) k převzetí adresy šestého prvku pole. `a` Výsledek je uložen v proměnné `pa`ukazatele:

```C
pa = &a[5];
```

Operátor dereference (__&#42;__) se v tomto příkladu používá pro přístup k `int` hodnotě na adrese uložené v. `pa` Hodnota je přiřazena celočíselné proměnné `x`:

```C
x = *pa;
```

Tento příklad ukazuje, že výsledek použití operátoru dereference na adresu `x` je stejný jako: `x`

```C
assert( x == *&x );
```

Tento příklad ukazuje ekvivalentní způsob deklarace ukazatele na funkci:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

Po deklaraci funkce `roundup` jsou na tuto funkci `roundup` deklarovány a inicializovány dva ukazatele. První ukazatel `proundup` je inicializován pouze pomocí názvu funkce, zatímco druhý ukazatel `pround` v inicializaci používá operátor adresa. Tyto inicializace jsou ekvivalentní.

## <a name="see-also"></a>Viz také

[Operátor dereference: &#42;](../cpp/indirection-operator-star.md)<br/>
[Operátor address-of: &](../cpp/address-of-operator-amp.md)
