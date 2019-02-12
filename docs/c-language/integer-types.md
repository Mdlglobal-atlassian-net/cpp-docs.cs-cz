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
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146876"
---
# <a name="integer-types"></a>Typy celého čísla

Každé celočíselné konstantě je předán typ na základě její hodnoty a způsobu, jakým je vyjádřena. Můžete vynutit jakákoli celočíselná konstanta typu **dlouhé** přidáním písmeno **l** nebo **L** na konec konstanty; lze vynutit typ `unsigned` připojením **u** nebo **U** k hodnotě. Malé písmeno **l** může být zaměněno za číslici 1 a mělo by se vyhnout. Některé formy **dlouhé** konstanty typu integer, postupujte podle:

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

Typ přiřazený konstantě závisí na hodnotě, kterou konstanta představuje. Hodnota konstanty musí být v rozsahu reprezentovatelných hodnot jejího typu. Typ konstanty Určuje, které převody jsou prováděny, když konstanta použita ve výrazu nebo když znaménko mínus (**-**) se použije. Tento seznam shrnuje pravidla převodu celočíselných konstant.

- Typ decimální konstanty bez přípony je buď `int`, **long int**, nebo **unsigned long int**. První z těchto tří typů, ve kterých lze hodnotu konstanty reprezentovat, je typ přiřazený konstantě.

- Typ přiřazený osmičkovým a šestnáctkovým konstantám bez přípony je `int`, `unsigned int`, **long int**, nebo **unsigned long int** v závislosti na velikosti konstanty.

- Typ přiřazený konstantám s **u** nebo **U** přípona je **unsigned int** nebo **unsigned long int** v závislosti na jejich velikosti.

- Typ přiřazený konstantám s **l** nebo **L** přípona je **long int** nebo **unsigned long int** v závislosti na jejich velikosti.

- Typ přiřazený konstantám s **u** nebo **U** a **l** nebo **L** přípona je **unsigned long int**.

## <a name="see-also"></a>Viz také:

[Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)
