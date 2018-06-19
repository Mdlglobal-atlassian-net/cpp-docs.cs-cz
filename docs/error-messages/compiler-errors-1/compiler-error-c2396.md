---
title: C2396 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd9007d15cb5b6f9badf8f0962c8c1aa29df5bf7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197452"
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