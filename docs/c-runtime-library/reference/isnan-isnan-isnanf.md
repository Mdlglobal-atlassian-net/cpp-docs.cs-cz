---
title: isNaN, _isnan –, _isnanf | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs:
- C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8552f59bc0d49ebae0d4a534225af5d9f5facb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="isnan-isnan-isnanf"></a>isNaN, _isnan –, _isnanf

Testy, pokud hodnotu s plovoucí desetinnou čárkou není číslo (NAN).

## <a name="syntax"></a>Syntaxe

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

V jazyce C **isnan** makro a **_isnan –** a **_isnanf** vracejí nenulovou hodnotu, pokud argument *x* typu NaN; v opačném případě se Vrátí 0.

V jazyce C++ **isnan** šablony funkce vrátí **true** Pokud argument *x* je NAN; v opačném případě, že budou vracet **false**.

## <a name="remarks"></a>Poznámky

C **isnan** makro a **_isnan –** a **_isnanf** funkce testování s plovoucí desetinnou čárkou *x*, vrátí nenulovou hodnotu, pokud *x* je hodnota číslo (NAN). NAN se vygeneruje, když ve formátu plovoucí desetinné čárky IEEE 754 pro zadaný typ není možné vyjádřit výsledek operace s plovoucí desetinnou čárkou. Informace o tom, jak je reprezentována NAN pro výstup najdete v tématu [printf](printf-printf-l-wprintf-wprintf-l.md).

Při kompilaci jako C++, **isnan** makro není definován a **isnan** funkce šablona je definována místo. Vrátí hodnotu typu **bool** místo celé číslo.

**_Isnan –** a **_isnanf** funkce se konkrétní společnosti Microsoft. **_Isnanf** funkce je dostupná pouze při zkompilovaném pro x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN**, **_isnanf**|\<Math.h >|\<Math.h > nebo \<cmath – >|
|**_isnan**|\<float.h – >|\<float.h – > nebo \<cfloat – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
