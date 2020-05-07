---
title: Deklarátory abstraktu jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 196eb39d901b38ab7b005b03a933827ec4288218
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335069"
---
# <a name="c-abstract-declarators"></a>Deklarátory abstraktu jazyka C

Abstraktní deklarátor je deklarátor bez identifikátoru, sestávající z jednoho nebo více ukazatelů, polí nebo modifikátorů funkce. Modifikátor ukazatele (<strong>\*</strong>) vždy předchází identifikátor v deklarátor; modifikátory Array (**[]**) a Function ( **()** ) následují za identifikátorem. Když toto víte, můžete určit, kde by se identifikátor v abstraktním deklarátoru měl objevit a interpretovat tento deklarátor odpovídajícím způsobem. Další informace a příklady komplexních deklarátory najdete v tématu [Interpretace](../c-language/interpreting-more-complex-declarators.md) složitějších deklarátory. Obecný `typedef` slouží ke zjednodušení deklarátorů. Viz [deklarace typedef](../c-language/typedef-declarations.md).

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
> Abstraktní deklarátor sestávající ze sady prázdných závorek **()** není povolen, protože je dvojznačný. Není možné určit, zda implicitní identifikátor patří do závorek (v tomto případě je to nezměněný typ) nebo před závorky (v tomto případě je to typ funkce).

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
