---
title: Chyba kompilátoru C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: bedc94039f8621a93672c0dfa0cad5a54aad796e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201159"
---
# <a name="compiler-error-c3367"></a>Chyba kompilátoru C3367

' static_member_function ': funkci Static nelze použít k vytvoření delegáta bez vazby

Při volání delegáta bez vazby je nutné předat instanci objektu. Vzhledem k tomu, že statická členská funkce je volána prostřednictvím názvu třídy, lze vytvořit instanci nevázaného delegáta s členskou funkcí instance.

Další informace o nevázaných delegátech naleznete v tématu [How to: Define andC++use Delegates (/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3367.

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```
