---
title: "C2344 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2344
dev_langs: C++
helpviewer_keywords: C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25a058240a72dd9b3ebafd9bafbc8b930bd2cefd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2344"></a>C2344 chyby kompilátoru
align(#): zarovnání musí být násobek dvou  
  
 Při použití [zarovnat](../../cpp/align-cpp.md) – klíčové slovo, předáte hodnotu musí být násobek dvou.  
  
 Následující kód například vygeneruje C2344, protože 3 není násobek dvou:  
  
```  
// C2344.cpp  
// compile with: /c  
__declspec(align(3)) int a;   // C2344  
__declspec(align(4)) int b;   // OK  
```