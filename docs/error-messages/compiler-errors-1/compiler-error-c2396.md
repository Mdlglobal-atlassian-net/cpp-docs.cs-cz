---
title: "C2396 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2396
dev_langs: C++
helpviewer_keywords: C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20eca11d402265bbc81d61a8079ae9975cceef67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2396"></a>C2396 chyby kompilátoru
' your_type::operator'type'': CLR nebo WinRT functionnot uživatelem definovaný převod platný. Musíte převést nebo převést na: 'T ^', se ^ %', se ^ & ", kde T = 'your_type'  
  
 Funkci pro převod v prostředí Windows Runtime nebo spravovaný typ neměl minimálně jeden parametr, jehož typ je stejný jako typ, který obsahuje funkci pro převod.  
  
 Následující ukázka generuje C2396 a ukazuje, jak to opravit:  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```