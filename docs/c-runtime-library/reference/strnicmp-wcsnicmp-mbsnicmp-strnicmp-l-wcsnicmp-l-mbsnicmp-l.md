---
title: _strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
ms.date: 4/2/2020
api_name:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
- _o__mbsnicmp
- _o__mbsnicmp_l
- _o__strnicmp
- _o__strnicmp_l
- _o__wcsnicmp
- _o__wcsnicmp_l
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnicmp_l
- _strnicmp
- _ftcsnicmp
- mbsnicmp_l
- _ftcsncicmp
- mbsnicmp
- _tcsncicmp
- _mbsnicmp
- _tcsnicmp
- strnicmp_l
- _wcsnicmp
- _wcsnicmp_l
- CORECRT_WSTRING/_wcsnicmp
- CORECRT_WSTRING/_wcsnicmp_l
- string/_strnicmp
- string/_strnicmp_l
helpviewer_keywords:
- tcsnicmp function
- _tcsncicmp function
- _mbsnicmp_l function
- mbsnicmp_l function
- wcsnicmp_l function
- wcsnicmp function
- string comparison [C++], lowercase
- ftcsnicmp function
- strnicmp_l function
- strncmp function
- _strnicmp function
- strings [C++], comparing characters of
- _wcsnicmp_l function
- tcsncicmp function
- string comparison [C++], strncmp function
- _mbsnicmp function
- ftcsncicmp function
- _tcsnicmp function
- _ftcsncicmp function
- _strnicmp_l function
- _ftcsnicmp function
- characters [C++], comparing
- mbsnicmp function
- _wcsnicmp function
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
ms.openlocfilehash: b0bde60a230f1fd428716073471cd85b2728a614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364830"
---
# <a name="_strnicmp-_wcsnicmp-_mbsnicmp-_strnicmp_l-_wcsnicmp_l-_mbsnicmp_l"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l

Porovná zadaný počet znaků dvou řetězců bez ohledu na případ.

> [!IMPORTANT]
> **_mbsnicmp** a **_mbsnicmp_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _strnicmp(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsnicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicmp_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsnicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězce ukončené hodnotou null k porovnání.

*Počet*<br/>
Počet znaků, které mají být porovnány.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Označuje vztah mezi podřetězci následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|podřetězec *string1* je menší než podřetězec *string2.*|
|0|podřetězec *string1* je shodný s *podřetězcem string2.*|
|> 0|podřetězec *string1* je větší než podřetězec *string2.*|

Při chybě ověření parametru **_NLSCMPERROR**tyto funkce vrátí \<_NLSCMPERROR , který \<je definován v> string.h> a mbstring.h.

## <a name="remarks"></a>Poznámky

Funkce **_strnicmp** řadově porovnává maximálně znaky prvního *počtu* *string1* a *string2*. Porovnání se provádí bez ohledu na případ převodem každého znaku na malá písmena. **_strnicmp** je verze **strncmp**bez rozlišování velkých a malých písmen . Porovnání končí, pokud je dosaženo ukončujícího znaku null v obou řetězci před porovnáním znaků *počtu.* Pokud řetězce jsou stejné při ukončení null znak je dosaženo v obou řetězců před *počet* znaků jsou porovnány, kratší řetězec je menší.

Znaky od 91 do 96 v tabulce ASCII\\("[,, ', ',,,,,^', ',,, '", '', a '\`') jsou vyhodnoceny jako menší než jakýkoli abecední znak. Toto pořadí je totožné s **pořadím stricmp**.

**_wcsnicmp** a **_mbsnicmp** jsou verze **_strnicmp**s širokými znaky a vícebajtovými znaky . Argumenty **_wcsnicmp** jsou řetězce s širokými znaky; **_mbsnicmp** jsou řetězce vícebajtových znaků. **_mbsnicmp** rozpozná vícebajtové sekvence znaků podle aktuální znakové stránky vícebajtů a vrátí **_NLSCMPERROR** na chybu. Další informace naleznete v [tématu Code Pages](../../c-runtime-library/code-pages.md). Tyto tři funkce se chovají stejně jinak. Tyto funkce jsou ovlivněny nastavením národního prostředí – verze, které nemají **příponu _l,** používají aktuální národní prostředí pro své chování závislé na národním prostředí; verze, které mají **příponu _l** místo toho použít *národní prostředí,* které je předáno. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřují jejich parametry. Pokud je *buď string1* nebo *string2* ukazatel null, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp**|**_strnicmp**|**_mbsnicmp**|**_wcsnicmp**|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strnicmp**, **_strnicmp_l**|\<string.h>|
|**_wcsnicmp** **_wcsnicmp_l**|\<string.h> \<nebo wchar.h>|
|**_mbsnicmp** **_mbsnicmp_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
