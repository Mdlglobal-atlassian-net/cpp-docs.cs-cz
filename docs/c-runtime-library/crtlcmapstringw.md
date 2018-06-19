---
title: __crtLCMapStringW | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b25f94b1127d1212ed5f44235ce48b363c6124dc
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451950"
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW
Mapuje jeden řetězec znaků do jiné, provádění Zadaná transformace závislých na národním prostředí. Tuto funkci lze také vygenerovat klíč řazení pro vstupní řetězec.  
  
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
 `Locale`  
 Identifikátor národního prostředí. Národní prostředí poskytuje kontext pro mapování řetězec nebo generování klíčů pro řazení. Aplikace můžete použít `MAKELCID` makra vytvořit identifikátor národního prostředí.  
  
 `dwMapFlags`  
 Typ transformace, které mají být použity během řetězec mapování nebo řazení generování klíče.  
  
 `lpSrcStr`  
 Ukazatel na zdrojový řetězec, který mapuje funkce nebo používá pro generování klíčů pro řazení. Tento parametr se předpokládá, že jako řetězec znaků Unicode.  
  
 `cchSrc`  
 Velikost v znaků řetězce, na kterou odkazuje `lpSrcStr` parametr. Tento počet zahrnout ukončení hodnotu null, nebo není její zahrnutí.  
  
 A `cchSrc` hodnota -1 určuje, že řetězec na kterou odkazuje `lpSrcStr` je ukončené hodnotou null. Pokud ano, a tato funkce se používá v režimu řetězec mapování, vypočítá délku řetězce samotné funkce a null ukončí namapované řetězec uložena do `*lpDestStr`.  
  
 `lpDestStr`  
 Dlouhé ukazatel na vyrovnávací paměť, do které uloží funkce namapované klíč řetězec nebo řazení.  
  
 `cchDest`  
 Velikost vyrovnávací paměti, na kterou odkazuje znakům `lpDestStr`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud hodnota `cchDest` je nenulové hodnoty, počtu znaků nebo bajtů Pokud `LCMAP_SORTKEY` je zadán, zapisovat do vyrovnávací paměti označuje úspěch. Tento počet zahrnuje prostor pro zakončením hodnotu null.  
  
 Pokud hodnota `cchDest` nula, velikost vyrovnávací paměti v znaků nebo bajtů, pokud je `LCMAP_SORTKEY` není zadaný, vyžaduje pro příjem přeložená řetězec nebo řazení klíč označuje úspěch. Tato velikost zahrnuje prostor pro zakončením hodnotu null.  
  
 Nula naznačuje chybu. Chcete-li získat rozšířené informace o chybě, zavolejte `GetLastError` funkce.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `cchSrc` je větší než nula a `lpSrcStr` je řetězce ukončené hodnotou null, `__crtLCMapStringW` nastaví `cchSrc` na délku řetězce. Potom `__crtLCMapStringW` volá široké řetězec (Unicode) verzi `LCMapString` funkce se zadanými parametry. Další informace o parametry a návratové hodnoty této funkce najdete v tématu `LCMapString` fungovat v [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__crtLCMapStringW|awint.h|