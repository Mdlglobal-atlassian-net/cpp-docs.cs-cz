---
title: Chyba kompilátoru C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 8a4a2011124056af7064c8241450e1f3613776a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406701"
---
# <a name="compiler-error-c3073"></a>Chyba kompilátoru C3073

'type': Třída ref class nemá žádné uživatelem definovaného kopírovacího konstruktoru

V [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) kompilace, že kompilátor nevygeneruje kopírovacího konstruktoru pro typ odkazu. V žádném **/CLR** kompilace, je nutné definovat vlastní kopírovacího konstruktoru pro typ odkazu Pokud očekáváte, že instance typu, které se mají zkopírovat.

Další informace najdete v tématu [C++ – sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3073.

```
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```