---
title: return – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: c8ea796ab40a2090ed9853377f7c9415914bc0e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178979"
---
# <a name="return-statement-c"></a>return – příkaz (C++)

Ukončí provádění funkce a vrátí řízení volající funkci (nebo operačnímu systému, je-li řízení předáváno z funkce `main`). Spuštění pokračuje ve volání funkce v bodě hned po volání.

## <a name="syntax"></a>Syntaxe

```
return [expression];
```

## <a name="remarks"></a>Poznámky

Je-li přítomna klauzule `expression`, je převedena na typ zadaný v deklaraci funkce, jako kdyby byla prováděna inicializace. Převod z typu výrazu na **návratový** typ funkce může vytvořit dočasné objekty. Další informace o tom, jak a kdy se dočasné objekty vytvářejí, najdete v tématu [dočasné objekty](../cpp/temporary-objects.md).

Hodnota klauzule `expression` je vrácena volající funkci. Pokud je výraz vynechán, návratová hodnota funkce není definována. Konstruktory a destruktory a funkce typu **void**nemůžou v příkazu **return** zadat výraz. Funkce všech ostatních typů musí v příkazu **return** určovat výraz.

Když tok řízení ukončí blok ohraničující definici funkce, výsledek je stejný, jako by byl proveden příkaz **return** bez výrazu. Toto neplatí u funkcí, které jsou deklarovány jako návratová hodnota.

Funkce může mít libovolný počet příkazů **return** .

Následující příklad používá výraz s příkazem **return** pro získání největších ze dvou celých čísel.

## <a name="example"></a>Příklad

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>Viz také

[Jump – příkazy](../cpp/jump-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
