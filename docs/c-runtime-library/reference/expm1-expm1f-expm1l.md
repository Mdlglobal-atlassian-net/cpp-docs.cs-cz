---
title: expm1 – expm1f –, expm1l – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
dev_langs:
- C++
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba382fb29b5ec841d9acd127ad5f48e0ca7b68fa
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Vypočítá exponenciální hodnoty, minus jeden e base.

## <a name="syntax"></a>Syntaxe

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Exponenciální hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Expm1 –** funkce vrátí hodnotu s plovoucí desetinnou čárkou, která reprezentuje konstantu e<sup>x</sup> – 1, pokud bylo úspěšné. Na přetečení **expm1 –** vrátí **huge_val –**, **expm1f –** vrátí **HUGE_VALF**, **expm1l –** vrátí **HUGE_VALL**, a **errno** je nastaven na **erange –**. Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **expm1 –** , přijmout a vrátit **float** a **dlouho** **dvojité** hodnoty. V programu C **expm1 –** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**expm1 –**, **expm1f –**, **expm1l –**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
