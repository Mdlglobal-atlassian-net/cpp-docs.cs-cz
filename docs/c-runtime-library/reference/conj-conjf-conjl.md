---
title: conj, conjf, conjl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- conj
- conjf
- conjl
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
- conj
- conjf
- conjl
- complex/conj
- complex/conjf
- complex/conjl
dev_langs:
- C++
helpviewer_keywords:
- conj function
- conjf function
- conjl function
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb91b566c499ba9f34c7c67c9cdc24d67924601d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394318"
---
# <a name="conj-conjf-conjl"></a>conj, conjf, conjl

Načte sdružené komplexního čísla.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex conj(
   _Dcomplex z
);
_Fcomplex conj(
   _Fcomplex z
);  // C++ only
_Lcomplex conj(
   _Lcomplex z
);  // C++ only
_Fcomplex conjf(
   _Fcomplex z
);
_Lcomplex conjl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní čísla.

## <a name="return-value"></a>Návratová hodnota

Sdružené *z*.  Výsledek obsahuje stejnou část skutečné a pomyslná jako *z*, ale s opačným znaménkem.

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **conj** , přijmout a vrátit **_Fcomplex** a **_Lcomplex** hodnoty. V programu C **conj** vždy provede a vrátí **_Dcomplex** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**conj**, **conjf**, **conjl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
