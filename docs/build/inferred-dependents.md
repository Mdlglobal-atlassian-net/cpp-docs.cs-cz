---
title: Odvozené závislé objekty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86ed1a8fe6c97ae11af50f59cb639ef6fd7c1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367895"
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty
Odvozené závislé je odvozený od odvozené pravidlo a je vyhodnocena před explicitní závislosti. Pokud odvozené závislé zastaralé s ohledem na cíli, NMAKE vyvolá příkazy bloku pro závislost. Pokud odvozené závislé neexistuje nebo je zastaralé s ohledem na svůj vlastní závislosti, aktualizuje NMAKE nejprve odvozené závislé položky. Další informace o odvozené závislé objekty najdete v tématu [odvozená pravidla](../build/inference-rules.md).  
  
## <a name="see-also"></a>Viz také  
 [Závislé prvky](../build/dependents.md)