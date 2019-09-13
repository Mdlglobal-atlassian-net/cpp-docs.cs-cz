---
title: feclearexcept1
ms.date: 04/05/2018
api_name:
- feclearexcept
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
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 9899d7068a289e7d5f71cb42a8373869d60c3070
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941273"
---
# <a name="feclearexcept"></a>feclearexcept

Pokusy o vymazání příznaků výjimek s plovoucí desetinnou čárkou, které jsou určeny argumentem.

## <a name="syntax"></a>Syntaxe

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Příznaky stavu výjimky, které mají být vymazány.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud *s výjimkou* je nula, nebo pokud byly všechny zadané výjimky úspěšně vymazány. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **feclearexcept** se pokusí vymazat příznaky stavu výjimky s plovoucí desetinnou čárkou, které jsou určené *výjimkou*. Funkce podporuje tato makra výjimky definovaná v fenv. h:

|Makro výjimky|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě v záčísle nebo objektu. byla vytvořena hodnota nekonečno.|
|FE_INEXACT|Funkce byla nucena zaokrouhlit uložený výsledek předchozí operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsahu; předchozí výsledek operace s plovoucí desetinnou čárkou byl pro reprezentaci příliš velký.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malý, aby byl reprezentován s plnou přesností. byla vytvořena deběžná hodnota.|
|FE_ALL_EXCEPT|Bitové nebo všechny podporované výjimky s plovoucí desetinnou čárkou.|

Argument *excepts* může být nula nebo BITOVÝ operátor OR jednoho nebo více podporovaných maker výjimek. Výsledek jakékoli jiné hodnoty argumentu není definován.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
