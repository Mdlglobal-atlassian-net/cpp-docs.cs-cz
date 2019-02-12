---
title: Deklarátory abstraktu jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: f2ca0f4a367abf939ed4307611517a883d8b82e0
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152661"
---
# <a name="c-abstract-declarators"></a>Deklarátory abstraktu jazyka C

Abstraktní deklarátor je deklarátor bez identifikátoru, sestávající z jednoho nebo více ukazatelů, polí nebo modifikátorů funkce. Modifikátor ukazatele (<strong>\*</strong>) vždy v deklarátoru předchází identifikátor pole (**[] č.**) a funkce ( **()** ) následují tento identifikátor modifikátory. Když toto víte, můžete určit, kde by se identifikátor v abstraktním deklarátoru měl objevit a interpretovat tento deklarátor odpovídajícím způsobem. Zobrazit [interpretace složitých Deklarátorů](../c-language/interpreting-more-complex-declarators.md) pro další informace a příklady složitých deklarátorů. Obecný `typedef` slouží ke zjednodušení deklarátorů. Zobrazit [deklarace Typedef](../c-language/typedef-declarations.md).

Abstraktní deklarátory mohou být složité. Závorky ve složitých abstraktních deklarátorech určují konkrétní interpretaci, stejně jako je tomu u komplexních deklarátorů v deklaracích.

Tyto příklady ilustrují abstraktní deklarátory:

```
int *         // The type name for a pointer to type int:

int *[3]      // An array of three pointers to int

int (*) [5]   // A pointer to an array of five int

int *()       // A function with no parameter specification
              // returning a pointer to int

// A pointer to a function taking no arguments and
// returning an int

int (*) ( void )

// An array of an unspecified number of constant pointers to
// functions each with one parameter that has type unsigned int
// and an unspecified number of other parameters returning an int

int (*const []) ( unsigned int, ... )
```

> [!NOTE]
>  Abstraktní deklarátor sestávající ze sady prázdných závorek, **()**, není povolená, protože není jednoznačný. Není možné určit, zda implicitní identifikátor patří do závorek (v tomto případě je to nezměněný typ) nebo před závorky (v tomto případě je to typ funkce).

## <a name="see-also"></a>Viz také:

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
