---
title: fesetexceptflag | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec9be76fd0d860385ac53cfc70ea89d00ae2b1ef
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fesetexceptflag"></a>fesetexceptflag

Nastaví příznaky zadaný stav s plovoucí desetinnou čárkou v aktuálním prostředí s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>Parametry

*pstatus*<br/>
Ukazatel na **fexcept_t** objekt obsahující hodnoty, které lze nastavit výjimky příznaky stavu. Objekt může být nastaven na předchozím voláním [fegetexceptflag](fegetexceptflag2.md).

*s výjimkou*<br/>
Příznaky stavu výjimek plovoucí desetinné čárky nastavit.

## <a name="return-value"></a>Návratová hodnota

Pokud mají všechny zadané výjimky příznaky stavu úspěšně, vrátí hodnotu 0. Jinak vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Fesetexceptflag** funkce nastaví stav příznaky stavu výjimek plovoucí desetinné čárky určeného *, s výjimkou* na odpovídající hodnoty nastavení **fexcept_t** objekt na kterou odkazuje *pstatus*.  Tato možnost nevyvolá výjimky. *Pstatus* ukazatel musí odkazovat na platný **fexcept_t** objekt nebo následné chování není definován. **Fesetexceptflag** funkce podporuje tyto hodnoty makro výjimka v *, s výjimkou*, definované v \<fenv.h >:

|Výjimka – makro|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dříve s plovoucí desetinnou čárkou operace; došlo k chybě singularity nebo pólu byl vytvořen nekonečnou hodnotu.|
|FE_INEXACT|Funkce musela být zaokrouhleno uložený výsledek dříve operace s plovoucí desetinnou čárkou.|
|FE_INVALID|Došlo k chybě domény v dříve operaci s plovoucí desetinnou čárkou.|
|FE_OVERFLOW|Rozsah došlo k chybě; výsledek operace s plovoucí desetinnou čárkou starší byl příliš velký a nelze je.|
|FE_UNDERFLOW|Výsledek operace s plovoucí desetinnou čárkou starší byla příliš malé a nelze na úplné přesnost; Hodnota denormal byla vytvořena.|
|FE_ALLEXCEPT|Bitová hodnota OR všech podporována s plovoucí desetinnou čárkou výjimky.|

*, S výjimkou* argument může být nula, jednoho z podporovaných výjimek plovoucí desetinné čárky makra nebo bitové hodnotě nebo dvou nebo více makra. Účinek jakoukoli jinou hodnotu argumentu není definován.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
