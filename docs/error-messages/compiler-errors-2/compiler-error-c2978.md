---
title: Chyba kompilátoru C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: 25798e793bec7d09ea1f307ec1e2d9a63b9dbe27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428103"
---
# <a name="compiler-error-c2978"></a>Chyba kompilátoru C2978

Chyba syntaxe: byl očekáván "keyword1" nebo 'keyword2'; našel se typ 'keyword3'; v obecných typech nejsou podporované netypové parametry

Obecné třídy byl deklarován nesprávně. Zobrazit [obecných typů](../../windows/generics-cpp-component-extensions.md)Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C2978.

```
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