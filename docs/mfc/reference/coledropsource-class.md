---
title: Třída COleDropSource | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3f601c2b15f5f117f77b1f916027107708e8f19
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038218"
---
# <a name="coledropsource-class"></a>COleDropSource – třída
Umožňuje data přetáhnout do cíle přetažení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|Vytvoří `COleDropSource` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|Změní kurzor během operace přetažení myší.|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|Zachycení myši zpracovává během operace přetažení myší.|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Kontroluje, zda přetahování by měly pokračovat.|  
  
## <a name="remarks"></a>Poznámky  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md) třída zpracovává přijímající část operaci přetažení myší. `COleDropSource` Objektu je zodpovědná za určení, kdy začne operaci přetažení, poskytnutí zpětné vazby během operace přetažení a určit, při ukončení operace přetažení.  
  
 Použít `COleDropSource` objektu, stačí zavolat konstruktoru. Tato funkce zjednodušuje proces pro určení toho, jaké události, jako je například kliknutí myší, začněte pomocí operace přetažení [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), nebo [ COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkce. Vytvoří se tyto funkce `COleDropSource` objektu za vás. Můžete chtít změnit výchozí chování `COleDropSource` přepisovatelné funkce. Tyto funkce člen bude volat v příslušnou dobu rozhraní.  
  
 Další informace o operací přetažení myší pomocí OLE, najdete v článku [přetažení a Drop (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Další informace najdete v tématu [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) ve Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="coledropsource"></a>  COleDropSource::COleDropSource  
 Vytvoří `COleDropSource` objektu.  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback  
 Voláno rámcem po volání [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) nebo [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>Parametry  
 *dropEffect*  
 Účinek, který se má zobrazit uživateli, obvykle označující, co by mohlo dojít, pokud došlo k chybě pokles v tomto okamžiku se vybraná data. Obvykle je to hodnoty vrácené nejnovější volání [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) nebo [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Může být jeden nebo více následujících akcí:  
  
- `DROPEFFECT_NONE` Pokles nebude možné.  
  
- `DROPEFFECT_COPY` Operace kopírování by se provedla.  
  
- `DROPEFFECT_MOVE` Operace přesunu by se provedla.  
  
- `DROPEFFECT_LINK` Odkaz z vynechaných dat na původní data by byla založena.  
  
- `DROPEFFECT_SCROLL` Operaci přetažení scroll dojde nebo dochází na cíli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **DRAGDROP_S_USEDEFAULTCURSORS** Pokud přetahování probíhá, **NOERROR** Pokud není.  
  
### <a name="remarks"></a>Poznámky  
 Funkci k poskytnutí zpětné vazby pro uživatele co by mohlo dojít, pokud došlo k chybě pokles v tomto okamžiku přepište. Výchozí implementace používá kurzory výchozí OLE. Další informace o operací přetažení myší pomocí OLE, najdete v článku [přetažení a Drop (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Další informace najdete v tématu [IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723), [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129), a [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) ve Windows SDK.  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 Volá framework při výskytu události, který by mohl spustit operaci přetažení, jako je například stisknutím levé tlačítko.  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Body do okna obsahující vybraná data.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud přetahování je povolen, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pokud chcete upravit způsob, jakým přetahování proces běží. Výchozí implementace zaznamená myši a zůstane v režimu přetažení, dokud uživatel klikne na tlačítko myši doleva nebo doprava nebo přístupy ESC, po kterém se uvolní myši.  
  
##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag  
 Po zahájení přetahování, tato funkce je volána opakovaně rámcem dokud operaci přetažení zrušena nebo byla dokončena.  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>Parametry  
 *bEscapePressed*  
 Uvádí, zda stisknutí klávesy ESC od posledního volání `COleDropSource::QueryContinueDrag`.  
  
 *dwKeyState*  
 Obsahuje stav modifikační klávesy na klávesnici. Jedná se o kombinaci libovolný počet následující: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, a **MK_RBUTTON**.  
  
### <a name="return-value"></a>Návratová hodnota  
 **DRAGDROP_S_CANCEL** Pokud stisknutí klávesy ESC nebo pravým tlačítkem, nebo levým tlačítkem je vyvolána před přetahování spustí. **DRAGDROP_S_DROP** Pokud má probíhat operace odstranění. V opačném případě `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Dojde k přepsání, které tuto funkci Pokud chcete změnit bod, ve které přetahování je zrušená nebo pokles.  
  
 Výchozí implementace zahájí rozevíracího nebo zruší přetahování následujícím způsobem. Operaci přetažení zruší při stisknutí klávesy ESC nebo pravým tlačítkem myši. Po vyvolání levé tlačítko myši po přetahování spuštění zahájí operace odstranění. Funkce `S_OK` a provede žádné další operace.  
  
 Protože tato funkce je volána často, ho by mělo být optimalizované co nejvíc.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



