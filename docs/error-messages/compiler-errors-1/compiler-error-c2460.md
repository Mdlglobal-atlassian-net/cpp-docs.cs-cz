---
title: "C2460 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2460
dev_langs: C++
helpviewer_keywords: C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 00e4015a0dae5054973ba72bb0e4f89c7443ae03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2460"></a>C2460 chyby kompilátoru
'identifier1': používá 'identifier2', který je definovaný  
  
 Třídu nebo strukturu (`identifier2`) je deklarován jako členem sebe sama (`identifier1`). Rekurzivní definice tříd a struktur nejsou povoleny.  
  
 Následující ukázka generuje C2460:  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 Místo toho použijte odkaz na ukazatel ve třídě.  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```