---
title: Chyba kompilátoru C2788 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2788
dev_langs:
- C++
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9a1464431d91e62ad07b4da0b3d1c8f9c13b243
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096207"
---
# <a name="compiler-error-c2788"></a>Chyba kompilátoru C2788

'identifier': více než jeden identifikátor GUID přidružený k tomuto objektu

[__Uuidof](../../cpp/uuidof-operator.md) operátor má uživatelem definovaný typ GUID připojený nebo objekt takový typ definovaný uživatelem. Tato chyba nastane, pokud argument je objekt s více identifikátorů GUID.

Následující ukázka generuje C2788:

```
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```