---
title: Typ kontroly (CRT) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.types
dev_langs: C++
helpviewer_keywords:
- checking type
- variable argument functions
- type checking
ms.assetid: 1ba7590b-d1c0-4636-b6a0-e231395abdad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d18ae0818dd839bee0d93bd7194dadcc9abf6627
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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