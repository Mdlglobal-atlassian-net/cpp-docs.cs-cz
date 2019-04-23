---
title: Chyba kompilátoru C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: 516690f2524d48e7abbf7546592c6346e92c3e2e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778862"
---
# <a name="compiler-error-c3380"></a>Chyba kompilátoru C3380

'class': Neplatné sestavení přístup specifikátor - 'public' nebo 'private' jsou povolené jenom

Při použití u spravované třídy nebo struktury, [veřejné](../../cpp/public-cpp.md) a [privátní](../../cpp/private-cpp.md) klíčová slova označuje, zda třída bude vystavená prostřednictvím metadata sestavení. Pouze `public` nebo `private` lze použít na třídu v programu kompilovaného s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

`ref` a `value` klíčová slova, při použití s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), označení, že třída je spravovaná (naleznete v tématu [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md)).

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
