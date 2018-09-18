---
title: Typy celého čísla | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22392a4f02fb81a7c141aaa0e7966a05988dfece
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076668"
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

## <a name="see-also"></a>Viz také

[Konstanty typu Integer jazyka C](../c-language/c-integer-constants.md)