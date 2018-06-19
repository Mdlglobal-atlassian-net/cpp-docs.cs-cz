---
title: Závažná chyba kompilátoru prostředků RW1025 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba216e63cb0cae92b4541800493a2fb6195553a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320011"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025
Nedostatek paměti úplně haldy  
  
 Zkontrolujte, zda rezidentní software, který může být zabírají příliš mnoho prostoru. Pomocí programu CHKDSK zjistit, kolik paměti máte.  
  
 Při vytváření souboru velké prostředků, rozdělení na dva soubory skriptu prostředků. Po vytvoření dva soubory .res, použijte příkazový řádek MS-DOS ke spojení je:  
  
```  
copy first.res /b + second.res /b full.res  
```