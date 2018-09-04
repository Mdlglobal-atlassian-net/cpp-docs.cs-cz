---
title: Cwintraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40c8404ad2f2ab56849bed22a15bd10805888d3c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690687"
---
# <a name="cwintraits-class"></a>Cwintraits – třída
Tato třída poskytuje metody pro standardizaci stylů použitých při vytváření objektu okno.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>Parametry  
 *t_dwStyle*  
 Výchozí styly standardní okno.  
  
 *t_dwExStyle*  
 Rozšířené styly oken ve výchozím nastavení.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statické) Načte rozšířené styly `CWinTraits` objektu.|  
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statické) Načte standardní styly `CWinTraits` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 To [vlastností okna](../../atl/understanding-window-traits.md) třída poskytuje jednoduchý způsob pro standardizaci stylů použitých pro vytvoření objektu ATL okna. Použít jako parametr šablony specializace této třídy [CWindowImpl](../../atl/reference/cwindowimpl-class.md) nebo jiného tříd oken ATL. Chcete-li určit výchozí standardní a rozšířené stylů použitých pro instance této třídy okna.  
  
 Tuto šablonu použít, pokud chcete zadat výchozí styly oken, které budou použity pouze v případě, že žádné další styly jsou zadány při volání funkce [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 Knihovna ATL poskytuje tři předdefinované specializace této šablony pro běžně používané kombinací styly oken:  
  
 `CControlWinTraits`  
 Navržené pro standardní ovládací prvek okno. Jsou použity následující standardní styly: WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Neexistují žádné rozšířené styly.  
  
 `CFrameWinTraits`  
 Navržené pro standardní rámce okna. Zahrnují standardní stylů použitých: WS_OVERLAPPEDWINDOW WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Rozšířené styly využívané zahrnují: WS_EX_APPWINDOW a WS_EX_WINDOWEDGE.  
  
 `CMDIChildWinTraits`  
 Navržené pro standardní podřízené okno MDI. Zahrnují standardní stylů použitých: WS_OVERLAPPEDWINDOW WS_CHILD, WS_VISIBLE, WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Rozšířené styly využívané zahrnují: WS_EX_MDICHILD.  
  
 Pokud chcete mít jistotu, že určité styly jsou nastavené pro všechny instance třídy okna při umožňující nastavit na základě jednotlivé instance i jiné styly použijte [cwintraitsor –](../../atl/reference/cwintraitsor-class.md) místo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="getwndstyle"></a>  CWinTraits::GetWndStyle  
 Volání této funkce načtete standardní stylů `CWinTraits` objektu.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Standardní stylů použitých pro vytvoření okna. Pokud *dwStyle* je 0, hodnoty šablony stylů (`t_dwStyle`) jsou vráceny. Pokud *dwStyle* nenulové, *dwStyle* je vrácena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní okno Styly objektu.  
  
##  <a name="getwndexstyle"></a>  CWinTraits::GetWndExStyle  
 Voláním této funkce načtete rozšířené styly `CWinTraits` objektu.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Rozšířené stylů použitých pro vytvoření okna. Pokud *dwExStyle* je 0, hodnoty šablony stylů (`t_dwExStyle`) jsou vráceny. Pokud *dwExStyle* nenulové, *dwExStyle* je vrácena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozšířené styly oken objektu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Principy vlastností okna](../../atl/understanding-window-traits.md)
