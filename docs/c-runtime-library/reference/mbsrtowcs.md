---
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 509046e1c55d89cd78b09076838983691423a1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338885"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Převede vícebajtový znakový řetězec v aktuálním národním prostředí na odpovídající široký řetězec znaků se schopností restartování uprostřed vícebajtového znaku. K dispozici je bezpečnější verze této funkce. viz [mbsrtowcs_s](mbsrtowcs-s.md).

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
Adresa pro uložení výsledného převedeného širokého znakového řetězce.

*mbstr*<br/>
Nepřímý ukazatel na umístění vícebajtového znakového řetězce, který chcete převést.

*Počet*<br/>
Maximální počet znaků (nikoli bajtů) pro převod a uložení v *souboru wcstr*.

*mbstate*<br/>
Ukazatel na **objekt stavu mbstate_t** převodu. Pokud je tato hodnota ukazatelem null, použije se statický objekt stavu vnitřního převodu. Vzhledem k tomu, že vnitřní **mbstate_t** objekt není bezpečný pro přístup z více vláken, doporučujeme vždy předat vlastní parametr *mbstate.*

## <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků, které byly úspěšně převedeny, bez případného ukončujícího znaku null. Vrátí (size_t)(-1) pokud došlo k chybě a nastaví **errno** na EILSEQ.

## <a name="remarks"></a>Poznámky

Funkce **mbsrtowcs** převede řetězec vícebajtových znaků nepřímo nasazených *pomocí mbstr*na široké znaky uložené ve vyrovnávací paměti, na kterou se vztahuje *funkce wcstr*, pomocí stavu převodu obsaženého v *mbstate*. Převod pokračuje pro každý znak, dokud není zjištěn ukončující vícebajtový znak null, vícebajtová sekvence, která neodpovídá platnému znaku v aktuálním národním prostředí, nebo dokud nejsou převedeny znaky *počtu.* Pokud **mbsrtowcs** narazí na vícebajtový znak null (\0') před nebo při *počítání,* převede jej na 16bitový ukončující znak null a zastaví se.

Široký řetězec znaků na *wcstr* je tedy null ukončena pouze v případě, **že mbsrtowcs** narazí vícebajtový znak null během převodu. Pokud se sekvence, na které se překrývají *nástroje mbstr* a *wcstr,* překrývají, chování **mbsrtowcs** není definováno. **Mbsrtowcs** je ovlivněna LC_TYPE kategorie aktuální národní prostředí.

Funkce **mbsrtowcs** se liší od [funkce mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) jeho restartovatelností. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí.  Aplikace by například měla používat **mbsrlen** místo **mbslen**, pokud je použito následné volání **mbsrtowcs** namísto **mbstowcs**.

Pokud *wcstr* není ukazatel null, je objektu ukazatele, na který odkazuje *mbstr,* přiřazen ukazatel null, pokud byl převod zastaven, protože bylo dosaženo ukončujícího znaku null. V opačném případě je přiřazena adresa těsně za poslední vícebajtový znak převeden, pokud existuje. To umožňuje následné volání funkce restartovat převod, kde toto volání zastaveno.

Pokud je argument *wcstr* nulový ukazatel, argument *počet* je ignorován a **mbsrtowcs** vrátí požadovanou velikost širokých znaků pro cílový řetězec. Pokud *mbstate* je ukazatel null, funkce používá objekt **statického** mbstate_t stavu převodu, který není bezpečný pro přístup z více vláken. Pokud sekvence znaků *mbstr* nemá odpovídající vícebajtovou reprezentaci znaků, je vrácena -1 a **errno** je nastaveno na **EILSEQ**.

Pokud *mbstr* isa null ukazatel, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí -1.

V jazyce C++ má tato funkce přetížení šablony, která vyvolá novější, bezpečný protějšek této funkce. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Funkce **mbsrtowcs** je bezpečná pro více vláken, pokud žádná funkce v aktuálním vlákně volá **setlocale,** pokud je tato funkce spuštěna a argument *mbstate* není nulovým ukazatelem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
