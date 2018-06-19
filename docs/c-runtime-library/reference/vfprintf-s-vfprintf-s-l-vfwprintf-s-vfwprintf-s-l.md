---
title: vfprintf_s –, _vfprintf_s_l –, vfwprintf_s –, _vfwprintf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vfwprintf_s
- _vfprintf_s_l
- vfprintf_s
- _vfwprintf_s_l
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
- _vftprintf_s
- vfwprintf_s
- vfprintf_s
dev_langs:
- C++
helpviewer_keywords:
- vfprintf_s_l function
- vfwprintf_s_l function
- vfwprintf_s function
- _vfprintf_s_l function
- _vfwprintf_s_l function
- vftprintf_s_l function
- vfprintf_s function
- _vftprintf_s_l function
- formatted text [C++]
- _vftprintf_s function
ms.assetid: eab6f563-46e2-4806-963f-2b23f339ecdc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bda1dce264597bfe7372b1cb0293dffccad4cdc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415751"
---
# <a name="vfprintfs-vfprintfsl-vfwprintfs-vfwprintfsl"></a>vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Toto jsou verze [vfprintf –, _vfprintf_l –, vfwprintf –, _vfwprintf_l –](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vfprintf_s(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vfwprintf_s(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vfprintf_s –** a **vfwprintf_s –** vrátí počet znaků zapsána, pokud dojde k chybě výstup není včetně ukončující znak hodnoty null nebo záporná hodnota. Pokud má jedna *datového proudu* nebo *formátu* je ukazatel s hodnotou null, nebo pokud řetězec formátu obsahuje neplatné znaky formátování, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí má ukazatel na seznam argumentů, pak naformátuje a zapíše daná data na *datového proudu*.

Tyto funkce liší od verze nezabezpečené pouze v tom zabezpečené verze zkontrolujte, zda *formát* řetězec obsahuje platné znaky formátování.

**vfwprintf_s –** je verze široká charakterová **vfprintf_s –**; dvě funkce chovají stejně jako datový proud se při otevření v režimu ANSI. **vfprintf_s –** nepodporuje aktuálně výstup do proudu kódování UNICODE.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *formát* není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_s –**|**vfprintf_s**|**vfprintf_s**|**vfwprintf_s –**|
|**_vftprintf_s_l –**|**_vfprintf_s_l**|**_vfprintf_s_l**|**_vfwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**vfprintf_s –**, **_vfprintf_s_l –**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**vfwprintf_s –**, **_vfwprintf_s_l –**|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility V systému UNIX.

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
