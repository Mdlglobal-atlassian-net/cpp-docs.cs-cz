---
title: Kompilátor upozornění (úroveň 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 293cbbcfe134f6cb4f5e1bf924be7c03fa278833
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408534"
---
# <a name="compiler-warning-level-1-c4325"></a>Kompilátor upozornění (úroveň 1) C4325

> atributy pro oddíl standard "*části*se ignoruje

## <a name="remarks"></a>Poznámky

Atributy oddíl standard nejde změnit. Příklad:

```cpp
#pragma section(".sdata", long)
```

To by přepsala `.sdata` oddíl standard, která používá **krátký** datový typ s **dlouhé** datového typu.

Zahrnují standardní oddíly, jejichž atributy nejde změnit

- .data

- .sdata

- .bss

- .sbss

- .text

- .const

- .sconst

- .rdata

- .srdata

Další oddíly mohou být přidány později.

## <a name="see-also"></a>Viz také:

[section](../../preprocessor/section.md)