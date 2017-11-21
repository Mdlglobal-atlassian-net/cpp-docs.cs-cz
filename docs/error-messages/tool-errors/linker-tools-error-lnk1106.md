---
title: "Chyba linkerů Lnk1106 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1106
dev_langs: C++
helpviewer_keywords: LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b97196ebed51c21e40fa74ab1b80d23f3c49eec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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