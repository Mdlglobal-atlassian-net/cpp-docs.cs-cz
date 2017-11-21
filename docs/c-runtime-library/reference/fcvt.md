---
title: "_fcvt – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fcvt
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
f1_keywords: _fcvt
dev_langs: C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 495460722a72f6002b602336d3a01bff4b9d3af6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fcvt"></a>_fcvt
Převede dvě desetinná čísla na řetězec. Bezpečnější verze této funkce je k dispozici. v tématu [_fcvt_s –](../../c-runtime-library/reference/fcvt-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_fcvt(   
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
 Počet číslic za desetinnou čárkou.  
  
 `dec`  
 Ukazatel na uložené pozici desetinné čárky.  
  
 `sign`  
 Ukazatel na uložené přihlašovací indikátoru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_fcvt`vrací ukazatel na řetězec číslic, NULL v případě chyby.  
  
## <a name="remarks"></a>Poznámky  
 `_fcvt` Funkce převede dvě desetinná čísla na řetězec znaků ukončený hodnotou null. `value` Parametr je číslo s plovoucí desetinnou čárkou má být převeden. `_fcvt`ukládá číslice z `value` jako řetězec a připojí znak hodnoty null ('\0'). `count` Parametr určuje počet číslic ukládaly za desetinnou čárkou. Jsou nadbytečné číslic zaokrouhlen `count` umístí. Pokud máte méně než `count` platných číslic, řetězec je doplněno nulami.  
  
 Celkový počet číslic vrácený `_fcvt` nesmí překročit `_CVTBUFSIZE`.  
  
 Pouze číslice jsou uloženy v řetězci. Pozice desetinné čárky a znaménko `value` lze získat z `dec` a přihlásit po volání. `dec` Parametr odkazuje na celočíselnou hodnotu; uvádí tato hodnota celé číslo pozice od desetinné čárky s ohledem na začátku řetězce. Nula nebo záporná celočíselná hodnota označuje, zda desetinné čárky je nalevo od první číslice. Parametr `sign` odkazuje na celé číslo udávající znaménko `value`. Celé číslo nastavena na 0, pokud `value` kladné a je nastavená na nenulové číslo Pokud `value` záporné.  
  
 Rozdíl mezi `_ecvt` a `_fcvt` je při interpretaci `count` parametr. `_ecvt`interpretuje `count` jako celkový počet číslic do výstupního řetězce, zatímco `_fcvt` interpretuje `count` jako počet číslic za desetinnou čárkou.  
  
 `_ecvt`a `_fcvt` ke konverzi použijte jeden staticky přidělené vyrovnávací paměti. Každé volání na jednu z těchto rutin zničí výsledky z předchozího volání.  
  
 Tato funkce ověří jeho parametry. Pokud `dec` nebo `sign` má hodnotu NULL, nebo `count` je 0, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a vrátí se hodnota NULL.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fcvt`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [atof –, _atof_l –, _wtof –, _wtof_l –](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt –](../../c-runtime-library/reference/ecvt.md)   
 [_gcvt –](../../c-runtime-library/reference/gcvt.md)