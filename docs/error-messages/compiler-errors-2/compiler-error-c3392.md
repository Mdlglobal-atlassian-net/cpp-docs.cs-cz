---
title: "C3392 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3392
dev_langs: C++
helpviewer_keywords: C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 12ed6dbcc7351926d51df4aa9e3397f3bb598f10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3392"></a>C3392 chyby kompilátoru
'type_arg': Neplatný typ argumentu pro obecný parametr 'param' z obecného 'generic_type', musí mít veřejný konstruktor  
  
 Obecný typ byl nesprávně vytvořit instance. Zkontrolujte definici typu. Další informace najdete v tématu [obecné typy](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
Následující příklad používá C# k vytvoření komponenty, která obsahuje obecný typ, který má určitá omezení, které nejsou podporovány při vytváření obecné typy v jazyce C + +/ CLI. Další informace najdete v tématu [omezení parametrů typů](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3392.cs  
// Compile by using: csc /target:library C3392.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
Pokud komponentu C3392.dll je k dispozici, generuje následující ukázka C3392.  
  
```cpp  
// C3392_b.cpp  
// Compile by using: cl /clr C3392_b.cpp  
#using <C3392.dll>  
  
ref class R { R(int) {} };  
ref class N { N() {} };  
  
value class V {};  
  
ref class N2 { public: N2() {} };  
ref class R2 { public: R2() {} };  
  
int main () {  
   GR<R^, V, N^>^ gr1;   // C3392  
   GR<R^, V, N2^>^ gr1a; // OK  
  
   GR<R^, N^, N^>^ gr3;  // C3392  
   GR<R^, V, N2^>^ gr3a; // OK  
  
   GR<R^, V, R^>^ gr4;   // C3392  
   GR<R^, V, R2^>^ gr4a; // OK  
}  
```