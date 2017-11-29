---
title: "_fflush_nolock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fflush_nolock
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fflush_nolock
- _fflush_nolock
dev_langs: C++
helpviewer_keywords:
- fflush_nolock function
- _fflush_nolock function
- streams, flushing
- flushing
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 779d986e2bca4c2b2d65100603462de1802e6061
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fflushnolock"></a>_fflush_nolock
Vyprázdnění datového proudu bez blokování vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fflush_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 V tématu [fflush –](../../c-runtime-library/reference/fflush.md).  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce je verze bez uzamčení `fflush`. Je stejný jako `fflush` s tím rozdílem, že není chráněn před narušení další vlákna. Může být rychlejší, protože není nesnižuje režii uzamykání jiná vlákna. Tuto funkci můžete používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fflush_nolock`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fclose –, _fcloseall –](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_flushall –](../../c-runtime-library/reference/flushall.md)   
 [setvbuf –](../../c-runtime-library/reference/setvbuf.md)