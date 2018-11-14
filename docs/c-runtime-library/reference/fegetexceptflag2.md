---
title: fegetexceptflag
ms.date: 04/05/2018
apiname:
- fegetexceptflag
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: 43259001bd05bb7df9e2e1636c174018dcdaef3c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522646"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Uloží aktuální stav příznaky zadané výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Ukazatel **fexcept_t** objekt obsahovat aktuální hodnoty příznaky výjimky určené *, s výjimkou*.

*s výjimkou*<br/>
Příznaky výjimky s plovoucí desetinnou čárkou k ukládání *pstatus*.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. V opačném případě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Fegetexceptflag** uloží aktuální stav příznaky stavu výjimky s plovoucí desetinnou čárkou určené funkce *, s výjimkou* v **fexcept_t** objekt, který odkazuje *pstatus*.  *pstatus* musí odkazovat na platný **fexcept_t** objektu nebo následné chování není definováno. **Fegetexceptflag** funkce podporuje těchto maker výjimek definovaných v \<fenv.h >:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pole byl vytvořen hodnotu nekonečno.|
|FE_INEXACT|Funkce musela být zaokrouhlit uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V rámci starší operace s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsah; předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš velký a nelze je reprezentovat.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malá, aby se dala vyjádřit v úplnou přesností; byl vytvořen nenormální hodnota.|
|FE_ALLEXCEPT|Bitový operátor OR všech nepodporuje výjimky s plovoucí desetinnou čárkou.|

*, S výjimkou* argument může být nula, jeden makra podporované výjimek s plovoucí desetinnou čárkou nebo bitový nebo dvě nebo více z makra. Účinek libovolné jiné hodnoty argumentu není definován.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
