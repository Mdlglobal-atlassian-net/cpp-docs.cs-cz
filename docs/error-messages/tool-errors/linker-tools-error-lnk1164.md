---
title: "Chyba linkerů Lnk1164 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1164
dev_langs: C++
helpviewer_keywords: LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b8d1e324821d8e4b91bc0f7b404e653a54f03ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1164"></a>Chyba linkerů LNK1164
část zarovnání oddílů (number) větší než hodnota /ALIGN  
  
 Velikost zarovnání pro daný oddíl v souboru objektu překračuje hodnotu zadanou pomocí [/ALIGN](../../build/reference/align-section-alignment.md) možnost. **/ALIGN** hodnota musí být násobkem 2 a musí být roven nebo překročí zarovnání oddílů zadaná v souboru objektu.  
  
 Buď pak ji znovu zkompilovat s menší zarovnání oddílů nebo zvyšte **/ALIGN** hodnotu.