---
title: 'Postupy: použití nativního typu v kompilaci - clr | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e56c3617b6b2a8168e35867c09858dffa84cea9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448061"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Postupy: Použití nativního typu v kompilaci /clr

Můžete definovat v nativním typu **/CLR** kompilace a veškeré jeho používání nativního typu v rámci sestavení je platný. Nativní typy však nebudou k dispozici pro použití z odkazovaných metadat.

Každé sestavení musí obsahovat definici každý nativní typ, který bude používat.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Tato ukázka vytvoří komponentu, která definuje a používá nativního typu.

```
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

## <a name="example"></a>Příklad

Tato ukázka definuje klienta, který využívá komponentu. Všimněte si, že jedná se o chybu pro přístup k nativním typu, pokud je definována v souboru pro kompilaci.

```
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)