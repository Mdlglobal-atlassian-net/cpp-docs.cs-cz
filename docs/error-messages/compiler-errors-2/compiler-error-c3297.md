---
title: Chyba kompilátoru C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 6fed01b0dcf50a657b6eb457ab8e546d0648beec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760088"
---
# <a name="compiler-error-c3297"></a>Chyba kompilátoru C3297

' constraint_2 ': nelze použít ' constraint_1 ' jako omezení, protože ' constraint_1 ' má omezení hodnoty

Třídy hodnot jsou zapečetěné. Pokud je omezení hodnotovou třídou, nelze z ní nikdy odvodit jiné omezení.

Další informace najdete v tématu [omezení parametrů obecného typuC++(/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3297.

```cpp
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```
