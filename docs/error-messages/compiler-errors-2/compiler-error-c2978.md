---
title: Chyba kompilátoru C2978 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2978
dev_langs:
- C++
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40d7569a250812d6807c4723366b88e2f290be85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045182"
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