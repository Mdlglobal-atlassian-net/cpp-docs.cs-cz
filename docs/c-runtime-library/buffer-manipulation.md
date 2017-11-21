---
title: "Zacházení s vyrovnávací paměť | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.memory
dev_langs: C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c74c3b9f98f40b87224ae1c12da06ec55207567
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="buffer-manipulation"></a>Zacházení s vyrovnávací pamětí
Použijte tyto rutiny pro práci s oblasti paměti na základě bajtů bajtů.  
  
### <a name="buffer-manipulation-routines"></a>Zacházení s vyrovnávací pamětí rutiny  
  
|Rutina|Použití|  
|-------------|---------|  
|[_memccpy –](../c-runtime-library/reference/memccpy.md)|Kopírování znaků z jedné vyrovnávací paměti do jiného dokud zadaný znak nebo zadaný počet znaků byl zkopírován|  
|[memchr, wmemchr –](../c-runtime-library/reference/memchr-wmemchr.md)|Vrátí ukazatel na první výskyt, v rámci zadaný počet znaků, z zadaný znak ve vyrovnávací paměti|  
|[memcmp wmemcmp –](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porovnání zadaný počet znaků z dvě vyrovnávací paměti|  
|[memcpy wmemcpy –](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s –, wmemcpy_s –](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Kopírovat zadaný počet znaků z jedné vyrovnávací paměti do jiného|  
|[_memicmp –, _memicmp_l –](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porovnání zadaný počet znaků z dvě vyrovnávací paměti bez ohledu na případ|  
|[memmove –, wmemmove –](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s –, wmemmove_s –](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Kopírovat zadaný počet znaků z jedné vyrovnávací paměti do jiného|  
|[memset –, wmemset –](../c-runtime-library/reference/memset-wmemset.md)|Použití zadaný znak k chybě při inicializaci zadaný počet bajtů ve vyrovnávací paměti|  
|[_swab –](../c-runtime-library/reference/swab.md)|Prohození bajtů dat a uložit je do zadaného umístění.|  
  
 Pokud zdrojové a cílové oblasti překrývají, pouze `memmove` záruku, že se správně zkopírovat úplný zdrojový.  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)