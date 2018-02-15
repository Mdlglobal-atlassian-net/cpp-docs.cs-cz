---
title: "_vsprintf_p –, _vsprintf_p_l –, _vswprintf_p –, _vswprintf_p_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _vsprintf_p
- _vswprintf_p
- _vsprintf_p_l
- _vswprintf_p_l
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
- vsprintf_p
- _vswprintf_p
- _vstprintf_p
- vswprintf_p
- _vsprintf_p
- vstprintf_p
dev_langs:
- C++
helpviewer_keywords:
- vstprintf_p_l function
- _vsprintf_p_l function
- _vstprintf_p function
- vsprintf_p_l function
- _vswprintf_p function
- vswprintf_p function
- vsprintf_p function
- vswprintf_p_l function
- _vswprintf_p_l function
- vstprintf_p function
- formatted text [C++]
- _vsprintf_p function
- _vstprintf_p_l function
ms.assetid: 00821c0d-9fee-4d8a-836c-0669cfb11317
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25051ad5e6c712328f216ed703e17d3d101b35b8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="vsprintfp-vsprintfpl-vswprintfp-vswprintfpl"></a>_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l
Zápis formátovaného výstupu pomocí ukazatel na seznam argumentů, s možností určit pořadí, ve kterém se používají argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _vsprintf_p(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_p_l(  
   char *buffer,  
   size_t sizeInBytes,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int _vswprintf_p(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_p_l(  
   wchar_t *buffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro výstup.  
  
 `sizeInBytes`  
 Velikost `buffer` ve znacích.  
  
 `count`  
 Maximální počet znaků k uložení v kódu UNICODE verze této funkce.  
  
 `format`  
 Specifikace formátu.  
  
 `argptr`  
 Ukazatel na seznam argumentů.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 `_vsprintf_p` a `_vswprintf_p` vrátí počet znaků zapsána, pokud dojde k chybě výstup není včetně ukončující znak hodnoty null nebo záporná hodnota.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí má ukazatel na seznam argumentů a naformátuje a zapíše daná data do paměti, na kterou odkazuje `buffer`.  
  
 Tyto funkce se liší od `vsprintf_s` a `vswprintf_s` pouze v tomto podporují poziční parametry. Další informace najdete v tématu [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.  
  
 Pokud `buffer` nebo `format` parametry jsou ukazatele na hodnotu NULL, pokud je počet nula nebo pokud řetězec formátu obsahuje neplatné znaky formátování, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vstprintf_p`|`_vsprintf_p`|`_vsprintf_p`|`_vswprintf_p`|  
|`_vstprintf_p_l`|`_vsprintf_p_l`|`_vsprintf_p_l`|`_vswprintf_p_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`_vsprintf_p`, `_vsprintf_p_l`|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|  
|`_vswprintf_p`, `_vswprintf_p_l`|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|  
  
 \* Vyžaduje se pro kompatibility V systému UNIX.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt__vsprintf_p.c  
// This program uses vsprintf_p to write to a buffer.  
// The size of the buffer is determined by _vscprintf_p.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <stdarg.h>  
  
void example( char * format, ... )  
{  
    va_list  args;  
    int      len;  
    char     *buffer = NULL;  
  
    va_start( args, format );  
  
    // _vscprintf doesn't count the   
    // null terminating string so we add 1.  
    len = _vscprintf_p( format, args ) + 1;  
  
    // Allocate memory for our buffer  
    buffer = (char*)malloc( len * sizeof(char) );  
    if (buffer)  
    {  
        _vsprintf_p( buffer, len, format, args );  
        puts( buffer );  
        free( buffer );  
    }  
    va_end( args );
}  
  
int main( void )  
{  
    // First example  
    example( "%2$d %1$c %3$d", '<', 123, 456 );  
  
    // Second example  
    example( "%s", "This is a string" );  
}  
```  
  
```Output  
123 < 456  
This is a string  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [vprintf – funkce](../../c-runtime-library/vprintf-functions.md)   
 [Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)