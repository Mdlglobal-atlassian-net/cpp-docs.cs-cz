---
title: "raw_interfaces_only – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eff60ded57ae66b43dee4b3b95699ad498fa0358
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Konkrétní C++**  
  
 Potlačí generování funkce obálky zpracování chyb a [vlastnost](../cpp/property-cpp.md) deklarace, které používají tyto funkce obálku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>Poznámky  
 `raw_interfaces_only` Atribut také způsobuje výchozí předponu v názvu funkce bez vlastnost odeberou. Za normálních okolností je předpona **raw_**. Pokud tento atribut je zadán, jsou názvy funkcí přímo z knihovny typů.  
  
 Tento atribut umožňuje vystavit pouze nízké úrovně obsah knihovny typů.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)