---
title: strcat_s, wcscat_s, _mbscat_s, _mbscat_s_l
ms.date: 01/22/2019
apiname:
- strcat_s
- _mbscat_s
- _mbscat_s_l
- wcscat_s
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
ms.openlocfilehash: bd7894ba77e7fa67fa3844587394bd3e2e821391
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210390"
---
# <a name="strcats-wcscats-mbscats-mbscatsl"></a>strcat_s, wcscat_s, _mbscat_s, _mbscat_s_l

Připojí řetězec. Tyto verze [strcat – wcscat –, _mbscat –](strcat-wcscat-mbscat.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscat_s –** a **_mbscat_s_l** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Vyrovnávací paměti pro řetězec cíle zakončený hodnotou Null.

*numberOfElements*<br/>
Velikost vyrovnávací paměti cílového řetězce.

*strSource*<br/>
Vyrovnávací paměti pro řetězec zakončený hodnotou Null zdroje.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|*strDestination*|*numberOfElements*|*strSource*|Návratová hodnota|Obsah *strDestination*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL** nebo neukončený|Všechny|Všechny|**EINVAL**|Nezměněno|
|Všechny|Všechny|**NULL**|**EINVAL**|*strDestination*[0] nastavit na hodnotu 0|
|Všechny|0 nebo příliš malá|Všechny|**ERANGE**|*strDestination*[0] nastavit na hodnotu 0|

## <a name="remarks"></a>Poznámky

**Strcat_s** připojí funkce *strSource* k *strDestination* a ukončí výsledný řetězec znakem null. Počáteční znak *strSource* přepíše ukončující znak null proměnné *strDestination*. Chování **strcat_s** není definováno, pokud se zdrojový a cílový řetězec překrývají.

Všimněte si, že druhý parametr je celková velikost vyrovnávací paměti, nikoli zbývající velikost:

```C
char buf[16];
strcpy_s(buf, 16, "Start");
strcat_s(buf, 16, " End");               // Correct
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect
```

**wcscat_s –** a **_mbscat_s –** jsou širokoznaké a vícebajtové verze **strcat_s**. Argumenty a vrácené hodnoty **wcscat_s –** jsou širokoznaké řetězce **_mbscat_s –** jsou vícebajtové znakové řetězce. Tyto tři funkce chovají identicky jinak.

Pokud *strDestination* je ukazatel s hodnotou null nebo není ukončený hodnotou null, nebo pokud *strSource* je **NULL** ukazatele, nebo pokud cílový řetězec je příliš malá, neplatný parametr je vyvolána obslužná rutina, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastavte **errno** k **EINVAL**.

Verze funkcí, které mají **_l** přípony mají stejné chování, ale používá parametr národního prostředí, které je předáno namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat_s**|**strcat_s**|**_mbscat_s**|**wcscat_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcat_s**|\<string.h>|
|**wcscat_s**|\<String.h > nebo \<wchar.h >|
|**_mbscat_s**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad kódu v [strcpy_s wcscpy_s –, _mbscpy_s –](strcpy-s-wcscpy-s-mbscpy-s.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
