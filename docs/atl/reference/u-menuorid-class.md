---
title: _U_MENUorID třída
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325837"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID třída

Tato třída poskytuje `CreateWindow` obálky pro a `CreateWindowEx`.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_MENUorID
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Úchyt k nabídce.|

## <a name="remarks"></a>Poznámky

Tato třída adaptéru argument umožňuje buď ID (UINTs) nebo popisovače nabídky (HMENU) být předány funkce bez nutnosti explicitní přetypování na straně volajícího.

Tato třída je určena pro implementaci obálky rozhraní API systému Windows, zejména [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) a [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) funkce, které přijímají hmenu argument, který může být identifikátor podřízené okno (UINT) spíše než popisovač nabídky. Například můžete vidět tuto třídu v použití jako parametr [CWindowImpl::Create](cwindowimpl-class.md#create).

Třída definuje dvě přetížení konstruktoru: jeden přijímá argument UINT a druhý přijímá argument HMENU. UINT Argument je právě přetypována HMENU v konstruktoru a výsledek uloženv jedné datové člen třídy, [m_hMenu](#_u_menuorid__m_hmenu). Argument konstruktoru HMENU je uložen přímo bez převodu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

Třída obsahuje hodnotu předanou některému z jeho konstruktorů jako veřejný datový člen HMENU.

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

UINT Argument je právě přetypována HMENU v konstruktoru a výsledek uloženv jedné datové člen třídy, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Podřízený identifikátor okna.

*hNabídka*<br/>
Úchyt nabídky.

### <a name="remarks"></a>Poznámky

Argument konstruktoru HMENU je uložen přímo bez převodu.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
