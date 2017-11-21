---
title: "Závažná chyba kompilátoru prostředků RW1025 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW1025
dev_langs: C++
helpviewer_keywords: RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d6e8b8ced110b13b65d91f968e476b5d20cf93c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025
Nedostatek paměti úplně haldy  
  
 Zkontrolujte, zda rezidentní software, který může být zabírají příliš mnoho prostoru. Pomocí programu CHKDSK zjistit, kolik paměti máte.  
  
 Při vytváření souboru velké prostředků, rozdělení na dva soubory skriptu prostředků. Po vytvoření dva soubory .res, použijte příkazový řádek MS-DOS ke spojení je:  
  
```  
copy first.res /b + second.res /b full.res  
```