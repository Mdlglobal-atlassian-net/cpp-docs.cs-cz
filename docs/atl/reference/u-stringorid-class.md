---
title: _U_STRINGorID – třída
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: c57d983e9680ce6d2cab375e427b80f4d3b6c2d6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739583"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID – třída

Tato třída adaptéru argumentu umožňuje předat názvy prostředků (LPCTSTRs) nebo ID prostředků (UINTs) funkci bez nutnosti volajícího převést ID na řetězec pomocí makra MAKEINTRESOURCE.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_STRINGorID
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identifikátor prostředku.|

## <a name="remarks"></a>Poznámky

Tato třída je navržená pro implementaci obálek do rozhraní API pro správu prostředků systému Windows, jako jsou funkce [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)a [LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw) , které přijímají Argument LPCTSTR, který může být buď název prostředku, nebo jeho ID.

Třída definuje dvě přetížení konstruktoru: jeden akceptuje Argument LPCTSTR a druhý akceptuje argument UINT. Argument UINT je převeden na typ prostředku kompatibilní s funkcemi správy prostředků systému Windows pomocí makra MAKEINTRESOURCE a výsledku uloženého v jednom datovém členu třídy [m_lpstr](#_u_stringorid__m_lpstr). Argument konstruktoru LPCTSTR je uložen přímo bez konverze.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

Třída obsahuje hodnotu předanou do některého z jeho konstruktorů jako veřejný datový člen LPCTSTR.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

Konstruktor UINT převede svůj argument na typ prostředku kompatibilní s funkcemi správy prostředků systému Windows pomocí makra MAKEINTRESOURCE a výsledek je uložen v jednom datovém členu třídy [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID prostředku.

*lpString*<br/>
Název prostředku.

### <a name="remarks"></a>Poznámky

Argument konstruktoru LPCTSTR je uložen přímo bez konverze.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
