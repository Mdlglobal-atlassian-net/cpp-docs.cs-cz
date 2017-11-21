---
title: "Chyba linkerů Lnk2027 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2027
dev_langs: C++
helpviewer_keywords: LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b9cefb948ffd09421a6d4a9c1c540ef22f8736fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2027"></a>Chyba linkerů LNK2027
modul nerozpoznaný odkaz 'module'  
  
 Soubor předaný linkeru má závislost na modul, který byl zadán ani s **/ASSEMBLYMODULE** ani předaný linkeru.  
  
 Pro vyřešení LNK2027, proveďte jednu z těchto možností:  
  
-   Nepředávejte k linkeru soubor, který má závislost modulu.  
  
-   Zadejte modul s **/ASSEMBLYMODULE**.  
  
-   Pokud modul bezpečné .netmodule, předejte modul přímo do linkeru.  
  
 Další informace najdete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) a [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).