---
title: _strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l
ms.date: 11/04/2016
api_name:
- _strlwr_s_l
- _mbslwr_s_l
- _mbslwr_s
- _wcslwr_s
- _strlwr_s
- _wcslwr_s_l
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strlwr_s_l
- _strlwr_s
- mbslwr_s_l
- strlwr_s_l
- _wcslwr_s
- strlwr_s
- mbslwr_s
- _wcslwr_s_l
- wcslwr_s_l
- _tcslwr_s
- _tcslwr_s_l
- _mbslwr_s_l
- wcslwr_s
- _mbslwr_s
helpviewer_keywords:
- _tcslwr_s function
- wcslwr_s function
- _mbslwr_s function
- _wcslwr_s function
- strlwr_s_l function
- mbslwr_s_l function
- _strlwr_s function
- string conversion [C++], case
- strlwr_s function
- wcslwr_s_l function
- _tcslwr_s_l function
- mbslwr_s function
- strings [C++], case
- _wcslwr_s_l function
- converting case, CRT functions
- _strlwr_s_l function
- _mbslwr_s_l function
- case, converting
- tcslwr_s function
- tcslwr_s_l function
- strings [C++], converting case
ms.assetid: 4883d31b-bdac-4049-83a1-91dfdeceee79
ms.openlocfilehash: 70009f1d7d0230b37c6a59da20996842f976d02f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947588"
---
# <a name="_strlwr_s-_strlwr_s_l-_mbslwr_s-_mbslwr_s_l-_wcslwr_s-_wcslwr_s_l"></a>_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l

Převede řetězec na malá písmena pomocí aktuálního národního prostředí nebo objektu, který je předán. Tyto verze [_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbslwr_s** a **_mbslwr_s_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strlwr_s(
   char *str,
   size_t numberOfElements
);
errno_t _strlwr_s_l(
   char *str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _mbslwr_s(
   unsigned char *str,
   size_t numberOfElements
);
errno_t _mbslwr_s_l(
   unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _wcslwr_s(
   wchar_t *str,
   size_t numberOfElements
);
errno_t _wcslwr_s_l(
   wchar_t *str,
   size_t numberOfElements,
   _locale_t locale
);
template <size_t size>
errno_t _strlwr_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _strlwr_s_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbslwr_s(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
errno_t _mbslwr_s_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _wcslwr_s(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
errno_t _wcslwr_s_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec zakončený hodnotou null, který má být převeden na malá písmena.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; nenulový kód chyby při selhání.

Tyto funkce ověřují své parametry. Pokud *str* není platný řetězec zakončený hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**. Pokud je *numberOfElements* menší než délka řetězce, funkce také vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_strlwr_s** převádí na místě všechna velká písmena v *str* na malá. **_mbslwr_s** je Vícebajtová znaková verze **_strlwr_s**. **_wcslwr_s** je verze **_strlwr_s**s velkým znakem.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFD. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr_s**|**_strlwr_s**|**_mbslwr_s**|**_wcslwr_s**|
|**_tcslwr_s_l**|**_strlwr_s_l**|**_mbslwr_s_l**|**_wcslwr_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strlwr_s**, **_strlwr_s_l**|\<String. h >|
|**_mbslwr_s**, **_mbslwr_s_l**|\<Mbstring. h >|
|**_wcslwr_s**, **_wcslwr_s_l**|\<String. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
// crt_strlwr_s.cpp
// This program uses _strlwr_s and _strupr_s to create
// uppercase and lowercase copies of a mixed-case string.
//

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{
   char str[] = "The String to End All Strings!";
   char *copy1, *copy2;
   errno_t err;

   err = _strlwr_s( copy1 = _strdup(str), strlen(str) + 1);
   err = _strupr_s( copy2 = _strdup(str), strlen(str) + 1);

   printf( "Mixed: %s\n", str );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );

   return 0;
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)<br/>
