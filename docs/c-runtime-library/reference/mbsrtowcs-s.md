---
title: mbsrtowcs_s
ms.date: 11/04/2016
apiname:
- mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: a935b5181078f3b08ba5f2f89c581ed8cce8ded5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156665"
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

Převeďte řetězec vícebajtového znaku v aktuální národní prostředí na jeho řetězcovou reprezentaci širokého znaku. Verze [mbsrtowcs –](mbsrtowcs.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Počet znaků, převodu.

*wcstr*<br/>
Adresa vyrovnávací paměť pro ukládání výsledný převést řetězec širokých znaků.

*sizeInWords*<br/>
Velikost *wcstr* slovy (širokých znaků).

*mbstr*<br/>
Nepřímý odkaz na umístění vícebajtový řetězec, který má být převeden.

*Počet*<br/>
Maximální počet širokých znaků k ukládání *wcstr* vyrovnávací paměti, bez ukončujícího znaku null, nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel **mbstate_t** převodu stavu objektu. Pokud tato hodnota je ukazatel s hodnotou null, použije se statické interní převodu stav objektu. Protože vnitřní **mbstate_t** objektu není bezpečná pro vlákno, doporučujeme vám vždy předání vlastní *mbstate* parametru.

## <a name="return-value"></a>Návratová hodnota

Nula v případě, že převod je úspěšný, nebo při selhání kód chyby.

|Chybový stav|Vrátí hodnotu a **errno**|
|---------------------|------------------------------|
|*wcstr* je ukazatel s hodnotou null a *sizeInWords* > 0|**EINVAL**|
|*mbstr* je ukazatel s hodnotou null|**EINVAL**|
|Řetězec nepřímo odkazované *mbstr* obsahuje vícebajtové sekvence, která není platná pro aktuální národní prostředí.|**EILSEQ**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (není-li *počet* je **_TRUNCATE**; Další informace viz poznámky)|**ERANGE**|

Pokud dojde k jedné z těchto podmínek, je vyvolána výjimku neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, funkce vrátí chybový kód a nastaví **errno** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

**Mbsrtowcs_s –** funkce převede řetězec vícebajtových znaků nepřímo odkazované *mbstr* do široké znaky, které jsou uloženy ve vyrovnávací paměti, na které odkazuje *wcstr*, použití stavu převodu součástí *mbstate*. Převod bude pokračovat pro jednotlivé znaky, dokud nebude splněna jedna z těchto podmínek:

- Zjistil se vícebajtový znak null

- Zjistil se neplatný vícebajtový znak

- Počet širokých znaků, které jsou uložené v *wcstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec *wcstr* je vždy zakončený hodnotou null, i v případě chybu, pokud *wcstr* je ukazatel s hodnotou null.

Pokud *počet* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s –** převede největší část řetězce, jako se vejde do cílové vyrovnávací paměti a stále ponechají prostor s hodnotou Null ukončovací znak.

Pokud **mbsrtowcs_s –** úspěšně převede zdrojový řetězec, uloží je v široké znaky převedený řetězec a ukončovacího znaku null do velikosti  *&#42;pReturnValue*, k dispozici  *pReturnValue* není ukazatel s hodnotou null. K tomu dojde i v případě, *wcstr* argument je ukazatel s hodnotou null a vám umožní určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *wcstr* je ukazatel s hodnotou null, *počet* se ignoruje.

Pokud *wcstr* není nulový ukazatel, ukazatel objektu odkazované *mbstr* se přiřadí ukazatel s hodnotou null, pokud převod zastavena, protože bylo dosaženo ukončujícího znaku null. V opačném případě je přiřazena adresa pouze posledních převést poslední vícebajtového znaku, případné. To umožňuje volání další funkce restartovat převod, kde toto volání zastavení.

Pokud *mbstate* je ukazatel s hodnotou null, interní knihovny **mbstate_t** převodu stavu statický objekt se používá. Vzhledem k tomu, že tato interní statického objektu není bezpečná pro vlákno, doporučujeme, že předáte vlastní *mbstate* hodnotu.

Pokud **mbsrtowcs_s –** zaznamená vícebajtového znaku, který není platný v aktuálním národním prostředí, -1 se vloží do  *&#42;pReturnValue*, nastaví cílové vyrovnávací paměti *wcstr* na prázdný řetězec, nastaví **errno** k **EILSEQ**a vrátí **EILSEQ**.

Pokud sekvence odkazované *mbstr* a *wcstr* překrývají, chování **mbsrtowcs_s –** není definován. **mbsrtowcs_s –** vliv podle kategorie LC_TYPE aktuálního národního prostředí.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* nepřekrývají a že *počet* správně odráží číslo k převodu vícebajtových znaků.

**Mbsrtowcs_s –** funkce se liší od [mbstowcs_s _mbstowcs_s_l –](mbstowcs-s-mbstowcs-s-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány. Například by měla aplikace použít **mbsrlen** místo **mbslen –**, pokud je následných volání **mbsrtowcs_s –** se použije namísto **mbstowcs_s**.

V jazyce C++ je použití této funkce zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (eliminuje požadavek na zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky pomocí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Mbsrtowcs_s –** funkce je s více vlákny bezpečné, pokud žádné funkce v aktuální vlákno vyvolá **setlocale** tak dlouho, dokud tato funkce provádí a *mbstate* argument je není ukazatel s hodnotou null.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
