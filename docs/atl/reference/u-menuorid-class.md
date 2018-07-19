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
ms.openlocfilehash: 0f945766283fa6e58b1eb3430cc780b1ae136e9f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884734"
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
  
 Tato třída slouží k implementaci obálek rozhraní Windows API, zejména [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) a [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkce, které přijímají argument HMENU, které mohou být podřízené okno identifikátor (UINT) spíše než popisovač nabídky. Například můžete zobrazit tato třída používá jako parametr [CWindowImpl::Create](cwindowimpl-class.md#create).  

  
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
 *nID*  
 Identifikátor podřízené okno.  
  
 *hMenu*  
 Popisovač nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Argument pro konstruktor HMENU ukládána přímo bez převodu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
