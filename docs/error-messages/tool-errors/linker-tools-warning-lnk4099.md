---
title: Upozornění linkerů Lnk4099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22764705b35b2e882c5a03e819c9812d084dc118
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300810"
---
# <a name="linker-tools-warning-lnk4099"></a>Upozornění linkerů LNK4099
PDB 'název souboru' nebyla nalezena 'objektu/knihovny' nebo 'path'; propojování objektů, jako kdyby žádné informace o ladění  
  
 Linkeru se nepodařilo najít souboru pdb. Zkopírujte jej do adresáře, který obsahuje `object/library`.  
  
 K vyhledání názvu souboru PDB přidružené k objektu souboru:  
  
1.  Extrahujte soubor objektu z knihovny s [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Zkontrolujte cestu k souboru pdb s **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 Může také kompilovat s [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), takže pdb nemusí použít nebo odebrat [/DEBUG](../../build/reference/debug-generate-debug-info.md) – možnost linkeru Pokud nemají soubory PDB pro objekty, které se připojujete.