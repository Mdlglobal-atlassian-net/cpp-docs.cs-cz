---
title: "Třída _U_MENUorID | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs: C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ddde6ff5d45c90e675bd2e44ac421e840d1357b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="umenuorid-class"></a>_U_MENUorID – třída
Tato třída poskytuje obálek pro **CreateWindow** a **CreateWindowEx**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
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
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Popisovač pro nabídky.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída argument adaptér umožňuje buď ID ( **Celé_číslo**s) nebo nabídky obslužné rutiny ( `HMENU`s) mají být předány funkce bez nutnosti explicitní přetypování v části volajícího.  
  
 Tato třída slouží k implementaci obálky rozhraní API systému Windows, zejména v [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) a [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkce, které přijímají `HMENU` argument, který může být podřízeným okno identifikátor ( **Celé_číslo**) namísto popisovač nabídky. Například můžete zobrazit tuto třídu používá jako parametr, který se [CWindowImpl::Create](cwindowimpl-class.md#create).  

  
 Třída definuje dvě přetížení konstruktor: jeden přijme **Celé_číslo** argument a dalších přijímá `HMENU` argument. **Celé_číslo** argument je právě přetypovat `HMENU` v konstruktoru a výsledek uložený v single – datový člen dané třídy, [m_hMenu](#_u_menuorid__m_hmenu). Argument `HMENU` konstruktor ukládána přímo bez převodu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu  
 Třída obsahuje hodnotu předanou buď jeho konstruktory jako veřejné `HMENU` – datový člen.  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID  
 **Celé_číslo** argument je právě přetypovat `HMENU` v konstruktoru a výsledek uložený v single – datový člen dané třídy, [m_hMenu](#_u_menuorid__m_hmenu).  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor podřízené okno.  
  
 `hMenu`  
 Popisovač nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Argument `HMENU` konstruktor ukládána přímo bez převodu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
