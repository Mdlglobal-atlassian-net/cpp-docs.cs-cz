---
title: Kompilátor upozornění (úroveň 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: 44f2dea9b5f0afb5b97867f9137f420ad92c388a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443118"
---
# <a name="compiler-warning-level-1-c4176"></a>Kompilátor upozornění (úroveň 1) C4176

'%1.dílčí součást': Neznámá dílčí komponenta pro prohlížeč komponenta #pragma

**Komponenty** – Direktiva pragma obsahuje neplatný dílčí komponenta. Vyloučit odkazy na konkrétní název, je nutné použít **odkazy** možnost před název.

## <a name="example"></a>Příklad

```
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```