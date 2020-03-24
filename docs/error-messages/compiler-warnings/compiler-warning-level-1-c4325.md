---
title: Upozornění kompilátoru (úroveň 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163021"
---
# <a name="compiler-warning-level-1-c4325"></a>Upozornění kompilátoru (úroveň 1) C4325

> atributy standardního oddílu oddíl se*ignorují.*

## <a name="remarks"></a>Poznámky

Atributy standardního oddílu nemůžete změnit. Příklad:

```cpp
#pragma section(".sdata", long)
```

Tím by došlo k přepsání oddílu `.sdata` Standard, který používá **krátký** datový typ s datovým typem **Long** .

Standardní oddíly, jejichž atributy nemůžete změnit, zahrnují

- .data

- .sdata

- . bss

- . sbss

- .text

- . const

- .sconst

- .rdata

- .srdata

Další oddíly lze přidat později.

## <a name="see-also"></a>Viz také

[section](../../preprocessor/section.md)
