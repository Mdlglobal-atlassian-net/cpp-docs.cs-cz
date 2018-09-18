---
title: Zastaralé formy deklarací a definic funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edd33a59c5ae5120d8c9cdc15f32171b7df4993a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109857"
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

```
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

Tuto deklaraci byste měli přepsat jako prototyp:

```
void funct1( int a, ... )
{
}
```

Deklarace funkce starého typu také vygenerují upozornění, pokud následně deklarujete nebo definujete stejnou funkci se třemi tečkami nebo parametr typu, který není stejný jako jeho povýšený typ.

Další části [definice funkcí jazyka C](../c-language/c-function-definitions.md), je uvedena syntaxe pro definice funkcí, včetně syntaxe starého typu. Neterminál seznamu parametrů v syntaxi starého typu je *seznam identifikátorů*.

## <a name="see-also"></a>Viz také

[Přehled funkcí](../c-language/overview-of-functions.md)