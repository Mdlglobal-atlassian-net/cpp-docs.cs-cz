---
title: PogoSafeMode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- PogoSafeMode
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f40dad6feff9e49deeb495e8acbf2584dea3e41
ms.sourcegitcommit: 5cd2e3e51ecc8d9fc0d889555b4bfa193ba1d6a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2018
---
# <a name="pogosafemode"></a>PogoSafeMode
Určete, zda chcete použít rychlého režimu nebo v nouzovém režimu pro profilace aplikací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PogoSafeMode  
```  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace na základě profilu (PGO) má dva možné režimy profilování fázi: rychlý režimu a v nouzovém režimu. Při vytváření profilu je v rychlého režimu, použije **INC** instrukce ke zvýšení dat čítače. **INC** instrukce je rychlejší, ale není bezpečné pro přístup z více vláken. Při vytváření profilu je v nouzovém režimu, použije **ZÁMKU INC** instrukce ke zvýšení dat čítače. **INC ZÁMKU** instrukce má stejné funkce jako **INC** instrukce a bezpečné pro přístup z více vláken, ale je nižší než **INC** instrukcí.  
  
 Ve výchozím nastavení vytváření profilů PGO funguje v rychlého režimu. `PogoSafeMode` je požadován, pouze pokud budete chtít použít nouzový režim.  
  
 Pokud chcete spustit PGO profilace v nouzovém režimu, je nutné použít proměnné prostředí `PogoSafeMode` nebo přepínač linkeru **- PogoSafeMode**, v závislosti na systému. Pokud provádíte profilace na x64 počítače, je potřeba použít přepínač linkeru. Pokud provádíte profilace na x86 počítače, je nutné zadat proměnné prostředí na jakoukoli hodnotu před zahájením procesu optimalizace.  
  
## <a name="example"></a>Příklad  
  
```  
set PogoSafeMode=1  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)