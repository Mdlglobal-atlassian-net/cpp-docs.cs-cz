---
title: Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a06140522f9d4074eaa0403d0d05fe0f79adec0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Vyhledávání názvu závislého na argumentu (Koenig) ve funkcích
Kompilátor může použít vyhledávání názvu závislého na argumentu pro vyhledání definice neúplného volání funkce. Pro vyhledávání názvu závislého na argumentu je rovněž používán termín vyhledávání Koenig. Typ každého argumentu ve volání funkce je definován v rámci hierarchie oborů názvů, tříd, struktur, sjednocení nebo šablon. Pokud zadáte nekvalifikované [přípony](../cpp/postfix-expressions.md) volání funkce kompilátoru hledá v definici funkce v hierarchii spojené s každou typ argumentu.  
  
## <a name="example"></a>Příklad  
 V příkladu kompilátor zaznamená, že funkce `f()` přebírá argument `x`. Argument `x` je typu `A::X`, který je definován v oboru názvů `A`. Kompilátor vyhledá obor názvů `A` a najde definici funkce `f()`, která přebírá argument typu `A::X`.  
  
```  
// argument_dependent_name_koenig_lookup_on_functions.cpp  
namespace A  
{  
   struct X  
   {  
   };  
   void f(const X&)  
   {  
   }  
}  
int main()  
{  
// The compiler finds A::f() in namespace A, which is where   
// the type of argument x is defined. The type of x is A::X.  
   A::X x;  
   f(x);     
}  
```  
