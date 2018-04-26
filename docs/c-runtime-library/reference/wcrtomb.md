---
title: wcrtomb – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wcrtomb
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
- wcrtomb
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7618900dd313a31f7d514698c0ac7a670446d96d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="wcrtomb"></a>wcrtomb

Široká znaková převeďte do reprezentace vícebajtových znaků. Bezpečnější verze této funkce je k dispozici. v tématu [wcrtomb_s –](wcrtomb-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Převést výsledné vícebajtových znaků.

*wchar*<br/>
Široká znaková převést.

*mbstate*<br/>
Ukazatel na **mbstate_t** objektu.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů požadovaných představující převedený vícebajtových znaků, jinak hodnota -1 Pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**Wcrtomb –** funkce převede široký znak, od ve stavu zadanou konverzi obsažené v *mbstate*, z hodnoty obsažené v *wchar*, do Adresa reprezentována *mbchar*. Vrácená hodnota je počet bajtů požadovaných k reprezentaci odpovídající vícebajtových znaků, ale nebudou vráceny více než **mb_cur_max –** bajtů.

Pokud *mbstate* má hodnotu null, interní **mbstate_t** objekt, který obsahuje stav převodu *mbchar* se používá. Pokud sekvence znaků *wchar* nemá odpovídající vícebajtových reprezentace znak, je vrácen -1 a **errno** je nastaven na **eilseq –**.

**Wcrtomb –** funkce se liší od [wctomb –, _wctomb_l –](wctomb-wctomb-l.md) podle jeho restartability. Stav převodu je uložený ve *mbstate* pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování. Například byste použili aplikaci **wcsrlen** místo **wcsnlen –**, pokud následných volání **wcsrtombs –** používaly místo **wcstombs –**.

Tato funkce v jazyce C++ má šabloně přetížení, které vyvolá novější a zabezpečené svými protějšky této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcrtomb –** tak dlouho, dokud volání funkce neexistuje v aktuální vlákno je funkce s více vlákny bezpečné **setlocale** během této funkce je prováděna a při *mbstate* má hodnotu null.

## <a name="example"></a>Příklad

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
