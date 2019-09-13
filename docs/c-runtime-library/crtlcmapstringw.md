---
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 8d9458529e5772f31e3ae5463d3a6ff5a7b726e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940450"
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