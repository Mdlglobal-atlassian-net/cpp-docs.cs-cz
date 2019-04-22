---
title: Chyba kompilátoru C3374
ms.date: 11/04/2016
f1_keywords:
- C3374
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
ms.openlocfilehash: 4b00b1cea8ac462c82c11d9f5b207706af74959c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022629"
---
# <a name="compiler-error-c3374"></a>Chyba kompilátoru C3374

nejde převzít adresu 'function', pokud se nevytváří instance delegáta

Adresa funkce byla získána v jiném kontextu než vytvoření instance delegáta.

Následující ukázka generuje C3374:

```
// C3374.cpp
// compile with: /clr
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      System::Console::WriteLine("in func1 {0}", i);
   }
};

int main() {
   &A::func1;   // C3374

   // OK
   A ^ a = gcnew A;
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);
}
```

## <a name="see-also"></a>Viz také:

[Postupy: Definice a používání delegátů (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)