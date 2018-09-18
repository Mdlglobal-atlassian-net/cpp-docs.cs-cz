---
title: Vrátí Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 466a56bf4d1a309aadccbcbbccc91de6a59e6e1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067341"
---
# <a name="return-statement-c"></a>return – příkaz (C)

`return` Příkaz ukončí provádění funkce a vrátí řízení volající funkci. Provádění pokračuje ve volání funkce v okamžiku, ihned po volání. A `return` příkaz může také vracet hodnotu volající funkci. Zobrazit [návratový typ](../c-language/return-type.md) Další informace.

## <a name="syntax"></a>Syntaxe

*příkaz-skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Vrátí** *výraz*<sub>optimalizované</sub> **;**

Hodnota *výraz*, pokud jsou k dispozici, je vrácena volající funkci. Pokud *výraz* je tento parametr vynechán, návratová hodnota funkce není definován. Výraz, pokud jsou k dispozici, je vyhodnocen a poté převeden na typ vrácené funkcí. Pokud funkce byla deklarována s návratovým typem `void`, `return` příkazu, který obsahuje výraz vygeneruje upozornění a tento výraz není vyhodnocen.

Pokud ne `return` příkazu se zobrazí v definici funkce, ovládací prvek automaticky vrátí k volání funkce po provedení posledního prohlášení o volané funkce. V tomto případě je definován na návratový typ volané funkce. Pokud vrácená hodnota není vyžadována, deklarujte funkci mít `void` návratový typ; v opačném případě výchozí hodnota je návratový typ `int`.

Mnoho programátorů použít závorky k uzavření *výraz* argument `return` příkazu. C nevyžaduje závorky.

Tento příklad ukazuje, `return` – příkaz:

```C
#include <limits.h>
#include <stdio.h>

void draw( int i, long long ll );
long long sq( int s );

int main()
{
    long long y;
    int x = INT_MAX;

    y = sq( x );
    draw( x, y );
    return x;
}

long long sq( int s )
{
    // Note that parentheses around the return expression
    // are allowed but not required here.
    return( s * (long long)s );
}

void draw( int i, long long ll )
{
    printf( "i = %d, ll = %lld\n", i, ll );
    return;
}
```

V tomto příkladu `main` funkce volá dvě funkce: `sq` a `draw`. `sq` Funkce vrátí hodnotu `x * x` k `main`, kde návratová hodnota je přiřazená `y`. Závorky kolem vrácený výraz v `sq` jsou vyhodnoceny jako součást výrazu a nejsou požadována návratový příkaz. Protože vrácený výraz je vyhodnocen, než je převedena na typ vrácené hodnoty, `sq` vynutí typ výrazu jako návratový typ pomocí přetypování zabránil přetečení celého čísla je to možné, což by mohlo vést k neočekávaným výsledkům. `draw` Není funkce deklarována jako `void` funkce. Vypíše hodnoty jeho parametrů a poté prázdný příkaz return ukončení funkce a nevrací hodnotu. Pokus o přiřazení návratová hodnota `draw` by způsobilo diagnostickou zprávu vystavování. `main` Funkce vrátí hodnotu `x` v operačním systému.

Výstup v příkladu vypadá takto:

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)