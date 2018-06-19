---
title: Chyba linkerů Lnk2027 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156310a0d21651b9fd2ee6002ace419db4996681
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301369"
---
# <a name="linker-tools-error-lnk2027"></a>Chyba linkerů LNK2027
modul nerozpoznaný odkaz 'module'  
  
 Soubor předaný linkeru má závislost na modul, který byl zadán ani s **/ASSEMBLYMODULE** ani předaný linkeru.  
  
 Pro vyřešení LNK2027, proveďte jednu z těchto možností:  
  
-   Nepředávejte k linkeru soubor, který má závislost modulu.  
  
-   Zadejte modul s **/ASSEMBLYMODULE**.  
  
-   Pokud modul bezpečné .netmodule, předejte modul přímo do linkeru.  
  
 Další informace najdete v tématu [/ASSEMBLYMODULE (Přidání modulu MSIL do sestavení)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) a [.netmodule soubory jako vstup Linkeru](../../build/reference/netmodule-files-as-linker-input.md).