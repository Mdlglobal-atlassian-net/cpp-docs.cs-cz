---
title: "Upozornění linkerů Lnk4099 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4099
dev_langs: C++
helpviewer_keywords: LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c9407ba96c899c6b88585f6c3894fea8f12947d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4099"></a>Upozornění linkerů LNK4099
PDB 'název souboru' nebyla nalezena 'objektu/knihovny' nebo 'path'; propojování objektů, jako kdyby žádné informace o ladění  
  
 Linkeru se nepodařilo najít souboru pdb. Zkopírujte jej do adresáře, který obsahuje `object/library`.  
  
 K vyhledání názvu souboru PDB přidružené k objektu souboru:  
  
1.  Extrahujte soubor objektu z knihovny s [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Zkontrolujte cestu k souboru pdb s **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 Může také kompilovat s [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), takže pdb nemusí použít nebo odebrat [/DEBUG](../../build/reference/debug-generate-debug-info.md) – možnost linkeru Pokud nemají soubory PDB pro objekty, které se připojujete.