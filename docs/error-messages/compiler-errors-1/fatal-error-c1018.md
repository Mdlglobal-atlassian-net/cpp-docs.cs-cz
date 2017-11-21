---
title: "Závažná chyba C1018 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1018
dev_langs: C++
helpviewer_keywords: C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4bab21cfcdbc0336e7485055c989314fa3710e8f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1018"></a>Závažná chyba C1018
neočekávané #elif  
  
 `#elif` – Direktiva se zobrazí mimo `#if`, `#ifdef`, nebo `#ifndef` vytvořit. Použití `#elif` pouze do jedné z těchto konstrukce.  
  
 Následující ukázka generuje C1018:  
  
```  
// C1018.cpp  
#elif      // C1018  
#endif  
  
int main() {}  
```  
  
 Možná řešení:  
  
```  
// C1018b.cpp  
#if 1  
#elif  
#endif  
  
int main() {}  
```