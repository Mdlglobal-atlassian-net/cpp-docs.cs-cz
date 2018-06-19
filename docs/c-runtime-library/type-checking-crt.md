---
title: Typ kontroly (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types
dev_langs:
- C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 959dd52847e6140667671b9992471155d68e9646
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409342"
---
# <a name="type-checking-crt"></a>Kontrola typu (CRT)
Kompilátor provádí omezené typ kontroly na funkce, které může provádět proměnný počet argumentů, následujícím způsobem:  
  
|Volání funkce|Argumenty typu zaškrtnutí|  
|-------------------|-----------------------------|  
|`_cprintf_s`, `_cscanf_s`, `printf_s`, `scanf_s`|První argument (řetězec formátu)|  
|`fprintf_s`, `fscanf_s`, `sprintf_s`, `sscanf_s`|První dva argumenty (soubor nebo vyrovnávací paměti a formát string)|  
|`_snprintf_s`|První tři argumenty (soubor nebo vyrovnávací paměti, počet a řetězec formátu)|  
|`_open`|První dva argumenty (cesta a `_open` příznak)|  
|`_sopen_s`|První tři argumenty (cesta, `_open` příznak a sdílení režim)|  
|`_execl`, `_execle`, `_execlp`, `_execlpe`|První dva argumenty (cesta a první argument ukazatele)|  
|`_spawnl`, `_spawnle`, `_spawnlp`, `_spawnlpe`|První tři argumenty (příznak režimu, cesta a první argument ukazatele)|  
  
 Kompilátor provádí stejný typ omezené kontrolu na svými protějšky široká charakterová těchto funkcí.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)