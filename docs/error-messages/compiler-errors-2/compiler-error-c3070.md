---
title: Chyba kompilátoru C3070
ms.date: 11/04/2016
f1_keywords:
- C3070
helpviewer_keywords:
- C3070
ms.assetid: ac88584d-40a6-4176-90f3-2371c3c935f2
ms.openlocfilehash: d97550560e12ef9778553a809e02c1fb0d2d8b19
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758200"
---
# <a name="compiler-error-c3070"></a>Chyba kompilátoru C3070

' Property ': vlastnost nemá metodu ' set '

Metoda set přístupového objektu vlastnosti nebyla definována. Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md).

Následující ukázka generuje C3070:

```cpp
// C3070.cpp
// compile with: /clr
ref class R {
public:
   R(int size) {
      m_data = gcnew array<int>(size);
   }

   property int % MyProp[int] {
      int% get(int index) {
         return m_data[index];
      }
   }

   property int % MyProp2[int] {
      int% get(int index) {
         return m_data[index];
      }
      void set(int index, int % value) {}
   }

   property const int % MyProp3[int] {
      const int% get(int index) {
         return m_data[index];
      }
      void set(int index, const int % value) {}
   }

private:
   array<int>^ m_data;
};

int main() {
   R^ r = gcnew R(10);
   r->MyProp[4] = 4;   // C3070

   int value = 4;
   r->MyProp2[4] = value;   // OK
   r->MyProp3[4] = 4;   // OK
}
```
