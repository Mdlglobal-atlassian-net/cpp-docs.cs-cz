---
title: vfprintf_s – _vfprintf_s_l –, vfwprintf_s – _vfwprintf_s_l – | Dokumentace Microsoftu
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
ms.openlocfilehash: 8f1c9d6bde39fcd763416e4c8dd50f0b756cb6b4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220291"
---
# <a name="vfprintfs-vfprintfsl-vfwprintfs-vfwprintfsl"></a>vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Jde o verzích [vfprintf – _vfprintf_l –, vfwprintf – _vfwprintf_l –](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Stream*<br/>
Ukazatel na **souboru** struktury.

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

**vfprintf_s –** a **vfwprintf_s –** vrátí počet napsaných znaků, nikoli včetně ukončujícího znaku null, nebo zápornou hodnotu, pokud dojde k chybě výstupu. Pokud *stream* nebo *formátu* je ukazatel s hodnotou null, nebo pokud řetězec formátu obsahuje neplatné formátovací znaky, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje poskytnutá data do *stream*.

Tyto funkce se liší od nebezpečných verzí pouze v tom, že bezpečné verze kontrolují, který *formátu* řetězec obsahuje platné formátovací znaky.

**vfwprintf_s –** je verze širokého znaku **vfprintf_s –**; tyto dvě funkce se chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **vfprintf_s –** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_s –**|**vfprintf_s**|**vfprintf_s**|**vfwprintf_s –**|
|**_vftprintf_s_l –**|**_vfprintf_s_l**|**_vfprintf_s_l**|**_vfwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**vfprintf_s –**, **_vfprintf_s_l –**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**vfwprintf_s –**, **_vfwprintf_s_l –**|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility systému UNIX V.

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
