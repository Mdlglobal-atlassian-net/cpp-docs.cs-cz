---
title: ASIN, asinf –, asinl – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
dev_langs:
- C++
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee65e4c8ce884ac42de35a23c81dbf5009dd1185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393274"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Vypočítá Arkus sinus.

## <a name="syntax"></a>Syntaxe

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, jejíž Arkus sinus je vypočtena.

## <a name="return-value"></a>Návratová hodnota

**Asin** funkce vrátí Arkus sinus (inverzní sinus funkce) z *x* v rozsahu - pí/2 do pí/2 radiánech.

Ve výchozím nastavení pokud *x* je menší než -1 nebo větší než 1, **asin** vrátí neomezené.

|Vstup|Výjimka SEH|Matherr – výjimka|
|-----------|-------------------|-----------------------|
|± ∞|**NEPLATNÝ**|**_DOMAIN –**|
|ROZMEZÍ **QNAN**, **IND**|žádná|**_DOMAIN –**|
|&#124;x&#124;>1|**NEPLATNÝ**|**_DOMAIN –**|

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **asin** s **float** a **dlouho** **dvojité** hodnoty. V programu C **asin** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf –**, **asinl –**|\<Math.h >|\<cmath – > nebo \<math.h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [acos, acosf –, acosl –](acos-acosf-acosl.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[Cos, cosf –, cosl –](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
