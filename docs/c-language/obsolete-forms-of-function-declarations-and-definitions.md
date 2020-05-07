---
title: Zastaralé formy deklarací a definic funkcí
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: f26e79a586ea451cc51b339b5be593c2359e1f1a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745874"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Zastaralé formy deklarací a definic funkcí

Deklarace a definice funkcí starého typu používají mírně odlišná pravidla pro deklarování parametrů než syntaxe doporučená standardem ANSI jazyka C. Za prvé, deklarace starého typu nemají seznam parametrů. Za druhé, parametry jsou uvedeny v definici funkce, ale jejich typy nejsou deklarovány v seznamu parametrů. Deklarace typů předcházejí složený příkaz tvořící tělo funkce. Syntaxe starého typu je zastaralá a neměla by se v novém kódu používat. Ačkoli kód používající syntaxi starého typu je nadále podporován. Tento příklad ukazuje zastaralé tvary deklarací a definicí:

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Funkce, která vrátí celé číslo nebo ukazatel se stejnou velikostí jako typ `int`, nemusí mít deklaraci, i když je deklarace doporučena.

Z důvodu dodržení standardu ANSI jazyka C staré typy deklarací funkce používající tři tečky nyní vygenerují chybu při kompilaci s možnosti /Za a upozornění úrovně 4 při kompilaci s možností /Ze. Příklad:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Tuto deklaraci byste měli přepsat jako prototyp:

```cpp
void funct1( int a, ... )
{
}
```

Deklarace funkce starého typu také vygenerují upozornění, pokud následně deklarujete nebo definujete stejnou funkci se třemi tečkami nebo parametr typu, který není stejný jako jeho povýšený typ.

V další části [definice funkcí jazyka C](../c-language/c-function-definitions.md)se zobrazuje syntaxe definic funkcí, včetně syntaxe starého stylu. Neterminálový seznam parametrů v syntaxi starého stylu je *seznam identifikátorů*.

## <a name="see-also"></a>Viz také

[Přehled funkcí](../c-language/overview-of-functions.md)
