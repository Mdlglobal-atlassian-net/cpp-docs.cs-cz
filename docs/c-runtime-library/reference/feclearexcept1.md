---
title: feclearexcept1 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- feclearexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feclearexcept
- fenv/feclearexcept
dev_langs:
- C++
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc980cea3df0b86848f2cad2b2eceb48bfb2f039
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="feclearexcept"></a>feclearexcept

Pokusí se Vymazat příznaky výjimek plovoucí desetinné čárky určený argumentem.

## <a name="syntax"></a>Syntaxe

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Příznaky stavu výjimka zrušte.

## <a name="return-value"></a>Návratová hodnota

Vrátí nula v případě *, s výjimkou* rovná nule, nebo pokud byly úspěšně vymazán všechny zadané výjimky. Jinak vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Feclearexcept** funkce pokusí zrušte procedura bod příznaky stavu výjimka určeného *, s výjimkou*. Funkce podporuje tyto makra výjimek definované v fenv.h:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|

*, S výjimkou* argument může být nula nebo bitová hodnota OR jeden nebo více makra podporované výjimek. Výsledek jakoukoli jinou hodnotu argumentu není definován.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
