---
title: Typy celého čísla
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 23da055b56e2ae77fed796d9ba8e7f227e572a9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232849"
---
# <a name="integer-types"></a>Typy celého čísla

Každé celočíselné konstantě je předán typ na základě její hodnoty a způsobu, jakým je vyjádřena. Můžete vynutit libovolnou celočíselnou konstantu pro typ **Long** připojením písmene **l** nebo **l** ke konci konstanty; můžete vynutit, aby bylo typu `unsigned` k hodnotě připojeny **u** nebo **u** . Malé písmeno **l** může být zaměněno s číslicí 1 a je třeba se jim vyhnout. Následuje několik forem **dlouhých** celočíselných konstant:

```
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

Typ přiřazený konstantě závisí na hodnotě, kterou konstanta představuje. Hodnota konstanty musí být v rozsahu reprezentovatelných hodnot jejího typu. Typ konstanty určuje, které převody jsou provedeny při použití konstanty ve výrazu nebo při použití znaménka mínus (**-**). Tento seznam shrnuje pravidla převodu celočíselných konstant.

- Typ pro desítkovou konstantu bez přípony je buď `int`, **Long int**nebo **unsigned long int**. První z těchto tří typů, v nichž může být hodnota konstanty reprezentovaná, je typ přiřazený konstantě.

- Typ přiřazený osmičkové a šestnáctkové konstantě bez přípon `int`je `unsigned int`, **Long int**nebo **unsigned long int** v závislosti na velikosti konstanty.

- Typ přiřazený konstantám s příponou **u** nebo **u** je **bez znaménka int** nebo **unsigned long int** v závislosti na jejich velikosti.

- Typ přiřazený konstantám s příponou **l** nebo **l** je **Long int** nebo **unsigned long int** v závislosti na jejich velikosti.

- Typ přiřazený konstantám s příponou **u** nebo **u** a **l** nebo **l** je **bez znaménka long int**.

## <a name="see-also"></a>Viz také

[Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)
