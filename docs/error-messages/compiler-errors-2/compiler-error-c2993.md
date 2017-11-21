---
title: "C2993 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2993
dev_langs: C++
helpviewer_keywords: C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a6306b2c3c632d25ee6b37a025516f759cc126a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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