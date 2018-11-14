---
title: mbrtoc16 mbrtoc323
ms.date: 11/04/2016
apiname:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: f8573ac321772d19141be0228891b290ba48b217
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520139"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16 mbrtoc32

Převede první vícebajtového znaku v úzký řetězcový na ekvivalentní UTF-16 nebo UTF-32 znaků.

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

*cíl*<br/>
Ukazatel **char16_t** nebo **char32_t** ekvivalent vícebajtový znak pro převod. Pokud má hodnotu null, funkce hodnotu neukládá.

*source*<br/>
Ukazatel na řetězec vícebajtový znak pro převod.

*max_bytes*<br/>
Maximální počet bajtů v *zdroj* prozkoumat pro znak pro převod. Toto musí být číslo v rozsahu od 1 do počtu bajtů, včetně jakékoli ukončovacího znaku null, zbývajících v *zdroj*.

*Stav*<br/>
Ukazatel **mbstate_t** převodu stav objektu použité k interpretaci vícebajtový řetězec, který má jeden nebo více znaků výstupu.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu první z těchto podmínek, které se vztahuje, aktuálně stanovaném *stavu* hodnotu:

|Hodnota|Podmínka|
|-----------|---------------|
|0|Další *max_bytes* nebo méně znaků převést z *zdroj* odpovídají široké znaky null, což je hodnota uložená Pokud *cílové* nemá hodnotu null.<br /><br /> *Stav* obsahuje počáteční posun stavu.|
|Mezi 1 a *max_bytes*včetně|Vrácená hodnota je počet bajtů *zdroj* dokončit, který je platný vícebajtový znak. Převedený širokého znaku je uložen, pokud *cílové* nemá hodnotu null.|
|-3|Dalšího širokého znaku vyplývající z předchozího volání funkce jsou uložená v *cílové* Pokud *cílové* nemá hodnotu null. Žádné bajty z *zdroj* se spotřebovávají toto volání funkce.<br /><br /> Když *zdroj* odkazuje na vícebajtového znaku, který vyžaduje více než jeden širokého znaku představující (například náhradní pár), pak bude *stavu* hodnota je aktualizována tak, aby se zapíše následující volání funkce  na další znak.|
|-2|Další *max_bytes* bajtů představují neúplný, ale potenciálně platný, vícebajtového znaku. Žádná hodnota je uložená v *cílové*. Tento výsledek může dojít, pokud *max_bytes* je nula.|
|-1|Došlo k chybě kódování. Další *max_bytes* nebo menší počet bajtů se nepodílejí na dokončení a je platný vícebajtový znak. Žádná hodnota je uložená v *cílové*.<br /><br /> **EILSEQ** je uložen v **errno** a stav převodu *stavu* není zadána.|

## <a name="remarks"></a>Poznámky

**Mbrtoc16** funkce přečte až *max_bytes* bajtů z *zdroj* najít první kompletní a platný vícebajtový znak a potom úložiště ekvivalentní UTF-16 znak *cílové*. Zdroj bajtů se interpretují podle aktuální národní prostředí pro vlákno vícebajtové. Pokud vícebajtový znak vyžaduje více než jeden znak výstup kódování UTF-16, jako je například náhradní pár, pak bude *stavu* je hodnota nastavena na ukládání další znak v kódování UTF-16 *cílové* na další volání **mbrtoc16**. **Mbrtoc32** funkcí jsou identické, ale výstup se ukládá jako UTF-32 znaků.

Pokud *zdroj* má hodnotu null, tyto funkce vrácená ekvivalent volání bylo vytvořeno s použitím argumenty **NULL** pro *cílové*, **""** pro *zdroj*a 1 pro *max_bytes*. Předané hodnoty *cílové* a *max_bytes* jsou ignorovány.

Pokud *zdroj* není null, funkce začne na začátku řetězce a zkontroluje až *max_bytes* bajtů k určení počtu bajtů vyžadovaných k dokončení dalšího vícebajtového znaku, včetně Všechny sekvence shift. Pokud přezkoumán bajtů obsahovat platnou a kompletní vícebajtový znak, funkce převede znak na odpovídající 16bitové nebo 32bitové široký znak nebo znaky. Pokud *cílové* není null, funkce ukládá výsledek první (a případně pouze) znaku v cílové. Pokud potřebujete další výstupní znaky, je hodnota *stavu*tak, aby následná volání funkce výstupní další znaky a vrátí hodnotu -3. Pokud další znaky výstup nejsou povinné, pak *stavu* nastavena do stavu počáteční posun.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
