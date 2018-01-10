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
ms.workload: cplusplus
ms.openlocfilehash: 410e52dd9ee9605f6e29b81491bda0f4883e1cf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty
Odvozené závislé je odvozený od odvozené pravidlo a je vyhodnocena před explicitní závislosti. Pokud odvozené závislé zastaralé s ohledem na cíli, NMAKE vyvolá příkazy bloku pro závislost. Pokud odvozené závislé neexistuje nebo je zastaralé s ohledem na svůj vlastní závislosti, aktualizuje NMAKE nejprve odvozené závislé položky. Další informace o odvozené závislé objekty najdete v tématu [odvozená pravidla](../build/inference-rules.md).  
  
## <a name="see-also"></a>Viz také  
 [Závislé prvky](../build/dependents.md)