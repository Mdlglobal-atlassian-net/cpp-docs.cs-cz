---
title: Typ a velikost proměnných ve vloženém sestavení
ms.date: 08/30/2018
ms.topic: reference
f1_keywords:
- length
- Type
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: 36c97ee866ca449e9bbcf514e464a13f24f12cd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539097"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ a velikost proměnných ve vloženém sestavení

**Specifické pro Microsoft**

**Délka**, **velikost**, a **typ** operátory mají omezenou význam ve vloženém sestavení. Nelze je použít na všech s `DUP` – operátor (protože nelze definovat data pomocí direktivy MASM nebo operátory). Ale můžete je použít k vyhledání velikost proměnné jazyka C nebo C++ nebo typy:

- **Délka** operátor může vrátit počet prvků v poli. Vrátí hodnotu 1 pro proměnné bez pole.

- **Velikost** operátor může vrátit velikost proměnné jazyka C nebo C++. Velikost proměnné je produkt jeho **délka** a **typ**.

- **Typ** operátor může vrátit velikost typu jazyka C nebo C++ nebo proměnné. Pokud je pole, proměnná **typ** vrátí velikost položky jediný prvek pole.

Například, pokud program neobsahuje 8 element **int** pole,

```cpp
int arr[8];
```

Následující C a sestavení výrazy yield velikost `arr` a jeho elementy.

|__asm|C|Velikost|
|-------------|-------|----------|
|**Délka** směrování žádostí na aplikace|`sizeof`(arr)/`sizeof`(arr[0])|8|
|**VELIKOST** směrování žádostí na aplikace|`sizeof`(arr)|32|
|**TYP** směrování žádostí na aplikace|`sizeof`(arr[0])|4|

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>