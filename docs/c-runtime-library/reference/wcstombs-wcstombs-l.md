---
title: wcstombs –, _wcstombs_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wcstombs
- _wcstombs_l
dev_langs:
- C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 604ca2d2172e340459d7d5cbf406f01c484750ff
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l

Převede posloupnost široké znaky na odpovídající posloupnost více-bajtové znaky. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [wcstombs_s –, _wcstombs_s_l –](wcstombs-s-wcstombs-s-l.md).

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
Adresa posloupnost více-bajtové znaky.

*wcstr*<br/>
Adresa posloupnost široké znaky.

*Počet*<br/>
Maximální počet bajtů, které mohou být uloženy ve více-bajtové výstupní řetězec.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Pokud **wcstombs –** úspěšně převede vícebajtové řetězce, vrátí počet bajtů zapsaných do řetězce vícebajtových výstup, s výjimkou ukončující null (pokud existuje). Pokud *mbstr* argument je **NULL**, **wcstombs –** vrátí požadovaná velikost v bajtech cílový řetězec. Pokud **wcstombs –** zaznamená široká znaková nelze převést na vícebajtových znaků, vrátí hodnotu -1 přetypovat na typ **size_t –** a nastaví **errno** k **eilseq –** .

## <a name="remarks"></a>Poznámky

**Wcstombs –** funkce převede řetězec široká charakterová, na kterou odkazuje *wcstr* na odpovídající vícebajtových znaků a ukládá výsledky do *mbstr* pole. *Počet* určuje maximální počet bajtů, které mohou být uloženy v řetězci vícebajtové výstup (to znamená, velikost *mbstr*). Obecně platí není znám, kolik bajtů se bude vyžadovat při převodu řetězce široká charakterová. Některé široké znaky bude vyžadovat pouze jeden bajt do výstupního řetězce; jiné vyžadují dva. Pokud existují dva bajty v řetězci vícebajtové výstup pro každý široké znak ve vstupním řetězci (včetně široká znaková null), výsledek záruku.

Pokud **wcstombs –** zaznamená znak hodnoty null široká charakterová (L '\0') před nebo po *počet* dojde, převede ji 0 8bitové a zastaví se. Proto řetězce vícebajtových znaků na *mbstr* je ukončené hodnotou null jenom v případě **wcstombs –** širokého znaku prázdný znak, zaznamená při převodu. Pokud daná pořadí na kterou odkazuje *wcstr* a *mbstr* překrývají, chování **wcstombs –** není definován.

Pokud *mbstr* argument je **NULL**, **wcstombs –** vrátí požadovaná velikost v bajtech cílový řetězec.

**wcstombs –** ověří jeho parametry. Pokud *wcstr* je **NULL**, nebo pokud *počet* je větší než **INT_MAX**, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastaví funkci **errno** k **einval –** a vrátí hodnotu -1.

**wcstombs –** používá aktuální národní prostředí pro chování všech závislých na národním prostředí; **_wcstombs_l –** se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcstombs –**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program znázorňuje chování **wcstombs –** funkce.

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
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
