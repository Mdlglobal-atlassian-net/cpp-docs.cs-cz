---
title: "Kompilátoru (úroveň 4) upozornění C4131 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4131
dev_langs: C++
helpviewer_keywords: C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 48e7ed1c5570e8bfa9d571cde649e618f51bcc2a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4131"></a>C4131 kompilátoru upozornění (úroveň 4)
'function': používá deklarátor starého stylu  
  
 Deklarace zadaná funkce není v podobě prototypu.  
  
 Deklarace funkcí starého stylu mají být převedeny na prototypu formuláře.  
  
 Následující příklad ukazuje deklaraci starého funkce:  
  
```  
// C4131.c  
// compile with: /W4 /c  
void addrec( name, id ) // C4131 expected  
char *name;  
int id;  
{ }  
```  
  
 Následující příklad ukazuje prototypu formuláře:  
  
```  
void addrec( char *name, int id )  
{ }  
```