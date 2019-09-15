---
title: mbsrtowcs_s
ms.date: 11/04/2016
api_name:
- mbsrtowcs_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: d79cceaf923c1da126a1d133a8d2eb8752883457
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952104"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Převede vícebajtový řetězec znaků v aktuálním národním prostředí na jeho řetězcovou reprezentaci řetězce s velkým znakem. Verze [mbsrtowcs](mbsrtowcs.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Adresa vyrovnávací paměti pro uložení výsledného převedeného řetězce velkých znaků

*sizeInWords*<br/>
Velikost *wcstr* v slovech (v různých znacích).

*mbstr*<br/>
Nepřímý ukazatel na umístění vícebajtového řetězce znaků, který má být převeden.

*výpočtu*<br/>
Maximální počet velkých znaků, které se mají Uložit do vyrovnávací paměti *wcstr* , včetně ukončující hodnoty null nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel na objekt stavu převodu **mbstate_t** . Pokud je tato hodnota ukazatel s hodnotou null, je použit statický objekt stavu převodu. Vzhledem k tomu, že interní objekt **mbstate_t** není bezpečný pro přístup z více vláken, doporučujeme vždy předat vlastní parametr *mbstate* .

## <a name="return-value"></a>Návratová hodnota

Nula, pokud je převod úspěšný, nebo chybový kód při selhání.

|Chybový stav|Návratová hodnota a **errno**|
|---------------------|------------------------------|
|*wcstr* je ukazatel s hodnotou null a *sizeInWords* > 0|**EINVAL**|
|*mbstr* je ukazatel s hodnotou null.|**EINVAL**|
|Řetězec nepřímo odkazoval na *mbstr* obsahuje vícebajtovou sekvenci, která není platná pro aktuální národní prostředí.|**EILSEQ**|
|Cílová vyrovnávací paměť je příliš malá, aby obsahovala převedený řetězec (Pokud není *počet* **_TRUNCATE**; Další informace naleznete v tématu poznámky).|**ERANGE**|

Pokud dojde k některé z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce kód chyby a nastaví **errno** , jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **mbsrtowcs_s** převede řetězec vícebajtových znaků, na které se nepřímo odkazovalo na *mbstr* , do velkých znaků uložených ve vyrovnávací paměti, na které ukazuje *wcstr*, pomocí stavu převodu obsaženého v *mbstate*. Převod bude pro každý znak pokračovat, dokud nebude splněna jedna z těchto podmínek:

- Byl zjištěn vícebajtový znak null.

- Zjistil se neplatný vícebajtový znak.

- Počet velkých znaků uložených ve vyrovnávací paměti *wcstr* se rovná *počtu*.

Cílový řetězec *wcstr* je vždy zakončený hodnotou null, a to i v případě chyby, pokud *wcstr* není ukazatel s hodnotou null.

Pokud *Count* je speciální hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** se převede jako velká část řetězce, která se vejde do cílové vyrovnávací paměti, a stále ponechává místo pro ukončovací znak null.

Pokud **mbsrtowcs_s** úspěšně převede zdrojový řetězec, umístí velikost do velkých písmen převedených řetězců a ukončovací znak null do  *&#42;pReturnValue*, zadaný *pReturnValue* není ukazatel s hodnotou null. K tomu dojde i v případě, že argument *wcstr* je ukazatel s hodnotou null a umožňuje určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud je *wcstr* ukazatel s hodnotou null, *počet* se ignoruje.

Pokud *wcstr* není ukazatel s hodnotou null, je objekt ukazatele, na který odkazuje *mbstr* , přiřazen ukazatel s hodnotou null, pokud se převod zastavil, protože bylo dosaženo ukončujícího znaku null. V opačném případě se jim přiřadí adresa hned za poslední vícebajtový znak, pokud nějaký existuje. To umožňuje následné volání funkce pro restartování převodu tam, kde bylo toto volání zastaveno.

Pokud je *mbstate* ukazatel s hodnotou null, je použit statický objekt stavu konverze interní **mbstate_t** knihovny. Vzhledem k tomu, že tento interní statický objekt není bezpečný pro přístup z více vláken, doporučujeme předat vlastní hodnotu *mbstate* .

Pokud **mbsrtowcs_s** narazí na vícebajtový znak, který není platný v aktuálním národním prostředí, převede-1 v  *&#42;pReturnValue*, nastaví cílovou vyrovnávací paměť *wcstr* na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které ukazuje *mbstr* a *wcstr* , překrývají, chování **mbsrtowcs_s** není definováno. **mbsrtowcs_s** je ovlivněna kategorií LC_TYPE aktuálního národního prostředí.

> [!IMPORTANT]
> Zajistěte, aby se *wcstr* a *mbstr* nepřekrývaly, a tento *počet* správně odráží počet vícebajtových znaků, které se mají převést.

Funkce **mbsrtowcs_s** se od jejího spuštění liší od [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) . Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí. Například aplikace by měla používat **mbsrlen** namísto **mbslen**, pokud je místo **mbstowcs_s**použito následné volání **mbsrtowcs_s** .

V C++systému je použití této funkce zjednodušeno pomocí přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují požadavek na zadání velikosti argumentu) a můžou automaticky nahradit starší nezabezpečené funkce pomocí jejich novějších a zabezpečených protějšků. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

Funkce **mbsrtowcs_s** je vláknově bezpečná, pokud žádná funkce v aktuálním vlákně nevolá funkci **setlocale** , pokud je tato funkce spuštěná a argument *mbstate* není ukazatel s hodnotou null.

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
