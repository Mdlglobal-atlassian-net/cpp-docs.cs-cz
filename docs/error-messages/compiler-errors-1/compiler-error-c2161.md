---
title: "C2161 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2161
dev_langs: C++
helpviewer_keywords: C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 987fc13615648d44d5c21769100963843fececa7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2161"></a>C2161 chyby kompilátoru
' ##' nelze provést na konci definici – makro  
  
 Definice makra bylo dokončeno s operátor vložení tokenu (##).  
  
 Následující ukázka generuje C2161:  
  
```  
// C2161.cpp  
// compile with: /c  
#define mac(a,b) a   // OK  
#define mac(a,b) a##   // C2161  
```