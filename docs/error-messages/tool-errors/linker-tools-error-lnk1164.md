---
title: Chyba linkerů Lnk1164 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f85ad1c223c9d4b22e3763f1d24a6c2631f6342d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1164"></a>Chyba linkerů LNK1164
část zarovnání oddílů (number) větší než hodnota /ALIGN  
  
 Velikost zarovnání pro daný oddíl v souboru objektu překračuje hodnotu zadanou pomocí [/ALIGN](../../build/reference/align-section-alignment.md) možnost. **/ALIGN** hodnota musí být násobkem 2 a musí být roven nebo překročí zarovnání oddílů zadaná v souboru objektu.  
  
 Buď pak ji znovu zkompilovat s menší zarovnání oddílů nebo zvyšte **/ALIGN** hodnotu.