---
title: Chyba linkerů Lnk1106 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3dedaa2bd500b11f06f9cfa98802fdd6ca84534
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1106"></a>Chyba linkerů LNK1106
Neplatný soubor nebo disk plný: Nelze nastavit na umístění  
  
 Nástroj nelze číst nebo zapisovat na `location` v souboru mapované paměti.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Disk je plný.  
  
     Uvolněte místo na disku a znovu připojit.  
  
2.  Chcete propojit přes síť.  
  
     Některé sítě plně nepodporují soubory mapované paměti používané linkeru. Zkuste propojení na váš místní disk.  
  
3.  Chybný bloku na disku.  
  
     I když operační systém a hardware disku by měl mít takové došlo k chybě, můžete spustit program kontrolu disku.  
  
4.  Nedostatek místa na haldy.  
  
     V tématu [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Další informace.