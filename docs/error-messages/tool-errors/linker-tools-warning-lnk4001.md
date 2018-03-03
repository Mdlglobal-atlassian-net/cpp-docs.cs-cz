---
title: "Upozornění linkerů Lnk4001 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ecc78fe50fd34a0c6f583bf103d368e23f19f2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4001"></a>Upozornění linkerů LNK4001
žádné soubory objekt zadané; použít knihovny  
  
 Soubory .lib jeden nebo více, ale ne soubory .obj, byl předán linkeru.  
  
 Protože linkeru není mít přístup k informacím v souboru .lib, která bude mít přístup k souboru .obj, toto upozornění označuje, že budete mít k explicitnímu zadání dalších možností linkeru. Například možná budete muset zadat [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), nebo [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti.