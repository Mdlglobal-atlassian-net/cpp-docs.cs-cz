---
title: Upozornění (úroveň 1) C4076 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928b0a78c09773e334c1a291877b74304dab66ec
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198475"
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