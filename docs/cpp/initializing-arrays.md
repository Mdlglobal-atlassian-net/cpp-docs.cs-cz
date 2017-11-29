---
title: "Inicializace polí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- initializing arrays [C++]
- arrays [C++], initializing
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13e02dda301059204f6feaa085ce97d1568e74d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="initializing-arrays"></a>Inicializace polí
Má-li třída konstruktor, pole této třídy jsou inicializována konstruktorem. Je-li v seznamu inicializátorů méně položek než prvků pole, je pro zbývající prvky použit výchozí konstruktor. Není-li pro třídu definován výchozí konstruktor, musí být seznam inicializátorů úplný – pro každý prvek pole tedy musí existovat jeden inicializátor.  
  
 Vezměte v úvahu třídu `Point` definující dva konstruktory:  
  
```  
// initializing_arrays1.cpp  
class Point  
{  
public:  
   Point()   // Default constructor.  
   {  
   }  
   Point( int, int )   // Construct from two ints  
   {  
   }  
};  
  
// An array of Point objects can be declared as follows:  
Point aPoint[3] = {  
   Point( 3, 3 )     // Use int, int constructor.  
};  
  
int main()  
{  
}  
```  
  
 První prvek pole `aPoint` je vytvořen pomocí konstruktoru `Point( int, int )`. Zbývající dva prvky jsou vytvořeny výchozím konstruktorem.  
  
 Statický člen pole (jestli **const** nebo ne) jde inicializovat na jejich definice (mimo deklaraci třídy). Příklad:  
  
```  
// initializing_arrays2.cpp  
class WindowColors  
{  
public:  
    static const char *rgszWindowPartList[7];  
};  
  
const char *WindowColors::rgszWindowPartList[7] = {  
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",  
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };  
int main()  
{  
}  
```  
  