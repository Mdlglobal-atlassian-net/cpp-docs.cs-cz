---
title: Chyba kompilátoru C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: 3996e8e8d40ca24bf54fdf5bbbfde90f3d609c9d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751548"
---
# <a name="compiler-error-c2978"></a>Chyba kompilátoru C2978

Chyba syntaxe: očekával se typ ' keyword1 ' nebo ' keyword2 '; byl nalezen typ keyword3; parametry bez typu nejsou v obecných typech podporované.

Obecná třída byla deklarována nesprávně. Další informace najdete v tématu [Obecné](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2978.

```cpp
// C2978.cpp
// compile with: /clr /c
generic <ref class T>   // C2978
// try the following line instead
// generic <typename T>   // OK
ref class Utils {
   static void sort(T elems, size_t size);
};

generic <int>
// try the following line instead
// generic <class T>
ref class Utils2 {
   static void sort(T elems, size_t size);
};
```
