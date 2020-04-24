---
title: Seznamy argumentů s proměnnou délkou (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: 8ea4d71bf9a22fc96c794a92ba43bed6548cf5d1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032301"
---
# <a name="variable-argument-lists--ccli"></a>Seznamy argumentů s proměnnou délkou (...) (C++/CLI)

Tento příklad ukazuje, jak `...` můžete použít syntaxi v jazyce C++/CLI k implementaci funkcí, které mají proměnný počet argumentů.

> [!NOTE]
> Toto téma se týkajících se C++/CLI. Informace o použití `...` normy ISO Standard C++ naleznete v [tématu Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md) a tři tečky a výchozí argumenty ve [výrazech Postfix](../cpp/postfix-expressions.md).

Parametr, který `...` používá, musí být posledním parametrem v seznamu parametrů.

## <a name="example"></a>Příklad

### <a name="code"></a>kód

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

Následující příklad ukazuje, jak volat z Jazyka C# visual c++ funkce, která má proměnný počet argumentů.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Funkce `f` může být volána z jazyka C# nebo Visual Basic, například, jako by to byla funkce, která může trvat proměnný počet argumentů.

V c#, argument, který `ParamArray` je předán parametru může být volána proměnný počet argumentů. Následující ukázka kódu je v c#.

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

Volání v `f` jazyce Visual C++ může předat inicializované pole nebo pole proměnné délky.

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

## <a name="see-also"></a>Viz také

[Pole](arrays-cpp-component-extensions.md)
