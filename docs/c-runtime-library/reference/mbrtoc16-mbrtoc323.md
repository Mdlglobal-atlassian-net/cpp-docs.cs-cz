---
title: mbrtoc16 mbrtoc323 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a12e90f9a4bc0cc27df421c27d77a1b9b69334b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16 mbrtoc32

Změní první vícebajtových znaků v řetězci omezený na ekvivalentní UTF-16 nebo UTF-32 znaků.

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

*Cílový*<br/>
Ukazatel **char16_t** nebo **char32_t** ekvivalentní vícebajtových znaků pro převod. Pokud hodnotu null, funkce neukládá hodnotu.

*Zdroj*<br/>
Ukazatel na vícebajtový řetězec k převedení.

*max_bytes*<br/>
Maximální počet bajtů v *zdroj* prozkoumat pro znak pro převod. To by měl mít hodnotu mezi jeden a počet bajtů, včetně všech null ukončovací zbývající v *zdroj*.

*Stav*<br/>
Ukazatel na **mbstate_t** objekt stavu převod použité k interpretaci vícebajtové řetězec, který má jeden nebo více znaků výstup.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu první z těchto podmínek, které se vztahuje zadaný aktuální *stavu* hodnotu:

|Hodnota|Podmínka|
|-----------|---------------|
|0|Další *max_bytes* nebo méně znaků převedena z *zdroj* odpovídají null široké znaku, který je s hodnotou uloženou Pokud *cílové* není null.<br /><br /> *Stav* obsahuje stav počáteční shift.|
|Mezi 1 a *max_bytes*(včetně)|Hodnota vrácená je počet bajtů *zdroj* , dokončete platný vícebajtových znaků. Převedený široká znaková je uložen, pokud *cílové* není null.|
|-3|Další široká znaková vyplývající z předchozího volání funkce byla uložena v *cílové* Pokud *cílové* není null. Žádné bajtů z *zdroje* jsou spotřebovávají toto volání funkce.<br /><br /> Když *zdroj* odkazuje na vícebajtových znaků, který vyžaduje více než jeden znak širokou představovat (například náhradní pár), pak se *stavu* hodnota je aktualizována tak, aby zapíše další volání funkce  na další znak.|
|-2|Další *max_bytes* bajtů představují neúplnou, ale potenciálně platný, vícebajtových znaků. Žádná hodnota je uložena v *cílový*. Tento výsledek může dojít, pokud *max_bytes* je nulová.|
|-1|Došlo k chybě kódování. Další *max_bytes* nebo méně bajtů nepřispívají k dokončení a platné vícebajtových znaků. Žádná hodnota je uložena v *cílový*.<br /><br /> **Eilseq –** je uložen v **errno** a stav převodu *stavu* není zadáno.|

## <a name="remarks"></a>Poznámky

**Mbrtoc16** funkce přečte až *max_bytes* bajtů z *zdroj* najít první dokončení, platný vícebajtových znaků a potom úložiště ekvivalentní UTF-16 znak v *cílový*. Počet bajtů zdroje se interpretují podle aktuální vícebajtové národní prostředí vlákna. Pokud vícebajtových znaků vyžaduje více než jeden znak výstup UTF-16, jako je například náhradní pár, pak se *stavu* hodnota nastavena na ukládat další znak UTF-16 v *cílové* na další volání **mbrtoc16**. **Mbrtoc32** funkce je stejné, ale výstup se ukládají jako znakové sady UTF-32 znaků.

Pokud *zdroj* má hodnotu null, tyto funkce návratový ekvivalent volání vytvořené pomocí argumenty **NULL** pro *cílové*, **""** pro *zdroj*a 1 pro *max_bytes*. Předané hodnoty *cílové* a *max_bytes* jsou ignorovány.

Pokud *zdroj* je hodnotou not null, funkce spustí na začátku řetězce a zkontroluje až *max_bytes* bajtů můžete určit počet bajtů, které jsou nutné pro dokončení další vícebajtových znaků, včetně jakékoli shift pořadí. Pokud testovaných bajtů neobsahují platný a dokončení vícebajtových znaků, převede funkce znak ekvivalentní 16bitové nebo 32bitové široká znaková nebo znaky. Pokud *cílové* není null, funkce úložiště výsledek první (a případně pouze) znak v cílovém umístění. Pokud jsou vyžadovány další výstup znaky, je zadána hodnota *stavu*tak, aby následující volání funkce výstup další znaky a vrátí hodnotu -3. Pokud další znaky výstup nejsou povinné, pak *stavu* nastavena do stavu počáteční shift.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
