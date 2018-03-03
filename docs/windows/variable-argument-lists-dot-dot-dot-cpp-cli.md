---
title: "Seznam argumentů s proměnnou délkou (...) (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b78b244a93bea0c669c37b5df32ec7146f7ac3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="variable-argument-lists--ccli"></a>Seznamy argumentů s proměnnou délkou (...) (C++/CLI)
Tento příklad ukazuje, jak můžete použít `...` syntaxe v jazyce Visual C++ implementovat funkce, které mají proměnný počet argumentů.  
  
> [!NOTE]
>  Toto téma se věnuje pro C + +/ CLI. Informace o používání `...` v ISO Standard C++, najdete v části [tři tečky a Variadické šablony](../cpp/ellipses-and-variadic-templates.md) a výpustky a výchozí argumenty v [výrazy přípony](../cpp/postfix-expressions.md).  
  
 Parametr, který používá `...` musí být poslední parametr v seznamu parametrů.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
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
  
### <a name="output"></a>Výstup  
  
```  
3  
```  
  
## <a name="code-example"></a>Příklad kódu  
 Následující příklad ukazuje, jak volat z jazyka C# Visual C++ funkce, která přebírá proměnný počet argumentů.  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 Funkce `f` lze volat z jazyka C# nebo Visual Basic, například jako by šlo funkci, která může trvat proměnný počet argumentů.  
  
 V jazyce C#, argument, který je předán `ParamArray` parametr může být volána proměnný počet argumentů. Následující ukázka kódu je v jazyce C#.  
  
```  
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
  
 Volání `f` v jazyce Visual C++ můžete předat inicializovaného pole nebo pole proměnlivou délkou.  
  
```  
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
 [Pole](../windows/arrays-cpp-component-extensions.md)