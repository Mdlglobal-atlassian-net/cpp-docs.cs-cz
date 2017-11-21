---
title: "C2728 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2728
dev_langs: C++
helpviewer_keywords: C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f83665f1f2b388ac751dd4fd4aec2f75e8651a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2728"></a>C2728 chyby kompilátoru
'type': nativní pole nemůže obsahovat tento typ  
  
 Syntaxe vytváření pole byla použita k vytvoření pole spravované nebo WinRT objekty. Nelze vytvořit pole spravované nebo WinRT objekty pomocí syntaxe nativní pole.  
  
 Další informace najdete v tématu [pole](../../windows/arrays-cpp-component-extensions.md).  
  
 Následující ukázka generuje C2728 a ukazuje, jak to opravit:  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  
