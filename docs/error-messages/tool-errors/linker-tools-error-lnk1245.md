---
title: Chyba linkerů Lnk1245 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47a1c2e5f7bf66946dcc5816d7a20fd485b59b45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1245"></a>Chyba linkerů LNK1245
Neplatný subsystému subsystému zadaný; / SUBSYSTEM musí být WINDOWS, WINDOWSCE nebo KONZOLY  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) byl použit ke kompilaci objektu a byl true jeden z následujících podmínek:  
  
-   Byl definován vlastní vstupního bodu ([/Entry](../../build/reference/entry-entry-point-symbol.md)), tak, aby linkeru nepodařilo odvodit podsystému.  
  
-   Byla předána hodnota [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) propojovacího, který není platný pro objekty/CLR.  
  
 V obou situacích je řešení zadejte platnou hodnotu pro možnost /SUBSYSTEM linkeru.