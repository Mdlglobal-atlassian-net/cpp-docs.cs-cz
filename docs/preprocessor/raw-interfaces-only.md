---
title: raw_interfaces_only – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4643181bf70bc92f4ef5e88b8a9add1ba7bdaad7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849298"
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