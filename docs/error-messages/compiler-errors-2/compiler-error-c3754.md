---
title: Chyba kompilátoru C3754 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3754
dev_langs:
- C++
helpviewer_keywords:
- C3754
ms.assetid: 14b877bc-9277-40ec-af1c-196a58b45f10
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9d25d09343cc2a8d341925727529be7d435d9da
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023472"
---
# <a name="compiler-error-c3754"></a>Chyba kompilátoru C3754

Konstruktor Delegate: členskou funkci 'function' nelze volat na instanci typu 'type'

Došlo k volání funkce prostřednictvím ukazatele na typ, který neobsahuje funkci.

## <a name="example"></a>Příklad

Následující ukázka generuje C3754:

```
// C3754a.cpp
// compile with: /clr
using namespace System;

delegate void MyDel();

interface class MyInterface {};

ref struct MyClass : MyInterface {
   void f() {}
};

int main() {
   MyInterface^ p = gcnew MyClass;
   MyDel^ q = gcnew MyDel(p, &MyClass::f);   // C3754
   // try the following line instead
//   MyDel^ q = gcnew MyDel(safe_cast<MyClass^>(p), &MyClass::f);
}
```
