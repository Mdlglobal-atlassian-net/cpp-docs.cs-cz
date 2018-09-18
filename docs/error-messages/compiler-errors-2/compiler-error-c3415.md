---
title: Chyba kompilátoru C3415 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3415
dev_langs:
- C++
helpviewer_keywords:
- C3415
ms.assetid: fa2db8ab-2820-4ec3-a740-fb5e2adcfb29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dd99f96bbc756261676962f86c3f4cbad46abe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105060"
---
# <a name="compiler-error-c3415"></a>Chyba kompilátoru C3415

více oddílů 'název_oddílu' nalezen s rozdílnými atributy (hodnota)

Byly zadány konfliktní hodnoty v [části](../../preprocessor/section.md) direktivy pragma.

`value` je aktuální nastavení pro oddíl, jak je uvedeno v ntimage.h. Příklad:

```
// Section contains extended relocations.
#define IMAGE_SCN_LNK_NRELOC_OVFL            0x01000000
// Section can be discarded.
#define IMAGE_SCN_MEM_DISCARDABLE            0x02000000
// Section is not cachable.
#define IMAGE_SCN_MEM_NOT_CACHED             0x04000000
// Section is not pageable.
#define IMAGE_SCN_MEM_NOT_PAGED              0x08000000
// Section is shareable.
#define IMAGE_SCN_MEM_SHARED                 0x10000000
// Section is executable.
#define IMAGE_SCN_MEM_EXECUTE                0x20000000
// Section is readable.
#define IMAGE_SCN_MEM_READ                   0x40000000
// Section is writeable.
#define IMAGE_SCN_MEM_WRITE                  0x80000000
```

Následující ukázka generuje C3415:

```
// C3415.cpp
#pragma section("mysec1",write)
#pragma section("mysec1",read)   // C3415
```