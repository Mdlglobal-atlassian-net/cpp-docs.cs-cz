---
title: fegetexceptflag | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baccf3f32381568472bd4d0d5f37d434ca789fc8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Uloží aktuální stav příznaky zadaný výjimek plovoucí desetinné čárky.

## <a name="syntax"></a>Syntaxe

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);

```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Ukazatel **fexcept_t** objekt, který chcete obsahují aktuální hodnoty příznaky výjimka určeného *, s výjimkou*.

*s výjimkou*<br/>
Příznaky výjimek plovoucí desetinné čárky a uložit v *pstatus*.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. Jinak vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

**Fegetexceptflag** funkce uloží aktuální stav příznaky stavu výjimek plovoucí desetinné čárky určeného *, s výjimkou* v **fexcept_t** objektu na kterou odkazuje *pstatus*.  *pstatus* musí odkazovat na platný **fexcept_t** objekt nebo následné chování není definován. **Fegetexceptflag** funkce podporuje tyto makra výjimek definované v \<fenv.h >:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|

*, S výjimkou* argument může být nula, jednoho z podporovaných výjimek plovoucí desetinné čárky makra nebo bitové hodnotě nebo dvou nebo více makra. Účinek jakoukoli jinou hodnotu argumentu není definován.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
