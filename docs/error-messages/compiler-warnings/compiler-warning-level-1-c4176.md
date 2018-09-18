---
title: Upozornění (úroveň 1) C4176 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4176
dev_langs:
- C++
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f173e132a2bd0d54c32fb0c2f7ae3b13dff1657d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085703"
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