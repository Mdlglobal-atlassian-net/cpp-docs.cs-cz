---
title: Makra zpracování výjimek
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330090"
---
# <a name="exception-handling-macros"></a>Makra zpracování výjimek

Tato makra poskytují podporu pro zpracování výjimek.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Příkazy pro zpracování chyb vyskytujících `_ATLTRY`se v přidružené .|
|[_ATLCATCHALL](#_atlcatchall)|Příkazy pro zpracování chyb vyskytujících `_ATLTRY`se v přidružené .|
|[_ATLTRY](#_atltry)|Označí oddíl s hlídaným kódem, kde by mohlo dojít k chybě.|

## <a name="requirements"></a>Požadavky:

**Záhlaví:** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

Příkazy pro zpracování chyb vyskytujících `_ATLTRY`se v přidružené .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parametry

*E*<br/>
Výjimka catch.

### <a name="remarks"></a>Poznámky

Používá se `_ATLTRY`ve spojení s . Řeší na C++ [catch(CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování daného typu výjimky jazyka C++.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

Příkazy pro zpracování chyb vyskytujících `_ATLTRY`se v přidružené .

```
_ATLCATCHALL
```

### <a name="remarks"></a>Poznámky

Používá se `_ATLTRY`ve spojení s . Řeší do C++ [catch(...)](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování všech typů výjimek jazyka C++.

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

Označí oddíl s hlídaným kódem, kde by mohlo dojít k chybě.

```
_ATLTRY
```

### <a name="remarks"></a>Poznámky

Používá se ve spojení s [_ATLCATCH](#_atlcatch) nebo [_ATLCATCHALL](#_atlcatchall). Překládá na symbol [C++ zkuste](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
