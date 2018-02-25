---
title: "raw_native_types – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4908f1f06ef0479121d3ec5ac8fa56a797ed05ca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="rawnativetypes"></a>raw_native_types
**Konkrétní C++**  
  
 Zakáže použití třídy, které podporují COM v funkce vysoké úrovně obálku a místo toho vynutí používání nízké úrovně datových typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_native_types  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, vysoké úrovně metody zpracování chyb použití třídy COM podporu [_bstr_t](../cpp/bstr-t-class.md) a [_variant_t](../cpp/variant-t-class.md) místě `BSTR` a **VARIANT** datové typy a Nezpracovaná ukazatele rozhraní COM. Tyto třídy zapouzdření podrobnosti o přidělování a rušení přidělení paměti úložiště pro tyto datové typy a výrazně zjednodušit operace přetypování a převody typu.  
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)