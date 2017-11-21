---
title: "C2790 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2790
dev_langs: C++
helpviewer_keywords: C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 11ea7285d20808f16f2588d50caebe99429c8da0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2790"></a>C2790 chyby kompilátoru
'super: Toto klíčové slovo lze použít pouze v hlavní funkce člena třídy  
  
 Tato chybová zpráva se zobrazí, pokud uživatel někdy pokusí používá klíčové slovo [super](../../cpp/super.md) mimo kontext členské funkce.  
  
 Následující ukázka generuje C2790:  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```