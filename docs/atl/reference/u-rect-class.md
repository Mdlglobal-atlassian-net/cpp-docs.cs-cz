---
title: _U_rect – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274522"
---
# <a name="urect-class"></a>_U_rect – třída

Tato třída argument adaptér umožňuje buď `RECT` ukazatele nebo odkazy, které se mají předat funkci, která je implementovaná jako ukazatele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_RECT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Ukazatel `RECT`.|

## <a name="remarks"></a>Poznámky

Třída definuje dvě přetížení konstruktoru: jeden přijímá **RECT &** přijímá argument a druhý `LPRECT` argument. První konstruktor uloží adresa argument odkazu single – datový člen třídy, [m_lpRect](#_u_rect__m_lprect). Argument pro konstruktor ukazatel se ukládají přímo bez převodu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

Třída obsahuje hodnotu předanou buď z jejích konstruktorů jako veřejnou `LPRECT` datový člen.

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

Adresa argument odkazu je uložen v single – datový člen třídy, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*rc*<br/>
A `RECT` odkaz.

*lpRect*<br/>
A `RECT` ukazatele.

### <a name="remarks"></a>Poznámky

Argument pro konstruktor ukazatel se ukládají přímo bez převodu.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
