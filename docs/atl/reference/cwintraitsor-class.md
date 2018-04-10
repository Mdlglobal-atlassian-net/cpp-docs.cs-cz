---
title: Třída CWinTraitsOR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac6cf07fcd6d3703ffb6b483ba19a2d12520cb0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR – třída
Tato třída poskytuje metody pro standardizaci styly použité při vytváření objektu okno.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>Parametry  
 `t_dwStyle`  
 Výchozí styly oken.  
  
 `t_dwExStyle`  
 Výchozí rozšířené styly oken.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Načte rozšířené styly pro `CWinTraitsOR` objektu.|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Načte standardní styly pro `CWinTraitsOR` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 To [okno Vlastnosti](../../atl/understanding-window-traits.md) třída poskytuje jednoduchý způsob standardizace styly využívané pro vytvoření objektu knihovny ATL okno. Použít specializace této třídy jako parametr šablony, který se [CWindowImpl](../../atl/reference/cwindowimpl-class.md) nebo jiné tříd oken ATL pro k určení minimální sadu standardních a rozšířené styly má být použit pro instance této třídy oken.  
  
 Použijte specializace této šablony, pokud chcete zajistit, že určité styly jsou nastavené pro všechny instance třídy okno při umožňující další styly nastavení na základě instance ve volání [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 Pokud chcete zadat výchozí styly oken, které se použijí jenom v případě, že nejsou zadány žádné jiné styly ve volání `CWindowImpl::Create`, použijte [CWinTraits](../../atl/reference/cwintraits-class.md) místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 Volání této funkce načíst kombinací (s použitím logický operátor OR) standardní stylů `CWinTraits` objekt a výchozí styly určeného `t_dwStyle`.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Styly využívané pro vytvoření časového období.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kombinace stylů, které se předávají v `dwStyle` a ve výchozím nastavení těch, které jsou určeného `t_dwStyle`, pomocí logický operátor OR.  
  
##  <a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 Volání této funkce načíst kombinací (s použitím logický operátor OR) rozšířené stylů `CWinTraits` objekt a výchozí styly určeného `t_dwStyle`.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Rozšířené styly použit pro vytvoření časového období.  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozšířené styly, které se předávají v kombinaci `dwExStyle` zadaných ve výchozích a `t_dwExStyle`, pomocí logický operátor OR  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Principy vlastností okna](../../atl/understanding-window-traits.md)

