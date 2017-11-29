---
title: "Manipulátory výstupního datového proudu s jedním argumentem (int nebo long) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 418b9e1f982e1bb37559ee35b6953d7d3f198b61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulátory výstupního datového proudu s jedním argumentem (int nebo long)
Iostream – knihovna tříd poskytuje sadu makra pro vytváření parametrizované manipulátory. Manipulátory s jedním `int` nebo `long` argument představují zvláštní případ. Chcete-li vytvořit manipulator datového proudu výstup, který přijímá jeden `int` nebo `long` argument (jako `setw`), je nutné použít makro _Smanip, která je definována v \<iomanip – >. Tento příklad definuje `fillblank` manipulator, který se vloží do datového proudu zadaný počet prázdných hodnot:  
  
## <a name="example"></a>Příklad  
  
```cpp  
// output_stream_manip.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
void fb( ios_base& os, int l )  
{  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
}  
  
_Smanip<int>  
   __cdecl fillblank(int no)  
   {     
   return (_Smanip<int>(&fb, no));  
   }  
  
int main( )  
{  
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vlastní manipulátory bez argumentů](../standard-library/custom-manipulators-with-arguments.md)
