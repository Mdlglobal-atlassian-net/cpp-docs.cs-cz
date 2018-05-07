---
title: Upozornění linkerů Lnk4001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acf65c00c5c039769a05e009dcfe46ea42633ac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4001"></a>Upozornění linkerů LNK4001
žádné soubory objekt zadané; použít knihovny  
  
 Soubory .lib jeden nebo více, ale ne soubory .obj, byl předán linkeru.  
  
 Protože linkeru není mít přístup k informacím v souboru .lib, která bude mít přístup k souboru .obj, toto upozornění označuje, že budete mít k explicitnímu zadání dalších možností linkeru. Například možná budete muset zadat [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), nebo [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti.