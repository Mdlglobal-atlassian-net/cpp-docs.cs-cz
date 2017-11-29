---
title: "btowc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: btowc
dev_langs: C++
helpviewer_keywords: btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71af03a57886b150d6543e3aa11bfb0e05896890
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="btowc"></a>btowc
Určení, zda celé reprezentuje platný znak jednobajtové ve stavu počáteční shift.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wint_t btowc(  
   int c  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Celé číslo pro testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí reprezentaci široká charakterová znaku, pokud na celé číslo představuje platný znak jednobajtové ve stavu počáteční shift. Vrátí weof – Pokud je hodnota EOF na celé číslo nebo není platný znak jednobajtové ve stavu počáteční shift. Výstup této funkce je ovlivňován aktuální `LC_TYPE` národního prostředí.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`btowc`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [mbtowc –, _mbtowc_l –](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)