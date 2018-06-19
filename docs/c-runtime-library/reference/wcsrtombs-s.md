---
title: wcsrtombs_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcsrtombs_s
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
- wcsrtombs_s
dev_langs:
- C++
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94e27965d1660f4c344d0026bbfce8685a935c7a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417298"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

Široká znaková řetězec převeďte na řetězcovou reprezentaci vícebajtových znaků. Verzi [wcsrtombs –](wcsrtombs.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Počet znaků převést.

*mbstr*<br/>
Adresa vyrovnávací paměti pro výsledný řetězec převedený vícebajtových znaků.

*sizeInBytes*<br/>
Velikost v bajtech *mbstr* vyrovnávací paměti.

*wcstr*<br/>
Odkazuje na široká znaková řetězec, který má být převeden.

*Počet*<br/>
Maximální počet bajtů, které mají být uloženy v *mbstr* vyrovnávací paměti, nebo [_truncate –](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel na **mbstate_t** převodu stavu objektu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

|Chybový stav|Vrátí hodnotu a **kód chyby**|
|---------------------|------------------------------|
|*mbstr* je **NULL** a *sizeInBytes* > 0|**EINVAL –**|
|*wcstr* je **hodnotu NULL.**|**EINVAL –**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (Pokud *počet* je **_truncate –**; viz poznámky níže)|**ERANGE –**|

Pokud dojde k některé z těchto podmínek, jak je popsáno v je vyvolána výjimka neplatný parametr [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, funkce vrátí kód chyby a nastaví **errno** , které je uvedené v tabulce.

## <a name="remarks"></a>Poznámky

**Wcsrtombs_s –** funkce převede řetězec z široké znaky, na kterou odkazuje *wcstr* do více-bajtové znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje *mbstr*pomocí Převod stavu obsažené v *mbstate*. Převod bude pokračovat pro jednotlivé znaky, dokud je splněna jedna z těchto podmínek:

- Vyskytl se null široká znaková

- Vyskytl se široká znaková, kterou nelze převést

- Počet bajtů, které jsou uložené v *mbstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec je vždy ukončený hodnotou null (i v případě chyby).

Pokud *počet* je speciální hodnota [_truncate –](../../c-runtime-library/truncate.md), pak **wcsrtombs_s –** převede co nejvíc řetězec jako bude začlenit do cílové vyrovnávací paměti, a přesto nechat místnosti s hodnotou Null ukončovací znak.

Pokud **wcsrtombs_s –** úspěšně převede zdrojový řetězec, uloží je velikost v bajtech převedený řetězec, včetně null ukončení do  *&#42;pReturnValue* (zadat  *pReturnValue* není **NULL**). K tomu dojde i v případě *mbstr* argument je **NULL** a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *mbstr* je **NULL**, *počet* je ignorována.

Pokud **wcsrtombs_s –** zaznamená široká znaková nelze převést na vícebajtových znaků, odešle -1 do  *\*pReturnValue*, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví **errno** k **eilseq –** a vrátí **eilseq –**.

Pokud daná pořadí na kterou odkazuje *wcstr* a *mbstr* překrývají, chování **wcsrtombs_s –** není definován. **wcsrtombs_s –** je ovlivňován LC_TYPE kategorii aktuální národní prostředí.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odpovídá počtu široké znaky převést.

**Wcsrtombs_s –** funkce se liší od [wcstombs_s –, _wcstombs_s_l –](wcstombs-s-wcstombs-s-l.md) podle jeho restartability. Stav převodu je uložený ve *mbstate* pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování. Například byste použili aplikaci **wcsrlen** místo **wcslen –**, pokud následných volání **wcsrtombs_s –** používaly místo **wcstombs_s –**.

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcsrtombs_s –** tak dlouho, dokud volání funkce neexistuje v aktuální vlákno je funkce s více vlákny bezpečné **setlocale** průběhu této funkce je provádění a *mbstate* má hodnotu null.

## <a name="example"></a>Příklad

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

void main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
