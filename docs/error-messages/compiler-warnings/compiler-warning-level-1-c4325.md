---
title: Upozornění (úroveň 1) C4325 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd265938afb51cc402dc84f38b7e95188c6292a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197482"
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

- .sdata.

- .BSS

- .sbss

- .text

- .const

- .sconst

- .rdata

- .srdata

Další oddíly mohou být přidány později.

## <a name="see-also"></a>Viz také:

[section](../../preprocessor/section.md)