---
title: "_fprintf_p –, _fprintf_p_l –, _fwprintf_p –, _fwprintf_p_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fwprintf_p
- _fprintf_p_l
- _fwprintf_p_l
- _fprintf_p
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
- _fprintf_p
- _ftprintf_p
- fwprintf_p
- _fwprintf_p
- fprintf_p
- ftprintf_p
dev_langs:
- C++
helpviewer_keywords:
- fprintf_p_l function
- fprintf_p function
- _fprintf_p_l function
- _fprintf_p function
- _ftprintf_p_l function
- streams, printing formatted data to
- _fwprintf_p function
- fwprintf_p function
- _ftprintf_p function
- _fwprintf_p_l function
- ftprintf_p function
- printing [C++], formatted data to streams
- ftprintf_p_l function
- fwprintf_p_l function
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22844c3cc43b0da3c6b2a1fad485abf208aaa329
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fprintfp-fprintfpl-fwprintfp-fwprintfpl"></a>_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l
Tisk formátovaných dat do datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fprintf_p(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_p_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int _fwprintf_p(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_p_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Ukazatel `FILE` struktura.  
  
 `format`  
 Řetězec řízení formátu  
  
 `argument`  
 Volitelné argumenty  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 `_fprintf_p` a `_fwprintf_p` vrátí počet znaků, které jsou zapsány nebo může vracet záporná při výskytu chyby výstupu.  
  
## <a name="remarks"></a>Poznámky  
 `_fprintf_p` Naformátuje a vytiskne řady znaků a hodnot pro výstup `stream`. Jednotlivé funkce `argument` (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v `format`. Pro `_fprintf_p`, `format` argument má stejnou syntaxi a použití, který má v `_printf_p`. Tyto funkce podporují poziční parametry, což znamená, že lze změnit pořadí parametrů používaných řetězec formátu. Další informace o poziční parametry najdete v tématu [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_fwprintf_p` široká charakterová verze `_fprintf_p`; v `_fwprintf_p`, `format` je široká charakterová řetězec. Tyto funkce chovají stejně jako datový proud se při otevření v režimu ANSI. `_fprintf_p` nepodporuje aktuálně výstup do proudu kódování UNICODE.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem.  
  
 Jako verze nezabezpečeného (najdete v části [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)), tyto funkce ověřit jejich parametrů a vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), pokud má jedna `stream` nebo `format` je ukazatel s hodnotou null nebo pokud nejsou žádné formátování specifikátory neznámý nebo chybně vytvořený. Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ftprintf_p`|`_fprintf_p`|`_fprintf_p`|`_fwprintf_p`|  
|`_ftprintf_p_l`|`_fprintf_p_l`|`_fprintf_p_l`|`_fwprintf_p_l`|  
  
 Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fprintf_p`, `_fprintf_p_l`|\<stdio.h>|  
|`_fwprintf_p`, `_fwprintf_p_l`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fprintf_p.c  
// This program uses _fprintf_p to format various  
// data and print it to the file named FPRINTF_P.OUT. It  
// then displays FPRINTF_P.OUT on the screen using the system  
// function to invoke the operating-system TYPE command.  
//   
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
    FILE    *stream = NULL;  
    int     i = 10;  
    double  fp = 1.5;  
    char    s[] = "this is a string";  
    char    c = '\n';  
  
    // Open the file  
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)  
    {  
        // Format and print data  
        _fprintf_p( stream, "%2$s%1$c", c, s );  
        _fprintf_p( stream, "%d\n", i );  
        _fprintf_p( stream, "%f\n", fp );  
  
        // Close the file  
        fclose( stream );  
    }  
  
    // Verify our data  
    system( "type fprintf_p.out" );  
}  
```  
  
```Output  
this is a string  
10  
1.500000  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_cprintf –, _cprintf_l –, _cwprintf –, _cwprintf_l –](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf, _fscanf_l, fwscanf, _fwscanf_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)   
 [_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)   
 [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)