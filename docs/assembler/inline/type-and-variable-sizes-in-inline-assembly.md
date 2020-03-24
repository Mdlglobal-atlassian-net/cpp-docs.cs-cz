---
title: Typ a velikost proměnných ve vloženém sestavení
ms.date: 08/30/2018
ms.topic: reference
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
ms.openlocfilehash: bc98c8561a7fd06f875781802558cdd7e71a67ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169237"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ a velikost proměnných ve vloženém sestavení

**Specifické pro společnost Microsoft**

Operátory **Length**, **Size**a **Type** mají omezený význam ve vloženém sestavení. Nelze je použít vůbec pomocí operátoru `DUP` (protože nelze definovat data pomocí direktiv MASM nebo operátorů). Ale můžete je použít k nalezení velikosti C nebo C++ proměnných nebo typů:

- Operátor **Length** může vracet počet prvků v poli. Vrátí hodnotu 1 pro proměnné, které nejsou pole.

- Operátor **Size** může vracet velikost proměnné C nebo C++ . Velikost proměnné je součinem jeho **délky** a **typu**.

- Operátor **typu** může vracet velikost C++ typu nebo proměnné jazyka C. Pokud je proměnná pole, **typ** vrátí velikost jednoho prvku pole.

Například pokud má program pole typu **int** s 8 prvky,

```cpp
int arr[8];
```

Následující výrazy jazyka C a sestavení vynášejí velikost `arr` a jeho prvků.

|__asm|C|Velikost|
|-------------|-------|----------|
|**Délka** ARR|`sizeof`(ARR)/`sizeof`(šipka [0])|8|
|**Velikost** ARR|`sizeof`(ARR)|32|
|**Typ** ARR|`sizeof`(ARR [0])|4|

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
