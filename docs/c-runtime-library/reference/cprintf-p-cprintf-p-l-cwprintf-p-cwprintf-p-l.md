---
title: "_cprintf_p –, _cprintf_p_l –, _cwprintf_p –, _cwprintf_p_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cprintf_p_l
- _cwprintf_p_l
- _cwprintf_p
- _cprintf_p
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
- cprintf_p
- cwprintf_p
- tcprintf_p
- _cwprintf_p_l
- _cprintf_p
- csprintf_p_l
- _cprintf_p_l
- _cwprintf_p
- _tcprintf_p
- cprintf_p_l
dev_langs: C++
helpviewer_keywords:
- _cwprintf_p_l function
- cwprintf_p function
- tcprintf_p_l function
- cprintf_p_l function
- _tcprintf_p function
- _tcprintf_p_l function
- _cprintf_p function
- _cprintf_p_l function
- cwprintf_p_l function
- _cwprintf_p function
- tcprintf_p function
- cprintf_p function
ms.assetid: 1f82fd7d-13c8-4c4a-a3e4-db0df3873564
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5e0e5bdfbb4a42b0911e253c3d5fd9aa4f84fa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cprintfp-cprintfpl-cwprintfp-cwprintfpl"></a>_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l
Naformátuje a vytiskne ke konzole a podporuje poziční parametry ve formátovacím řetězci.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _cprintf_p(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_p_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_p(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_p_l(  
   const wchar * format,  
   locale_t locale [,  
   argument] ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Řetězec řízení formátu  
  
 `argument`  
 Volitelné parametry.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet znaků, vytisknout nebo záporná, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce formátování a tisk řady znaků a hodnot přímo do konzoly, pomocí `_putch` a `_putwch` funkce výstup znaků. Každý `argument` (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v `format`. Formát má stejné tvoří a fungovat jako `format` parametr pro [printf_p –](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) funkce. Rozdíl mezi `_cprintf_p` a `cprintf_s` je, že `_cprintf_p` podporuje poziční parametry, které umožní určení pořadí, ve kterém jsou argumenty použít v řetězec formátu. Další informace najdete v tématu [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Na rozdíl od `fprintf_p`, `printf_p`, a `sprintf_p` funguje, ani `_cprintf_p` ani `_cwprintf_p` překládá posun řádku znaků do kombinace znaků CR vrátit LF (CR-LF) při výstupu. Zásadní rozdíl je, že `_cwprintf_p` zobrazí znaky znakové sady Unicode, když se používá v systému Windows NT. Na rozdíl od `_cprintf_p`, `_cwprintf_p` používá aktuální nastavení národního prostředí konzoly.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem.  
  
 Také jako `_cprintf_s` a `_cwprintf_s`, jejich ověření vstupu ukazatele a řetězec formátu. Pokud `format` nebo `argument` jsou `NULL`, nebo formátu řetězec obsahuje neplatné znaky formátování, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcprintf_p`|`_cprintf_p`|`_cprintf_p`|`_cwprintf_p`|  
|`_tcprintf_p_l`|`_cprintf_p_l`|`_cprintf_p_l`|`_cwprintf_p_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_cprintf_p`,`_cprintf_p_l`|\<conio.h >|  
|`_cwprintf_p`,`_cwprintf_p_l`|\<conio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_cprintf_p.c  
// This program displays some variables to the console  
// using the _cprintf_p function.  
  
#include <conio.h>  
  
int main( void )  
{  
    int         i = -16,  
                h = 29;  
    unsigned    u = 62511;  
    char        c = 'A';  
    char        s[] = "Test";  
  
    // Note that console output does not translate  
    // \n as standard output does. Use \r\n instead.  
    _cprintf_p( "%2$d  %1$.4x  %3$u  %4$c %5$s\r\n",   
                h, i, u, c, s );  
}  
```  
  
```Output  
-16  001d  62511  A Test  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cscanf –, _cscanf_l –, _cwscanf –, _cwscanf_l –](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [_cscanf_s –, _cscanf_s_l –, _cwscanf_s –, _cwscanf_s_l –](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [_fprintf_p –, _fprintf_p_l –, _fwprintf_p –, _fwprintf_p_l –](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf_s –, _fprintf_s_l –, fwprintf_s –, _fwprintf_s_l –](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [_printf_p –, _printf_p_l –, _wprintf_p –, _wprintf_p_l –](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_sprintf_p –, _sprintf_p_l –, _swprintf_p –, _swprintf_p_l –](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [_vfprintf_p –, _vfprintf_p_l –, _vfwprintf_p –, _vfwprintf_p_l –](../../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)   
 [_cprintf_s –, _cprintf_s_l –, _cwprintf_s –, _cwprintf_s_l –](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)   
 [Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)