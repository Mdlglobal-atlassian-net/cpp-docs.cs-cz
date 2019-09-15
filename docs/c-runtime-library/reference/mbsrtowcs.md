---
title: mbsrtowcs
ms.date: 11/04/2016
api_name:
- mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: de7b25ea8a520dfe2c9cb26ec8989624b670dcb9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952052"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Převede vícebajtový řetězec znaků v aktuálním národním prostředí na odpovídající řetězec s velkým počtem znaků s možností restartu uprostřed vícebajtového znaku. K dispozici je bezpečnější verze této funkce; viz [mbsrtowcs_s](mbsrtowcs-s.md).

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
Adresa pro uložení výsledného převedeného řetězce velkých znaků.

*mbstr*<br/>
Nepřímý ukazatel na umístění vícebajtového řetězce znaků, který má být převeden.

*výpočtu*<br/>
Maximální počet znaků (není bajtů), který se má převést a uložit v *wcstr*.

*mbstate*<br/>
Ukazatel na objekt stavu převodu **mbstate_t** . Pokud je tato hodnota ukazatel s hodnotou null, je použit statický objekt stavu převodu. Vzhledem k tomu, že interní objekt **mbstate_t** není bezpečný pro přístup z více vláken, doporučujeme vždy předat vlastní parametr *mbstate* .

## <a name="return-value"></a>Návratová hodnota

Vrátí počet převedených znaků, včetně ukončujícího znaku null, pokud existuje. Vrátí (size_t) (-1), pokud došlo k chybě, a nastaví **errno** na EILSEQ.

## <a name="remarks"></a>Poznámky

Funkce **mbsrtowcs** převede řetězec vícebajtových znaků, na které se nepřímo odkazovalo na *mbstr*, do velkých znaků uložených ve vyrovnávací paměti, na které ukazuje *wcstr*, pomocí stavu převodu obsaženého v *mbstate*. Převod pro každý znak pokračuje, dokud není nalezen ukončovací znak null, který nesouhlasí s platným znakem v aktuálním národním prostředím, nebo dokud nejsou znaky *Count* veden. Pokud **mbsrtowcs** narazí na vícebajtový znak null (' \ 0 ') buď před, nebo pokud dojde k *výpočtu* , převede ho na 16bitový ukončující znak null a zastaví se.

Proto je řetězec s velkým znakem na *wcstr* zakončený hodnotou null pouze v případě, že při převodu dojde v **mbsrtowcs** k vícebajtovém znaku null. Pokud se sekvence, na které ukazuje *mbstr* a *wcstr* , překrývají, chování **mbsrtowcs** není definováno. **mbsrtowcs** je ovlivněna kategorií LC_TYPE aktuálního národního prostředí.

Funkce **mbsrtowcs** se od jejího spuštění liší od [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) . Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí.  Například aplikace by měla používat **mbsrlen** namísto **mbslen**, pokud je místo **mbstowcs**použito následné volání **mbsrtowcs** .

Pokud *wcstr* není ukazatel s hodnotou null, je objekt ukazatele, na který odkazuje *mbstr* , přiřazen ukazatel s hodnotou null, pokud se převod zastavil, protože bylo dosaženo ukončujícího znaku null. V opačném případě se jim přiřadí adresa hned za poslední vícebajtový znak, pokud nějaký existuje. To umožňuje následné volání funkce pro restartování převodu tam, kde bylo toto volání zastaveno.

Pokud je argument *wcstr* ukazatel s hodnotou null, je argument *Count* ignorován a **mbsrtowcs** vrátí požadovanou velikost pro cílový řetězec v různých znacích. Pokud je *mbstate* ukazatel s hodnotou null, funkce používá statický objekt stavu konverze **mbstate_t** , který není bezpečný pro přístup z více vláken. Pokud znak sekvence *mbstr* neobsahuje odpovídající vícebajtovou reprezentaci znaků, je vrácena znak-1 a **errno** je nastaven na hodnotu **EILSEQ**.

Pokud je ukazatel s hodnotou null *mbstr* ISA, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí-1.

V C++systému má tato funkce přetížení šablony, které vyvolá novější a zabezpečený protějšek této funkce. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

Funkce **mbsrtowcs** je vláknově bezpečná, dokud žádná funkce v aktuálním vlákně nevolá funkci **setlocale** , pokud je tato funkce prováděna a argument *mbstate* není ukazatel s hodnotou null.

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
