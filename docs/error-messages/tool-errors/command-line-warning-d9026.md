---
title: Upozornění příkazového řádku D9026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2d99573ee46c51178cc2fe995fa0f526b800f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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