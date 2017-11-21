---
title: "Upozornění linkerů Lnk4001 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4001
dev_langs: C++
helpviewer_keywords: LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfb73e0c62a49fe5190103987277483d29af71fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4001"></a>Upozornění linkerů LNK4001
žádné soubory objekt zadané; použít knihovny  
  
 Soubory .lib jeden nebo více, ale ne soubory .obj, byl předán linkeru.  
  
 Protože linkeru není mít přístup k informacím v souboru .lib, která bude mít přístup k souboru .obj, toto upozornění označuje, že budete mít k explicitnímu zadání dalších možností linkeru. Například možná budete muset zadat [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), nebo [/Entry](../../build/reference/entry-entry-point-symbol.md) možnosti.