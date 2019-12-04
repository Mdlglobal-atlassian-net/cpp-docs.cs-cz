---
title: Chyba kompilátoru C3162
ms.date: 11/04/2016
f1_keywords:
- C3162
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
ms.openlocfilehash: 95cd2c4af614906da7ba2d1c4c5dd488059f970a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761800"
---
# <a name="compiler-error-c3162"></a>Chyba kompilátoru C3162

' type ': typ odkazu, který má destruktor, nelze použít jako typ statického datového členu ' member '

Modul common language runtime nemůže rozpoznat, kdy se má spustit uživatelsky definovaný destruktor, pokud třída obsahuje také statickou členskou funkci.

Destruktor nebude nikdy spuštěn, dokud není objekt explicitně odstraněn.

Další informace najdete v tématu.

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C3162.

```cpp
// C3162.cpp
// compile with: /clr /c
ref struct A {
   ~A() { System::Console::WriteLine("in destructor"); }
   static A i;   // C3162
   static A^ a = gcnew A;   // OK
};

int main() {
   A ^ a = gcnew A;
   delete a;
}
```
