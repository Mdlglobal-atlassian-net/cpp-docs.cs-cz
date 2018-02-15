---
title: "_findclose – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _findclose
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _findclose
- findclose
dev_langs:
- C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1f79ea7e5c39c4de7ba25699729864688ababf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="findclose"></a>_findclose
Zavře popisovač zadaný hledaný a související prostředky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _findclose(   
   intptr_t handle   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handle`  
 Popisovač hledání vrácené z předchozího volání `_findfirst`.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `_findclose` vrátí hodnotu 0. Jinak vrátí hodnotu -1 a nastaví `errno` k `ENOENT`, která udává, že žádné další odpovídající soubory nebyla nalezena.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_findclose`|\<io.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Systémová volání](../../c-runtime-library/system-calls.md)   
 [Funkce hledání názvů souborů](../../c-runtime-library/filename-search-functions.md)