---
title: fegetexceptflag
ms.date: 04/05/2018
api_name:
- fegetexceptflag
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: b840408ce704ad5519fbf233de41c8d5422006ad
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972179"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Ukládá aktuální stav zadaných příznaků výjimek s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Ukazatel na objekt **fexcept_t** , který obsahuje aktuální hodnoty příznaků výjimek určených *výjimkou*.

*s výjimkou*<br/>
Příznaky výjimky s plovoucí desetinnou čárkou pro uložení v *pStatus*.

## <a name="return-value"></a>Návratová hodnota

Po úspěchu vrátí hodnotu 0. V opačném případě vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Funkce **fegetexceptflag** ukládá aktuální stav příznaků stavu výjimky s plovoucí desetinnou čárkou, které jsou určeny *výjimkou* v objektu **fexcept_t** , na který odkazuje *pStatus*.  *pStatus* musí ukazovat na platný objekt **fexcept_t** , nebo následné chování není definováno. Funkce **fegetexceptflag** podporuje tato makra výjimek definovaná v \<fenv. h >:

|Makro výjimky|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě v záčísle nebo objektu. byla vytvořena hodnota nekonečno.|
|FE_INEXACT|Funkce byla nucena zaokrouhlit uložený výsledek předchozí operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsahu; předchozí výsledek operace s plovoucí desetinnou čárkou byl pro reprezentaci příliš velký.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malý, aby byl reprezentován s plnou přesností. byla vytvořena deběžná hodnota.|
|FE_ALL_EXCEPT|Bitové nebo všechny podporované výjimky s plovoucí desetinnou čárkou.|

Argument *excepts* může být nula, jedna z podporovaných maker výjimek s plovoucí desetinnou čárkou nebo bitovou nebo dvou nebo více makrů. Účinek jakékoli jiné hodnoty argumentu není definován.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace s plovoucí desetinnou čárkou, které by mohly zabránit přístupu pomocí direktivy `#pragma fenv_access(on)` před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
