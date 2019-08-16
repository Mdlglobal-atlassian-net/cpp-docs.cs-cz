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
ms.openlocfilehash: e79ac5d4072595ef1034a0483b9edc8eada916d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500217"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

Mapuje jeden řetězec znaků na jiný a provede zadanou transformaci závislé na národním prostředí. Tato funkce se dá použít také k vygenerování klíče řazení pro vstupní řetězec.

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
Identifikátor národního prostředí. Národní prostředí poskytuje kontext pro mapování řetězců nebo generování klíče řazení. Aplikace může pomocí `MAKELCID` makra vytvořit identifikátor národního prostředí.

*dwMapFlags*<br/>
Typ transformace, který má být použit při mapování řetězců nebo generování klíče řazení.

*lpSrcStr*<br/>
Ukazatel na zdrojový řetězec, který funkce mapuje nebo používá pro generování klíče řazení. Tento parametr se považuje za řetězec Unicode.

*cchSrc*<br/>
Velikost řetězce, na který odkazuje `lpSrcStr` parametr, ve znacích. Tento počet může zahrnovat ukončovací znak null nebo ho nesmí obsahovat.

Hodnota-1 určuje, že řetězec, `lpSrcStr` na který ukazuje, je zakončený hodnotou null. `cchSrc` Pokud se jedná o tento případ a tato funkce se používá v režimu mapování řetězců, funkce vypočítá vlastní délku řetězce a hodnotu null-ukončí mapovaný řetězec uložený v `*lpDestStr`.

*lpDestStr*<br/>
Dlouhodobý ukazatel na vyrovnávací paměť, do které funkce ukládá mapovaný řetězec nebo klíč řazení.

*cchDest*<br/>
Velikost, ve znacích, na vyrovnávací paměti, na `lpDestStr`kterou ukazuje.

## <a name="return-value"></a>Návratová hodnota

Pokud hodnota `cchDest` je nenulová, počet znaků nebo bajtů, pokud `LCMAP_SORTKEY` je zadán, zapsaný do vyrovnávací paměti indikuje úspěch. Tento počet zahrnuje místo pro ukončovací znak null.

Pokud je hodnota `cchDest` nula, je velikost vyrovnávací paměti ve znacích nebo v bajtech, pokud `LCMAP_SORTKEY` je zadána, vyžadována pro příjem přeloženého řetězce nebo klíč řazení, který označuje úspěch. Tato velikost zahrnuje místo pro ukončovací znak null.

Nula značí chybu. Chcete-li získat rozšířené informace o chybě `GetLastError` , zavolejte funkci.

## <a name="remarks"></a>Poznámky

Pokud `cchSrc` je větší než nula a `lpSrcStr` je řetězec zakončený hodnotou null, `__crtLCMapStringW` nastaví `cchSrc` na délku řetězce. Pak `__crtLCMapStringW` zavolá verzi `LCMapString` rozhraní s použitím rozhraní Unicode (roztažitelné String) funkce se zadanými parametry. Další informace o parametrech a vrácené hodnotě této funkce naleznete v tématu [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__crtLCMapStringW|awint. h|