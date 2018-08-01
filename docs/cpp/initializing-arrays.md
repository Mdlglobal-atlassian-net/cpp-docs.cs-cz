---
title: Inicializace polí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- initializing arrays [C++]
- arrays [C++], initializing
ms.assetid: 41efe5f0-15b5-4f49-9196-c4902f8fc705
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e1ecb15cfc34ec518f46474497a3577a51b00c4e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408575"
---
# <a name="initializing-arrays"></a>Inicializace polí
Má-li třída konstruktor, pole této třídy jsou inicializována konstruktorem. Je-li v seznamu inicializátorů méně položek než prvků pole, je pro zbývající prvky použit výchozí konstruktor. Není-li pro třídu definován výchozí konstruktor, musí být seznam inicializátorů úplný – pro každý prvek pole tedy musí existovat jeden inicializátor.  
  
 Vezměte v úvahu třídu `Point` definující dva konstruktory:  
  
```cpp 
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
  
 Statická členská pole (ať už **const** nebo ne) lze inicializovat v jejich definicích (mimo deklaraci třídy). Příklad:  
  
```cpp 
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