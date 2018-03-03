---
title: "Závažná chyba kompilátoru prostředků RW1025 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 487968f8a1242dd4c36e4bbd9b4ede08a5ab4d95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025
Nedostatek paměti úplně haldy  
  
 Zkontrolujte, zda rezidentní software, který může být zabírají příliš mnoho prostoru. Pomocí programu CHKDSK zjistit, kolik paměti máte.  
  
 Při vytváření souboru velké prostředků, rozdělení na dva soubory skriptu prostředků. Po vytvoření dva soubory .res, použijte příkazový řádek MS-DOS ke spojení je:  
  
```  
copy first.res /b + second.res /b full.res  
```