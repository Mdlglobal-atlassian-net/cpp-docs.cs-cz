---
title: fetestexcept
ms.date: 04/05/2018
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
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: ae170e4c5826e2053b330d81773b75f176303332
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667438"
---
# <a name="fetestexcept"></a>fetestexcept

Určuje, které příznaky stavu zadané výjimky s plovoucí desetinnou čárkou jsou aktuálně nastaveny.

## <a name="syntax"></a>Syntaxe

```C
int fetestexcept(
   int excepts
);

```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Bitový operátor OR příznaků s plovoucí desetinnou čárkou stav testování.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí bitová maska obsahující bitový operátor OR maker výjimek s plovoucí desetinnou čárkou, které odpovídají příznaky výjimky stav aktuálně nastavit. Vrátí hodnotu 0, pokud žádný z výjimky jsou nastavené.

## <a name="remarks"></a>Poznámky

Můžete určit, výjimek, které byly vyvolány pomocí plovoucí pomocí funkce fetestexcept bodu operace. Použití *, s výjimkou* parametr k určení stavu příznacích výjimek k testování. **Fetestexcept** funkce používá těchto maker výjimek definovaných v \<fenv.h > v *, s výjimkou* a návratovou hodnotu:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pole byl vytvořen hodnotu nekonečno.|
|FE_INEXACT|Funkce musela být zaokrouhlit uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V rámci starší operace s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsah; předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš velký a nelze je reprezentovat.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malá, aby se dala vyjádřit v úplnou přesností; byl vytvořen nenormální hodnota.|
|FE_ALLEXCEPT|Bitový operátor OR všech nepodporuje výjimky s plovoucí desetinnou čárkou.|

Zadaný *, s výjimkou* argument může být 0, jeden makra podporované výjimek s plovoucí desetinnou čárkou nebo bitový nebo dvě nebo více z makra. Vliv ostatních *, s výjimkou* hodnota argumentu není definován.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
