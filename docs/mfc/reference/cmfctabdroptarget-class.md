---
title: Třída CMFCTabDropTarget | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53988248ac183fd551d100ede29648bcecd067f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372911"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget – třída
Poskytuje mechanismus komunikace mezi ovládacího prvku karta a knihoven OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Voláno rámcem, když uživatel nastavuje tažením objekt do okna Karta. (Přepisuje [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|  
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Voláno rámcem, když uživatel nastavuje tažením objekt mimo okno karty, který má právě fokus. (Přepisuje [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|  
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Voláno rámcem, když uživatel nastavuje tažením objektu na kartě okně, které má právě fokus. (Přepisuje [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|  
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Voláno rámcem, když uživatel uvolní tlačítko myši na konci operace přetažení. (Přepisuje [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|  
|[CMFCTabDropTarget::Register](#register)|Zaregistruje ovládacího prvku jako ten, který může být cílem operace přetažení myší OLE.|  
  
### <a name="remarks"></a>Poznámky  
 Tato třída poskytuje podporu přetahování myší, aby `CMFCBaseTabCtrl` třídy. Pokud vaše aplikace inicializuje knihoven OLE pomocí [AfxOLEInit –](ole-initialization.md#afxoleinit) funkce, `CMFCBaseTabCtrl` objekty zaregistrovat pro operací přetažení myší.  
  
 `CMFCTabDropTarget` Třída rozšiřuje její základní třída tím, že na kartu, která je pod kurzor, dojde-li operaci přetažení aktivní. Další informace o operací přetažení myší najdete v tématu [přetažení a Drop (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCTabDropTarget` objektu a použít jeho `Register` metoda.  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbasetabctrl.h  
  
##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter  
 Voláno rámcem, když uživatel nastavuje tažením objekt do okna Karta.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] `pWnd`|Nepoužívá se.|  
|[v] `pDataObject`|Ukazatel na objekt, který uživatel nastavuje tažením.|  
|[v] `dwKeyState`|Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, a `MK_RBUTTON`.|  
|[v] `point`|Umístění kurzoru v souřadnicích klienta.|  
  
### <a name="return-value"></a>Návratová hodnota  
 O tom, že výsledků Pokud rozevíracího dochází v umístění, které `point`. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `DROPEFFECT_NONE` Pokud nástrojů framework není v režimu přizpůsobení nebo formát dat schránky není k dispozici. Jinak vrátí výsledek volání `CMFCBaseTabCtrl::OnDragEnter` s zadané parametry.  
  
 Další informace o přizpůsobení režimu najdete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formáty dat schránky najdete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave  
 Voláno rámcem, když uživatel nastavuje tažením objekt mimo okno karty, který má právě fokus.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] `pWnd`|Nepoužívá se.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá `CMFCBaseTabCtrl::OnDragLeave` metoda k provedení operace přetažení.  
  
##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver  
 Voláno rámcem, když uživatel nastavuje tažením objektu na kartě okně, které má právě fokus.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] `pWnd`|Nepoužívá se.|  
|[v] `pDataObject`|Ukazatel na objekt, který uživatel nastavuje tažením.|  
|[v] `dwKeyState`|Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, a `MK_RBUTTON`.|  
|[v] `point`|Umístění ukazatele myši v souřadnice klienta.|  
  
### <a name="return-value"></a>Návratová hodnota  
 O tom, že výsledků Pokud rozevíracího dochází v umístění, které `point`. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje kartu, která je pod kurzor, dojde-li operaci přetažení aktivní. Vrátí `DROPEFFECT_NONE` Pokud nástrojů framework není v režimu přizpůsobení nebo formát dat schránky není k dispozici. Jinak vrátí výsledek volání `CMFCBaseTabCtrl::OnDragOver` s zadané parametry.  
  
 Další informace o přizpůsobení režimu najdete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formáty dat schránky najdete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx  
 Voláno rámcem, když uživatel uvolní tlačítko myši na konci operace přetažení.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] `pWnd`|Nepoužívá se.|  
|[v] `pDataObject`|Ukazatel na objekt, který uživatel nastavuje tažením.|  
|[v] `dropEffect`|Operace odstranění výchozí.|  
|[v] `dropList`|Nepoužívá se.|  
|[v] `point`|Umístění ukazatele myši v souřadnice klienta.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledný efekt vyřaďte. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá `CMFCBaseTabCtrl::OnDrop` Pokud rozhraní nástrojů je v režimu přizpůsobení a formát dat schránky je k dispozici. Pokud volání `CMFCBaseTabCtrl::OnDrop` vrátí nenulovou hodnotu, tato metoda vrátí výchozí efekt rozevírací určeného `dropEffect`. Jinak tato metoda vrátí hodnotu `DROPEFFECT_NONE`. Další informace o vyřazení důsledky, najdete v části [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).  
  
 Další informace o přizpůsobení režimu najdete v tématu [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Další informace o formáty dat schránky najdete v tématu [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="register"></a>  CMFCTabDropTarget::Register  
 Zaregistruje ovládacího prvku jako ten, který může být cílem operace přetažení myší OLE.  
  
```  
BOOL Register(CMFCBaseTabCtrl *pOwner);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] `pOwner`|Ovládacího prvku karta zaregistrovat jako cíle přetažení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla registrace úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) zaregistrovat ovládací prvek pro operací přetažení myší.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Přetažení (OLE)](../../mfc/drag-and-drop-ole.md)



