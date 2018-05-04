---
title: mbsrtowcs_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8885d11c7fca10c63077464020a8bbab2b6f3ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="mbsrtowcss"></a>mbsrtowcs_s

Převod řetězce vícebajtových znaků v aktuální národní prostředí na jeho široká znaková řetězcová reprezentace. Verzi [mbsrtowcs –](mbsrtowcs.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Počet znaků převést.

*wcstr*<br/>
Adresa vyrovnávací paměti k uložení výsledná převést řetězec široké znaků.

*sizeInWords*<br/>
Velikost *wcstr* v slova (široké znaky).

*mbstr*<br/>
Nepřímý odkaz na umístění řetězce vícebajtových znaků, který má být převeden.

*Počet*<br/>
Maximální počet široké znaky a uložit v *wcstr* vyrovnávací paměti není včetně ukončující null, nebo [_truncate –](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ukazatel na **mbstate_t** převodu stavu objektu. Pokud tato hodnota je ukazatel s hodnotou null, použije se objekt statické vnitřní převod stavu. Protože interní **mbstate_t** objekt není bezpečné pro přístup z více vláken, doporučujeme, aby vždy předáte vlastní *mbstate* parametr.

## <a name="return-value"></a>Návratová hodnota

Pokud převod úspěšný 0 pro nulu nebo kód chyby při selhání.

|Chybový stav|Vrátí hodnotu a **kód chyby**|
|---------------------|------------------------------|
|*wcstr* je ukazatel s hodnotou null a *sizeInWords* > 0|**EINVAL –**|
|*mbstr* je ukazatel s hodnotou null|**EINVAL –**|
|Řetězec nepřímo na kterou odkazuje *mbstr* obsahuje posloupnost vícebajtové, který není platný pro aktuální národní prostředí.|**EILSEQ –**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (Pokud *počet* je **_truncate –**; Další informace najdete v tématu poznámky)|**ERANGE –**|

Pokud dojde k některé z těchto podmínek, jak je popsáno v vyvolání výjimky neplatný parametr [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, funkce vrátí kód chyby a nastaví **errno** , které je uvedené v tabulce.

## <a name="remarks"></a>Poznámky

**Mbsrtowcs_s –** funkce převede řetězec vícebajtové znaky, na kterou nepřímo odkazuje *mbstr* do široké znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje *wcstr*, pomocí použití stavu převod obsažené v *mbstate*. Převod bude pokračovat pro jednotlivé znaky, dokud je splněna jedna z těchto podmínek:

- Vyskytl se vícebajtových znaků hodnotu null

- Je zjištěna neplatná vícebajtových znaků

- Počet široké znaky, které jsou uložené v *wcstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec *wcstr* je vždy ukončené hodnotou null i v případě chybu, pokud *wcstr* je ukazatel s hodnotou null.

Pokud *počet* je speciální hodnota [_truncate –](../../c-runtime-library/truncate.md), **mbsrtowcs_s –** převede co nejvíc řetězec jako bude začlenit do cílové vyrovnávací paměti, a přesto nechat místnosti s hodnotou Null ukončovací znak.

Pokud **mbsrtowcs_s –** úspěšně převede zdrojový řetězec, uloží je velikost v široké znaky převedený řetězec a null ukončení do  *&#42;pReturnValue*, zadaný  *pReturnValue* není nulový ukazatel. K tomu dojde i v případě *wcstr* argument je ukazatel s hodnotou null a vám umožní určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *wcstr* je ukazatel s hodnotou null, *počet* je ignorována.

Pokud *wcstr* ukazatel s hodnotou null, není objekt ukazatel na kterou odkazuje *mbstr* je přiřazen ukazatele null, pokud převod zastavena, protože bylo dosaženo ukončující znak hodnoty null. Pokud existuje, jinak hodnota je přiřazen pouze posledních adresu převést poslední vícebajtových znaků. To umožňuje volání funkce následné restartování převodu, kde byla zastavena toto volání.

Pokud *mbstate* je ukazatel s hodnotou null, interní knihovna **mbstate_t** převodu stavu statické objekt se používá. Protože tato interní statické objekt není bezpečné pro přístup z více vláken, doporučujeme, předáte vlastní *mbstate* hodnotu.

Pokud **mbsrtowcs_s –** zaznamená vícebajtových znaků, který není platný pro aktuální prostředí, odešle -1 do  *&#42;pReturnValue*, nastaví cílové vyrovnávací paměti *wcstr* prázdný řetězec, nastaví **errno** k **eilseq –**a vrátí **eilseq –**.

Pokud daná pořadí na kterou odkazuje *mbstr* a *wcstr* překrývají, chování **mbsrtowcs_s –** není definován. **mbsrtowcs_s –** je ovlivňován LC_TYPE kategorii aktuální národní prostředí.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odpovídá počtu více-bajtové znaky převést.

**Mbsrtowcs_s –** funkce se liší od [mbstowcs_s –, _mbstowcs_s_l –](mbstowcs-s-mbstowcs-s-l.md) podle jeho restartability. Stav převodu je uložený ve *mbstate* pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování. Například by měla použít aplikace **mbsrlen** místo **mbslen –**, pokud následných volání **mbsrtowcs_s –** se používá místo **mbstowcs_s –**.

V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (což eliminuje požadavek na zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit pomocí jejich protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Výjimky

**Mbsrtowcs_s –** Pokud žádná funkce v aktuálním volání vláken je funkce s více vlákny bezpečné **setlocale** tak dlouho, dokud tato funkce je prováděna a *mbstate* argument je ukazatele není null.

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
