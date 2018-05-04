---
title: wcsrtombs – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcsrtombs
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
- wcsrtombs
dev_langs:
- C++
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2ea0252714803fe8cad48635486d2011275407
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="wcsrtombs"></a>wcsrtombs

Široká znaková řetězec převeďte na řetězcovou reprezentaci vícebajtových znaků. Bezpečnější verze této funkce je k dispozici. v tématu [wcsrtombs_s –](wcsrtombs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Výsledná převést vícebajtový řetězec adresu umístění.

*wcstr*<br/>
Nepřímo odkazuje na umístění široká znaková řetězce, který má být převeden.

*Počet*<br/>
Počet znaků, které má být převeden.

*mbstate*<br/>
Ukazatel na **mbstate_t** převodu stavu objektu.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů úspěšně převést, včetně není null ukončení null bajtů (pokud existuje), jinak hodnota -1, pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

**Wcsrtombs –** funkce převede řetězec z široké znaky, počínaje zadanou konverzi stav obsažené v *mbstate*, z nepřímých hodnot nastavena v *wcstr*, do adresu *mbstr*. Převod bude pokračovat pro každý znak dokud: po došlo s hodnotou null se ukončuje široká znaková, když je zjištěna bez odpovídajícího znaku nebo pokud další znak by překročilo limit obsažené v *počet*. Pokud **wcsrtombs –** zaznamená znak hodnoty null široká charakterová (L '\0') před nebo po *počet* dojde, převede ji 0 8bitové a zastaví se.

Proto řetězce vícebajtových znaků na *mbstr* je ukončené hodnotou null jenom v případě **wcsrtombs –** širokého znaku prázdný znak, zaznamená při převodu. Pokud daná pořadí na kterou odkazuje *wcstr* a *mbstr* překrývají, chování **wcsrtombs –** není definován. **wcsrtombs –** je ovlivňován LC_TYPE kategorii aktuální národní prostředí.

**Wcsrtombs –** funkce se liší od [wcstombs –, _wcstombs_l –](wcstombs-wcstombs-l.md) podle jeho restartability. Stav převodu je uložený ve *mbstate* pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování.  Například byste použili aplikaci **wcsrlen** místo **wcsnlen –**, pokud následných volání **wcsrtombs –** používaly místo **wcstombs –**.

Pokud *mbstr* argument je **NULL**, **wcsrtombs –** vrátí požadovaná velikost v bajtech cílový řetězec. Pokud *mbstate* má hodnotu null, interní **mbstate_t** převod stavu se používá. Pokud sekvence znaků *wchar* nemá odpovídající vícebajtových reprezentace znak, je vrácen -1 a **errno** je nastaven na **eilseq –**.

Tato funkce v jazyce C++ má šabloně přetížení, které vyvolá novější a zabezpečené protějšku této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcsrtombs –** tak dlouho, dokud volání funkce neexistuje v aktuální vlákno je funkce s více vlákny bezpečné **setlocale** průběhu této funkce je provádění a *mbstate* není null.

## <a name="example"></a>Příklad

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
