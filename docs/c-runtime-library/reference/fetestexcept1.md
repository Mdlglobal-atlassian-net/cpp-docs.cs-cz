---
title: fetestexcept | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fetestexcept
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
- fetestexcept
- fenv/fetestexcept
dev_langs:
- C++
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0450fcaddf8ca05484d0b2bd122ff006eb8355f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397395"
---
# <a name="fetestexcept"></a>fetestexcept

Určuje, které příznaky stavu s plovoucí desetinnou čárkou výjimce momentálně nastaven.

## <a name="syntax"></a>Syntaxe

```C
int fetestexcept(
   int excepts
);

```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Bitový operátor OR příznaků s plovoucí desetinnou čárkou stav pro testování.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí bitová maska obsahující bitové operace OR makra výjimek plovoucí desetinné čárky, které odpovídají příznaky stavu výjimka aktuálně nastavit. Vrátí hodnotu 0, pokud žádná z výjimky jsou nastavené.

## <a name="remarks"></a>Poznámky

Pomocí funkce fetestexcept k určení výjimek, které byly vydané plovoucí bodu operaci. Použití *, s výjimkou* parametr k určení stavu příznacích výjimky k testování. **Fetestexcept** funkce používá tyto makra výjimek definované v \<fenv.h > v *, s výjimkou* a návratovou hodnotu:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|

Zadaný *, s výjimkou* argument může mít hodnotu 0, jednoho z podporovaných výjimek plovoucí desetinné čárky makra nebo bitové hodnotě nebo dva nebo víc makra. Účinek jakékoliv *, s výjimkou* hodnota argumentu není definován.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
