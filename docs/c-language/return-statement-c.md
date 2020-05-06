---
title: return – příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
ms.openlocfilehash: c3975076ee65d267f3d278e20a7770e6750c06d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158382"
---
# <a name="return-statement-c"></a>return – příkaz (C)

`return` Příkaz ukončí provádění funkce a vrátí řízení volající funkci. Spuštění pokračuje ve volání funkce v bodě hned po volání. `return` Příkaz může také vrátit hodnotu volající funkci. Další informace naleznete v části [návratový typ](../c-language/return-type.md) .

## <a name="syntax"></a>Syntaxe

*příkaz skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**návratový** *výraz*<sub>opt</sub> **;**

Hodnota *výrazu*, je-li k dispozici, je vrácena voláním funkce. Pokud je *výraz* vynechán, návratová hodnota funkce není definována. Výraz, je-li k dispozici, je vyhodnocen a následně převeden na typ vrácený funkcí. Pokud byla funkce deklarována s návratovým `void`typem, `return` příkaz obsahující výraz vygeneruje upozornění a výraz není vyhodnocen.

Pokud se `return` v definici funkce nezobrazí žádný příkaz, řízení se po provedení posledního příkazu volané funkce automaticky vrátí na volající funkci. V tomto případě není definována návratová hodnota volané funkce. Pokud není požadovaná návratová hodnota, Deklarujte funkci tak, aby `void` vracela návratový typ; v opačném případě je `int`výchozí návratový typ.

Mnoho programátorů používá závorky k uzavření argumentu *výrazu* `return` příkazu. Jazyk C však nevyžaduje závorky.

Tento příklad ukazuje `return` příkaz:

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

V tomto příkladu `main` funkce volá dvě funkce: `sq` a. `draw` `sq` Funkce vrátí hodnotu `x * x` do `main`, kde je přiřazena návratová hodnota `y`. Závorky kolem návratového výrazu v `sq` jsou vyhodnocovány jako součást výrazu a nejsou vyžadovány příkazem Return. Vzhledem k tomu, že se návratový výraz vyhodnocuje před jeho převodem na `sq` návratový typ, vynutí typ výrazu návratový typ s přetypováním, aby se zabránilo možnému přetečení celého čísla, což by mohlo vést k neočekávaným výsledkům. `draw` Funkce je deklarována jako `void` funkce. Vytiskne hodnoty jeho parametrů a pak prázdný návratový příkaz ukončí funkci a nevrátí hodnotu. Pokus o přiřazení návratové hodnoty `draw` by způsobil vydání diagnostické zprávy. `main` Funkce pak vrátí hodnotu `x` pro operační systém.

Výstup tohoto příkladu vypadá takto:

```Output
i = 2147483647, ll = 4611686014132420609
```

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)
