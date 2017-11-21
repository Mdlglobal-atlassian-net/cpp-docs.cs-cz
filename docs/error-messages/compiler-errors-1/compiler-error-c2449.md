---
title: "C2449 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2449
dev_langs: C++
helpviewer_keywords: C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3a32347d4c03f191e2984e99b5098c2fe80bd08d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2449"></a>C2449 chyby kompilátoru
najít ' {' v souboru oboru (chybí záhlaví funkce?)  
  
 Otevřete levá složená závorka nastane v rozsahu souboru.  
  
 Tato chyba může být způsobeno středníkem mezi hlavičku funkce a závorka v definici funkce.  
  
 Následující ukázka generuje C2499:  
  
```  
// C2449.c  
// compile with: /c  
void __stdcall func(void) {}   // OK  
void __stdcall func(void);  // extra semicolon on this line  
{                         // C2449 detected here  
```