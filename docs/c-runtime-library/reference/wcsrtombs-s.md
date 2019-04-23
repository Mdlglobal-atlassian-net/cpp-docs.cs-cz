---
title: wcsrtombs_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: bd965271a65fa91b427c7af7bbd4173b129e1d8c
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124912"
---
# <a name="wcsrtombss"></a>wcsrtombs_s

Převeďte řetězec širokých znaků na jeho řetězcovou reprezentaci vícebajtového znaku. Verze [wcsrtombs –](wcsrtombs.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Velikost v bajtech převedený řetězec, včetně ukončovacího znaku null.

*mbstr*<br/>
Adresa vyrovnávací paměti pro výsledný řetězec převedený vícebajtového znaku.

*sizeInBytes*<br/>
Velikost v bajtech *mbstr* vyrovnávací paměti.

*wcstr*<br/>
Odkazuje na řetězec širokých znaků, který má být převeden.

*Počet*<br/>
Maximální počet bajtů, které mají být uloženy v *mbstr* vyrovnávací paměti, nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel **mbstate_t** převodu stavu objektu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, při selhání kód chyby.

|Chybový stav|Vrátí hodnotu a **errno**|
|---------------------|------------------------------|
|*mbstr* je **NULL** a *sizeInBytes* > 0|**EINVAL**|
|*wcstr* je **NULL**|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (není-li *počet* je **_TRUNCATE**; viz poznámky níže)|**ERANGE**|

Pokud některá z těchto podmínek dojde k je vyvolána výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, funkce vrátí chybový kód a nastaví **errno** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

**Wcsrtombs_s –** funkce převede řetězec širokých znaků, na které odkazuje *wcstr* na vícebajtové znaky, které jsou uloženy ve vyrovnávací paměti, na které odkazuje *mbstr*, použije Převod stavu součástí *mbstate*. Převod bude pokračovat pro jednotlivé znaky, dokud nebude splněna jedna z těchto podmínek:

- Zjistil se široké znaky null

- Zjistil se široký znak, který nejde převést

- Počet bajtů uložených v *mbstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec je vždy zakončený (i v případě chyby).

Pokud *počet* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), pak **wcsrtombs_s –** převede největší část řetězce, jako se vejde do cílové vyrovnávací paměti a stále ponechají prostor s hodnotou Null ukončovací znak.

Pokud **wcsrtombs_s –** úspěšně převede zdrojový řetězec uloží velikost v bajtech převedený řetězec, včetně ukončovacího znaku null do  *&#42;pReturnValue* (k dispozici  *pReturnValue* není **NULL**). K tomu dojde i v případě, *mbstr* argument je **NULL** a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *mbstr* je **NULL**, *počet* se ignoruje.

Pokud **wcsrtombs_s –** nejde převést na vícebajtový znak, široký znak, zaznamená se vloží hodnota -1  *\*pReturnValue*, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví **errno** k **EILSEQ**a vrátí **EILSEQ**.

Pokud sekvence odkazované *wcstr* a *mbstr* překrývají, chování **wcsrtombs_s –** není definován. **wcsrtombs_s –** vliv podle kategorie LC_TYPE aktuálního národního prostředí.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* nepřekrývají a že *počet* správně odráží počet širokých znaků pro převod.

**Wcsrtombs_s –** funkce se liší od [wcstombs_s – _wcstombs_s_l –](wcstombs-s-wcstombs-s-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány. Například byste použili aplikaci **wcsrlen** spíše než **wcslen –**, pokud je následných volání **wcsrtombs_s –** používaly místo **wcstombs_s –**.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Wcsrtombs_s –** funkce je bezpečné s více vlákny za předpokladu, žádné funkce v aktuálním vlákně volá **setlocale** při provádění této funkce a *mbstate* má hodnotu null.

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

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
