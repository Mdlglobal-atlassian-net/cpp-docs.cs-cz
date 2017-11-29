---
title: "C2937 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2937
dev_langs: C++
helpviewer_keywords: C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f741a47699263eed55fd8984b9a8cc3e2a96b4fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2937"></a>C2937 chyby kompilátoru
'class': id – třída typu předefinovat jako globální – typedef  
  
 Třídu generic nebo šablonu nelze použít jako globální konfiguraci `typedef`.  
  
 Následující ukázka generuje C2937:  
  
```  
// C2937.cpp  
// compile with: /c  
template<class T>   
struct TC { };  
typedef int TC<int>;   // C2937  
typedef TC<int> c;   // OK  
```  
  
 C2937 může dojít také při použití obecných typů:  
  
```  
// C2937b.cpp  
// compile with: /clr  
generic<class T>  
ref struct GC { };  
typedef int GC<int>;   // C2937  
typedef GC<int> xx;   // OK  
```