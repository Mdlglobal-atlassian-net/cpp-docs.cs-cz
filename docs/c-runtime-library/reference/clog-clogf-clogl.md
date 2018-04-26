---
title: clog, clogf, clogl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
dev_langs:
- C++
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7d0f27af3c63b4f3dd43caae6b628b184f8c872a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Načte přirozený logaritmus čísla komplexní s větev vyjmout záporné skutečné osy.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Základ logaritmu.

## <a name="return-value"></a>Návratová hodnota

Přirozený logaritmus *z*. Výsledkem je, bez vazby skutečné osy a v intervalu [-iπ, + iπ] pomyslná osy.

Návratové hodnoty jsou:

|z parametru|Návratová hodnota|
|-----------------|------------------|
|Kladné|10 logaritmus z|
|Nula|- ∞|
|Záporný|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **clog** , přijmout a vrátit **_Fcomplex** a **_Lcomplex** hodnoty. V programu C **clog** vždy provede a vrátí **_Dcomplex** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**clog**, **clogf**, **clogl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
