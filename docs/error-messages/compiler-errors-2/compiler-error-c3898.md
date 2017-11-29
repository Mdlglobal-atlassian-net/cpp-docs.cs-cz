---
title: "C3898 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3898
dev_langs: C++
helpviewer_keywords: C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c5ff2b3079de90efbf370082be4fee03dbfaab3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3898"></a>C3898 chyby kompilátoru
'příkaz var': členy typu dat lze pouze členy spravované typy  
  
 [Initonly](../../dotnet/initonly-cpp-cli.md) – datový člen byla deklarována v nativních tříd.  `initonly` – Datový člen lze deklarovat pouze ve třídě CLR.  
  
 Následující ukázka generuje C3898:  
  
```  
// C3898.cpp  
// compile with: /clr  
struct Y1 {  
   initonly  
   static int data_var = 9;   // C3898  
};  
```  
  
 Možná řešení:  
  
```  
// C3898b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int data_var = 9;  
};  
```