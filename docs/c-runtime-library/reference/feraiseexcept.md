---
title: feraiseexcept | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
dev_langs:
- C++
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfd60612c92f8e3ff542fd22bbf5b4a01f7b7365
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="feraiseexcept"></a>feraiseexcept

Vyvolá zadané výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
S plovoucí desetinnou čárkou výjimky vygeneroval.

## <a name="return-value"></a>Návratová hodnota

Pokud všechny zadané výjimky jsou vyvolány úspěšně, vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Feraiseexcept** funkce pokusí vyvolat s plovoucí desetinnou čárkou výjimky určeného *, s výjimkou*.   **Feraiseexcept** funkce podporuje tyto makra výjimek definované v \<fenv.h >:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|

*, S výjimkou* argument může být nula, jednoho z hodnoty makro výjimky nebo bitové hodnotě nebo dvou nebo více makra podporované výjimek. Je-li makra zadanou výjimkou FE_OVERFLOW nebo FE_UNDERFLOW, může být FE_INEXACT výjimka vyvolána jako vedlejší účinek.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

**Microsoft specifické:** výjimky zadaný v *, s výjimkou* jsou vyvolány v pořadí FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Ale FE_INEXACT může být vyvolá, když FE_OVERFLOW nebo FE_UNDERFLOW je vyvolána, i když není zadaný v *, s výjimkou*. **Konkrétní Microsoft end**

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
