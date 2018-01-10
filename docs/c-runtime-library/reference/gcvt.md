---
title: "_gcvt – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _gcvt
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
f1_keywords: _gcvt
dev_langs: C++
helpviewer_keywords:
- _gcvt function
- _CVTBUFSIZE
- gcvt function
- floating-point functions, converting number to string
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22561495a972c7561f827c4b7f445bb3fa5c256f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="gcvt"></a>_gcvt
Převede hodnotu s plovoucí desetinnou čárkou na řetězec, který je uložený ve vyrovnávací paměti. Bezpečnější verze této funkce je k dispozici. v tématu [_gcvt_s –](../../c-runtime-library/reference/gcvt-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_gcvt(   
   double value,  
   int digits,  
   char *buffer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Hodnota má být převeden.  
  
 `digits`  
 Počet platných číslic, které jsou uložené.  
  
 `buffer`  
 Umístění úložiště pro výsledek.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_gcvt`vrací ukazatel na řetězec číslic.  
  
## <a name="remarks"></a>Poznámky  
 `_gcvt` Funkce převede s plovoucí desetinnou čárkou `value` na řetězec znaků (která zahrnuje desetinné čárky a možné přihlašovací bajtů) a ukládá řetězec v `buffer`. `buffer` By měl být dostatečně velký na to, aby dokázala pojmout převedená hodnota plus ukončující prázdný znak, který se automaticky připojí. Pokud velikost vyrovnávací paměti `digits` + 1 se používá, funkce přepíše konce vyrovnávací paměti. Je to proto, že převedený řetězec obsahuje desetinné čárky a může obsahovat znak a exponentu informace. Neexistuje žádné přidělení pro přetečení. `_gcvt`pokusí se vytvořit `digits` číslic ve formátu desetinného čísla. Pokud ne, vyvolá `digits` číslic v exponenciálním formátu. Koncové nuly může potlačit v převodu.  
  
 A `buffer` délky `_CVTBUFSIZE` je dostatečná pro všechny plovoucí bodu hodnotu.  
  
 Tato funkce ověří jeho parametry. Pokud `buffer` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `NULL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_gcvt`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_gcvt.c  
// compile with: /W3  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   char buffer[_CVTBUFSIZE];  
   double value = -1234567890.123;  
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );  
   _gcvt( value, 12, buffer ); // C4996  
   // Note: _gcvt is deprecated; consider using _gcvt_s instead  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
  
   printf( "\n" );  
   value = -12.34567890123;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
}  
```  
  
```Output  
The following numbers were converted by _gcvt(value,12,buffer):  
buffer: '-1234567890.12' (14 chars)  
buffer: '-12345678901.2' (14 chars)  
buffer: '-123456789012' (13 chars)  
buffer: '-1.23456789012e+012' (19 chars)  
  
buffer: '-12.3456789012' (14 chars)  
buffer: '-1.23456789012' (14 chars)  
buffer: '-0.123456789012' (15 chars)  
buffer: '-1.23456789012e-002' (19 chars)  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [atof –, _atof_l –, _wtof –, _wtof_l –](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt –](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)