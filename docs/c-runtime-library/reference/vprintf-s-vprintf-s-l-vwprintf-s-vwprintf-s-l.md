---
title: vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l
ms.date: 11/04/2016
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
ms.openlocfilehash: 1bca7c39ebea75a0981c2a9a8238c854930353ea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499146"
---
# <a name="vprintf_s-_vprintf_s_l-vwprintf_s-_vwprintf_s_l"></a>vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l

Zapisuje formátovaný výstup pomocí ukazatele na seznam argumentů. Tyto verze [vprintf –, _vprintf_l, vwprintf, _vwprintf_l](vprintf-vprintf-l-vwprintf-vwprintf-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*format*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*jazyka*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vprintf_s** a **vwprintf_s** vrátí počet zapsaných znaků, včetně ukončujícího znaku null, nebo zápornou hodnotu, pokud dojde k chybě výstupu. Pokud je *Formát* ukazatel s hodnotou null, nebo pokud řetězec formátu obsahuje neplatné formátovací znaky, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje daná data do **stdout**.

Zabezpečené verze těchto funkcí se liší od **vprintf –** a **vwprintf** pouze v tom, že zabezpečené verze kontrolují, zda řetězec formátu obsahuje platné formátovací znaky.

**vwprintf_s** je **vprintf_s**verze s velkým znakem; Tyto dvě funkce se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **vprintf_s** v současné době nepodporuje výstup do datového proudu Unicode.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

> [!IMPORTANT]
> Ujistěte se, že *Formát* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtprintf_s**|**vprintf_s**|**vprintf_s**|**vwprintf_s**|
|**_vtprintf_s_l**|**_vprintf_s_l**|**_vprintf_s_l**|**_vwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**vprintf_s**, **_vprintf_s_l**|\<stdio. h > a \<STDARG. h >|\<varargs.h>*|
|**vwprintf_s**, **_vwprintf_s_l**|\<stdio. h > nebo \<WCHAR. h > a \<STDARG. h >|\<varargs.h>*|

\*Vyžaduje se pro kompatibilitu se systémem UNIX V.

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
