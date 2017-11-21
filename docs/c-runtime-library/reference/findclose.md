---
title: "_findclose – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _findclose
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
dev_langs: C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8deae0204a9165ee9ab89036faab3b762c536349
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|`_findclose`|\<IO.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Systémová volání](../../c-runtime-library/system-calls.md)   
 [Název souboru – funkce hledání](../../c-runtime-library/filename-search-functions.md)