---
title: C2993 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e25e70a9d16ee166772cf03ea1837afaf14cae29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33242312"
---
# <a name="compiler-error-c2993"></a>C2993 chyby kompilátoru
"identifikátor": Neplatný typ pro parametr šablony bez typu "parametr"  
  
 Šablonu s struktura nebo union argument nelze deklarovat. Používáte ukazatele k předání struktury a sjednocení jako parametry šablony.  
  
 Následující ukázka generuje C2993:  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 Tato chyba bude vygenerována také v důsledku kompilátoru shoda práci, kterou bylo provedeno v sadě Visual Studio .NET 2003: plovoucí bodu parametry šablon bez typu již není povoleno. Standardní C++ neumožňuje plovoucí desetinné čárky parametry šablon bez typu.  
  
 Pokud je funkce šablony, použijte argument funkce předávat procedura bodu parametr šablony bez typu (Tento kód bude v verze Visual C++ pro Visual Studio .NET 2003 a sady Visual Studio .NET). Pokud je šablona třídy, je snadné alternativní řešení.  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```