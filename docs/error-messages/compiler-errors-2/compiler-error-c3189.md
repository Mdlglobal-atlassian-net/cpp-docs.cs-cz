---
title: Chyba kompilátoru C3189
ms.date: 11/04/2016
f1_keywords:
- C3189
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
ms.openlocfilehash: 2b53056cf8a7b4b9b49720ef17e8f9318390059a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761618"
---
# <a name="compiler-error-c3189"></a>Chyba kompilátoru C3189

typ typeid\<abstract deklarátor >: Tato syntaxe už není podporovaná, místo toho použijte:: typeid.

Použili jste zastaralou formu [typeid](../../extensions/typeid-cpp-component-extensions.md) , použijte nový formulář.

Následující ukázka generuje C3189:

```cpp
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```
