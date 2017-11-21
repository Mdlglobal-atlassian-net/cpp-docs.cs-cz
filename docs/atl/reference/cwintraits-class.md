---
title: "Třída CWinTraits | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs: C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fecb7c614320c202a1159a527b34159c01099af6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cwintraits-class"></a>CWinTraits – třída
Tato třída poskytuje metody pro standardizaci styly použité při vytváření objektu okno.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>Parametry  
 `t_dwStyle`  
 Výchozí styly standardní okno.  
  
 `t_dwExStyle`  
 Výchozí rozšířené styly oken.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statické) Načte rozšířené styly pro `CWinTraits` objektu.|  
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statické) Načte standardní styly pro `CWinTraits` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 To [okno Vlastnosti](../../atl/understanding-window-traits.md) třída poskytuje jednoduchý způsob standardizace styly využívané pro vytvoření objektu knihovny ATL okno. Použít specializace této třídy jako parametr šablony, který se [CWindowImpl](../../atl/reference/cwindowimpl-class.md) nebo jiné tříd oken ATL na zadat výchozí standardní a rozšířené styly využívané pro instance této třídy oken.  
  
 Tuto šablonu použít, pokud chcete zadat výchozí styly oken, které se použijí jenom v případě, že nejsou zadány žádné jiné styly ve volání [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 ATL obsahuje tři předdefinované specializací této šablony pro běžně používané kombinace styly oken:  
  
 `CControlWinTraits`  
 Určená pro okno standardního ovládacího prvku. Jsou použity následující standardní styly: **ws_child –**, **ws_visible –**, **ws_clipchildren –**, a **ws_clipsiblings –**. Neexistují žádné rozšířené styly.  
  
 `CFrameWinTraits`  
 Určená pro standardní rámce okna. Zahrnují standardní styly využívané: **ws_overlappedwindow –**, **ws_clipchildren –**, a **ws_clipsiblings –**. Rozšířené styly využívané patří: **ws_ex_appwindow –** a **ws_ex_windowedge –**.  
  
 `CMDIChildWinTraits`  
 Určená pro standardní podřízeného okna MDI. Zahrnují standardní styly využívané: **ws_overlappedwindow –**, **ws_child –**, **ws_visible –**, **ws_clipchildren –**a **Ws_clipsiblings –**. Rozšířené styly využívané patří: **ws_ex_mdichild –**.  
  
 Pokud chcete zajistit, že určité styly nastavené pro všechny instance třídy okno při současném povolení dalších styly nastavení na základě jednotlivých instancí použít [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraits::GetWndStyle  
 Volání této funkce načíst standardní stylů `CWinTraits` objektu.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Standardní styly použit pro vytvoření časového období. Pokud `dwStyle` 0, hodnoty styl šablony ( `t_dwStyle`) jsou vráceny. Pokud `dwStyle` nenulový, `dwStyle` je vrácen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní okno Styly objektu.  
  
##  <a name="getwndexstyle"></a>CWinTraits::GetWndExStyle  
 Volání této funkce načíst rozšířené stylů `CWinTraits` objektu.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Rozšířené styly použit pro vytvoření časového období. Pokud `dwExStyle` 0, hodnoty styl šablony ( `t_dwExStyle`) jsou vráceny. Pokud `dwExStyle` nenulový, `dwExStyle` je vrácen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozšířené styly oken objektu.  
  
## <a name="see-also"></a>Viz také  
 [Členy třídy](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Principy vlastnosti – okno](../../atl/understanding-window-traits.md)
