---
title: "vprintf –, _vprintf_l –, vwprintf –, _vwprintf_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- vprintf
- _vwprintf_l
- _vprintf_l
- vwprintf
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
- vwprintf
- _vtprintf
dev_langs:
- C++
helpviewer_keywords:
- vwprintf function
- _vwprintf_l function
- vwprintf_l function
- _vtprintf function
- vtprintf_l function
- vprintf function
- _vprintf_l function
- vprintf_l function
- vtprintf function
- _vtprintf_l function
- formatted text [C++]
ms.assetid: 44549505-00a0-4fa7-9a85-f2e666f55a38
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1f55df49b554fd43912eac252fef1575b3bc411
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="vprintf-vprintfl-vwprintf-vwprintfl"></a>vprintf, _vprintf_l, vwprintf, _vwprintf_l
Výstup zápisy ve formátu pomocí ukazatel na seznam argumentů. Bezpečnější verze tyto funkce jsou k dispozici, najdete v části [vprintf_s –, _vprintf_s_l –, vwprintf_s –, _vwprintf_s_l –](../../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int vprintf(  
   const char *format,  
   va_list argptr   
);  
int _vprintf_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vwprintf(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vwprintf_l(  
   const wchar_t *format,  
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
  
 Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 `vprintf` a `vwprintf` vrátí počet znaků zapsána, pokud dojde k chybě výstup není včetně ukončující znak hodnoty null nebo záporná hodnota. Pokud `format` je ukazatel s hodnotou null, nebo pokud řetězec formátu obsahuje neplatné znaky formátování, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí má ukazatel na seznam argumentů, pak naformátuje a zapíše daná data na `stdout`.  
  
 `vwprintf` je verze široká charakterová `vprintf`; dvě funkce chovají stejně jako datový proud se při otevření v režimu ANSI. `vprintf` nepodporuje aktuálně výstup do proudu kódování UNICODE.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.  
  
> [!IMPORTANT]
>  Ujistěte se, že `format` není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795). Všimněte si, že neplatný formát řetězce jsou zjištěny a výsledkem je chyba.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vtprintf`|`vprintf`|`vprintf`|`vwprintf`|  
|`_vtprintf_l`|`_vprintf_l`|`_vprintf_l`|`_vwprintf_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`vprintf`, `_vprintf_l`|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|  
|`vwprintf`, `_vwprintf_l`|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|  
  
 \* Vyžaduje se pro kompatibility V systému UNIX.  
  
Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, `stdin`, `stdout`, a `stderr`, C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [vprintf – funkce](../../c-runtime-library/vprintf-functions.md)   
 [fprintf, _fprintf_l –, fwprintf –, _fwprintf_l –](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)