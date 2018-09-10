---
title: _strnicmp – _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0da454b2b980be3565ee27fde4ee14d7eadd42fb
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313623"
---
# <a name="strnicmp-wcsnicmp-mbsnicmp-strnicmpl-wcsnicmpl-mbsnicmpl"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
Porovná zadaný počet znaků, bez ohledu na případ dvou řetězců.

> [!IMPORTANT]
> **_mbsnicmp –** a **_mbsnicmp_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězec zakončený hodnotou Null pro srovnání.

*Počet*<br/>
Počet znaků, které mají být porovnány.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Označuje vztah mezi podřetězci, následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* dílčí řetězec je menší než *řetězec2* dílčí řetězec.|
|0|*řetězec1* se shoduje s podřetězcem *řetězec2* dílčí řetězec.|
|> 0|*řetězec1* je větší než podřetězec *řetězec2* dílčí řetězec.|

Na parametr chyby ověřování, vrátí tyto funkce **_NLSCMPERROR**, který je definován v \<string.h > a \<mbstring.h >.

## <a name="remarks"></a>Poznámky

**_Strnicmp –** funkce ordinally porovná maximálně, první *počet* znaků *řetězec1* a *řetězec2*. Porovnání je provedeno bez ohledu na případ převedením jednotlivé znaky na malá písmena. **_strnicmp –** je velká a malá písmena verze **strncmp –**. Porovnání končí, když je dosaženo ukončujícího znaku null v jednom z řetězců před *počet* znaků. Pokud jsou řetězce shodné při dosažení ukončujícího znaku null v jednom z řetězců před *počet* jsou porovnány znaky, kratší řetězec je menší.

Znaky z 91 96 v tabulce ASCII ('[','\\","] "," ^ ","_"a"\`") vyhodnotit jako méně než libovolný znak abecedy. Toto řazení je stejné jako u **stricmp –**.

**_wcsnicmp –** a **_mbsnicmp –** jsou širokoznaké a vícebajtové verze **_strnicmp –**. Argumenty **_wcsnicmp –** jsou širokoznaké řetězce **_mbsnicmp –** jsou vícebajtové znakové řetězce. **_mbsnicmp –** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtové znakové stránce a vrátí **_NLSCMPERROR** v případě chyby. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Tyto tři funkce chovají identicky jinak. Tyto funkce se vztahuje nastavení národního prostředí – verze, které nemají **_l** používají aktuální národní prostředí pro své chování závislé na národním prostředí; ty, které mají **_l** příponu Místo toho použít *národní prostředí* , který je předán. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřují své parametry. Pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastavte **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp –**|**_strnicmp**|**_mbsnicmp –**|**_wcsnicmp**|
|**_tcsnicmp –**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strnicmp –**, **_strnicmp_l –**|\<String.h >|
|**_wcsnicmp –**, **_wcsnicmp_l –**|\<String.h > nebo \<wchar.h >|
|**_mbsnicmp –**, **_mbsnicmp_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [strncmp –](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

## <a name="see-also"></a>Viz také:

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
