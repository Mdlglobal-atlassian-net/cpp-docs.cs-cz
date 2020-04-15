---
title: _strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l
ms.date: 4/2/2020
api_name:
- _mbsspnp
- _wcsspnp
- _mbsspnp_l
- _strspnp
- _o__mbsspnp
- _o__mbsspnp_l
api_location:
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsspnp
- _mbsspnp
- strspnp
- _ftcsspnp
- _mbsspnp_l
- wcsspnp
- mbsspnp_l
- _wcsspnp
- _strspnp
- mbsspnp
helpviewer_keywords:
- _strspnp function
- _wcsspnp function
- _mbsspnp_l function
- strspnp function
- mbsspnp function
- wcsspnp function
- _mbsspnp function
- mbsspnp_l function
- _tcsspnp function
- tcsspnp function
ms.assetid: 1ce18100-2edd-4c3b-af8b-53f204d80233
ms.openlocfilehash: c45fc42fb9edce1b82b0910f8aae81d4058d5974
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317025"
---
# <a name="_strspnp-_wcsspnp-_mbsspnp-_mbsspnp_l"></a>_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l

Vrátí ukazatel na první znak v daném řetězci, který není v jiném daném řetězci.

> [!IMPORTANT]
> **_mbsspnp** a **_mbsspnp_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strspnp(
   const char *str,
   const char *charset
);
wchar_t *_wcsspnp(
   const unsigned wchar_t *str,
   const unsigned wchar_t *charset
);
unsigned char *_mbsspnp(
   const unsigned char *str,
   const unsigned char *charset
);
unsigned char *_mbsspnp_l(
   const unsigned char *str,
   const unsigned char *charset,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec ukončený hodnotou Null pro vyhledávání.

*Charset*<br/>
Znaková sada ukončená hodnotou Null.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_strspnp**, **_wcsspnp**a **_mbsspnp** vrátí ukazatel na první znak v *str,* který nepatří do sady znaků v *znakové sadě*. Každá z těchto funkcí vrátí **hodnotu NULL,** pokud *str* obsahuje výhradně znaky z *znakové sady*. Pro každou z těchto rutin není vyhrazena žádná vrácená hodnota, která by označovala chybu.

## <a name="remarks"></a>Poznámky

Funkce **_mbsspnp** vrátí ukazatel na vícebajtový znak, který je prvním znakem v *str,* který nepatří do sady znaků v *znakové sadě*. **_mbsspnp** rozpoznává vícebajtové sekvence znaků podle aktuálně používáné [vícebajtové znakové stránky.](../../c-runtime-library/code-pages.md) Hledání nezahrnuje ukončující prázdné znaky.

Pokud *str* nebo *charset* je ukazatel null, tato funkce vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **hodnotu NULL** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsspnp**|**_strspnp**|**_mbsspnp**|**_wcsspnp**|

**_strspnp** a **_wcsspnp** jsou jednobajtové znakové a širokoomístné verze **_mbsspnp**. **_strspnp** a **_wcsspnp** se chovají stejně jako **_mbsspnp** jinak; jsou poskytovány pouze pro toto mapování a neměly by být používány z žádného jiného důvodu. Další informace naleznete [v tématu Použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a mapování [obecného textu](../../c-runtime-library/generic-text-mappings.md).

**_mbsspnp_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsspnp**|\<mbstring.h>|
|**_strspnp**|\<tchar.h>|
|**_wcsspnp**|\<tchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mbsspnp.c
#include <mbstring.h>
#include <stdio.h>

int main( void ) {
   const unsigned char string1[] = "cabbage";
   const unsigned char string2[] = "c";
   unsigned char *ptr = 0;
   ptr = _mbsspnp( string1, string2 );
   printf( "%s\n", ptr);
}
```

### <a name="output"></a>Výstup

```Output
abbage
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
