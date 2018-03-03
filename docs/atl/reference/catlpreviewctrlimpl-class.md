---
title: "Třída CAtlPreviewCtrlImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
dev_langs:
- C++
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01c6ac22ecdbf6f66afcec3816ae9d3a3d686942
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl – třída
Tato třída je implementací ATL okno, které je umístěn na hostitelské okno poskytuje prostředí pro verzi Preview formátováním.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destructs objekt ovládacího prvku preview.|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Vytvoří objekt ovládacího prvku preview.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](#create)|Volá obslužnou rutinou bohaté Preview vytvořit období systému Windows.|  
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Voláno bohaté Preview obslužnou rutinou, pokud je chcete-li odstranit tento ovládací prvek.|  
|[CAtlPreviewCtrlImpl::Focus](#focus)|Nastaví vstupní zaměření tohoto ovládacího prvku.|  
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Zpracovává zprávy WM_PAINT.|  
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Tento ovládací prvek pro ho překreslit informuje.|  
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Nastaví novou nadřazenou položku pro tento ovládací prvek.|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Volat bohaté Preview obslužnou rutinou, pokud je potřeba nastavit vizuální prvky bohaté Preview obsahu.|  
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Nastaví nové ohraničující obdélník pro tento ovládací prvek.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Voláno rámcem k vykreslení ve verzi preview.|  
  
### <a name="protected-constants"></a>Chráněné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Písmo použité k zobrazení textu v podokně náhledu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Barva pozadí okna náhledu.|  
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Barva textu z okna náhledu.|  

  
## <a name="remarks"></a>Poznámky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl >](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlpreviewctrlimpl.h  
  
##  <a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl  
 Vytvoří objekt ovládacího prvku preview.  
  
```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dtor"></a>CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl  
 Destructs objekt ovládacího prvku preview.  
  
```
virtual ~CAtlPreviewCtrlImpl(void);
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>CAtlPreviewCtrlImpl::Create  
 Volá obslužnou rutinou bohaté Preview vytvořit období systému Windows.  
  
```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Popisovač pro okno hostitele poskytl prostředí pro verzi Preview formátováním.  
  
 `prc`  
 Určuje počáteční velikost a umístění okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="destroy"></a>CAtlPreviewCtrlImpl::Destroy  
 Voláno bohaté Preview obslužnou rutinou, pokud je chcete-li odstranit tento ovládací prvek.  
  
```
virtual void Destroy();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="dopaint"></a>CAtlPreviewCtrlImpl::DoPaint  
 Voláno rámcem k vykreslení ve verzi preview.  
  
```
virtual void DoPaint(HDC hdc);
```  
  
### <a name="parameters"></a>Parametry  
 `hdc`  
 Popisovač pro kontext zařízení pro malování.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="focus"></a>CAtlPreviewCtrlImpl::Focus  
 Nastaví vstupní zaměření tohoto ovládacího prvku.  
  
```
virtual void Focus();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_clrback"></a>CAtlPreviewCtrlImpl::m_clrBack  
 Barva pozadí okna náhledu.  
  
```
COLORREF m_clrBack;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_clrtext"></a>CAtlPreviewCtrlImpl::m_clrText  
 Barva textu z okna náhledu.  
  
```
COLORREF m_clrText;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_plf"></a>CAtlPreviewCtrlImpl::m_plf  
 Písmo použité k zobrazení textu v podokně náhledu.  
  
```
const LOGFONTW* m_plf;
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onpaint"></a>CAtlPreviewCtrlImpl::OnPaint  
 Zpracovává zprávy WM_PAINT.  
  
```
LRESULT OnPaint(  
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Parametry  
 `nMsg`  
 Nastavte na WM_PAINT.  
  
 `wParam`  
 Tento parametr není používán.  
  
 `lParam`  
 Tento parametr není používán.  
  
 `bHandled`  
 Když tato funkce vrátí, obsahuje `TRUE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="redraw"></a>CAtlPreviewCtrlImpl::Redraw  
 Tento ovládací prvek pro ho překreslit informuje.  
  
```
virtual void Redraw();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost  
 Nastaví novou nadřazenou položku pro tento ovládací prvek.  
  
```
virtual void SetHost(HWND hWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 Popisovač do nového nadřazeného okna.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals  
 Volat bohaté Preview obslužnou rutinou, pokud je potřeba nastavit vizuální prvky bohaté Preview obsahu.  
  
```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```  
  
### <a name="parameters"></a>Parametry  
 `clrBack`  
 Barva pozadí okna náhledu.  
  
 `clrText`  
 Barva textu z okna náhledu.  
  
 `plf`  
 Písmo použité k zobrazení textu v podokně náhledu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect  
 Nastaví nové ohraničující obdélník pro tento ovládací prvek.  
  
```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```  
  
### <a name="parameters"></a>Parametry  
 `prc`  
 Určuje nové velikost a umístění ovládacího prvku preview.  
  
 `bRedraw`  
 Určuje, zda by měl být překreslen ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)
