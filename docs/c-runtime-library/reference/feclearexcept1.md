---
title: feclearexcept1
ms.date: 04/05/2018
apiname:
- feclearexcept
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
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 3c2f037a5be903fc006debfa7319c483431fdd92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334733"
---
# <a name="feclearexcept"></a>feclearexcept

Pokusí se Vymazat příznaky výjimky s plovoucí desetinnou čárkou určený argumentem.

## <a name="syntax"></a>Syntaxe

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Příznaky výjimky stav vymazání.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud *, s výjimkou* je nula, nebo pokud byly úspěšně vymazal všechny zadané výjimky. V opačném případě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Feclearexcept** pokusí funkce zrušte plovoucí bod příznaky výjimky stav určeného *, s výjimkou*. Funkce podporuje těchto maker výjimek definovaných v fenv.h:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pole byl vytvořen hodnotu nekonečno.|
|FE_INEXACT|Funkce musela být zaokrouhlit uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V rámci starší operace s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsah; předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš velký a nelze je reprezentovat.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malá, aby se dala vyjádřit v úplnou přesností; byl vytvořen nenormální hodnota.|
|FE_ALL_EXCEPT|Bitový operátor OR všech nepodporuje výjimky s plovoucí desetinnou čárkou.|

*, S výjimkou* argument může být nula nebo bitový operátor OR jednoho nebo více z maker výjimek podporované. Výsledek libovolné jiné hodnoty argumentu není definován.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
