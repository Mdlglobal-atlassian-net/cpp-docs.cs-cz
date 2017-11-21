---
title: "C3755 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3755
dev_langs: C++
helpviewer_keywords: C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c302a3a0a417b8668d18c8329b083648cb28ccab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3755"></a>C3755 chyby kompilátoru
'delegovat': delegáta nesmí být definován.  
  
 A [delegáta (rozšíření komponent C++)](../../windows/delegate-cpp-component-extensions.md) lze deklarovat, ale není definován.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3755.  
  
```  
// C3755.cpp  
// compile with: /clr /c  
delegate void MyDel() {};   // C3755  
```  
  
## <a name="example"></a>Příklad  
 C3755 může také nastat, pokud se pokusíte vytvořit šablonu delegáta. Následující ukázka generuje C3755.  
  
```  
// C3755_b.cpp  
// compile with: /clr /c  
ref struct R {  
   template<class T>  
   delegate void D(int) {}   // C3755  
};  
```