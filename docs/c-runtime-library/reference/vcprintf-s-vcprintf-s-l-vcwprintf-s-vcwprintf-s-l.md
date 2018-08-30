---
title: _vcprintf_s – _vcprintf_s_l –, _vcwprintf_s – _vcwprintf_s_l – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39f169c18554aa91e3f66a3e30a62a801c9d345d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208985"
---
# <a name="vcprintfs-vcprintfsl-vcwprintfs-vcwprintfsl"></a>_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l

Zapíše formátovaný výstup na konzoli pomocí ukazatele na seznam argumentů. Tyto verze [_vcprintf – _vcprintf_l –, _vcwprintf – _vcwprintf_l –](vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Počet napsaných znaků, nebo zápornou hodnotu, pokud dojde k chybě výstupu.

Méně bezpečné verze těchto funkcí, například pokud *formátu* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Navíc na rozdíl od méně bezpečné verze těchto funkcí Pokud *formátu* neurčuje platný formát je generována výjimka neplatného parametru. Pokud smí provádění pokračovat, tyto funkce vrátí chybový kód a nastaví **errno** na tento chybový kód. Výchozí chybový kód je **EINVAL** Pokud konkrétní hodnotu nevztahuje.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje poskytnutá data do konzoly. **_vcwprintf_s –** je verze širokého znaku **_vcprintf_s –**. Bere jako argument řetězec širokého znaku.

Verze těchto funkcí, které mají **_l** přípona jsou stejné s tím rozdílem, že používají Předaný parametr národního prostředí namísto aktuálního národního prostředí.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtcprintf_s –**|**_vcprintf_s**|**_vcprintf_s**|**_vcwprintf_s –**|
|**_vtcprintf_s_l –**|**_vcprintf_s_l**|**_vcprintf_s_l**|**_vcwprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_vcprintf_s –**, **_vcprintf_s_l –**|\<conio.h > a \<stdarg.h >|\<varargs.h>*|
|**_vcwprintf_s –**, **_vcwprintf_s_l –**|\<conio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility systému UNIX V.

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
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
    eprintf_s("(%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,
              "<some error text>");
    eprintf_s("    (Related to symbol '%s' defined on line %d).\n",
              "<symbol>", 5 );
}
```

```Output
(10,23): Error C2111 : <some error text>
    (Related to symbol '<symbol>' defined on line 5).
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
