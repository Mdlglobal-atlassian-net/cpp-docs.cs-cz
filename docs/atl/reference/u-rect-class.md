---
title: _U_RECT třída
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325814"
---
# <a name="_u_rect-class"></a>_U_RECT třída

Tato třída adaptéru `RECT` argument umožňuje ukazatele nebo odkazy, které mají být předány funkce, která je implementována z hlediska ukazatelů.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_RECT
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Ukazatel na `RECT`.|

## <a name="remarks"></a>Poznámky

Třída definuje dva přetížení konstruktoru: jeden přijímá **RECT&** argument `LPRECT` a druhý přijímá argument. První konstruktor ukládá adresu referenčního argumentu do jediného datového člena třídy, [m_lpRect](#_u_rect__m_lprect). Argument konstruktoru ukazatele je uložen přímo bez převodu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT::m_lpRect

Třída obsahuje hodnotu předanou některému z `LPRECT` jeho konstruktorů jako člen veřejných dat.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT::_U_RECT

Adresa referenčního argumentu je uložena v jediném datovém členu třídy, [m_lpRect](#_u_rect__m_lprect).

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Rc*<br/>
Odkaz. `RECT`

*lpRect*<br/>
Ukazatel. `RECT`

### <a name="remarks"></a>Poznámky

Argument konstruktoru ukazatele je uložen přímo bez převodu.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
