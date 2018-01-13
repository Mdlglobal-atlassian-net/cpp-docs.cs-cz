---
title: "_cprintf –, _cprintf_l –, _cwprintf –, _cwprintf_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cwprintf_l
- _cprintf_l
- _cwprintf
- _cprintf
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
- _cwprintf
- cwprintf
- tcprintf
- _tcprintf
- _cprintf
- cwprintf_l
- tcprintf_l
- _tcprintf_l
- cprintf_l
- _cprintf_l
- _cwprintf_l
dev_langs: C++
helpviewer_keywords:
- _cprintf_l function
- _cwprintf_l function
- cwprintf function
- cprintf_l function
- characters, printing to console
- printing characters to console
- _tcprintf_l function
- tcprintf function
- _tcprintf function
- tcprintf_l function
- _cwprintf function
- cwprintf_l function
- _cprintf function
ms.assetid: 67ffefd4-45b3-4be0-9833-d8d26ac7c4e2
caps.latest.revision: "34"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 984cb8fb3c034d19f4d171f756f2336773187976
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cprintf-cprintfl-cwprintf-cwprintfl"></a>_cprintf, _cprintf_l, _cwprintf, _cwprintf_l
Formáty a tisk do konzoly. Bezpečnější verze jsou k dispozici. v tématu [_cprintf_s –, _cprintf_s_l –, _cwprintf_s –, _cwprintf_s_l –](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _cprintf(   
   const char * format [, argument_list]  
);  
int _cprintf_l(  
   const char * format,  
   locale_t locale [, argument_list]  
);  
int _cwprintf(  
   const wchar * format [, argument_list]  
);  
int _cwprintf_l(  
   const wchar * format,  
   locale_t locale [, argument_list]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Řetězec řízení formátu  
  
 `argument_list`  
 Volitelné parametry pro řetězec formátu.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet znaků, vytisknout.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce formátování a tisk řady znaků a hodnot přímo do konzoly, pomocí `_putch` – funkce (`_putwch` pro `_cwprintf`) výstup znaků. Každý argument v `argument_list` (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v `format`. `format` Používá argument [formátu syntaxe specifikace pro funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). Na rozdíl od `fprintf`, `printf`, a `sprintf` funguje, ani `_cprintf` ani `_cwprintf` překládá posun řádku znaků do kombinace znaků CR vrátit LF (CR-LF) při výstupu.  
  
 Zásadní rozdíl je, že `_cwprintf` zobrazí znaky znakové sady Unicode, když se používá v systému Windows. Na rozdíl od `_cprintf`, `_cwprintf` používá aktuální nastavení národního prostředí konzoly.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí.  
  
 `_cprintf`ověří `format` parametr. Pokud `format` je ukazatel s hodnotou null, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění `errno` k `EINVAL`.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcprintf`|`_cprintf`|`_cprintf`|`_cwprintf`|  
|`_tcprintf_l`|`_cprintf_l`|`_cprintf_l`|`_cwprintf_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_cprintf`,`_cprintf_l`|\<conio.h >|  
|`_cwprintf`, `_cwprintf_l`|\<conio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_cprintf.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
    int         i = -16,  
                h = 29;  
    unsigned    u = 62511;  
    char        c = 'A';  
    char        s[] = "Test";  
  
    // Note that console output does not translate \n as  
    // standard output does. Use \r\n instead.  
    //  
    _cprintf( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
```Output  
-16  001d  62511  A Test  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cscanf –, _cscanf_l –, _cwscanf –, _cwscanf_l –](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vfprintf –, _vfprintf_l –, vfwprintf –, _vfwprintf_l –](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)   
 [_cprintf_s –, _cprintf_s_l –, _cwprintf_s –, _cwprintf_s_l –](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [_cprintf_p –, _cprintf_p_l –, _cwprintf_p –, _cwprintf_p_l –](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)