---
title: ceil, ceilf –, ceill – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68ff857db09d1426fbed6ea497624e13cc362a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394262"
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill

Vypočítá mezní hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Ceil** funkce vrátí hodnotu s plovoucí desetinnou čárkou, která reprezentuje nejmenší celé číslo, které je větší než nebo rovno *x*. Neexistuje žádný návratový chyby.

|Vstup|Výjimka SEH|Matherr – výjimka|
|-----------|-------------------|-----------------------|
|ROZMEZÍ **QNAN**, **IND**|žádná|**_DOMAIN –**|

**ceil –** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). Informace a omezení o pomocí implementace SSE2 najdete v tématu [_set_sse2_enable –](set-sse2-enable.md).

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **ceil** trvají **float** nebo **dlouho** **dvojité** typy. V programu C **ceil** vždy provede a vrátí **dvojité**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ceil –**, **ceilf –**, **ceill –**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [podlaží](floor-floorf-floorl.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
