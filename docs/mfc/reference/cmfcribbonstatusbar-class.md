---
title: Cmfcribbonstatusbar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: b927012f241c30b1beec23ff7e0bbc9e8302d8da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296602"
---
# <a name="cmfcribbonstatusbar-class"></a>Cmfcribbonstatusbar – třída

`CMFCRibbonStatusBar` Třída implementuje ovládací prvek panel stav, který dokáže zobrazit prvky pásu.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Přidá dynamický element na stavový panel pásu karet.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Přidá nový prvek pásu karet na stavový panel pásu karet.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Přidá prvek pásu karet do oblasti rozšířené stavový panel pásu karet.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Přidá oddělovač na stavový panel pásu karet.|
|[CMFCRibbonStatusBar::Create](#create)|Vytvoří stavový panel pásu karet.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Vytvoří stavový panel pásu karet pomocí rozšířeného stylu.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Vrací ukazatel na prvek, který má ID zadaného příkazu.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Vrátí počet prvků, které se nacházejí v hlavní oblasti stavový panel pásu karet.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Vrací ukazatel na prvek, který se nachází na zadaném indexu.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Vrátí počet prvků, které se nacházejí v oblasti rozšířené stavový panel pásu karet.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Vrací ukazatel na prvek, který se nachází na zadaném indexu v oblasti rozšířené stavový panel pásu karet.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Určuje, jestli je povolený režim informace pro stavový panel pásu karet.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Přepíše [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Odebere všechny prvky z stavový panel pásu karet.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Odebere element, který má zadaný příkaz ID z stavový panel pásu karet.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Povolí nebo zakáže režim informace pro stavový panel pásu karet.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Zobrazí informace o řetězec, který se zobrazí na pásu karet stavovém řádku když je povolený režim informace.|

## <a name="remarks"></a>Poznámky

Uživatelé mohou změnit, zda se prvky pásu karet na stavový panel pásu karet pomocí předdefinovaných kontextové nabídky pro stavový panel pásu karet. Můžete přidat nebo odebrat prvky dynamicky.

Stavový panel pásu karet má dvě oblasti: hlavní oblasti a rozšířené oblasti. Rozšířené oblasti se zobrazí na pravé straně stavový panel pásu karet a zobrazí se jinou barvou, než hlavní oblasti.

Obvykle hlavní oblasti ve stavovém řádku zobrazí oznámení o stavu a rozšířené oblasti se zobrazí ovládací prvky zobrazení. Rozšířené oblasti zůstane, dokud viditelná, když uživatel změní stavový panel pásu karet.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonStatusBar` třídy. Tento příklad ukazuje, jak přidat nový prvek pásu karet na stavový panel pásu karet, přidejte prvek pásu karet do oblasti rozšířené ve stavovém řádku pásu karet, přidejte oddělovače a povolte normálního režimu pro stavový panel pásu karet.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonstatusbar.h

##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement

Přidá dynamický element na stavový panel pásu karet.

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[in] Ukazatel na prvek dynamické.

### <a name="remarks"></a>Poznámky

Na rozdíl od pravidelných prvky dynamické prvky nejsou upravitelné a přizpůsobit nabídku ve stavovém řádku nezobrazí je.

##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement

Přidá nový prvek pásu karet na stavový panel pásu karet.

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[in] Ukazatel na přidání elementu.

*lpszLabel*<br/>
[in] Text popisku elementu.

*bIsVisible*<br/>
[in] Hodnota TRUE, pokud chcete přidat jako viditelný, element FALSE. Pokud chcete přidat jako skrytý element.

##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement

Přidá prvek pásu karet do oblasti rozšířené stavový panel pásu karet.

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[in] Ukazatel na přidání elementu.

*lpszLabel*<br/>
[in] Text popisku elementu.

*bIsVisible*<br/>
[in] Hodnota TRUE, pokud chcete přidat jako viditelný, element FALSE. Pokud chcete přidat jako skrytý element.

### <a name="remarks"></a>Poznámky

Rozšířené oblast je na pravé straně ovládacího prvku panelu stavu.

##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator

Přidá oddělovač na stavový panel pásu karet.

```
void AddSeparator();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework přidá oddělovač za metodu [CMFCRibbonStatusBar::AddElement](#addelement). Vloží poslední prvek.

##  <a name="create"></a>  CMFCRibbonStatusBar::Create

Vytvoří stavový panel pásu karet.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Ukazatel do nadřazeného okna.

*dwStyle*<br/>
[in] Logický OR kombinace – styly ovládacího prvku.

*nID*<br/>
[in] ID ovládacího prvku na stavovém řádku.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud stavový řádek je úspěšně vytvořen, FALSE v opačném případě.

##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx

Vytvoří stavový panel pásu karet, který má rozšířeného stylu.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel do nadřazeného okna.

*dwCtrlStyle*<br/>
Logický OR kombinace další styly pro vytvoření objektu panelu stavu.

*dwStyle*<br/>
Stylu ovládacího prvku ve stavovém řádku.

*nID*<br/>
ID ovládacího prvku na stavovém řádku.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud stavový řádek je úspěšně vytvořen, FALSE v opačném případě.

##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *uiCmdID*<br/>
[in] *BOOL*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement

Vrací ukazatel na prvek, který má ID zadaného příkazu.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] ID elementu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který má ID zadaného příkazu. Hodnota NULL, pokud neexistuje žádný takový prvek.

##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount

Vrátí počet prvků, které se nacházejí v hlavní oblasti stavový panel pásu karet.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které se nacházejí v hlavní oblasti stavový panel pásu karet.

##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement

Vrací ukazatel na prvek, který se nachází na zadaném indexu.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index založený na nule, který je umístěný v oblasti hlavního panelu ovládacího prvku stav elementu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který se nachází na zadaném indexu. Hodnota NULL, pokud je index záporný nebo větší než počet elementů ve stavovém řádku.

### <a name="remarks"></a>Poznámky

##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount

Vrátí počet prvků, které se nacházejí v oblasti rozšířené stavový panel pásu karet.

```
int GetExCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které se nacházejí v oblasti rozšířené stavový panel pásu karet.

##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement

Vrací ukazatel na prvek, který se nachází na zadaném indexu v oblasti rozšířené stavový panel pásu karet. Rozšířené oblast je na pravé straně ovládacího prvku panelu stavu.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[in] Určuje index založený na nule element, který se nachází v oblasti Rozšířené ovládací prvek panel stavu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který se nachází na zadaném indexu v oblasti rozšířené stavový panel pásu karet. Hodnota NULL, pokud *nIndex* je záporný nebo větší než počet elementů v oblasti rozšířené stavový panel pásu karet.

### <a name="remarks"></a>Poznámky

##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[in] *rect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parametry

[in] *pElement*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode

Určuje, jestli je povolený režim informace pro stavový panel pásu karet.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud stavový řádek můžete pracovat v režimu informace. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

V režimu informace stavového řádku skryje všechny regulárních podokna a zobrazí řetězec zprávy.

##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation

Zobrazí řetězec, který se zobrazí na pásu karet stavovém řádku když je povolený režim informace.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*strInfo*<br/>
[in] Informace řetězce.

*rectInfo*<br/>
[in] Ohraničující obdélník.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled řetězec informací na stavovém řádku. Použití [CMFCRibbonStatusBar::SetInformation](#setinformation) metoda put stavového řádku v režimu informace. V tomto režimu se stavový řádek skryje všechny podokna a zobrazí informace o řetězec určený *strInfo*.

##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll

Odebere všechny prvky z stavový panel pásu karet.

```
void RemoveAll();
```

##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement

Odebere element, který má zadaný příkaz ID z stavový panel pásu karet.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] ID elementu odebrání stavový řádek.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud element se zadaným *uiID* se odebere. FALSE v opačném případě.

##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation

Povolí nebo zakáže režim informace pro stavový panel pásu karet.

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parametry

*lpszInfo*<br/>
[in] Informace řetězce.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete umístit na stavovém řádku v režimu informace. V tomto režimu se stavový řádek skryje všechny podokna a zobrazí informace o řetězec určený *lpszInfo*.

Když lpszInfo má hodnotu NULL, stavového řádku se vrátí do normálního režimu.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
