---
title: CPaneDialog Class
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
ms.openlocfilehash: c78b8f2cd19e87fa559c3f9bbd24d07543d887c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373086"
---
# <a name="cpanedialog-class"></a>CPaneDialog Class

`CPaneDialog` Podporuje nemodální ukotvitelné dialogové třídy.

## <a name="syntax"></a>Syntaxe

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Výchozí konstruktor.|
|`CPaneDialog::~CPaneDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPaneDialog::Create](#create)|Vytvoří ukotvitelné dialogové okno a připojí ho k `CPaneDialog` objektu.|
|`CPaneDialog::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CPaneDialog::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Zpracovává [nezavěsíte](/windows/desktop/dlgbox/wm-initdialog) zprávy. (Předefinuje `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Zpracovává [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd) zprávy. (Předefinuje [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Zpracovává [WM_LBUTTONDBLCLK](/windows/desktop/inputdev/wm-lbuttondblclk) zprávy. (Předefinuje [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Zpracovává [WM_LBUTTONDOWN](/windows/desktop/inputdev/wm-lbuttondown) zprávy. (Předefinuje [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Volá se rozhraním, chcete-li aktualizovat pole dialogovém okně. (Přepíše [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Zpracovává [WM_WINDOWPOSCHANGING](/windows/desktop/winmsg/wm-windowposchanging) zprávy. (Předefinuje [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Určuje šablonu pro dialogové okno, které je kontejnerem ovládacího prvku OLE.|

## <a name="remarks"></a>Poznámky

Vytvoření `CPaneDialog` objektu ve dvou krocích. Nejprve se vytvoří objekt v kódu. Za druhé volání [CPaneDialog::Create](#create). Je nutné zadat Identifikátor názvu nebo šabloně platný prostředek šablony a předat ukazatel do nadřazeného okna. V opačném případě se nezdaří v procesu vytváření. Dialogové okno musíte zadat WS_CHILD a WS_VISIBLE stylu. Doporučujeme zadat také WS_CLIPCHILDREN a WS_CLIPSIBLINGS styly. Další informace najdete v tématu [styly oken](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpanedialog.h

##  <a name="create"></a>  CPaneDialog::Create

Vytvoří ukotvené dialogové okno a připojí ho k `CPaneDialog` objektu.

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

*lpszWindowName*<br/>
[in] Název dialogového okna ukotvení.

*pParentWnd*<br/>
[in] Body do nadřazeného okna.

*bHasGripper*<br/>
[in] TRUE, pokud chcete vytvořit dialogové okno ukotvení s popiskem (úchytu); v opačném případě hodnota FALSE.

*lpszTemplateName*<br/>
[in] Název prostředku šablony dialogového okna.

*nStyle*<br/>
[in] Styl Windows.

*nID*<br/>
[in] ID ovládacího prvku.

*nIDTemplate*<br/>
[in] ID prostředku šablony dialogového okna.

*dwTabbedStyle*<br/>
[in] Styl okna s kartami, která vznikne, když uživatel přetáhne jiného ovládacího prvku podokna na titulek tento ovládací prvek stavového řádku. Výchozí hodnota je AFX_CBRS_REGULAR_TABS. Další informace najdete v části poznámky [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.

*dwControlBarStyle*<br/>
[in] Další šablony atributy. Výchozí hodnota je AFX_DEFAULT_DOCKING_PANE_STYLE. Další informace najdete v části poznámky [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda uspěje; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `Create` metodu `CPaneDialog` třídy. V tomto příkladu je součástí [nastavit velikost podokna ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

Zpracovává [nezavěsíte](/windows/desktop/dlgbox/wm-initdialog) zprávy.

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[in] Zpracování do ovládacího prvku, který se zobrazí výchozí fokus klávesnice.

*lParam*<br/>
[in] Určuje další inicializační data.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE. Kromě toho TRUE nastaví fokus klávesnice pro ovládací prvek určený *wParam* parameter; FALSE brání nastavení výchozí fokus klávesnice.

### <a name="remarks"></a>Poznámky

Rozhraní používá tato metoda se inicializovat ovládací prvky a vzhled dialogového okna. Rozhraní volá tuto metodu, než se zobrazí dialogové okno.

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

Určuje šablonu pro dialogové okno, které je kontejnerem ovládacího prvku OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
[in] Ukazatel na pole šablony dialogového okna, která se používá k vytvoření objektu pole dialogového okna. Hodnota tohoto parametru je následně předán [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) metody.

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje [coccmanager –](../../mfc/reference/coccmanager-class.md) třídu, která spravuje OLE ovládací prvky stránky a ovládací prvky ActiveX. Struktura _AFX_OCC_DIALOG_INFO je definována v hlavičkovém souboru afxocc.h.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)<br/>
[Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles)
