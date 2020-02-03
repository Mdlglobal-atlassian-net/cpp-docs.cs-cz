---
title: fetestexcept
ms.date: 04/05/2018
api_name:
- fetestexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: e70ae1b74420b8186cccd8fc8a817423df618adf
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972162"
---
# <a name="fetestexcept"></a>fetestexcept

Určuje, které ze zadaných příznaků stavu výjimky s plovoucí desetinnou čárkou jsou aktuálně nastaveny.

## <a name="syntax"></a>Syntaxe

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Bitové příznaky stavu s plovoucí desetinnou čárkou pro testování.

## <a name="return-value"></a>Návratová hodnota

Při úspěchu vrátí bitovou masku obsahující bitovou nebo logickou makra výjimky s plovoucí desetinnou čárkou, která odpovídá aktuálně nastaveným příznakům stavu výjimky. Vrátí hodnotu 0, pokud není nastavena žádná výjimka.

## <a name="remarks"></a>Poznámky

Použijte funkci fetestexcept k určení, které výjimky byly vyvolány operací s plovoucí desetinnou čárkou. Použijte parametr *s výjimkou* k určení, které příznaky stavu výjimek mají být testovány. Funkce **fetestexcept** používá tato makra výjimek definovaná v \<fenv. h > v *s výjimkou* a návratovou hodnotou:

|Makro výjimky|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě v záčísle nebo objektu. byla vytvořena hodnota nekonečno.|
|FE_INEXACT|Funkce byla nucena zaokrouhlit uložený výsledek předchozí operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsahu; předchozí výsledek operace s plovoucí desetinnou čárkou byl pro reprezentaci příliš velký.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malý, aby byl reprezentován s plnou přesností. byla vytvořena deběžná hodnota.|
|FE_ALL_EXCEPT|Bitové nebo všechny podporované výjimky s plovoucí desetinnou čárkou.|

Zadaný *s výjimkou* argumentu může mít hodnotu 0, jednu z podporovaných maker výjimek s plovoucí desetinnou čárkou nebo bitovou nebo dvě či více maker. Účinek jakékoli jiné *s výjimkou* hodnoty argumentu není definován.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace s plovoucí desetinnou čárkou, které by mohly zabránit přístupu pomocí direktivy `#pragma fenv_access(on)` před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>
