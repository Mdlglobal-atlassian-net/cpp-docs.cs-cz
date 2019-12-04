---
title: Chyba kompilátoru C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: 560f4e8ef39e265f20d3c119858ff06b463d9841
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758135"
---
# <a name="compiler-error-c3669"></a>Chyba kompilátoru C3669

member: specifikátor override override není povolený u statických členských funkcí nebo konstruktorů.

Přepsání bylo nesprávně zadáno. Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3669.

```cpp
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```
