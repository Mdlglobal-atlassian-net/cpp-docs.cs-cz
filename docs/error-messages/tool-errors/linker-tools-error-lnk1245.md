---
title: "Chyba linkerů Lnk1245 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1245
dev_langs: C++
helpviewer_keywords: LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e937962fc71b0767dce94614f0505c2d30e915bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1245"></a>Chyba linkerů LNK1245
Neplatný subsystému subsystému zadaný; / SUBSYSTEM musí být WINDOWS, WINDOWSCE nebo KONZOLY  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) byl použit ke kompilaci objektu a byl true jeden z následujících podmínek:  
  
-   Byl definován vlastní vstupního bodu ([/Entry](../../build/reference/entry-entry-point-symbol.md)), tak, aby linkeru nepodařilo odvodit podsystému.  
  
-   Byla předána hodnota [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) propojovacího, který není platný pro objekty/CLR.  
  
 V obou situacích je řešení zadejte platnou hodnotu pro možnost /SUBSYSTEM linkeru.