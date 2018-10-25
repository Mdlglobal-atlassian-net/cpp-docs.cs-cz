---
title: _U_menuorid – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3eb9ab5f08fe1984e52ed16eb26064093fb8e003
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052951"
---
# <a name="umenuorid-class"></a>_U_menuorid – třída

Tato třída poskytuje obálky pro `CreateWindow` a `CreateWindowEx`.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class _U_MENUorID
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Konstruktor|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Popisovač nabídky.|

## <a name="remarks"></a>Poznámky

Tato třída argument adaptér umožňuje ID (uvedený) nebo nabídku popisovače (HMENUs), které se mají předat funkci bez nutnosti explicitního přetypování straně volajícího.

Tato třída slouží k implementaci obálek rozhraní Windows API, zejména [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) a [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkce, které přijímají argument HMENU, které mohou být podřízené okno identifikátor (UINT) spíše než popisovač nabídky. Například můžete zobrazit tato třída používá jako parametr [CWindowImpl::Create](cwindowimpl-class.md#create).

Třída definuje dvě přetížení konstruktoru: přijímá jeden UINT argument a druhý HMENU argument. UINT argumentu je stačí přetypován na HMENU v konstruktoru a výsledek uložený v single – datový člen třídy, [m_hMenu](#_u_menuorid__m_hmenu). Argument pro konstruktor HMENU ukládána přímo bez převodu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu

Třída obsahuje hodnotu předanou jako veřejné datový člen HMENU některou z jejích konstruktorů.

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID

UINT argumentu je stačí přetypován na HMENU v konstruktoru a výsledek uložený v single – datový člen třídy, [m_hMenu](#_u_menuorid__m_hmenu).

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor podřízené okno.

*hMenu*<br/>
Popisovač nabídky.

### <a name="remarks"></a>Poznámky

Argument pro konstruktor HMENU ukládána přímo bez převodu.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
