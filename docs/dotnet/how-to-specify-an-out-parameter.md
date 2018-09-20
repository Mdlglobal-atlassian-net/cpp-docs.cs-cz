---
title: 'Postupy: určení výstupního parametru | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3af9c1d10206e89b0ad8462bd95fdf3b6062d713
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419500"
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