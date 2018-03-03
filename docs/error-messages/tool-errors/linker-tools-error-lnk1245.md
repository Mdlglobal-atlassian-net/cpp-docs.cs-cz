---
title: "Chyba linkerů Lnk1245 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 142d88489748f30308395d64f3db78178a9b856f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1245"></a>Chyba linkerů LNK1245
Neplatný subsystému subsystému zadaný; / SUBSYSTEM musí být WINDOWS, WINDOWSCE nebo KONZOLY  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) byl použit ke kompilaci objektu a byl true jeden z následujících podmínek:  
  
-   Byl definován vlastní vstupního bodu ([/Entry](../../build/reference/entry-entry-point-symbol.md)), tak, aby linkeru nepodařilo odvodit podsystému.  
  
-   Byla předána hodnota [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) propojovacího, který není platný pro objekty/CLR.  
  
 V obou situacích je řešení zadejte platnou hodnotu pro možnost /SUBSYSTEM linkeru.