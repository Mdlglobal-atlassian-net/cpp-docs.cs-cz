---
title: "Kompilátoru (úroveň 3) upozornění C4240 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4240
dev_langs: C++
helpviewer_keywords: C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb26996ce68a29126292923ebe27e3dcfefd8f7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4240"></a>C4240 kompilátoru upozornění (úroveň 3)
nestandardní rozšíření používané: přístup k nyní definována jako 'přístup specifikátor', dříve ho classname byl definován jako "přístup specifikátor"  
  
 V části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), nelze přístup do vnořené třídy. V části rozšíření Microsoft výchozí (/Ze) je to možné, se toto upozornění.  
  
## <a name="example"></a>Příklad  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```