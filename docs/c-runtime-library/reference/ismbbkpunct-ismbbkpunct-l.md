---
title: "_ismbbkpunct –, _ismbbkpunct_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ismbbkpunct_l
- _ismbbkpunct
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ismbbkpunct_l
- _ismbbkpunct_l
- ismbbkpunct
- _ismbbkpunct
dev_langs:
- C++
helpviewer_keywords:
- _ismbbkpunct_l function
- ismbbkpunct_l function
- ismbbkpunct function
- _ismbbkpunct function
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4bcf41bfa1e06643aebaf77575d98409be694a48
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ismbbkpunct-ismbbkpunctl"></a>_ismbbkpunct, _ismbbkpunct_l
Zkontroluje, jestli vícebajtových znaků interpunkční znaménko.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbbkpunct(  
   unsigned int c   
);  
int _ismbbkpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Celé číslo má být testována.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_ismbbkpunct` vrátí nenulovou hodnotu, pokud na celé číslo `c` je jiné než ASCII interpunkční symbol, nebo 0, pokud není. Například v pouze znaková stránka 932 `_ismbbkpunct` testů pro katakana interpunkce. `_ismbbkpunct` používá aktuální národní prostředí pro všechna nastavení znak závislých na národním prostředí. `_ismbbkpunct_l` se shoduje s tím rozdílem, že používá národní prostředí, je předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbbkpunct`|\<mbctype.h>|  
|`_ismbbkpunct_l`|\<mbctype.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../../c-runtime-library/byte-classification.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)