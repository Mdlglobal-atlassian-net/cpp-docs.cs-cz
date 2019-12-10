---
title: 'Postupy: Určení výstupního parametru'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 5f0b462e672de4408d50bf95d65c749bf1881078
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988435"
---
# <a name="how-to-specify-an-out-parameter"></a>Postupy: Určení výstupního parametru

Tento příklad ukazuje, jak určit, že parametr funkce je výstupní parametr a jak tuto funkci volat z C# programu.

V vizuálu C++ je zadaný výstupní parametr s <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="example"></a>Příklad

První část této ukázky je vizuální C++ knihovna DLL s typem, který obsahuje funkci s výstupním parametrem.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>Příklad

Jedná se o C# klienta, který využívá vizuální C++ komponentu vytvořenou v předchozím příkladu.

```
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
