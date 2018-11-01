---
title: Chyba kompilátoru C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: db448b462cd3a3f325c529e730e5c8f65e2b8f51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598806"
---
# <a name="compiler-error-c3185"></a>Chyba kompilátoru C3185

použít typeid spravovaných nebo typ WinRT 'type', použijte 'operator'

Nelze použít [typeid](../../cpp/typeid-operator.md) operátor pro spravované nebo WinRT typ; použijte [typeid](../../windows/typeid-cpp-component-extensions.md) místo.

Následující ukázka generuje C3185 a ukazuje, jak ho opravit:

```
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```
