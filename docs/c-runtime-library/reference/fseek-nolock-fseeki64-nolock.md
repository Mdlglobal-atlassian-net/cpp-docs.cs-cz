---
title: "_fseek_nolock –, _fseeki64_nolock – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fseek_nolock
- _fseeki64_nolock
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
apitype: DLLExport
f1_keywords:
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
dev_langs: C++
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2f29ce9e4e08ed75ba06e0cb27db0ddac1d923e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fseeknolock-fseeki64nolock"></a>_fseek_nolock, _fseeki64_nolock
Přesune ukazatele souboru do zadaného umístění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fseek_nolock(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64_nolock(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel `FILE` struktura.  
  
 `offset`  
 Počet bajtů z`origin.`  
  
 `origin`  
 Počáteční pozice.  
  
## <a name="return-value"></a>Návratová hodnota  
 Stejné jako [fseek, _fseeki64 –](../../c-runtime-library/reference/fseek-fseeki64.md) v uvedeném pořadí.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce jsou verze bez uzamčení `fseek` a `_fseeki64`, v uvedeném pořadí. Tyto jsou stejné jako `fseek` a `_fseeki64` s tím rozdílem, že nejsou chráněny z narušení jiná vlákna. Tato funkce může být rychlejší, protože nevznikají nároky na uzamčení jiná vlákna. Tyto funkce lze používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fseek`|\<stdio.h >|  
|`_fseeki64`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [ftell –, _ftelli64 –](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek –, _lseeki64 –](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [REWIND](../../c-runtime-library/reference/rewind.md)