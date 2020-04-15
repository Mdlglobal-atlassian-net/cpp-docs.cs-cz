---
title: třída _U_STRINGorID
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325828"
---
# <a name="_u_stringorid-class"></a>třída _U_STRINGorID

Tato třída adaptéru argument umožňuje názvy prostředků (LPCTSTRs) nebo ID prostředků (UINTs) být předány funkci bez nutnosti volajícího převést ID na řetězec pomocí makeintresource makro.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_STRINGorID
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identifikátor prostředku.|

## <a name="remarks"></a>Poznámky

Tato třída je určena pro implementaci obálky rozhraní API pro správu prostředků systému Windows, jako je [například FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)a [LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw) funkce, které přijímají argument LPCTSTR, který může být název prostředku nebo jeho ID.

Třída definuje dva přetížení konstruktoru: jeden přijímá argument LPCTSTR a druhý přijímá argument UINT. Argument UINT je převeden na typ prostředku kompatibilní s funkcemi správy prostředků systému Windows pomocí makra MAKEINTRESOURCE a výsledku uloženého v jediném datovém členu [třídy, m_lpstr](#_u_stringorid__m_lpstr). Argument konstruktoru LPCTSTR je uložen přímo bez převodu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

Třída obsahuje hodnotu předanou některému z jeho konstruktorů jako veřejný datový člen LPCTSTR.

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

Konstruktor UINT převede svůj argument na typ prostředku kompatibilní s funkcemi správy prostředků systému Windows pomocí makra MAKEINTRESOURCE a výsledek je uložen v jediném datovém členu třídy, [m_lpstr](#_u_stringorid__m_lpstr).

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
ID prostředku.

*lpString*<br/>
Název prostředku.

### <a name="remarks"></a>Poznámky

Argument konstruktoru LPCTSTR je uložen přímo bez převodu.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
