---
title: "C2388 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2388
dev_langs: C++
helpviewer_keywords: C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3a2ad344bc1c23568b554a7a89fb42470c299e8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2388"></a>C2388 chyby kompilátoru
'symbol': symbol nelze deklarovat s obou __declspec(appdomain) a \__declspec(process)  
  
 `appdomain` a `process` `__declspec` Modifikátory nelze použít na stejné symbol. Úložiště pro proměnnou existuje pro proces, nebo v doméně aplikace.  
  
 Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [proces](../../cpp/process.md).  
  
 Následující ukázka generuje C2388:  
  
```  
// C2388.cpp  
// compile with: /clr /c  
__declspec(process) __declspec(appdomain) int i;   // C2388  
__declspec(appdomain) int i;   // OK  
```