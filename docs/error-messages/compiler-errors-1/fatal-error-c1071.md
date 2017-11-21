---
title: "Závažná chyba C1071 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1071
dev_langs: C++
helpviewer_keywords: C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: acd48401d3abc17d994e861bf6fb046450d88ca6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1071"></a>Závažná chyba C1071
Neočekávaný konec souboru nalezen v komentář  
  
 Kompilátor bylo dosaženo konce souboru při prohledávání komentář.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Chybí ukončovací komentář (* /).  
  
2.  Chybí znak nového řádku po komentář na posledním řádku zdrojového souboru.  
  
 Následující ukázka generuje C1071:  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```