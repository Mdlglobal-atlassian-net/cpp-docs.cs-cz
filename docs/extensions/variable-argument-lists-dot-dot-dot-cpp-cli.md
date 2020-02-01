---
title: Seznamy argumentů s proměnnou délkou (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 4db75653251a558d6f43f5be63098fbb26e1e6ff
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912843"
---
# <a name="variable-argument-lists--ccli"></a>Seznamy argumentů s proměnnou délkou (...) (C++/CLI)

Tento příklad ukazuje, jak lze použít syntaxi `...` v C++/CLI k implementaci funkcí, které mají proměnný počet argumentů.

> [!NOTE]
> Toto téma se C++týká/CLI. Informace o použití `...` v normě C++ISO najdete v tématu [elipsy a šablony variadické](../cpp/ellipses-and-variadic-templates.md) a tři tečky a výchozí argumenty ve [výrazech přípony](../cpp/postfix-expressions.md).

Parametr, který používá `...`, musí být posledním parametrem v seznamu parametrů.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>Příklad kódu

Následující příklad ukazuje, jak volat z C# vizuální C++ funkce, která přijímá proměnný počet argumentů.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Funkci `f` lze volat z C# nebo Visual Basic, například jako by byla funkce, která může převzít proměnný počet argumentů.

V C#, argument, který je předán parametru `ParamArray`, může být volán proměnným počtem argumentů. Následující ukázka kódu je v C#.

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Volání `f` v vizuálu C++ může předat inicializované pole nebo pole s proměnnou délkou.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>Viz také:

[Pole](arrays-cpp-component-extensions.md)