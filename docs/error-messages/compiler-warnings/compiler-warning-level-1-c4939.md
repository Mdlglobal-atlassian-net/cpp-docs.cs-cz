---
title: Kompilátor upozornění (úroveň 1) C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408248"
---
# <a name="compiler-warning-level-1-c4939"></a>Kompilátor upozornění (úroveň 1) C4939

\#vtordisp – Direktiva pragma je zastaralá a v příští verzi Visual C++ se odebere

[Vtordisp](../../preprocessor/vtordisp.md) – Direktiva pragma se odebere v budoucí verzi jazyka Visual C++.

## <a name="example"></a>Příklad

Následující ukázka generuje C4939.

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```