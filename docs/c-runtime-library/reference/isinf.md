---
title: isinf –
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: be99970a0c7b152ba213eabd59b53a7503cd3c54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331607"
---
# <a name="isinf"></a>isinf –

Určuje, zda s plovoucí desetinnou čárkou hodnota nekonečno.

## <a name="syntax"></a>Syntaxe

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

**isinf –** vrací nenulovou hodnotu (**true** v kódu jazyka C++) Pokud je argument *x* je kladné nebo záporné nekonečno. **isinf –** vrátí hodnotu 0 (**false** v kódu jazyka C++) Pokud je argumentem konečná nebo NAN. Normální a subnormal hodnoty s plovoucí desetinnou čárkou jsou považovány za omezené.

## <a name="remarks"></a>Poznámky

**isinf –** je makro při kompilaci jako C a vložené funkce šablony při kompilaci jako C++.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<Math.h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
