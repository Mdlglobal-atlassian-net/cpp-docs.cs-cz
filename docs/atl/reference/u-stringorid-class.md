---
title: _U_stringorid – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 000e43926a83bdd7457c33c656383ae44dce6259
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046274"
---
# <a name="ustringorid-class"></a>_U_stringorid – třída

Tato třída argument adaptér umožňuje názvy prostředků (LPCTSTRs) nebo ID prostředků (uvedený), které se mají předat funkci bez nutnosti volajícího k převodu na řetězec za použití makra MAKEINTRESOURCE ID.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_STRINGorID
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identifikátor URI.|

## <a name="remarks"></a>Poznámky

Tato třída slouží k implementaci obálky pro správu prostředků Windows API, jako [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona), a [LoadMenu](/windows/desktop/api/winuser/nf-winuser-loadmenua) funkce, které přijímají LPCTSTR argument, který může být název prostředku nebo ID.

Třída definuje dvě přetížení konstruktoru: přijímá jeden LPCTSTR argument a druhý UINT argument. UINT argument je převeden na typ prostředku, který je kompatibilní s funkcí správy prostředků Windows – makro MAKEINTRESOURCE a výsledek uložený v single – datový člen třídy, [m_lpstr](#_u_stringorid__m_lpstr). Argument pro konstruktor LPCTSTR ukládána přímo bez převodu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

Třída obsahuje hodnotu předanou jako veřejné datový člen LPCTSTR některou z jejích konstruktorů.

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

Konstruktor UINT Převede argument na typ prostředku, který je kompatibilní s funkcí správy prostředků Windows makro MAKEINTRESOURCE a výsledek je uložen v single – datový člen třídy, [m_lpstr](#_u_stringorid__m_lpstr).

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

Argument pro konstruktor LPCTSTR ukládána přímo bez převodu.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
