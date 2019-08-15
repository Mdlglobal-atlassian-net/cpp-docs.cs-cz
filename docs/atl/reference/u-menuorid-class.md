---
title: _U_MENUorID – třída
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 9388ca1751ee27fb25d6751c961d23e5243f2918
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495136"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID – třída

Tato třída poskytuje obálky pro `CreateWindow` a. `CreateWindowEx`

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_MENUorID
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Popisovač do nabídky|

## <a name="remarks"></a>Poznámky

Tato třída adaptéru argumentu umožňuje předání buď identifikátorů (UINT), nebo popisovačů nabídek (HMENUs) do funkce bez nutnosti explicitního přetypování na straně volajícího.

Tato třída je určena pro implementaci obálek do rozhraní API systému Windows, zejména funkcí [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) a [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) , z nichž obě přijímají argument HMENU, který může být podřízeným identifikátorem okna (uint), nikoli popisovačem nabídky. Tuto třídu můžete například zobrazit jako parametr, aby [CWindowImpl:: Create](cwindowimpl-class.md#create).

Třída definuje dvě přetížení konstruktoru: jeden akceptuje argument UINT a druhý akceptuje argument HMENU. Argument UINT je pouze přetypování na HMENU v konstruktoru a výsledek uložený v jediném datovém členu třídy [m_hMenu](#_u_menuorid__m_hmenu). Argument konstruktoru HMENU je uložen přímo bez konverze.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

Třída obsahuje hodnotu předanou do některého z jeho konstruktorů jako veřejný datový člen HMENU.

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

Argument UINT je pouze přetypování na HMENU v konstruktoru a výsledek uložený v jediném datovém členu třídy [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor podřízeného okna.

*hMenu*<br/>
Obslužná rutina nabídky

### <a name="remarks"></a>Poznámky

Argument konstruktoru HMENU je uložen přímo bez konverze.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
