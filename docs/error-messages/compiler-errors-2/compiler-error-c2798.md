---
title: "C2798 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2798
dev_langs: C++
helpviewer_keywords: C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb0a411651cf7c7f614942563baee5f04075fdf3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2798"></a>C2798 chyby kompilátoru
je nejednoznačný 'super::member.  
  
 Více zděděné struktury obsahovat člen odkazovaná adresou [super](../../cpp/super.md). Buď může opravte chybu:  
  
-   Odebrání B1 nebo B2 ze seznamu dědičnosti D.  
  
-   Změna názvu datového člena v B1 nebo B2.  
  
 Následující ukázka generuje C2798:  
  
```  
// C2798.cpp  
struct B1 {  
   int i;  
};  
  
struct B2 {  
   int i;  
};  
  
struct D : B1, B2 {  
   void g() {  
      __super::i = 4; // C2798  
   }  
};  
```