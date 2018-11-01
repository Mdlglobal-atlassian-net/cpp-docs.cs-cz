---
title: _finite – _finitef
ms.date: 04/05/2018
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: 7b1bce6f1b2da77ed9de255f49dd8d0160e33e31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431657"
---
# <a name="finite-finitef"></a>_finite – _finitef

Určuje, zda je konečnou hodnotu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

Obě **_finite –** a **_finitef** vrátí nenulovou hodnotu, pokud argument *x* je omezenou; který je, pokud -INF < *x* < + INF. Vrátí 0, pokud je argument nekonečno a NAN.

## <a name="remarks"></a>Poznámky

**_Finite –** a **_finitef** funkce jsou specifické pro Microsoft. **_Finitef** pouze je funkce dostupná, jenom Pokud sestavili x86, ARM, ARM64 nebo platformy.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------------|-------------------------------|
|**_finite –**|\<float.h > nebo \<math.h >|\<float.h >, \<math.h >, \<cfloat – >, nebo \<cmath >|
|**_finitef**|\<Math.h >|\<Math.h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
