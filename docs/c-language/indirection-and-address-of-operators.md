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
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534365"
---
# <a name="indirection-and-address-of-operators"></a>Deferenční operátory a operátory adresy

Operátor unární dereference (__&#42;__) nepřímo přistupuje k hodnotě prostřednictvím ukazatele. Operand musí být typu ukazatel. Výsledkem operace je hodnota adresovaná operandem, tedy hodnota na adrese, na kterou operand ukazuje. Typ výsledku je typ adresovaný operandem.

Výsledek operátoru dereference *typ* je-li operand typu *ukazatel na typ*. Ukazuje-li operand na funkci, je výsledkem označení funkce. Ukazuje-li objekt, je výsledkem l-hodnotou označující objekt.

Pokud hodnota ukazatele je neplatná, výsledek operátor dereference není definován. Tady jsou některé z nejběžnějších situací, které zneplatňují hodnotu ukazatele:

- Ukazatel je nulový.

- Ukazatel Určuje adresu objektu po konci životnosti (například objekt, který je nepřejdou mimo rozsah nebo, která není přidělená) v době reference.

- Ukazatel určuje adresu, která je pro typ objektu, na který ukazatel ukazuje, nesprávně zarovnána.

- Ukazatel určuje adresu, která není používána spuštěným programem.

Operátor unární address-of (**&**) poskytuje adresu svého operandu. Operand musí být buď l-hodnotou označující objekt, který není deklarován __zaregistrovat__ a není bitové pole, nebo výsledek unární __&#42;__ operátor nebo pole přistoupit přes ukazatel (__&#91; &#93;__) – operátor ani označení funkce. Výsledek je typu *ukazatel na typ* pro operand typu *typ*.

Je-li operand výsledek unární __&#42;__ operátor ani operátor je vyhodnocen a výsledkem je, jako by oba byly vynechány. Výsledek není l-hodnota a stále platí omezení na operátory. Je-li operand výsledek __&#91; &#93;__ operátor, ani __&__ operátor ani unární __&#42;__ implikována __&#91; &#93;__ operátor je vyhodnocen. Výsledek má stejný účinek jako odebrání __&__ operátor a změna __&#91; &#93;__ operátor __+__ operátor. Jinak výsledkem je ukazatel na objekt nebo funkci určeném operandem.

## <a name="examples"></a>Příklady

Následující příklady používají tyto běžné deklarace:

```C
int *pa, x;
int a[20];
double d;
```

Tento příkaz používá operátor address-of (**&**) převzít adresu šestého prvku v poli `a`. Výsledek je uložen v proměnné ukazatele `pa`:

```C
pa = &a[5];
```

Operátor dereference (__&#42;__) se v tomto příkladu používá pro přístup `int` hodnota na adrese uložené v `pa`. Hodnota je přiřazená k celočíselné proměnné `x`:

```C
x = *pa;
```

Tento příklad ukazuje, že výsledek použití operátoru dereference na adresu `x` je stejný jako `x`:

```C
assert( x == *&x );
```

Tento příklad ukazuje deklaraci ukazatele na funkci ekvivalentní způsoby:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

Po deklaraci funkce `roundup` jsou na tuto funkci `roundup` deklarovány a inicializovány dva ukazatele. První ukazatel `proundup` je inicializován pouze pomocí názvu funkce, zatímco druhý ukazatel `pround` v inicializaci používá operátor adresa. Tyto inicializace jsou ekvivalentní.

## <a name="see-also"></a>Viz také:

[Deferenční operátor:&#42;](../cpp/indirection-operator-star.md)<br/>
[Operátor address-of: &](../cpp/address-of-operator-amp.md)
