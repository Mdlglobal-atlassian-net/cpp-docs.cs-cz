---
title: 'Postupy: Určení výstupního parametru'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 8c3499a2916eda7ab96f7958df190c803206741e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437074"
---
# <a name="how-to-specify-an-out-parameter"></a>Postupy: Určení výstupního parametru

Tato ukázka předvádí, jak určit, že parametr funkce je výstupní parametr a jak tuto funkci volat z programu v jazyce C#.

Výstupní parametr je zadaný v jazyce Visual C++ s <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="example"></a>Příklad

První část této ukázce se knihovny DLL Visual C++ s typem, který obsahuje funkci s výstupní parametr.

```
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

To je klient jazyka C#, která využívá komponentu jazyka Visual C++ vytvořené v předchozím příkladu.

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

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)