---
title: "Kompilátoru (úroveň 1) upozornění C4087 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4087
dev_langs: C++
helpviewer_keywords: C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d3a474b0f9c516cdd35d11fdd834da1ce6ac118
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4087"></a>C4087 kompilátoru upozornění (úroveň 1)
'function': deklarovat s seznam parametrů, void.  
  
 Deklarace funkce nemá žádné formální parametry, ale má volání funkce skutečného parametry. Další parametry jsou předány podle konvence volání funkce.  
  
 Toto upozornění je pro kompilátor jazyka C.  
  
## <a name="example"></a>Příklad  
  
```  
// C4087.c  
// compile with: /W1  
int f1( void ) {  
}  
  
int main() {  
   f1( 10 );   // C4087  
}  
```