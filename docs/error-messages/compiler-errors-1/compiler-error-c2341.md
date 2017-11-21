---
title: "C2341 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2341
dev_langs: C++
helpviewer_keywords: C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5460ff70c95fd593539a16140c52fa1490bffc4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2341"></a>C2341 chyby kompilátoru
'název sekce': segment musí být definován pomocí #pragma data_seg, code_seg nebo předchozí část použít  
  
 [Přidělit](../../cpp/allocate.md) příkaz odkazuje na segment ještě definované [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md), nebo [části](../../preprocessor/section.md) direktivy.  
  
 Následující ukázka generuje C2341:  
  
```  
// C2341.cpp  
// compile with: /c  
__declspec(allocate(".test"))   // C2341  
int j = 1;  
```  
  
 Možná řešení:  
  
```  
// C2341b.cpp  
// compile with: /c  
#pragma data_seg(".test")  
__declspec(allocate(".test"))  
int j = 1;  
```