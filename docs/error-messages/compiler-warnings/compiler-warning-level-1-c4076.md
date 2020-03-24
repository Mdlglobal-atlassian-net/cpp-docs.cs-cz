---
title: Upozornění kompilátoru (úroveň 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200253"
---
# <a name="compiler-warning-level-1-c4076"></a>Upozornění kompilátoru (úroveň 1) C4076

> *modifikátor typu*: nelze použít s typem*TypeName*.

## <a name="remarks"></a>Poznámky

Modifikátor typu, bez ohledu **na znaménko** nebo **znaménko**, nelze použít s typem, který není typu Integer. *modifikátor typu* se ignoruje.

## <a name="example"></a>Příklad

Následující ukázka generuje C4076; Pokud ho chcete opravit, odeberte modifikátor typu **bez znaménka** :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
