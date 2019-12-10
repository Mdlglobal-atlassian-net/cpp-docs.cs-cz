---
title: 'Postupy: použití nativního typu v kompilaci-clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: b506c3d825c4c26236a4ac3fc9682067a011315a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988425"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Postupy: Použití nativního typu v kompilaci /clr

V kompilaci **/CLR** můžete definovat nativní typ a jakékoli použití tohoto nativního typu v rámci sestavení je platné. Nativní typy však nebudou k dispozici pro použití z odkazovaných metadat.

Každé sestavení musí obsahovat definici každého nativního typu, který bude používat.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Tato ukázka vytvoří komponentu, která definuje a používá nativní typ.

```cpp
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

Tato ukázka definuje klienta, který využívá komponentu. Všimněte si, že se jedná o chybu pro přístup k nativnímu typu, pokud není definováno v rozhraní kompilantu.

```cpp
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

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
