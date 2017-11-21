---
title: "C2936 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2936
dev_langs: C++
helpviewer_keywords: C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c7949f958a6656c5e29210fcc4533c5730d18e02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2936"></a>C2936 chyby kompilátoru
'class': id – třída typu předefinovat jako proměnnou a globální data  
  
 Třídu generic nebo šablonu nelze použít jako globální data proměnné.  
  
 Tato chyba může být způsobena Pokud nesprávně se splní složené závorky.  
  
 Následující ukázka generuje C2936:  
  
```  
// C2936.cpp  
// compile with: /c  
template<class T> struct TC { };   
int TC<int>;   // C2936  
  
// OK  
struct TC2 { };   
int TC2;  
```  
  
 C2936 může dojít také při použití obecných typů:  
  
```  
// C2936b.cpp  
// compile with: /clr /c  
generic<class T>  
ref struct GC {};  
int GC<int>;   // C2936  
  
// OK  
ref struct GC2 {};  
int GC2;  
```