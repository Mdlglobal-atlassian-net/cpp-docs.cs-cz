---
title: "C3353 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3353
dev_langs: C++
helpviewer_keywords: C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47a0231a161a2502c26786fceeb1b3634b236eaf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3353"></a>C3353 chyby kompilátoru
'delegovat': delegáta lze vytvořit pouze z globální funkce nebo členské funkce spravované nebo WinRT typu  
  
 Delegáti, deklarovat s [delegovat](../../windows/delegate-cpp-component-extensions.md) – klíčové slovo, lze deklarovat pouze na globální rozsah.  
  
 Následující ukázka generuje C3353:  
  
```  
// C3353.cpp  
// compile with: /clr  
delegate int f;   // C3353  
```