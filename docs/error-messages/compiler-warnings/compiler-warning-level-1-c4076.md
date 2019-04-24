---
title: Kompilátor upozornění (úroveň 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208024"
---
# <a name="compiler-warning-level-1-c4076"></a>Kompilátor upozornění (úroveň 1) C4076

> "*modifikátor typu*': nelze použít s typem '*typename*.

## <a name="remarks"></a>Poznámky

Modifikátor typu, ať už jde o **podepsané** nebo **bez znaménka**, nelze použít s typem jiných než celých čísel. *Modifikátor typu* se ignoruje.

## <a name="example"></a>Příklad

Následující ukázka generuje C4076; Chcete-li problém odstranit, odeberte **bez znaménka** modifikátor typu:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```