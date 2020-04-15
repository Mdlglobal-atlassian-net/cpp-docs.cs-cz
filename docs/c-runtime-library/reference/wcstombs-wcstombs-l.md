---
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: fb95c6d73a3979a39995b9104a76fc42ca9e8535
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366712"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Převede posloupnost širokých znaků na odpovídající posloupnost vícebajtových znaků. K dispozici jsou bezpečnější verze těchto funkcí. viz [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Adresa posloupnosti vícebajtových znaků.

*wcstr*<br/>
Adresa posloupnosti širokých znaků.

*Počet*<br/>
Maximální počet bajtů, které mohou být uloženy v vícebajtovém výstupním řetězci.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **wcstombs** úspěšně převede vícebajtový řetězec, vrátí počet bajtů zapsaných do vícebajtového výstupního řetězce, s výjimkou ukončující null (pokud existuje). Pokud je argument *mbstr* **null**, **vrátí wcstombs** požadovanou velikost v bajtech cílového řetězce. Pokud **wcstombs** narazí na široký znak, který nelze převést na vícebajtový znak, vrátí -1 přetypovací na typ **size_t** a nastaví **errno** na **EILSEQ**.

## <a name="remarks"></a>Poznámky

Funkce **wcstombs** převede řetězec široký znak, na který je odkazováno *wcstr,* na odpovídající vícebajtové znaky a uloží výsledky do pole *mbstr.* Parametr *count* označuje maximální počet bajtů, které mohou být uloženy ve vícebajtovém výstupním řetězci (to znamená velikost *mbstr).* Obecně není známo, kolik bajtů bude vyžadováno při převodu řetězce s širokým znakem. Některé široké znaky budou vyžadovat pouze jeden bajt ve výstupním řetězci; jiné vyžadují dva. Pokud jsou dva bajty v vícebajtovém výstupním řetězci pro každý široký znak ve vstupním řetězci (včetně širokého znaku null), výsledek je zaručeno, že se vejde.

Pokud **wcstombs** narazí na znak null znaku široký znak (L'\0') před nebo při *počítání* dojde, převede jej na 8bitový znak 0 a zastaví. Vícebajtový znakový řetězec na *mbstr* je tedy ukončen a nula pouze v případě, **že wcstombs** narazí na znak null široký znak během převodu. Pokud se sekvence, na které se překrývají *wcstr* a *mbstr,* chování **wcstombs** není definováno.

Pokud je argument *mbstr* **null**, **vrátí wcstombs** požadovanou velikost v bajtech cílového řetězce.

**wcstombs** ověřuje jeho parametry. Pokud *je wcstr* **null**nebo pokud je *počet* větší než **INT_MAX**, tato funkce vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí -1.

**wcstombs** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_wcstombs_l** je identické s tím rozdílem, že používá národní prostředí předané v místo. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování **funkce wcstombs.**

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
