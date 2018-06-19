---
title: TRUNC, truncf –, truncl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- trunc
- truncf
- truncl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
dev_langs:
- C++
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67c179065a6b2c6fc10a4ba6ba87868c8306a2aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409456"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Určuje, na nejbližší celé číslo, která je menší než nebo rovna zadané hodnotě s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota zkrátit.

## <a name="return-value"></a>Návratová hodnota

Pokud bylo úspěšné, vrátí metoda hodnotu *x*, zaokrouhleno směrem k nule.

Jinak může vrátit jednu z těchto možností:

|Problém|Vrátí|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* = ±0|x|
|*x* = NaN.|NaN|

Vznikly chyby uvedené v [_matherr –](matherr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **trunc** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **trunc** vždy provede a vrátí **dvojité**.

Protože největší hodnoty s plovoucí desetinnou čárkou jsou přesný celá čísla, tato funkce nebude přetečení svoje vlastní. Může ale způsobit funkce přetečení vrácením hodnotu do celočíselného typu.

Vám může také zaokrouhlí dolů podle implicitní převod z s plovoucí desetinnou čárkou do integrální; to proto je však omezená na hodnoty, které mohou být uloženy ve cílový typ.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**TRUNC**, **truncf –**, **truncl**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
