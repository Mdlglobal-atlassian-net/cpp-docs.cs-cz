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
ms.openlocfilehash: 8afb2019e38f7548467e85d9a2c1c12c538cf744
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276244"
---
# <a name="exception-handling-macros"></a>Makra zpracování výjimek

Tato makra poskytovat podporu pro zpracování výjimek.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.|
|[_ATLCATCHALL](#_atlcatchall)|Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.|
|[_ATLTRY](#_atltry)|Označí strážených kód části, kde může případně dojít k chybě.|

## <a name="requirements"></a>Požadavky:

**Záhlaví:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parametry

*e*<br/>
Výjimka pro zachycení.

### <a name="remarks"></a>Poznámky

Použít ve spojení s `_ATLTRY`. Přeloží na C++ [catch (catlexception – e)](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování daného typu výjimky jazyka C++.

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Poznámky

Použít ve spojení s `_ATLTRY`. Přeloží na C++ [catch(...) ](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování všech druhů výjimky jazyka C++.

##  <a name="_atltry"></a>  _ATLTRY

Označí strážených kód části, kde může případně dojít k chybě.

```
_ATLTRY
```

### <a name="remarks"></a>Poznámky

Použít ve spojení s [_ATLCATCH](#_atlcatch) nebo [_ATLCATCHALL](#_atlcatchall). Přeloží na symbolu C++ [zkuste](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Viz také:

[Makra](../../atl/reference/atl-macros.md)
