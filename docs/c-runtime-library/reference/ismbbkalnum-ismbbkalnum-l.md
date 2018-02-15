---
title: "_ismbbkalnum –, _ismbbkalnum_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ismbbkalnum
- _ismbbkalnum_l
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
- _ismbbkalnum
- ismbbkalnum
- ismbbkalnum_l
- _ismbbkalnum_l
dev_langs:
- C++
helpviewer_keywords:
- _ismbbkalnum_l function
- ismbbkalnum_l function
- _ismbbkalnum function
- ismbbkalnum function
ms.assetid: e1d70e7b-29d0-469c-9d93-442b99de22ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de4a09460e5c9da6aef8a9b9564c3f193bfba719
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ismbbkalnum-ismbbkalnuml"></a>_ismbbkalnum, _ismbbkalnum_l
Určuje, zda je konkrétní vícebajtových znaků symbol jiné sady než ASCII text.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbbkalnum(  
   unsigned int c   
);  
int _ismbbkalnum_l(  
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
 `_ismbbkalnum` vrátí nenulovou hodnotu, pokud na celé číslo `c` je jiné než ASCII text symbol než interpunkční znaménka, nebo 0, pokud není. `_ismbbkalnum` používá aktuální národní prostředí informace znak závislých na národním prostředí. `_ismbbkalnum_l` je stejný jako `_ismbbkalnum` s tím rozdílem, že trvá národní prostředí jako parametr. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbbkalnum`|\<mbctype.h>|  
|`_ismbbkalnum_l`|\<mbctype.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../../c-runtime-library/byte-classification.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)