---
title: strrchr, wcsrchr, _mbsrchr, _mbsrchr_l
ms.date: 4/2/2020
api_name:
- strrchr
- wcsrchr
- _mbsrchr
- _mbsrchr_l
- _o__mbsrchr
- _o__mbsrchr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsrchr
- _ftcsrchr
- strrchr
- wcsrchr
- _mbsrchr
helpviewer_keywords:
- _mbsrchr function
- tcsrchr function
- mbsrchr_l function
- characters [C++], scanning for
- ftcsrchr function
- _tcsrchr function
- strings [C++], scanning
- mbsrchr function
- strrchr function
- scanning strings
- wcsrchr function
- _ftcsrchr function
- _mbsrchr_l function
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
ms.openlocfilehash: b0aaa670cb6aa5af9e6f8a28234ba5c442d2f633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365048"
---
# <a name="strrchr-wcsrchr-_mbsrchr-_mbsrchr_l"></a>strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

Prohledá řetězec pro poslední výskyt znaku.

> [!IMPORTANT]
> `_mbsrchr`a `_mbsrchr_l` nelze jej použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strrchr(
   const char *str,
   int c
); // C only
char *strrchr(
   char *str,
   int c
); // C++ only
const char *strrchr(
   const char *str,
   int c
); // C++ only
wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcsrchr(
   wchar_t *str,
   wchar_t c
); // C++ only
const wchar_t *wcsrchr(
   const wchar_t *str,
   wchar_t c
); // C++ only
unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbsrchr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbsrchr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbsrchr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbsrchr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec ukončený hodnotou Null pro vyhledávání.

*C*<br/>
Znak, který má být umístěn.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na poslední výskyt *c* in *str*nebo NULL, pokud *c* nebyl nalezen.

## <a name="remarks"></a>Poznámky

Funkce `strrchr` vyhledá poslední výskyt *c* (převedena na **char**) v *str*. Hledání zahrnuje ukončující znak null.

`wcsrchr`a `_mbsrchr` jsou širokoúhlé a vícebajtové `strrchr`verze znaků . Argumenty a vrácená `wcsrchr` hodnota jsou řetězce širokých znaků; tyto `_mbsrchr` jsou vícebajtové řetězce znaků.

V C tyto funkce trvat **const** ukazatel pro první argument. V jazyce C++ jsou k dispozici dvě přetížení. Přetížení s ukazatelem **const** vrátí ukazatel **const**; verze, která má ukazatel na**non-const** vrátí ukazatel na**non-const**. Makro _CRT_CONST_CORRECT_OVERLOADS je definována, pokud jsou k dispozici verze těchto funkcí **const** i non-const.**const** Pokud požadujete chování bez**const** pro obě přetížení jazyka C++, definujte symbol _CONST_RETURN.

`_mbsrchr`ověří jeho parametry. Pokud *str* je NULL, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění je povoleno `errno` pokračovat, je nastavena na EINVAL a `_mbsrchr` vrátí 0. `strrchr`a `wcsrchr` neověřujte jejich parametry. Tyto tři funkce se chovají stejně jinak.

Výstupní hodnota je ovlivněna nastavením nastavení kategorie LC_CTYPE národního prostředí; Další informace naleznete [v tématu setlocale](setlocale-wsetlocale.md). Verze těchto funkcí bez **přípony _l** pro toto chování závislé na národním prostředí používají aktuální národní prostředí. verze s **příponou _l** jsou identické s tím rozdílem, že místo toho používají parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|
|**N/a**|**N/a**|`_mbsrchr_l`|**N/a**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strrchr`|\<string.h>|
|`wcsrchr`|\<string.h> \<nebo wchar.h>|
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Příklad použití `strrchr`naleznete v tématu [strchr](strchr-wcschr-mbschr-mbschr-l.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
