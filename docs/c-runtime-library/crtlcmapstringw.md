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
ms.openlocfilehash: f239d95c0dfd50f765b6f23d7874f01dce085054
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170992"
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
Identifikátor národního prostředí. Národní prostředí poskytuje kontext pro mapování řetězců nebo generování klíče řazení. Aplikace může pomocí makra `MAKELCID` vytvořit identifikátor národního prostředí.

*dwMapFlags*<br/>
Typ transformace, který má být použit při mapování řetězců nebo generování klíče řazení.

*lpSrcStr*<br/>
Ukazatel na zdrojový řetězec, který funkce mapuje nebo používá pro generování klíče řazení. Tento parametr se považuje za řetězec Unicode.

*cchSrc*<br/>
Velikost řetězce, na který ukazuje parametr `lpSrcStr`, ve znacích Tento počet může zahrnovat ukončovací znak null nebo ho nesmí obsahovat.

Hodnota `cchSrc`-1 určuje, že řetězec, na který se odkazuje pomocí `lpSrcStr`, je zakončený hodnotou null. Pokud se jedná o tento případ a tato funkce se používá v režimu mapování řetězců, funkce vypočítá vlastní délku řetězce a hodnotu null-ukončí mapovaný řetězec uložený do `*lpDestStr`.

*lpDestStr*<br/>
Dlouhodobý ukazatel na vyrovnávací paměť, do které funkce ukládá mapovaný řetězec nebo klíč řazení.

*cchDest*<br/>
Velikost vyrovnávací paměti ve znacích, na kterou ukazuje `lpDestStr`.

## <a name="return-value"></a>Návratová hodnota

Pokud je hodnota `cchDest` nenulová, počet znaků nebo bajtů, pokud je `LCMAP_SORTKEY` zadáno, zapsané do vyrovnávací paměti označují úspěch. Tento počet zahrnuje místo pro ukončovací znak null.

Pokud je hodnota `cchDest` nula, je velikost vyrovnávací paměti ve znacích nebo v bajtech, pokud je zadána `LCMAP_SORTKEY`, vyžadována pro příjem přeloženého řetězce nebo klíč řazení, který označuje úspěch. Tato velikost zahrnuje místo pro ukončovací znak null.

Nula značí chybu. Chcete-li získat rozšířené informace o chybě, zavolejte funkci `GetLastError`.

## <a name="remarks"></a>Poznámky

Pokud je `cchSrc` větší než nula a `lpSrcStr` je řetězec zakončený hodnotou null, `__crtLCMapStringW` sady `cchSrc` na délku řetězce. Pak `__crtLCMapStringW` zavolá verzi "`LCMapString` funkce s velkým řetězcem" (Unicode) se zadanými parametry. Další informace o parametrech a vrácené hodnotě této funkce naleznete v tématu [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__crtLCMapStringW|awint. h|
