---
title: mbsrtowcs
ms.date: 11/04/2016
apiname:
- mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 2bc0c8c9e2d871b6d1748c42dc02c627244dbf69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597142"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Převede řetězec vícebajtového znaku v aktuální národní prostředí na odpovídající řetězec širokých znaků, s možností objektu restartování uprostřed vícebajtového znaku. Bezpečnější verze této funkce je k dispozici. Zobrazit [mbsrtowcs_s –](mbsrtowcs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*wcstr*<br/>
Adresa pro uložení výsledný převést řetězec širokých znaků.

*mbstr*<br/>
Nepřímý odkaz na umístění řetězec vícebajtový znak pro převod.

*Počet*<br/>
Maximální počet znaků (ne v bajtech) můžete převést a uložit do *wcstr*.

*mbstate*<br/>
Ukazatel **mbstate_t** převodu stavu objektu. Pokud tato hodnota je ukazatel s hodnotou null, použije se statické interní převodu stav objektu. Protože vnitřní **mbstate_t** objektu není bezpečná pro vlákno, doporučujeme vám vždy předání vlastní *mbstate* parametru.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků úspěšně převeden, bez ukončujícího znaku null, pokud existuje. Vrátí (Pokud došlo k chybě a nastaví size_t)(-1) **errno** k EILSEQ.

## <a name="remarks"></a>Poznámky

**Mbsrtowcs –** funkce převede řetězec vícebajtových znaků nepřímo odkazované *mbstr*, do široké znaky, které jsou uloženy ve vyrovnávací paměti, na které odkazuje *wcstr*, použití stavu převodu součástí *mbstate*. Převod bude pokračovat pro jednotlivé znaky až do obou ukončujícího znaku null vícebajtového znaku, nalezen vícebajtové sekvence, která neodpovídá platnému znaku v aktuálním národním prostředí, nebo dokud *počet* byly převedeny znaků. Pokud **mbsrtowcs –** zaznamená vícebajtový znak null ('\0') před nebo po *počet* dojde, převede ho na 16-bit ukončující znak null a zastaví.

Díky tomu se řetězec širokých znaků na *wcstr* je zakončený hodnotou null jenom v případě **mbsrtowcs –** během převodu dojde vícebajtového znaku null. Pokud sekvence odkazované *mbstr* a *wcstr* překrývají, chování **mbsrtowcs –** není definován. **mbsrtowcs –** vliv podle kategorie LC_TYPE aktuálního národního prostředí.

**Mbsrtowcs –** funkce se liší od [mbstowcs _mbstowcs_l –](mbstowcs-mbstowcs-l.md) podle jeho restartability. Stav převodu je uložen v *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány.  Například by měla aplikace použít **mbsrlen** místo **mbslen –**, pokud je následných volání **mbsrtowcs –** se použije namísto **mbstowcs**.

Pokud *wcstr* není nulový ukazatel, ukazatel objektu odkazované *mbstr* se přiřadí ukazatel s hodnotou null, pokud převod zastavena, protože bylo dosaženo ukončujícího znaku null. V opačném případě je přiřazena adresa pouze posledních převést poslední vícebajtového znaku, případné. To umožňuje volání další funkce restartovat převod, kde toto volání zastavení.

Pokud *wcstr* argument je ukazatel s hodnotou null, *počet* argument ignorován a **mbsrtowcs –** vrátí požadovaná velikost pro cílový řetězec širokých znaků. Pokud *mbstate* je ukazatel s hodnotou null, funkce, která používá interní vláknově bezpečné statické **mbstate_t** převodu stavu objektu. Pokud sekvence znaků *mbstr* nemá odpovídající vícebajtové reprezentace znaku, vrátí se -1 a **errno** je nastavena na **EILSEQ**.

Pokud *mbstr* vyvolána isa ukazatel s hodnotou null, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

V jazyce C++ má tato funkce přetížení šablon, které vyvolá novější, zabezpečené protějšky této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Mbsrtowcs –** funkce je bezpečné s více vlákny za předpokladu, žádné funkce v aktuálním vlákně volá **setlocale** tak dlouho, dokud tato funkce provádí a *mbstate* argument není ukazatel s hodnotou null.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
