---
title: Chyba kompilátoru C3367 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3367
dev_langs:
- C++
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e063635e521efe1eabf8f2b50664ef8bf3e85e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020224"
---
# <a name="compiler-error-c3367"></a>Chyba kompilátoru C3367

'static_member_function': statické funkce nelze použít k vytvoření delegáta bez vazby

Při volání delegáta bez vazby, musíte předat instanci objektu. Protože statické členské funkce je volána pomocí názvu třídy, můžete vytvořit pouze instanci delegáta bez vazby s členskou funkci instance.

Další informace o nevázaní delegáti najdete v tématu [postupy: definování a používání delegátů (C + +/ CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

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