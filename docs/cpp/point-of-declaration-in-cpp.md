---
title: Bod deklarace v C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e42f43e6187e19df6e9c1111c0e92aa4b9929199
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
 [Rozsah](../cpp/scope-visual-cpp.md)