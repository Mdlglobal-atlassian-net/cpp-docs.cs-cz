---
title: wcstombs, _wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: d102cd74061faeb0c41823e6cf5c9a8ef335294f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188581"
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l

Převede sekvenci širokých znaků na odpovídající sekvence vícebajtových znaků. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [wcstombs_s – _wcstombs_s_l –](wcstombs-s-wcstombs-s-l.md).

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
Adresa sekvence vícebajtových znaků.

*wcstr*<br/>
Adresa sekvence širokých znaků.

*Počet*<br/>
Maximální počet bajtů, které mohou být uloženy ve vícebajtové výstupním řetězci.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **wcstombs –** úspěšně převede vícebajtový řetězec, vrátí počet bajtů zapsaný do výstupní vícebajtový řetězec, s výjimkou ukončujícího znaku null (pokud existuje). Pokud *mbstr* argument je **NULL**, **wcstombs –** vrací požadovaná velikost v bajtech cílový řetězec. Pokud **wcstombs –** nejde převést na vícebajtový znak, široký znak, zaznamená se vrátí hodnotu -1 přetypován na typ **size_t** a nastaví **errno** k **EILSEQ** .

## <a name="remarks"></a>Poznámky

**Wcstombs –** funkce převede řetězec širokých znaků, na které odkazuje *wcstr* na odpovídající vícebajtových znaků a ukládá výsledky *mbstr* pole. *Počet* parametr označuje maximální počet bajtů, které mohou být uloženy ve vícebajtové výstupním řetězci (tj, velikost *mbstr*). Obecně platí není znám, kolik bajtů se bude vyžadovat při převodu řetězce širokého znaku. Některé širokých znaků bude vyžadovat jenom jeden bajt ve výstupním řetězci; jiná vyžadují dva. Pokud existují dva bajty v řetězci vícebajtové výstup pro každý široký znak ve vstupním řetězci (včetně širokého znaku null), výsledek je zaručeno, že přizpůsobit.

Pokud **wcstombs –** zaznamená prázdný znak širokého znaku (L '\0') před nebo po *počet* dojde, převede ho 8 bitů 0 a zastaví. Proto vícebajtové znakové řetězce na *mbstr* je zakončený hodnotou null jenom v případě **wcstombs –** během převodu dojde prázdný znak širokého znaku. Pokud sekvence odkazované *wcstr* a *mbstr* překrývají, chování **wcstombs –** není definován.

Pokud *mbstr* argument je **NULL**, **wcstombs –** vrací požadovaná velikost v bajtech cílový řetězec.

**wcstombs –** ověří jeho parametry. Pokud *wcstr* je **NULL**, nebo pokud *počet* je větší než **INT_MAX**, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

**wcstombs –** používá aktuální národní prostředí pro všechna závislá chování; **_wcstombs_l –** je stejná s tím rozdílem, že používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ukazuje chování **wcstombs –** funkce.

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
