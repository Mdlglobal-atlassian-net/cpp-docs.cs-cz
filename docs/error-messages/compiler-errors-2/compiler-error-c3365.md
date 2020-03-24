---
title: Chyba kompilátoru C3365
ms.date: 11/04/2016
f1_keywords:
- C3365
helpviewer_keywords:
- C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
ms.openlocfilehash: 355c4530fffa89470ac495aff8bc2822278e2da3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201192"
---
# <a name="compiler-error-c3365"></a>Chyba kompilátoru C3365

operátor ' operator ': lišící se operandy typu ' typ1 ' a ' typ2 '

Byl proveden pokus o vytvoření delegátů s různými typy.  Další informace o delegátech naleznete v tématu [HowC++to: Define and use Delegates (/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3365:

```cpp
// C3365.cpp
// compile with: /clr
delegate void D1();
delegate void D2(int);

ref class R {
public:
   void f(){}
   void g(int){}
};

int main() {
   D1^ d1 = gcnew D1(gcnew R, &R::f);
   D2^ d2 = gcnew D2(gcnew R, &R::g);
   D1^ d3 = gcnew D1(gcnew R, &R::f);

   d1 += d2;   // C3365
   d1 += d3;   // OK
   d1();
}
```
