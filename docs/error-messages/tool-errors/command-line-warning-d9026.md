---
title: "Upozornění příkazového řádku D9026 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9127ad1887d476e5460798f806c2db1ff3144de3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9026"></a>Upozornění příkazového řádku D9026
možnosti se vztahují na celou příkazového řádku  
  
 Možnost byl v příkaz zadaný po byl zadán název souboru. Možnost byla použita k souboru, který je před.  
  
 Například v příkazu  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 pomocí možnosti /G5 není výchozí /G4 se zkompiluje soubor VERDI.c.  
  
 Toto chování se liší od některých předchozích verzí, které se použijí jen možností před název souboru, což vede k VERDI.c kompilován pomocí/G4 a PUCCINI.c kompilován pomocí /G5.