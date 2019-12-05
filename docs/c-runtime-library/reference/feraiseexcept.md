---
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
api_type:
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 07c8a79e0a9569db80607e1ec1e16cd4b502783c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857824"
---
# <a name="feraiseexcept"></a>feraiseexcept

Vyvolává zadané výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Výjimky s plovoucí desetinnou čárkou k vyvolání.

## <a name="return-value"></a>Návratová hodnota

Pokud jsou všechny zadané výjimky vyvolány úspěšně, vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Funkce **feraiseexcept** se pokusí vyvolat výjimky s plovoucí desetinnou čárkou, které jsou určené *výjimkou*.   Funkce **feraiseexcept** podporuje tato makra výjimek definovaná v \<fenv. h >:

|Makro výjimky|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě v záčísle nebo objektu. byla vytvořena hodnota nekonečno.|
|FE_INEXACT|Funkce byla nucena zaokrouhlit uložený výsledek předchozí operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsahu; předchozí výsledek operace s plovoucí desetinnou čárkou byl pro reprezentaci příliš velký.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malý, aby byl reprezentován s plnou přesností. byla vytvořena deběžná hodnota.|
|FE_ALLEXCEPT|Bitové nebo všechny podporované výjimky s plovoucí desetinnou čárkou.|

Argument *excepts* může být nula, jedna z hodnot makra výjimky nebo bitová nebo druhá z podporovaných maker výjimek. Pokud je jedno ze zadaných maker výjimek FE_OVERFLOW nebo FE_UNDERFLOW, může být výjimka FE_INEXACT vyvolána jako vedlejší efekt.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace s plovoucí desetinnou čárkou, které by mohly zabránit přístupu pomocí direktivy `#pragma fenv_access(on)` před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

**Specifické pro společnost Microsoft:** Výjimky, které jsou uvedeny v části *s výjimkou* , jsou vyvolány v pořadí FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Nicméně FE_INEXACT lze vyvolat při vyvolání FE_OVERFLOW nebo FE_UNDERFLOW, i když není zadáno v *s výjimkou*.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
