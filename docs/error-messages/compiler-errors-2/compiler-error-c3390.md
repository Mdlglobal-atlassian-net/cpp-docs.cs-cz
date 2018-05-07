---
title: C3390 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3390
dev_langs:
- C++
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc731f714976d8ab32c5e7a629d008fde008a218
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3390"></a>C3390 chyby kompilátoru
'type_arg': Neplatný typ argumentu pro obecný parametr 'param' z obecného 'generic_type' musí být typu odkazu.  
  
Obecný typ byl nesprávně vytvořit instance.  Zkontrolujte definici typu.  Další informace najdete v tématu [obecné typy](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
První ukázka používá C# k vytvoření komponenty, která obsahuje obecný typ, který má určitá omezení, které nejsou podporovány při vytváření obecné typy v jazyce C + +/ CLR. Další informace najdete v tématu [omezení parametrů typů](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3390.cs  
// Compile by using: csc /target:library C3390.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
Pokud komponentu C3390.dll je k dispozici, generuje následující ukázka C3390.  
  
```cpp  
// C3390_b.cpp  
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>  
ref class R { R(int) {} };  
value class V {};  
ref struct N { N() {} };  
  
int main () {  
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type  
   GR<R^, V, N^>^ gr2b; // OK  
}  
```