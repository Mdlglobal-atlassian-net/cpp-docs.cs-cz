---
title: "Kompilátoru (úroveň 1) upozornění C4659 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4659
dev_langs: C++
helpviewer_keywords: C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: abaef666a5553969ab1290118b8668c50c2bba3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4659"></a>C4659 kompilátoru upozornění (úroveň 1)
\#Direktiva pragma '– Direktiva pragma': použití vyhrazené segment 'segmentu, má undefined chování, použijte komentář #pragma (linker,...)  
  
 Možnost .drectve byl použit k předání možností linkeru. Místo toho použijte – Direktiva pragma [komentář](../../preprocessor/comment-c-cpp.md) pro předávání – možnost linkeru.  
  
```  
// C4659.cpp  
// compile with: /W1 /LD  
#pragma code_seg(".drectve")   // C4659  
```