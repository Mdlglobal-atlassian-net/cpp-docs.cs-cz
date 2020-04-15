---
title: CPaneDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364129"
---
# <a name="cpanedialog-class"></a>CPaneDialog – třída

Třída `CPaneDialog` podporuje nemodální, dokovatelné dialogové okno.

## <a name="syntax"></a>Syntaxe

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Výchozí konstruktor.|
|`CPaneDialog::~CPaneDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPaneDialog::Vytvořit](#create)|Vytvoří dokovatelné dialogové okno a `CPaneDialog` připojí ho k objektu.|
|`CPaneDialog::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CPaneDialog::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Zpracovává [zprávu WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Předefinuje `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Zpracovává [zprávu WM_ERASEBKGND.](/windows/win32/winmsg/wm-erasebkgnd) (Předefinuje [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Zpracovává [zprávu WM_LBUTTONDBLCLK.](/windows/win32/inputdev/wm-lbuttondblclk) (Předefinuje [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Zpracovává [zprávu WM_LBUTTONDOWN.](/windows/win32/inputdev/wm-lbuttondown) (Předefinuje [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Volat rámci aktualizovat okno dialogového okna. (Přepíše [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Zpracovává [zprávu WM_WINDOWPOSCHANGING.](/windows/win32/winmsg/wm-windowposchanging) (Předefinuje [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Určuje šablonu pro dialogové okno, které je kontejnerem ovládacího prvku OLE.|

## <a name="remarks"></a>Poznámky

Vytvořte `CPaneDialog` objekt ve dvou krocích. Nejprve vytvořte objekt v kódu. Za druhé volejte [CPaneDialog::Create](#create). Je nutné zadat platný název šablony prostředku nebo ID šablony a předat ukazatel do nadřazeného okna. V opačném případě se proces vytváření nezdaří. Dialogové okno musí určit styl WS_CHILD a WS_VISIBLE. Doporučujeme také zadat WS_CLIPCHILDREN a WS_CLIPSIBLINGS styly. Další informace naleznete v [tématu Styly oken](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Vytvořit

Vytvoří dialogové okno ukotvení a připojí `CPaneDialog` ho k objektu.

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszNázev_okna*<br/>
[v] Název dialogového okna ukotvení.

*pParentWnd*<br/>
[v] Odkazuje na nadřazené okno.

*bHasGripper*<br/>
[v] TRUE pro vytvoření dialogového okna ukotvení s titulkem (úchop); jinak NEPRAVDA.

*lpszTemplateName*<br/>
[v] Název šablony dialogového okna prostředku.

*nStyl*<br/>
[v] Styl systému Windows.

*Nid*<br/>
[v] ID ovládacího prvku.

*nIDŠablona*<br/>
[v] ID prostředku šablony dialogu.

*dwTabbedStyl*<br/>
[v] Styl okna s kartami, který vzniká, když uživatel přetáhne jiné ovládací podokno na titulek tohoto ovládacího podokna. Výchozí hodnota je AFX_CBRS_REGULAR_TABS. Další informace naleznete v části Poznámky metody [CBasePane::CreateEx.](../../mfc/reference/cbasepane-class.md#createex)

*dwControlBarStyle*<br/>
[v] Další atributy stylu. Výchozí hodnota je AFX_DEFAULT_DOCKING_PANE_STYLE. Další informace naleznete v části Poznámky metody [CBasePane::CreateEx.](../../mfc/reference/cbasepane-class.md#createex)

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda je úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `Create` používat metodu ve `CPaneDialog` třídě. Tento příklad je součástí [ukázky Velikost podokna sady](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Zpracovává [zprávu WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog)

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[v] Zpracovat ovládací prvek, který má přijímat výchozí fokus klávesnice.

*Lparam*<br/>
[v] Určuje další inicializační data.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA. Kromě toho true nastaví fokus klávesnice na ovládací prvek určený parametrem *wParam;* FALSE zabraňuje nastavení výchozího fokusu klávesnice.

### <a name="remarks"></a>Poznámky

Rozhraní framework používá tuto metodu k inicializaci ovládacích prvků a vzhleddialogového okna. Rozhraní Framework volá tuto metodu před zobrazením dialogového okna.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo

Určuje šablonu pro dialogové okno, které je kontejnerem ovládacího prvku OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
[v] Ukazatel na šablonu dialogového okna, která se používá k vytvoření objektu dialogového okna. Hodnota tohoto parametru je následně předána metodě [COccManager::CreateDlgControls.](../../mfc/reference/coccmanager-class.md#createdlgcontrols)

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE

### <a name="remarks"></a>Poznámky

Tato metoda podporuje třídu [COccManager,](../../mfc/reference/coccmanager-class.md) která spravuje řídicí weby OLE a ovládací prvky ActiveX. Struktura _AFX_OCC_DIALOG_INFO je definována v souboru záhlaví afxocc.h.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles)
