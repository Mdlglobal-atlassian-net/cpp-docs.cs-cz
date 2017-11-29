---
title: "_ecvt – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _ecvt
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
f1_keywords: _ecvt
dev_langs: C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 09fa0329da2e2c143c219291c3b8c2018f84e445
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ecvt"></a>_ecvt
Převede `double` čísel na řetězec. Bezpečnější verze této funkce je k dispozici. v tématu [_ecvt_s –](../../c-runtime-library/reference/ecvt-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_ecvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Číslo, které má být převeden.  
  
 `count`  
 Počet číslic, které jsou uložené.  
  
 `dec`  
 Uložené pozice desetinné čárky.  
  
 `sign`  
 Znak převedený číslo.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_ecvt`vrací ukazatel na řetězec číslic; Hodnota NULL, pokud došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `_ecvt` Funkce převede na řetězec znaků číslo s plovoucí desetinnou čárkou. `value` Parametr je číslo s plovoucí desetinnou čárkou má být převeden. Tato funkce ukládá až `count` číslice `value` jako řetězec a připojí znak hodnoty null ('\0'). Pokud počet číslic v `value` překračuje `count`, se zaokrouhlí na nejnižší číslici. Pokud máte méně než `count` číslic, řetězec je doplněno nulami.  
  
 Celkový počet číslic vrácený `_ecvt` nesmí překročit `_CVTBUFSIZE`.  
  
 Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko `value` lze získat z `dec` a `sign` po volání. `dec` Parametr odkazuje na celočíselnou hodnotu poskytnutí pozici od desetinné čárky s ohledem na začátku řetězce. Hodnota 0 nebo záporné celé číslo označuje, zda desetinné čárky je nalevo od první číslice. `sign` Parametr odkazuje na celé číslo, které označuje znak převedený číslo. Pokud je hodnota celé číslo 0, je kladné číslo. Jinak je číslo záporné.  
  
 Rozdíl mezi `_ecvt` a `_fcvt` je při interpretaci `count` parametr. `_ecvt`interpretuje `count` jako celkový počet číslic do výstupního řetězce, zatímco `_fcvt` interpretuje `count` jako počet číslic za desetinnou čárkou.  
  
 `_ecvt`a `_fcvt` ke konverzi použijte jeden staticky přidělené vyrovnávací paměti. Každé volání na jednu z těchto rutin zničí výsledek předchozí volání.  
  
 Tato funkce ověří jeho parametry. Pokud `dec` nebo `sign` má hodnotu NULL, nebo `count` je 0, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a vrátí se hodnota NULL.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_ecvt`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [atof –, _atof_l –, _wtof –, _wtof_l –](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_fcvt –](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt –](../../c-runtime-library/reference/gcvt.md)