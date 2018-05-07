---
title: C3225 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3225
dev_langs:
- C++
helpviewer_keywords:
- C3225
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f9f6691ddacf6b3c1347b9fd4cac134433741a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3225"></a>C3225 chyby kompilátoru
argument obecného typu 'arg' nemůže být "typ", musí to být hodnota typu nebo zpracovat typ  
  
 Argument obecného typu nebyla správného typu.  
  
 Další informace najdete v tématu [obecné typy](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Nelze vytvořit instanci obecného typu pomocí nativního typu. Následující ukázka generuje C3225.  
  
```  
// C3225.cpp  
// compile with: /clr  
class A {};  
  
ref class B {};  
  
generic <class T>  
ref class C {};  
  
int main() {  
   C<A>^ c = gcnew C<A>;   // C3225  
   C<B^>^ c2 = gcnew C<B^>;   // OK  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří komponentu pomocí jazyka C#. Všimněte si, že omezení určuje, že obecného typu může být vytvořena pouze s typem hodnoty.  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka využívá jazyka C#-vytvořena součásti a porušuje omezení, které může být pouze MyList vytvořen s typem hodnoty jiné než <xref:System.Nullable>. Následující ukázka generuje C3225.  
  
```  
// C3225_c.cpp  
// compile with: /clr  
#using "C3225_b.dll"  
ref class A {};  
value class B {};  
int main() {  
   MyList<A> x;   // C3225  
   MyList<B> y;   // OK  
}  
```