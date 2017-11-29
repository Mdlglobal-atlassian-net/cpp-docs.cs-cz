---
title: "C3390 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3390
dev_langs: C++
helpviewer_keywords: C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b4d2f74f23c58b234f6962f9a6a17ceec0f1bbc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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