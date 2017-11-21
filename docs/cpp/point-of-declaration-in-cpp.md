---
title: Bod deklarace v C++ | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a528bdeaa401aaab7d9287b0e9dd5aace2c93b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="point-of-declaration-in-c"></a>Bod deklarace v C++
Název se považuje deklarovat ihned po jeho deklarátor, ale před jeho inicializátoru (volitelné). (Další informace o deklarátory najdete v tématu [deklarace a definice](declarations-and-definitions-cpp.md).)  
  
 Vezměte v úvahu v tomto příkladu:  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 Pokud bod deklarace byly *po* inicializace a pak místní `dVar` bude inicializována tak, aby 7.0, hodnotu globální proměnné `dVar`. Nicméně, protože se nejedná o případ, `dVar` je inicializováno nedefinovanou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Obor](../cpp/scope-visual-cpp.md)