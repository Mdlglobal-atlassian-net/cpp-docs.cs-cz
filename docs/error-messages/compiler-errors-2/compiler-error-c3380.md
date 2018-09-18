---
title: Chyba kompilátoru C3380 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e35c4edaf24aacbd7eb9938a1dea2c470d32caae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062589"
---
# <a name="compiler-error-c3380"></a>Chyba kompilátoru C3380

'class': Neplatné sestavení přístup specifikátor - 'public' nebo 'private' jsou povolené jenom

Při použití u spravované třídy nebo struktury, [veřejné](../../cpp/public-cpp.md) a [privátní](../../cpp/private-cpp.md) klíčová slova označuje, zda třída bude vystavená prostřednictvím metadata sestavení. Pouze `public` nebo `private` lze použít na třídu v programu kompilovaného s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

`ref` a `value` klíčová slova, při použití s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), označení, že třída je spravovaná (naleznete v tématu [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md)).

Následující ukázka generuje C3380:

```
// C3380_2.cpp
// compile with: /clr
protected ref class A {   // C3380
// try the following line instead
// ref class A {
public:
   static int i = 9;
};

int main() {
   A^ myA = gcnew A;
   System::Console::WriteLine(myA->i);
}
```
