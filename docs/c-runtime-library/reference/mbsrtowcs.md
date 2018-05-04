---
title: mbsrtowcs – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccb5bda16238888905678ffb3b6de01b93555ad0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Převede řetězec vícebajtových znaků v aktuální národní prostředí na odpovídající široká znaková řetězec pomocí funkce restartování uprostřed vícebajtových znaků. Bezpečnější verze této funkce je k dispozici. v tématu [mbsrtowcs_s –](mbsrtowcs-s.md).

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
Adres výsledný řetězec převedený široká znaková uložit.

*mbstr*<br/>
Nepřímý odkaz na umístění vícebajtový řetězec k převedení.

*Počet*<br/>
Maximální počet znaků (ne v bajtech) můžete převést a uložit do *wcstr*.

*mbstate*<br/>
Ukazatel na **mbstate_t** převodu stavu objektu. Pokud tato hodnota je ukazatel s hodnotou null, použije se objekt statické vnitřní převod stavu. Protože interní **mbstate_t** objekt není bezpečné pro přístup z více vláken, doporučujeme, aby vždy předáte vlastní *mbstate* parametr.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků úspěšně převést, není včetně ukončující znak hodnoty null, pokud existuje. Vrátí (Pokud došlo k chybě a nastaví size_t)(-1) **errno** k eilseq –.

## <a name="remarks"></a>Poznámky

**Mbsrtowcs –** funkce převede řetězec vícebajtové znaky, na kterou nepřímo odkazuje *mbstr*, do široké znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje *wcstr*, pomocí použití stavu převod obsažené v *mbstate*. Převod pokračuje pro každý znak až do buď ukončující null vícebajtových znaků bez vícebajtové pořadí, které neodpovídá platný znak v aktuální národní prostředí je zjištěna, nebo dokud *počet* byla převedena znaků. Pokud **mbsrtowcs –** zaznamená vícebajtových znaků null (\0) před nebo po *počet* dojde, se převede na 16bitové ukončující znak hodnoty null a zastaví.

Proto široká znaková řetězce na *wcstr* je ukončené hodnotou null jenom v případě **mbsrtowcs –** vícebajtových znaků hodnotu null, zaznamená při převodu. Pokud daná pořadí na kterou odkazuje *mbstr* a *wcstr* překrývají, chování **mbsrtowcs –** není definován. **mbsrtowcs –** je ovlivňován LC_TYPE kategorii aktuální národní prostředí.

**Mbsrtowcs –** funkce se liší od [mbstowcs –, _mbstowcs_l –](mbstowcs-mbstowcs-l.md) podle jeho restartability. Stav převodu je uložený ve *mbstate* pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování.  Například by měla použít aplikace **mbsrlen** místo **mbslen –**, pokud následných volání **mbsrtowcs –** se používá místo **mbstowcs –**.

Pokud *wcstr* ukazatel s hodnotou null, není objekt ukazatel na kterou odkazuje *mbstr* je přiřazen ukazatele null, pokud převod zastavena, protože bylo dosaženo ukončující znak hodnoty null. Pokud existuje, jinak hodnota je přiřazen pouze posledních adresu převést poslední vícebajtových znaků. To umožňuje volání funkce následné restartování převodu, kde byla zastavena toto volání.

Pokud *wcstr* argument je ukazatel s hodnotou null, *počet* argument je ignorován a **mbsrtowcs –** vrátí požadovaná velikost široké znaky pro cílový řetězec. Pokud *mbstate* je ukazatel s hodnotou null, funkce, která používá interní není bezpečná pro přístup z více vláken statického **mbstate_t** převodu stavu objektu. Pokud sekvence znaků *mbstr* nemá odpovídající vícebajtových reprezentace znak, je vrácen -1 a **errno** je nastaven na **eilseq –**.

Pokud *mbstr* ukazatele null isa, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí hodnotu -1.

Tato funkce v jazyce C++ má šabloně přetížení, které vyvolá novější a zabezpečené protějšku této funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Mbsrtowcs –** tak dlouho, dokud volání funkce neexistuje v aktuální vlákno je funkce s více vlákny bezpečné **setlocale** tak dlouho, dokud tato funkce je prováděna a *mbstate* argument není nulový ukazatel.

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
