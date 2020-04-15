---
title: mbrtoc16, mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340981"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Převede první vícebajtový znak UTF-8 v řetězci do ekvivalentního znaku UTF-16 nebo UTF-32.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>Parametry

*Cíl*\
Ukazatel na **char16_t** nebo **char32_t** ekvivalent vícebajtového znaku UTF-8 převést. Pokud null, funkce neukládá hodnotu.

*Zdroj*\
Ukazatel na vícebajtový řetězec znaku UTF-8, který chcete převést.

*max_bytes*\
Maximální počet bajtů ve *zdroji* zkoumat znak převést. Tento argument by měl být hodnota mezi jedním a počtem bajtů, včetně všech hodnotnull zakončení, zbývající ve *zdroji*.

*Státu*\
Ukazatel na **objekt mbstate_t** stavu převodu používaný k interpretaci vícebajtového řetězce UTF-8 na jeden nebo více výstupních znaků.

## <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu první z těchto podmínek, která platí, vzhledem k aktuální hodnotě *stavu:*

|Hodnota|Podmínka|
|-----------|---------------|
|0|Další *max_bytes* nebo méně znaků převedených ze *zdroje* odpovídají znaku null wide, což je hodnota uložená, pokud *cíl* není null.<br /><br /> *obsahuje* počáteční stav posunu.|
|Od 1 do *max_bytes*, včetně|Vrácená hodnota je počet bajtů *zdroje,* které doplňují platný vícebajtový znak. Převedený široký znak je uložen, pokud *cíl* není null.|
|-3|Další široký znak vyplývající z předchozího volání funkce byl uložen v *cíli,* pokud *cíl* není null. Tímto voláním funkce nejsou spotřebovány žádné bajty ze *zdroje.*<br /><br /> Když *zdroj* odkazuje na vícebajtový znak UTF-8, který vyžaduje více než jeden široký znak k reprezentaci (například náhradní pár), pak je hodnota *stavu* aktualizována tak, aby další volání funkce zapíše další znak.|
|-2|Další *bajty max_bytes* představují neúplný, ale potenciálně platný vícebajtový znak UTF-8. V *cíli*není uložena žádná hodnota . K tomuto výsledku může dojít, pokud *je max_bytes* nula.|
|-1|Došlo k chybě kódování. Další *max_bytes* nebo méně bajtů nepřispívají k úplné a platné UTF-8 vícebajtový znak. V *cíli*není uložena žádná hodnota .<br /><br /> **EILSEQ** je uložen v **chybě** a *stav* hodnoty stavu převodu není určen.|

## <a name="remarks"></a>Poznámky

Funkce **mbrtoc16** čte až *max_bytes* bajtů ze *zdroje,* aby nalezla první úplný, platný vícebajtový znak UTF-8, a pak uloží ekvivalentní znak UTF-16 v *cíli*. Pokud znak vyžaduje více než jeden výstupní znak UTF-16, například náhradní pár, je hodnota *stavu* nastavena tak, aby při dalším volání **mbrtoc16**uložila další znak UTF-16 v *cíli* . Funkce **mbrtoc32** je identická, ale výstup je uložen jako znak UTF-32.

Pokud je *zdroj* null, vrátí tyto funkce ekvivalent volání provedeného `""` pomocí argumentů **NULL** pro *cíl*(prázdný řetězec s ukončeným hodnotou null) pro *zdroj*a 1 pro *max_bytes*. Předané hodnoty *cílovéa* a *max_bytes* jsou ignorovány.

Pokud *zdroj* není null, funkce začíná na začátku řetězce a kontroluje až *max_bytes* bajtů k určení počtu bajtů potřebných k dokončení další utf-8 vícebajtový znak, včetně všech posloupností směn. Pokud zkoumané bajty obsahují platný a úplný vícebajtový znak UTF-8, funkce převede znak na ekvivalentní 16bitový nebo 32bitový znak nebo znaky. Pokud *cíl* není null, funkce ukládá první (a možná pouze) výsledek znak v cílovém umístění. Pokud jsou požadovány další výstupní znaky, je ve *stavu*nastavena hodnota , takže následné volání výstupu funkce další znaky a vrátí hodnotu -3. Pokud nejsou požadovány žádné další výstupní znaky, je *stav* nastaven na počáteční stav posunu.

Chcete-li převést vícebajtové znaky jiné než UTF-8 na znaky UTF-16 LE, použijte funkce [mbrtowc](mbrtowc.md), [mbtowc nebo _mbtowc_l.](mbtowc-mbtowc-l.md)

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../data-conversion.md)\
[Národní prostředí](../locale.md)\
[Interpretace vícebajtových sekvencí](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rhrob](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
