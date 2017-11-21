---
title: "Odvozené závislé objekty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eaf75c067b2e96e5ae4a893b56376bfc1b9bd1e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty
Odvozené závislé je odvozený od odvozené pravidlo a je vyhodnocena před explicitní závislosti. Pokud odvozené závislé zastaralé s ohledem na cíli, NMAKE vyvolá příkazy bloku pro závislost. Pokud odvozené závislé neexistuje nebo je zastaralé s ohledem na svůj vlastní závislosti, aktualizuje NMAKE nejprve odvozené závislé položky. Další informace o odvozené závislé objekty najdete v tématu [odvozená pravidla](../build/inference-rules.md).  
  
## <a name="see-also"></a>Viz také  
 [Závislé objekty](../build/dependents.md)