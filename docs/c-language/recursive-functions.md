---
title: Rekurzivní funkce
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
ms.openlocfilehash: 82f0c820ab75fda4bae83db78fa402d7a07cb7fe
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152427"
---
# <a name="recursive-functions"></a>Rekurzivní funkce

Všechny funkce v programu jazyka C lze volat rekurzivně, což znamená, že volají samy sebe. Počet rekurzivních volání je omezen velikostí zásobníku. Zobrazit [/Stack (přidělení zásobníku)](../build/reference/stack-stack-allocations.md) (/ STACK) – možnost linkeru informace o linkeru možnostech tohoto nastavení velikosti zásobníku. Pokaždé, když je volána funkce přiděleno nové úložiště pro parametry a **automaticky** a **zaregistrovat** proměnné tak, aby jejich hodnoty v předchozím nedokončeném volání se nepřepíšou. Parametry jsou přímo přístupné pouze instanci funkce, ve které jsou vytvořeny. Předchozí parametry nejsou následné instanci funkce přímo přístupné.

Všimněte si, že proměnné deklarované s **statické** nevyžadují nové úložiště s každým rekurzivním voláním. Jejich úložiště existuje po dobu životnosti programu. Každý odkaz na takovou proměnnou přistupuje do stejné oblasti úložiště.

## <a name="example"></a>Příklad

Tento příklad ukazuje rekurzivní volání:

```C
int factorial( int num );      /* Function prototype */

int main()
{
    int result, number;
    .
    .
    .
    result = factorial( number );
}

int factorial( int num )      /* Function definition */
{
    .
    .
    .
    if ( ( num > 0 ) || ( num <= 10 ) )
        return( num * factorial( num - 1 ) );
}
```

## <a name="see-also"></a>Viz také:

[Volání funkcí](../c-language/function-calls.md)
