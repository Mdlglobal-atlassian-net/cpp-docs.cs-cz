---
title: Seznamy argumentů s proměnnou délkou (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: ec1e2cefa33bc9d749d0f05e170c2f2db9b25f02
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031612"
---
# <a name="variable-argument-lists--ccli"></a>Seznamy argumentů s proměnnou délkou (...) (C++/CLI)

Tento příklad ukazuje, jak můžete použít `...` syntaxe v jazyce C + +/ CLI k implementaci funkcí, které mají variabilní počet argumentů.

> [!NOTE]
> Toto téma se vztahuje k C + +/ CLI. Informace o používání `...` ve standardu ISO C++ naleznete v tématu [tři tečky a Variadické šablony](../cpp/ellipses-and-variadic-templates.md) a symbol tří teček a výchozí argumenty v [výrazy přípony](../cpp/postfix-expressions.md).

Parametr, který používá `...` musí být posledním parametrem v seznamu parametrů.

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

Následující příklad ukazuje, jak volat z jazyka C# funkci Visual C++, která přijímá proměnný počet argumentů.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Funkce `f` lze volat z C# nebo Visual Basic, například jako by šlo funkce, která může mít proměnný počet argumentů.

V jazyce C#, argument, který je předán `ParamArray` parametr může být volán proměnným počtem argumentů. Následující ukázka kódu je v jazyce C#.

```cs
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

Volání `f` v jazyce Visual C++ může předat inicializované pole nebo pole s proměnnou délkou.

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