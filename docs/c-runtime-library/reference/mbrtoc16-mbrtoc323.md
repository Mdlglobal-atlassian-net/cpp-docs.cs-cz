---
title: mbrtoc16, mbrtoc323
ms.date: 11/04/2016
api_name:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 52bcec5911fdc2ecbb073ae0042777aa4eb2b963
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952449"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Přeloží první vícebajtový znak v úzkém řetězci na ekvivalentní znak UTF-16 nebo UTF-32.

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

*destination*<br/>
Ukazatel na **char16_t** nebo **char32_t** ekvivalent vícebajtového znaku pro převod. Pokud má hodnotu null, funkce neuloží hodnotu.

*source*<br/>
Ukazatel na řetězec vícebajtových znaků, který se má převést.

*max_bytes*<br/>
Maximální počet bajtů ve *zdroji* , který má být prověřen pro znak, který má být převeden. Mělo by se jednat o hodnotu mezi 1 a počtem bajtů, včetně znaku null, zbývající ve *zdroji*.

*státech*<br/>
Ukazatel na objekt stavu konverze **mbstate_t** sloužící k interpretaci vícebajtového řetězce na jeden nebo více výstupních znaků.

## <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí hodnotu první z těchto podmínek, které platí, s ohledem na hodnotu aktuálního *stavu* :

|Value|Podmínka|
|-----------|---------------|
|0|Další *max_bytes* nebo méně znaků převedených ze *zdroje* odpovídají znaku null, který je uložený v případě, že *cílová* hodnota není null.<br /><br /> *stav* obsahuje počáteční stav posunutí.|
|Mezi 1 a *max_bytes*, včetně|Vrácená hodnota je počet bajtů *zdroje* , které dokončí platný vícebajtový znak. V případě, že *cíl* není null, je uložený široce převedený znak.|
|-3|Další širší znak, který je výsledkem předchozího volání funkce, byl uložen v *cíli* , pokud *cílová* hodnota není null. Toto volání funkce nespotřebovává žádné bajty ze *zdroje* .<br /><br /> Když *zdroj* odkazuje na vícebajtový znak, který vyžaduje více než jeden širší znak, který reprezentuje (například náhradní pár), pak je hodnota *stavu* aktualizována tak, aby další volání funkce zapisovalo další znak.|
|-2|Další *max_bytes* bajty reprezentují neúplný, ale potenciálně platný vícebajtový znak. V *cíli*není uložená žádná hodnota. K tomuto výsledku může dojít, pokud je *max_bytes* nula.|
|-1|Došlo k chybě kódování. Další *max_bytes* nebo méně bajtů nepřispívají k kompletnímu a platnému vícebajtovém znaku. V *cíli*není uložená žádná hodnota.<br /><br /> **EILSEQ** je uložený v **errno** a *stav* konverze není Neurčeno.|

## <a name="remarks"></a>Poznámky

Funkce **mbrtoc16** čte až *max_bytes* bajtů ze *zdroje* , aby našel první úplný, platný vícebajtový znak a pak v *cíli*uloží ekvivalentní znak UTF-16. Zdrojové bajty jsou interpretovány podle aktuálního vlákna vícebajtového národního prostředí. Pokud vícebajtový znak vyžaduje více než jeden výstupní znak UTF-16, například náhradní pár, pak je hodnota *stav* nastavená na uložení dalšího znaku UTF-16 v *cíli* při dalším volání **mbrtoc16**. Funkce **mbrtoc32** je shodná, ale výstup je uložen jako znak UTF-32.

Pokud má *zdroj* hodnotu null, vrátí tyto funkce ekvivalent volání pomocí argumentů s **hodnotou null** pro *cíl*, **""** pro *zdroj*a 1 pro *max_bytes*. Předané hodnoty *Destination* a *max_bytes* jsou ignorovány.

Pokud *zdroj* není null, funkce začíná na začátku řetězce a zkontroluje až *max_bytes* bajtů a určí počet bajtů vyžadovaných k dokončení dalšího vícebajtového znaku, včetně všech sekvencí posunutí. Pokud prošetřené bajty obsahují platný a kompletní vícebajtový znak, funkce převede znak na ekvivalentní 16bitový nebo 32 celý znak nebo znaky. Pokud *cíl* není null, funkce ukládá první (a možná pouze) výsledný znak v cíli. Pokud jsou požadovány další výstupní znaky, hodnota je nastavena ve *stavu*, takže následné volání funkce výstup dalších znaků a vrátí hodnotu-3. Pokud nejsou požadovány žádné další výstupní znaky, pak je *stav* nastaven na počáteční stav posunutí.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
