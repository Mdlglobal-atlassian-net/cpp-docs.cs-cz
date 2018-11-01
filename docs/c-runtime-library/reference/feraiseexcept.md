---
title: feraiseexcept
ms.date: 04/05/2018
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
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 581dd4026a20ce7221945c5815af3ae102f132fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532246"
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
Výjimky plovoucí desetinné čárky pro vyvolání.

## <a name="return-value"></a>Návratová hodnota

Pokud všechny zadané výjimky jsou vyvolány úspěšně, vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Feraiseexcept** funkce se pokusí vyvolat výjimky plovoucí desetinné čárky určené *, s výjimkou*.   **Feraiseexcept** funkce podporuje těchto maker výjimek definovaných v \<fenv.h >:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pole byl vytvořen hodnotu nekonečno.|
|FE_INEXACT|Funkce musela být zaokrouhlit uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V rámci starší operace s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsah; předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš velký a nelze je reprezentovat.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malá, aby se dala vyjádřit v úplnou přesností; byl vytvořen nenormální hodnota.|
|FE_ALLEXCEPT|Bitový operátor OR všech nepodporuje výjimky s plovoucí desetinnou čárkou.|

*, S výjimkou* argument může být nula, jeden hodnoty makra výjimek nebo bitový nebo dvě nebo více z maker výjimek podporované. Je-li zadané výjimky maker FE_OVERFLOW nebo FE_UNDERFLOW, může být FE_INEXACT výjimka vyvolána jako vedlejší efekt.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

**Specifické pro Microsoft:** výjimky podle *, s výjimkou* jsou vyvolány v pořadí FE_INVALID, FE_DIVBYZERO FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Ale FE_INEXACT mohou být vyvolány po vyvolání FE_OVERFLOW nebo FE_UNDERFLOW i v případě, že není zadán v *, s výjimkou*. **Specifické pro end Microsoft**

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
