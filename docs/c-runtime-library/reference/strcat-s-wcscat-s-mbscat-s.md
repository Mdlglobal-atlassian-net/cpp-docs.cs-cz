---
title: strcat_s, wcscat_s, _mbscat_s, _mbscat_s_l
ms.date: 4/2/2020
api_name:
- strcat_s
- _mbscat_s
- _mbscat_s_l
- wcscat_s
- _o__mbscat_s
- _o__mbscat_s_l
- _o_strcat_s
- _o_wcscat_s
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
- strcat_s
- wcscat_s
- _mbscat_s
- _mbscat_s_l
helpviewer_keywords:
- wcscat_s function
- strcat_s function
- mbscat_s function
- strings [C++], appending
- _mbscat_s function
- _mbscat_s_l function
- appending strings
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
ms.openlocfilehash: f7d890a753638112c4a1bb56cf6093a9510dbee2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910662"
---
# <a name="strcat_s-wcscat_s-_mbscat_s-_mbscat_s_l"></a>strcat_s, wcscat_s, _mbscat_s, _mbscat_s_l

Připojí řetězec. Tyto verze [strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscat_s** a **_mbscat_s_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t strcat_s(
   char *strDestination,
   size_t numberOfElements,
   const char *strSource
);
errno_t wcscat_s(
   wchar_t *strDestination,
   size_t numberOfElements,
   const wchar_t *strSource
);
errno_t _mbscat_s(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource
);
errno_t _mbscat_s_l(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource,
   _locale_t locale
);
template <size_t size>
errno_t strcat_s(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
errno_t wcscat_s(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s_l(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDestination*<br/>
Vyrovnávací paměť cílového řetězce zakončená hodnotou null

*numberOfElements*<br/>
Velikost vyrovnávací paměti cílového řetězce.

*strSource*<br/>
Vyrovnávací paměť zdrojového řetězce zakončená hodnotou null

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*strDestination*|*numberOfElements*|*strSource*|Návratová hodnota|Obsah *strDestination*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**Null** nebo neukončeno|jakýmikoli|jakýmikoli|**EINVAL**|Neupraveno|
|jakýmikoli|jakýmikoli|**PLATNOST**|**EINVAL**|*strDestination*[0] nastaví na 0.|
|jakýmikoli|0 nebo příliš malý|jakýmikoli|**ERANGE**|*strDestination*[0] nastaví na 0.|

## <a name="remarks"></a>Poznámky

Funkce **strcat_s** připojí *strSource* k *strDestination* a ukončí výsledný řetězec znakem null. Počáteční znak *strSource* přepíše ukončující znak null hodnoty *strDestination*. Chování **strcat_s** není definováno, pokud se zdrojový a cílový řetězec překrývají.

Všimněte si, že druhý parametr je celková velikost vyrovnávací paměti, nikoli zbývající velikost:

```C
char buf[16];
strcpy_s(buf, 16, "Start");
strcat_s(buf, 16, " End");               // Correct
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect
```

**wcscat_s** a **_mbscat_s** jsou verze **strcat_s**a vícebajtových znaků. Argumenty a návratová hodnota **wcscat_s** jsou řetězce s velkým počtem znaků; **_mbscat_s** jsou vícebajtové znakové řetězce. Tyto tři funkce se chovají identicky jinak.

Pokud je *strDestination* ukazatel s hodnotou null, nebo není zakončený hodnotou null, nebo pokud je *StrSource* ukazatel s **hodnotou null** , nebo pokud je cílový řetězec příliš malý, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastaví **errno** na **EINVAL**.

Verze funkcí, které mají příponu **_l** mají stejné chování, ale použijte předaný parametr národního prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. K zakázání tohoto chování použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat_s**|**strcat_s**|**_mbscat_s**|**wcscat_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcat_s**|\<String. h>|
|**wcscat_s**|\<String. h> nebo \<WCHAR. h>|
|**_mbscat_s**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad kódu v [strcpy_s, wcscpy_s _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
