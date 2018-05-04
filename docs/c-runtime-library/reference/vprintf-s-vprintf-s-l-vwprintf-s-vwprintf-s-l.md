---
title: vprintf_s –, _vprintf_s_l –, vwprintf_s –, _vwprintf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _vwprintf_s_l
- vwprintf_s
- _vprintf_s_l
- vprintf_s
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
- vprintf_s
- vwprintf_s
- _vtprintf_s
dev_langs:
- C++
helpviewer_keywords:
- vwprintf_s_l function
- _vwprintf_s_l function
- vwprintf_s function
- _vtprintf_s_l function
- vprintf_s_l function
- vtprintf_s_l function
- _vtprintf_s function
- vtprintf_s function
- _vprintf_s_l function
- formatted text [C++]
- vprintf_s function
ms.assetid: cf864996-a530-4b40-9c30-54c4cef439c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1c8f2780fb9a6b65c60c0622526020a13f74e7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="vprintfs-vprintfsl-vwprintfs-vwprintfsl"></a>vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l

Výstup zápisy ve formátu pomocí ukazatel na seznam argumentů. Tyto verze nástroje [vprintf –, _vprintf_l –, vwprintf –, _vwprintf_l –](vprintf-vprintf-l-vwprintf-vwprintf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vprintf_s(
   const char *format,
   va_list argptr
);
int _vprintf_s_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int vwprintf_s(
   const wchar_t *format,
   va_list argptr
);
int _vwprintf_s_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vprintf_s –** a **vwprintf_s –** vrátí počet znaků zapsána, pokud dojde k chybě výstup není včetně ukončující znak hodnoty null nebo záporná hodnota. Pokud *formátu* je ukazatel s hodnotou null, nebo pokud řetězec formátu obsahuje neplatné znaky formátování, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí má ukazatel na seznam argumentů, pak naformátuje a zapíše daná data na **stdout**.

Bezpečné verze těchto funkcí se liší od **vprintf –** a **vwprintf –** pouze v tom zabezpečené verze ověřit, zda řetězec formátu obsahuje platné znaky formátování.

**vwprintf_s –** je verze široká charakterová **vprintf_s –**; dvě funkce chovají stejně jako datový proud se při otevření v režimu ANSI. **vprintf_s –** nepodporuje aktuálně výstup do proudu kódování UNICODE.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *formát* není řetězec definovaný uživatelem. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtprintf_s –**|**vprintf_s**|**vprintf_s**|**vwprintf_s –**|
|**_vtprintf_s_l –**|**_vprintf_s_l**|**_vprintf_s_l**|**_vwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**vprintf_s –**, **_vprintf_s_l –**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**vwprintf_s –**, **_vwprintf_s_l –**|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility V systému UNIX.

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
