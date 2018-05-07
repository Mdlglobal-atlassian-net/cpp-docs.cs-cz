---
title: Třída COleDropTarget | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
dev_langs:
- C++
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb52739977b641cd5d52f018efcd30a51ecf1e32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="coledroptarget-class"></a>COleDropTarget – třída
Poskytuje mechanismus komunikace mezi okno a knihoven OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|Vytvoří `COleDropTarget` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|Voláno, pokud nejprve do okna pole kurzor.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Voláno, když ukazatel ocitne mimo okno.|  
|[COleDropTarget::OnDragOver](#ondragover)|Opakovaně volat, když je kurzor přetažen přes okna.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Voláno k určení, zda je kurzor přetažen Posunout oblast okna.|  
|[COleDropTarget::OnDrop](#ondrop)|Voláno, pokud je vynechána data do okna výchozí obslužnou rutinu.|  
|[COleDropTarget::OnDropEx](#ondropex)|Voláno, pokud je vynechána data do okna počáteční obslužné rutiny.|  
|[COleDropTarget::Register](#register)|Zaregistruje okna jako cíle přetažení platný.|  
|[COleDropTarget::Revoke](#revoke)|Způsobí, že okno na ukončení provádění se cíle přetažení platný.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu této třídy umožňuje okna tak, aby přijímal data pomocí mechanismu přetažení myší OLE.  
  
 Pokud chcete získat okna tak, aby přijímal příkazů drop, je vhodné nejdříve vytvořit objekt `COleDropTarget` třídy a pak zavolají [zaregistrovat](#register) funkce s ukazatel na požadovanou `CWnd` objektu jako jediný parametr.  
  
 Další informace o operací přetažení myší pomocí OLE, najdete v článku [přetažení a Drop (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget  
 Vytvoří objekt třídy `COleDropTarget`.  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [zaregistrovat](#register) pro tento objekt přidružit časového období.  
  
##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter  
 Voláno rámcem při přetažení ukazatele nejprve do okna.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Přechází do bodů do okna kurzor.  
  
 `pDataObject`  
 Odkazuje na datový objekt obsahující data, která může být přetažen.  
  
 `dwKeyState`  
 Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
 `point`  
 Obsahuje aktuální umístění kurzoru v souřadnice klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
 O tom, že by dojít, pokud byla podniknuta pokles v umístění, které `point`. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE` Pokles nebude možné.  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
- `DROPEFFECT_SCROLL` Operaci přetažení scroll dojde nebo dochází na cíli.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce umožňuje operací myší v okně k přepsání. Výchozí implementace volá [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), která vrátí jednoduše `DROPEFFECT_NONE` ve výchozím nastavení.  
  
 Další informace najdete v tématu [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) ve Windows SDK.  
  
##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave  
 Voláno rámcem, když ukazatel opustí okno při přetahování operace je v platnosti.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Po skončení bodů do okna kurzor.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pokud chcete zvláštní chování při operaci přetažení opustí vybrané okno. Výchozí implementace této funkce volá [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Další informace najdete v tématu [IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) ve Windows SDK.  
  
##  <a name="ondragover"></a>  COleDropTarget::OnDragOver  
 Voláno rámcem při přetažení ukazatele přes okno.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Body do okna přes se nachází kurzor.  
  
 `pDataObject`  
 Odkazuje na datový objekt, který obsahuje data, která mají být vyřazeny.  
  
 `dwKeyState`  
 Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
 `point`  
 Obsahuje aktuální umístění kurzoru v souřadnice klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
 O tom, že by dojít, pokud byla podniknuta pokles v umístění, které `point`. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE` Pokles nebude možné.  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
- `DROPEFFECT_SCROLL` Označuje, že posuňte operaci přetažení dojde nebo dochází na cíli.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být potlačena umožňující operací myší v okně. Výchozí implementace této funkce volá [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), která vrátí `DROPEFFECT_NONE` ve výchozím nastavení. Protože tato funkce je volána často během operace přetahování myší, ho by mělo být optimalizované co nejvíc.  
  
 Další informace najdete v tématu [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll  
 Voláno rámcem před voláním [ondragenter –](#ondragenter) nebo [ondragover –](#ondragover) k určení zda `point` v oblasti s možností posouvání.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Body do okna kurzor je aktuálně přes.  
  
 `dwKeyState`  
 Obsahuje stav modifikační klávesy. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
 `point`  
 Obsahuje umístění kurzoru v pixelech, relativně k obrazovce.  
  
### <a name="return-value"></a>Návratová hodnota  
 O tom, že by dojít, pokud byla podniknuta pokles v umístění, které `point`. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE` Pokles nebude možné.  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
- `DROPEFFECT_SCROLL` Označuje, že posuňte operaci přetažení dojde nebo dochází na cíli.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pokud chcete zadat speciální chování pro tuto událost. Výchozí implementace této funkce volá [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), která vrátí `DROPEFFECT_NONE` a posune okno, když je kurzor přetažen Posunout oblast výchozí uvnitř ohraničení okna.  
  
##  <a name="ondrop"></a>  COleDropTarget::OnDrop  
 Voláno rámcem při operace odstranění se má použít.  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Body do okna kurzor je aktuálně přes.  
  
 `pDataObject`  
 Odkazuje na datový objekt, který obsahuje data, která mají být vyřazeny.  
  
 `dropEffect`  
 O tom, že se uživatel rozhodl pro operace vyřazení. Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
 `point`  
 Obsahuje umístění kurzoru v pixelech, relativně k obrazovce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li rozevíracího úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 První volání framework [ondropex –](#ondropex). Pokud `OnDropEx` funkce nezpracovává rozevíracího, rozhraní pak zavolá tato funkce člen `OnDrop`. Obvykle se aplikace přepsání [ondropex –](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení pro zpracování pravé tlačítko myši přetažení. Obvykle třídy zobrazení [OnDrop](../../mfc/reference/cview-class.md#ondrop) slouží ke zpracování jednoduché přetažení.  
  
 Výchozí implementaci `COleDropTarget::OnDrop` volání [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), která vrátí jednoduše **FALSE** ve výchozím nastavení.  
  
 Další informace najdete v tématu [IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) ve Windows SDK.  
  
##  <a name="ondropex"></a>  COleDropTarget::OnDropEx  
 Voláno rámcem při operace odstranění se má použít.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Body do okna kurzor je aktuálně přes.  
  
 `pDataObject`  
 Odkazuje na datový objekt, který obsahuje data, která mají být vyřazeny.  
  
 `dropDefault`  
 O tom, že se uživatel rozhodl pro operace vyřazení výchozí na základě aktuálního stavu klíče. Může být `DROPEFFECT_NONE`. Vyřaďte důsledky jsou popsané v oddílu Poznámky.  
  
 `dropList`  
 Seznam rozevírací účinky, které podporuje zdroji vyřaďte. Vyřaďte vliv hodnoty lze spojovat pomocí bitová hodnota OR ( **&#124;**) operaci. Vyřaďte důsledky jsou popsané v oddílu Poznámky.  
  
 `point`  
 Obsahuje umístění kurzoru v pixelech, relativně k obrazovce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vliv rozevírací rozevírací pokus o umístění, které je výsledkem `point`. Vyřaďte důsledky jsou popsané v oddílu Poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je nejdřív volá framework. Pokud nezpracovává rozevíracího, pak zavolá rozhraní [OnDrop](#ondrop). Obvykle se přepíše [ondropex –](../../mfc/reference/cview-class.md#ondropex) ve třídě zobrazení pro podporu pravé tlačítko myši přetažení. Obvykle třídy zobrazení [OnDrop](../../mfc/reference/cview-class.md#ondrop) slouží ke zpracování případu podpory pro jednoduché přetažení.  
  
 Výchozí implementaci `COleDropTarget::OnDropEx` volání [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Ve výchozím nastavení [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) jednoduše vrátí hodnotu fiktivní udávajících [OnDrop](#ondrop) – členská funkce by měla být volána.  
  
 Účinky rozevírací popisují akce spojené s operace odstranění. Najdete v následujícím seznamu rozevírací důsledky:  
  
- `DROPEFFECT_NONE` Pokles nebude možné.  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
- `DROPEFFECT_SCROLL` Označuje, že posuňte operaci přetažení dojde nebo dochází na cíli.  
  
 Další informace najdete v tématu [IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) ve Windows SDK.  
  
##  <a name="register"></a>  COleDropTarget::Register  
 Volání této funkce při registraci vaší okno s OLE knihoven DLL jako cíle přetažení platný.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Body do okna, které má být registrován jako cíle přetažení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je registrace úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce musí být volána pro operace vyřaďte třeba přijmout.  
  
 Další informace najdete v tématu [RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) ve Windows SDK.  
  
##  <a name="revoke"></a>  COleDropTarget::Revoke  
 Volání této funkce před zničení jakékoli okno, který byl zaregistrován jako cíle přetažení prostřednictvím volání [zaregistrovat](#register) ho odebrat ze seznamu cílů umístění.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je automaticky volána z [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) obslužné rutiny pro údržbu, který byl zaregistrován, takže obvykle není nutné explicitně volání této funkce.  
  
 Další informace najdete v tématu [RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDropSource – třída](../../mfc/reference/coledropsource-class.md)
