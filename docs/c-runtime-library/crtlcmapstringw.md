---
title: __crtLCMapStringW
ms.date: 11/04/2016
apiname:
- __crtLCMapStringW
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 0c3752baba05e18903c32919505d702081d09dca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344496"
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW

Jeden řetězec znaků se mapuje na jinou, probíhá zadané transformace závislé na národním prostředí. Tuto funkci můžete také použít ke generování klíče řazení pro vstupní řetězec.

## <a name="syntax"></a>Syntaxe

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>Parametry

*Národní prostředí*<br/>
Identifikátor národního prostředí. Národní prostředí, které poskytuje kontext pro řetězec mapování nebo generování klíče řazení. Aplikace může použít `MAKELCID` – makro vytvořit identifikátor národního prostředí.

*dwMapFlags*<br/>
Typ transformace, které se použijí při řetězec mapování nebo řazení generování klíčů.

*lpSrcStr*<br/>
Ukazatel na řetězec zdroj, který mapuje funkce nebo používá pro generování klíče řazení. Tento parametr je považován za řetězec znaků Unicode.

*cchSrc*<br/>
Velikost ve znacích, řetězce, na které odkazují `lpSrcStr` parametru. Tento počet můžete zahrnout ukončovacího znaku null, nebo ho.

A `cchSrc` hodnota -1, určuje, že řetězec s odkazem `lpSrcStr` je zakončený hodnotou null. Pokud tomu tak, a tato funkce se používá v režimu mapování řetězců, funkce vypočítá délku řetězce, samotný a null ukončí mapované řetězec uložen do `*lpDestStr`.

*lpDestStr*<br/>
Dlouhé ukazatel do vyrovnávací paměti, do které uloží funkce mapované řetězec nebo řazení klíč.

*cchDest*<br/>
Velikost ve znacích, vyrovnávací paměti, na které odkazuje `lpDestStr`.

## <a name="return-value"></a>Návratová hodnota

Pokud hodnota `cchDest` nenulovou hodnotu, je počet znaků nebo bajtů Pokud `LCMAP_SORTKEY` je zadán, zapsán do vyrovnávací paměti označuje úspěch. Tento počet zahrnuje místo pro ukončovacího znaku null.

Pokud hodnota `cchDest` je nula, velikost vyrovnávací paměti v znaků nebo bajtů, pokud `LCMAP_SORTKEY` je zadán pro příjem přeložená vyžaduje řetězec nebo řazení klíč označuje úspěch. Tato velikost zahrnuje místo pro ukončovacího znaku null.

Nula znamená selhání. Chcete-li získat rozšířené informace o chybě, zavolejte `GetLastError` funkce.

## <a name="remarks"></a>Poznámky

Pokud `cchSrc` je větší než nula a `lpSrcStr` je řetězec zakončený hodnotou null `__crtLCMapStringW` nastaví `cchSrc` na délku řetězce. Potom `__crtLCMapStringW` volá širokého řetězce (Unicode) verzi `LCMapString` funkce se zadanými parametry. Další informace o parametrech a vrácených hodnotách této funkce najdete v článku [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|