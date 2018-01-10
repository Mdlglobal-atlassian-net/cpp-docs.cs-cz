---
title: "_vcprintf_s –, _vcprintf_s_l –, _vcwprintf_s –, _vcwprintf_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _vcprintf_s
- _vcprintf_s_l
- _vcwprintf_s
- _vcwprintf_s_l
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
- vcprintf_s
- vcwprintf_s_l
- _vcwprintf_s
- _vcwprintf_s_l
- _vcprintf_s_l
- _vtcprintf_s
- vcwprintf_s
- vcprintf_s_l
- _vcprintf_s
dev_langs: C++
helpviewer_keywords:
- _vtcprintf_s_l function
- _vcwprintf_s_l function
- _vtcprintf_s function
- vtcprintf_s_l function
- vcprintf_s_l function
- _vcprintf_s function
- _vcwprintf_s function
- vcwprintf_s_l function
- vcwprintf_s function
- vcprintf_s function
- _vcprintf_s_l function
- vtcprintf_s function
- formatted text [C++]
ms.assetid: 5a46d45a-30db-45df-9850-455cbdac5636
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e47d35c4f827351f76099c748f483a82f0e04d36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vcprintfs-vcprintfsl-vcwprintfs-vcwprintfsl"></a>_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l
Zápis ve formátu výstup do konzoly pomocí ukazatel na seznam argumentů. Tyto verze nástroje [_vcprintf –, _vcprintf_l –, _vcwprintf –, _vcwprintf_l –](../../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _vcprintf(  
   const char* format,  
   va_list argptr  
);  
int _vcprintf(  
   const char* format,  
   locale_t locale,  
   va_list argptr  
);  
int _vcwprintf_s(  
   const wchar_t* format,  
   va_list argptr  
);  
int _vcwprintf_s_l(  
   const wchar_t* format,  
   locale_t locale,  
   va_list argptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Specifikace formátu.  
  
 `argptr`  
 Ukazatel na seznam argumentů.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
 Další informace najdete v tématu [syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet znaků, které jsou zapsány nebo záporná, pokud dojde k chybě výstup.  
  
 Jako méně bezpečná verze těchto funkcí, pokud `format` je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Navíc, na rozdíl od méně bezpečná verze těchto funkcí Pokud `format` neurčuje platný formát, se vygeneruje výjimku neplatný parametr. Pokud je povoleno spuštění pokračovat, tyto funkce vrátí kód chyby a sadu `errno` tento kód chyby. Kód chyby výchozí `EINVAL` Pokud konkrétnější hodnotu nelze použít.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí má ukazatel na seznam argumentů a naformátuje a zapíše daná data do konzoly. `_vcwprintf_s`je verze široká charakterová `_vcprintf_s`. Jako argument trvá široká charakterová řetězec.  
  
 Verze tyto funkce, které mají `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí, který se předává v místo aktuální národní prostředí.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vtcprintf_s`|`_vcprintf_s`|`_vcprintf_s`|`_vcwprintf_s`|  
|`_vtcprintf_s_l`|`_vcprintf_s_l`|`_vcprintf_s_l`|`_vcwprintf_s_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`_vcprintf_s`, `_vcprintf_s_l`|\<conio.h > a \<stdarg.h >|\<VarArgs.h > *|  
|`_vcwprintf_s`, `_vcwprintf_s_l`|\<conio.h > nebo \<wchar.h >, a \<stdarg.h >|\<VarArgs.h > *|  
  
 \*Vyžaduje se pro kompatibility V systému UNIX.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_vcprintf_s.cpp  
#include <conio.h>  
#include <stdarg.h>  
  
// An error formatting function used to print to the console.  
int eprintf_s(const char* format, ...)  
{  
  va_list args;  
  va_start(args, format);  
  int result = _vcprintf_s(format, args);  
  va_end(args);  
  return result;
}  
  
int main()  
{  
   eprintf_s("  (%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,  
           "<some error text>");  
   eprintf_s("  (Related to symbol '%s' defined on line %d).\n",  
           "<symbol>", 5 );  
}  
```  
  
```Output  
(10,23): Error C2111 : <some error text>  
  (Related to symbol '<symbol>' defined on line 5).  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [vprintf – funkce](../../c-runtime-library/vprintf-functions.md)   
 [_cprintf –, _cprintf_l –, _cwprintf –, _cwprintf_l –](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)