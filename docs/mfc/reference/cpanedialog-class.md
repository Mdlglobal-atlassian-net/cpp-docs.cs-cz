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
ms.openlocfilehash: e7ff55e37194d0fa405925e4b3895428cfcaf9eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502985"
---
# <a name="cpanedialog-class"></a>CPaneDialog – třída

`CPaneDialog` Třída podporuje nemodální dialogové okno, ukotvit.

## <a name="syntax"></a>Syntaxe

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Výchozí konstruktor|
|`CPaneDialog::~CPaneDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPaneDialog::Create](#create)|Vytvoří dialogové okno ukotvit a připojí ho k `CPaneDialog` objektu.|
|`CPaneDialog::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|`CPaneDialog::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Zpracovává zprávu [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Předefinování `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Zpracovává zprávu [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) . (Předefinování [CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Zpracovává zprávu [WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk) . (Předefinování [CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Zpracovává zprávu [WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown) . (Předefinování [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Volá se rozhraním, aby se aktualizovalo okno dialogového okna. (Overrides [CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Zpracovává zprávu [WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging) . (Předefinování [CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Určuje šablonu pro dialogové okno, které je kontejnerem ovládacího prvku OLE.|

## <a name="remarks"></a>Poznámky

`CPaneDialog` Vytvořte objekt ve dvou krocích. Nejprve Sestavte objekt v kódu. Za druhé zavolejte [CPaneDialog:: Create](#create). Je nutné zadat platný název šablony prostředku nebo ID šablony a předat ukazatel do nadřazeného okna. V opačném případě proces vytváření selže. Dialogové okno musí určovat styl WS_CHILD a WS_VISIBLE. Doporučujeme také zadat styly WS_CLIPCHILDREN a WS_CLIPSIBLINGS. Další informace naleznete v tématu [styly oken](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpanedialog. h

##  <a name="create"></a>CPaneDialog:: Create

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
pro Název dialogového okna s ukotvením.

*pParentWnd*<br/>
pro Odkazuje na nadřazené okno.

*bHasGripper*<br/>
pro TRUE pro vytvoření ukotveného dialogového okna s titulkem (úchyt); v opačném případě FALSE.

*lpszTemplateName*<br/>
pro Název šablony dialogového okna prostředků

*nStyle*<br/>
pro Styl Windows

*nID*<br/>
pro ID ovládacího prvku

*nIDTemplate*<br/>
pro ID prostředku šablony dialogového okna

*dwTabbedStyle*<br/>
pro Styl okna s kartami, které je výsledkem, když uživatel přetáhne jiné podokno ovládacího prvku na titulek tohoto podokna ovládacích prvků. Výchozí hodnota je AFX_CBRS_REGULAR_TABS. Další informace naleznete v části poznámky metody [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

*dwControlBarStyle*<br/>
pro Další atributy stylu. Výchozí hodnota je AFX_DEFAULT_DOCKING_PANE_STYLE. Další informace naleznete v části poznámky metody [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `Create` metodu `CPaneDialog` ve třídě. Tento příklad je součástí [ukázky velikosti podokna nastavení](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Zpracovává zprávu [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) .

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
pro Obsluha ovládacího prvku, který má přijmout výchozí fokus klávesnice.

*lParam*<br/>
pro Určuje další inicializační data.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE. Hodnota TRUE navíc nastaví fokus klávesnice na ovládací prvek určený parametrem *wParam* ; FALSE zabraňuje nastavení výchozího fokusu klávesnice.

### <a name="remarks"></a>Poznámky

Rozhraní používá tuto metodu k inicializaci ovládacích prvků a vzhledu dialogového okna. Rozhraní volá tuto metodu před tím, než se zobrazí dialogové okno.

##  <a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo

Určuje šablonu pro dialogové okno, které je kontejnerem ovládacího prvku OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
pro Ukazatel na šablonu dialogového okna, která se používá k vytvoření objektu dialogového okna. Hodnota tohoto parametru je následně předána do metody [COccManager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) .

### <a name="return-value"></a>Návratová hodnota

Vždycky TRUE.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje třídu [COccManager](../../mfc/reference/coccmanager-class.md) , která spravuje weby ovládacího prvku OLE a ovládací prvky ActiveX. Struktura _AFX_OCC_DIALOG_INFO je definována v souboru hlaviček afxocc. h.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)<br/>
[Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles)
