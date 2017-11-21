---
title: "_rmtmp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _rmtmp
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
- rmtmp
- _rmtmp
dev_langs: C++
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 79103471b09815b2ca4a99c2e9c22ed5af512ef4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rmtmp"></a>_rmtmp
Odebere dočasné soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int _rmtmp( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `_rmtmp`Vrátí počet dočasné soubory, které se zavře a odstranit.  
  
## <a name="remarks"></a>Poznámky  
 `_rmtmp` Funkce vyčistí všechny dočasné soubory v aktuálním adresáři. Funkce odebere pouze ty soubory, které jsou vytvořené `tmpfile`; použít pouze ve stejném adresáři, ve kterém byly vytvořeny dočasné soubory.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_rmtmp`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [tmpfile –](../../c-runtime-library/reference/tmpfile.md).  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_flushall –](../../c-runtime-library/reference/flushall.md)   
 [tmpfile –](../../c-runtime-library/reference/tmpfile.md)   
 [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)