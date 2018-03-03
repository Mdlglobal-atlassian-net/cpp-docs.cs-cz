---
title: "C2460 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97ab5f3a2635bf25c01c2e54ba27c49447f1514a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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