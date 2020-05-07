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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0e3d5ceffa5adc9e9f6ba96cccb46a3fbcfca69a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919570"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Přeloží první vícebajtový znak UTF-8 v řetězci na ekvivalentní znak UTF-16 nebo UTF-32.

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

*tabulka*\
Ukazatel na **char16_t** nebo **char32_t** ekvivalent vícebajtového znaku UTF-8, který se má převést. Pokud má hodnotu null, funkce neuloží hodnotu.

*Zdrojová*\
Ukazatel na řetězec vícebajtových znaků UTF-8, který se má převést.

*max_bytes*\
Maximální počet bajtů ve *zdroji* , který má být prověřen pro znak, který má být převeden. Tento argument by měl být hodnota mezi 1 a počtem bajtů, včetně všech ukončovacích znaků null, zbývající ve *zdroji*.

*státech*\
Ukazatel na objekt stavu konverze **mbstate_t** slouží k interpretaci vícebajtového řetězce UTF-8 na jeden nebo více výstupních znaků.

## <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu první z těchto podmínek, které platí, s ohledem na hodnotu aktuálního *stavu* :

|Hodnota|Podmínka|
|-----------|---------------|
|0|Další *max_bytes* nebo méně znaků převedených ze *zdroje* odpovídají znaku null, který je uložený v případě, že *cílová* hodnota není null.<br /><br /> *stav* obsahuje počáteční stav posunutí.|
|Mezi 1 a *max_bytes*včetně|Vrácená hodnota je počet bajtů *zdroje* , které dokončí platný vícebajtový znak. V případě, že *cíl* není null, je uložený široce převedený znak.|
|-3|Další širší znak, který je výsledkem předchozího volání funkce, byl uložen v *cíli* , pokud *cíl* není null. Toto volání funkce nespotřebovává žádné bajty ze *zdroje* .<br /><br /> Když *zdroj* odkazuje na vícebajtový znak UTF-8, který vyžaduje více než jeden širší znak, který reprezentuje (například náhradní pár), pak se hodnota *stav* aktualizuje tak, aby další volání funkce zapisovalo další znak.|
|-2|Další *max_bytesové* bajty reprezentují neúplný, ale potenciálně platný vícebajtový znak UTF-8. V *cíli*není uložená žádná hodnota. K tomuto výsledku může dojít, pokud je *max_bytes* nula.|
|-1|Došlo k chybě kódování. Další *max_bytes* nebo méně bajtů nepřispívají k kompletnímu a platnému vícebajtovém znaku UTF-8. V *cíli*není uložená žádná hodnota.<br /><br /> **EILSEQ** je uložen v **errno** a *stav* hodnoty stavu převodu není určen.|

## <a name="remarks"></a>Poznámky

Funkce **mbrtoc16** čte až *max_bytes* bajtů ze *zdroje* , aby našel první úplný, platný vícebajtový znak UTF-8 a potom v *cíli*uloží ekvivalentní znak UTF-16. Pokud znak vyžaduje více než jeden výstupní znak UTF-16, například náhradní pár, pak je hodnota *stav* nastavená na uložení dalšího znaku UTF-16 v *cíli* při dalším volání **mbrtoc16**. Funkce **mbrtoc32** je shodná, ale výstup je uložen jako znak UTF-32.

Pokud má *zdroj* hodnotu null, vrátí tyto funkce ekvivalent volání pomocí argumentů **null** pro *cíl* `""` (prázdný řetězec zakončený hodnotou null) pro *zdroj*a 1 pro *max_bytes*. Předané hodnoty *cílového umístění* a *max_bytes* jsou ignorovány.

Pokud *zdroj* není null, funkce začíná na začátku řetězce a kontroluje až *max_bytes* bajtů, aby bylo možné určit počet bajtů vyžadovaných k dokončení dalšího vícebajtového znaku UTF-8, včetně všech sekvencí posunutí. Pokud prošetřené bajty obsahují platný a kompletní vícebajtový znak UTF-8, funkce převede znak na ekvivalentní 16bitový nebo 32 celý znak nebo znaky. Pokud *cíl* není null, funkce ukládá první (a možná pouze) výsledný znak v cíli. Pokud jsou požadovány další výstupní znaky, hodnota je nastavena ve *stavu*, takže následné volání funkce výstup dalších znaků a vrátí hodnotu-3. Pokud nejsou požadovány žádné další výstupní znaky, pak je *stav* nastaven na počáteční stav posunutí.

K převedení vícebajtových znaků nevyužívajících UTF-8 na znaky UTF-16 LE použijte funkce [mbrtowc](mbrtowc.md), [mbtowc nebo _mbtowc_l](mbtowc-mbtowc-l.md) .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|Hlavička C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar. h>|\<cuchar>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../data-conversion.md)\
[Jazyka](../locale.md)\
[Výklad sekvencí vícebajtových znaků](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
