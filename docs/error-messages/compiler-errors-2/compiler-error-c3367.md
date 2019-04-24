---
title: Chyba kompilátoru C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: f53312fa9225270ef79d50d2ad351adce790d6fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300530"
---
# <a name="compiler-error-c3367"></a>Chyba kompilátoru C3367

'static_member_function': statické funkce nelze použít k vytvoření delegáta bez vazby

Při volání delegáta bez vazby, musíte předat instanci objektu. Protože statické členské funkce je volána pomocí názvu třídy, můžete vytvořit pouze instanci delegáta bez vazby s členskou funkci instance.

Další informace o nevázaní delegáti najdete v tématu [jak: Definice a používání delegátů (C++vyhodnocovací)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

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