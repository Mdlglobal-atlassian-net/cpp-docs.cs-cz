---
title: _finite –, _finitef | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3367f13e68aa85e53d9f5f0ee83521ef465d3996
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396638"
---
# <a name="finite-finitef"></a>_finite –, _finitef

Určuje, zda je omezené hodnotu s plovoucí desetinnou čárkou.

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

Obě **_finite –** a **_finitef** vrátí nenulovou hodnotu, pokud argument *x* je konečného počtu permutací; je, pokud -INF < *x* < + INF. Vrátí 0, pokud je argument nekonečné nebo NAN.

## <a name="remarks"></a>Poznámky

**_Finite –** a **_finitef** funkce se konkrétní společnosti Microsoft. **_Finitef** funkce je pouze k dispozici v případě zkompilovaném pro x86 ARM nebo ARM64 platformy.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------------|-------------------------------|
|**_finite –**|\<float.h – > nebo \<math.h >|\<float.h – >, \<math.h >, \<cfloat – >, nebo \<cmath – >|
|**_finitef**|\<Math.h >|\<Math.h > nebo \<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
