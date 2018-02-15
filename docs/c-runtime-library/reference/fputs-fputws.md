---
title: "fputs –, fputws – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fputs
- fputws
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
- fputs
- fputws
- _fputts
dev_langs:
- C++
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31c559e49712fa74d5cd457b528266c4eaeaa17a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fputs-fputws"></a>fputs, fputws
Řetězec se zapíše do datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Výstupní řetězec.  
  
 `stream`  
 Ukazatel na `FILE` struktura.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací nezáporné hodnotu, pokud je úspěšné. Při chybě `fputs` a `fputws` vrátit `EOF`. Pokud `str` nebo `stream` je ukazatel s hodnotou null, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a potom `fputs` vrátí `EOF`, a `fputws` vrátí `WEOF`.  
  
 V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí kopie `str` k výstupu `stream` na aktuální pozici. `fputws` zkopíruje argument široká charakterová `str` k `stream` jako vícebajtových znaků řetězec nebo řetězec široká charakterová podle jestli `stream` je otevřen v režimu textových nebo binárních, v uvedeném pořadí. Ani funkcí zkopíruje ukončující znak hodnoty null.  
  
 Dvě funkce chovají stejně jako datový proud se při otevření v režimu ANSI. `fputs` aktuálně nepodporuje výstup do proudu kódování UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fputs`|\<stdio.h>|  
|`fputws`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
```Output  
Hello world from fputs.  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [fgets –, fgetws –](../../c-runtime-library/reference/fgets-fgetws.md)   
 [Získá _getws –](../../c-runtime-library/gets-getws.md)   
 [puts, _putws](../../c-runtime-library/reference/puts-putws.md)