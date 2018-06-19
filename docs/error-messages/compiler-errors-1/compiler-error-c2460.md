---
title: C2460 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4220be654f93ecd79d196efc14657ca7346411f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197777"
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