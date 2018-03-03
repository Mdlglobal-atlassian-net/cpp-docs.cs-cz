---
title: "Chyba linkerů Lnk1164 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5c1a62430397f95f33a5a4bd6f5845b1746557d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1164"></a>Chyba linkerů LNK1164
část zarovnání oddílů (number) větší než hodnota /ALIGN  
  
 Velikost zarovnání pro daný oddíl v souboru objektu překračuje hodnotu zadanou pomocí [/ALIGN](../../build/reference/align-section-alignment.md) možnost. **/ALIGN** hodnota musí být násobkem 2 a musí být roven nebo překročí zarovnání oddílů zadaná v souboru objektu.  
  
 Buď pak ji znovu zkompilovat s menší zarovnání oddílů nebo zvyšte **/ALIGN** hodnotu.