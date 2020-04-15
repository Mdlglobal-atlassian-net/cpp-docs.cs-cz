---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338905"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Převeďte vícebajtový znakový řetězec v aktuálním národním prostředí na jeho širokou reprezentaci řetězce znaků. Verze [nástroje MBSRtowcs](mbsrtowcs.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

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
Počet převedených znaků.

*wcstr*<br/>
Adresa vyrovnávací paměti pro uložení výsledného převedeného řetězce celého znaku.

*sizeInWords*<br/>
Velikost *wcstr* ve slovech (široké znaky).

*mbstr*<br/>
Nepřímý ukazatel na umístění vícebajtového znakového řetězce, který má být převeden.

*Počet*<br/>
Maximální počet širokých znaků pro uložení do vyrovnávací paměti *wcstr,* bez ukončující hodnoty null nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel na **objekt stavu mbstate_t** převodu. Pokud je tato hodnota ukazatelem null, použije se statický objekt stavu vnitřního převodu. Vzhledem k tomu, že vnitřní **mbstate_t** objekt není bezpečný pro přístup z více vláken, doporučujeme vždy předat vlastní parametr *mbstate.*

## <a name="return-value"></a>Návratová hodnota

Nula, pokud je převod úspěšný, nebo kód chyby při selhání.

|Chybový stav|Vrácená hodnota a **chybné číslo**|
|---------------------|------------------------------|
|*wcstr* je ukazatel null a *sizeInWords* > 0|**EINVAL**|
|*mbstr* je nulový ukazatel|**EINVAL**|
|Řetězec nepřímo ukázal *podle mbstr* obsahuje vícebajtovou sekvenci, která není platná pro aktuální národní prostředí.|**EILSEQ**|
|Cílová vyrovnávací paměť je příliš malá na to, aby obsahovala převedený řetězec (pokud není **_TRUNCATE** *počet* ; další informace naleznete v tématu Poznámky)|**ERANGE**|

Pokud dojde k některé z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, funkce vrátí kód chyby a nastaví **errno,** jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **mbsrtowcs_s** převede řetězec vícebajtových znaků nepřímo nasazených *mbstr* na široké znaky uložené ve vyrovnávací paměti, na kterou se vztahuje *funkce wcstr*, pomocí stavu převodu obsaženého v *mbstate*. Převod bude pokračovat pro každý znak, dokud nebude splněna jedna z těchto podmínek:

- Je zjištěn vícebajtový znak null.

- Byl zjištěn neplatný vícebajtový znak.

- Počet širokých znaků uložených ve vyrovnávací paměti *wcstr* se rovná *počtu*.

Cílový řetězec *wcstr* je vždy null ukončen, i v případě chyby, pokud *wcstr* není nulový ukazatel.

Pokud *count* je zvláštní hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** převede tolik řetězce, jak se vejde do cílové vyrovnávací paměti, zatímco stále ponechává prostor pro null zakončení.

Pokud **mbsrtowcs_s** úspěšně převede zdrojový řetězec, umístí velikost v širokých znacích převedeného řetězce a zakončení null do *&#42;pReturnValue*, za předpokladu, že hodnota *pReturnValue* není ukazatelem null. K tomu dochází i v *případě, že argument wcstr* je ukazatel null a umožňuje určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud *wcstr* je ukazatel null, *počet* je ignorován.

Pokud *wcstr* není ukazatel null, je objektu ukazatele, na který odkazuje *mbstr,* přiřazen ukazatel null, pokud byl převod zastaven, protože bylo dosaženo ukončujícího znaku null. V opačném případě je přiřazena adresa těsně za poslední vícebajtový znak převeden, pokud existuje. To umožňuje následné volání funkce restartovat převod, kde toto volání zastaveno.

Pokud *mbstate* je ukazatel null, knihovna vnitřní **mbstate_t** stav převodu statický objekt se používá. Vzhledem k tomu, že tento vnitřní statický objekt není bezpečný pro přístup z více vláken, doporučujeme předat vlastní hodnotu *mbstate.*

Pokud **mbsrtowcs_s** narazí na vícebajtový znak, který není platný v aktuálním národním prostředí, vloží hodnotu -1 v *&#42;hodnota pReturnValue*, nastaví cílovou vyrovnávací paměť *wcstr* na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **Hodnotu EILSEQ**.

Pokud se sekvence, na které se překrývají *mbstr* a *wcstr,* chování **mbsrtowcs_s** není definováno. **mbsrtowcs_s** je ovlivněna LC_TYPE kategorie aktuální národní prostředí.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odráží počet vícebajtových znaků převést.

Funkce **mbsrtowcs_s** se liší od [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) svou restartovatelností. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí. Aplikace by například měla používat **mbsrlen** místo **mbslen**, pokud je místo **mbstowcs_s**použito následné volání **mbsrtowcs_s** .

V jazyce C++ je použití této funkce zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (odstranění požadavku na určení argumentu velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce pomocí jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Funkce **mbsrtowcs_s** je bezpečná pro více vláken, pokud žádná funkce v aktuálním vlákně volá **setlocale,** pokud je tato funkce spuštěna a argument *mbstate* není nulovým ukazatelem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
