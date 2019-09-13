---
title: feupdateenv
ms.date: 04/05/2018
api_name:
- feupdateenv
api_location:
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
api_type:
- HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 8f40cab42e4a89b1fc5a100587b11b0e2aeeb55c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940978"
---
# <a name="feupdateenv"></a>feupdateenv

Uloží aktuálně vyvolané výjimky s plovoucí desetinnou čárkou, obnoví zadaný stav prostředí s plovoucí desetinnou čárkou a potom vyvolá uložené výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel na objekt **fenv_t** , který obsahuje prostředí s plovoucí desetinnou čárkou, jak je nastaveno voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Pomocí makra FE_DFL_ENV můžete také určit výchozí prostředí s plovoucí desetinnou čárkou, které je spouštěno.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud všechny akce byly úspěšně dokončeny. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **feupdateenv** provádí několik akcí. Za prvé ukládá aktuální vyvolání příznaků stavu výjimek s plovoucí desetinnou čárkou v automatickém úložišti. Pak nastaví aktuální prostředí s plovoucí desetinnou čárkou z hodnoty uložené v objektu **fenv_t** , na který odkazuje *penv*. Pokud *penv* není **FE_DFL_ENV** nebo neukazuje na platný objekt **fenv_t** , následné chování není definováno. Nakonec **feupdateenv** vyvolává místně uložené výjimky s plovoucí desetinnou čárkou.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace plovoucí desetinné čárky, které by mohly zabránit přístupu `#pragma fenv_access(on)` pomocí direktivy před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
