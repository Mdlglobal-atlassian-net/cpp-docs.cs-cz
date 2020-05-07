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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3be900679dddbbab7cba0982c11d5c75a190d685
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920083"
---
# <a name="_strnicmp-_wcsnicmp-_mbsnicmp-_strnicmp_l-_wcsnicmp_l-_mbsnicmp_l"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l

Porovná zadaný počet znaků dvou řetězců bez ohledu na velikost písmen.

> [!IMPORTANT]
> **_mbsnicmp** a **_mbsnicmp_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězec zakončený hodnotou null k porovnání

*výpočtu*<br/>
Počet znaků, které mají být porovnány.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Označuje vztah mezi podřetězci následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|podřetězec *řetězec1* je menší než *řetězec2* .|
|0|podřetězec *řetězec1* je identický s podřetězcem *řetězec2* .|
|> 0|podřetězec *řetězec1* je větší než *řetězec2* .|

Při ověřování parametru vrátí tyto funkce **_NLSCMPERROR**, což je definováno v \<řetězci. h> a \<Mbstring. h>.

## <a name="remarks"></a>Poznámky

Funkce **_strnicmp** pořadová čísla porovnává, většinou první *počet* znaků *řetězec1* a *řetězec2*. Porovnání je provedeno bez ohledu na případ převodem jednotlivých znaků na malá písmena. **_strnicmp** je verze **strncmp**bez rozlišení velkých a malých písmen. Porovnání končí, pokud je dosaženo ukončujícího znaku null v řetězci před porovnáním znaků *Count* . Pokud jsou řetězce stejné, když je dosaženo ukončujícího znaku null v řetězci předtím, než jsou znaky *Count* porovnány, kratší řetězec je menší.

Znaky od 91 do 96 v tabulce ASCII (' [', '\\', '] ', ' ^ ', ' _ ' a '\`') vyhodnotí jako znak, který je menší než jakýkoli abecední znak. Toto řazení je stejné jako u **stricmp**.

**_wcsnicmp** a **_mbsnicmp** jsou verze **_strnicmp**a vícebajtových znaků. Argumenty **_wcsnicmp** jsou řetězce s velkým počtem znaků; **_mbsnicmp** jsou vícebajtové znakové řetězce. **_mbsnicmp** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtové znakové stránky a vrátí **_NLSCMPERROR** při chybě. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Tyto tři funkce se chovají identicky jinak. Tyto funkce jsou ovlivněny nastavením národního prostředí – verze, které nemají příponu **_l** , používají aktuální národní prostředí pro své chování závislé na národním prostředí. verze, které mají příponu **_l** , místo toho používají *národní prostředí* , které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřují své parametry. Pokud je buď *řetězec1* nebo *řetězec2* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp**|**_strnicmp**|**_mbsnicmp**|**_wcsnicmp**|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strnicmp** **_strnicmp_l**|\<String. h>|
|**_wcsnicmp** **_wcsnicmp_l**|\<String. h> nebo \<WCHAR. h>|
|**_mbsnicmp** **_mbsnicmp_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

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
