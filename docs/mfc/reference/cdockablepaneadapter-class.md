---
title: Cdockablepaneadapter – třída
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 6088d7ed9f4d8f54bfe5ea7f7b77cdabfd11768f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522951"
---
# <a name="cdockablepaneadapter-class"></a>Cdockablepaneadapter – třída

Poskytuje podporu dokování pro `CWnd`-odvozené podoken.

## <a name="syntax"></a>Syntaxe

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Vrátí zabalené okno.|
|[CDockablePaneAdapter::LoadState](#loadstate)|(Přepíše [CDockablePane::LoadState](cdockablepane-class.md#loadstate).)|
|[CDockablePaneAdapter::SaveState](#savestate)|(Přepíše [CDockablePane::SaveState](cdockablepane-class.md).)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>Poznámky

Obvykle rozhraní vytvoří objekty této třídy při použití [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) nebo [CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) metody.

Pokud chcete přizpůsobit `CDockablePaneAdapter` chování, stačí odvozovat nové třídy a nastavit informace o třídě modulu runtime na okno s kartami pomocí [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject –](../../mfc/reference/cobject-class.md) [CCmdTarget –](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)

[Cbasepane –](../../mfc/reference/cbasepane-class.md) [cpane –](../../mfc/reference/cpane-class.md) [CDockablePane –](../../mfc/reference/cdockablepane-class.md)

[Cdockablepaneadapter –](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDockablePaneAdapter.h

##  <a name="getwrappedwnd"></a>  CDockablePaneAdapter::GetWrappedWnd

Vrátí základní okno ukotvitelné podokně adaptéru.

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno zabalené.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte pro přístup k zabalené okna.

##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState

Stav v podokně se načte z registru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Název profilu.

*nIndex*<br/>
[in] Index profilu.

*uiID*<br/>
[in] ID podokně.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="savestate"></a>  CDockablePaneAdapter::SaveState

Uloží stav v podokně do registru.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Název profilu.

*nIndex*<br/>
[in] Profil indexu (výchozí nastavení ID ovládacího prvku v okně).

*uiID*<br/>
[in] ID podokně.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="setwrappedwnd"></a>  CDockablePaneAdapter::SetWrappedWnd

Nastaví základní okno ukotvitelné podokně adaptéru.

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Ukazatel do okna pro podokno adaptér zabalit.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
