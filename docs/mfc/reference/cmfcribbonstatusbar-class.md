---
title: Třída cmfcpásového pruhu
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
ms.openlocfilehash: 8d90e01db022c33edd654e83af05e9986799f2b9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754053"
---
# <a name="cmfcribbonstatusbar-class"></a>Třída cmfcpásového pruhu

Třída `CMFCRibbonStatusBar` implementuje ovládací prvek stavového řádku, který může zobrazit prvky pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCPásový pruh::AddDynamicElement](#adddynamicelement)|Přidá dynamický prvek na stavový řádek pásu karet.|
|[CMFCPásový pruh::Přidat prvek](#addelement)|Přidá nový prvek pásu karet na stavový řádek pásu karet.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Přidá prvek pásu karet do rozšířené oblasti stavového řádku pásu karet.|
|[CMFCRibbonStatusBar::Oddělovač přidání](#addseparator)|Přidá oddělovač na stavový řádek pásu karet.|
|[CMFCRibbonStatusBar::Vytvořit](#create)|Vytvoří stavový řádek pásu karet.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Vytvoří stavový řádek pásu karet s rozšířeným stylem.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCPásový pruh::FindElement](#findelement)|Vrátí ukazatel na prvek, který má zadané ID příkazu.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Vrátí počet prvků, které se nacházejí v hlavní oblasti stavového řádku pásu karet.|
|[CMFCPásový pruh::GetElement](#getelement)|Vrátí ukazatel na prvek, který je umístěn na zadaný index.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Vrátí počet prvků, které jsou umístěny v rozšířené oblasti stavového řádku pásu karet.|
|[CMFCPásový pruh::GetExElement](#getexelement)|Vrátí ukazatel na prvek, který je umístěn na zadaný index v rozšířené oblasti stavového řádku pásu karet.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCPásový pruh::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::isExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::Režim isinformationMode](#isinformationmode)|Určuje, zda je pro stavový řádek pásu karet povolen informační režim.|
|[CMFCRibbonStatusBar::Rozložení převržení](#recalclayout)|(Přepíše [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::Removeall](#removeall)|Odebere všechny prvky ze stavového řádku pásu karet.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Odebere prvek, který má zadané ID příkazu ze stavového řádku pásu karet.|
|[CMFCPásový pruh::SetInformation](#setinformation)|Povolí nebo zakáže informační režim pro stavový řádek pásu karet.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformace](#ondrawinformation)|Zobrazí informační řetězec, který se zobrazí na stavovém řádku pásu karet, když je povolen informační režim.|

## <a name="remarks"></a>Poznámky

Uživatelé mohou změnit viditelnost prvků pásu karet na stavovém řádku pásu karet pomocí předdefinované kontextové nabídky pro stavový řádek pásu karet. Prvky můžete přidávat nebo odebírat dynamicky.

Stavový řádek pásu karet má dvě oblasti: hlavní oblast a rozšířenou oblast. Rozšířená oblast se zobrazí na pravé straně stavového řádku pásu karet a zobrazí se v jiné barvě než hlavní oblast.

Hlavní oblast stavového řádku obvykle zobrazuje oznámení o stavu a rozšířená oblast zobrazuje ovládací prvky zobrazení. Rozšířená oblast zůstane viditelná co nejdéle, když uživatel změní velikost stavového řádku pásu karet.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonStatusBar` metody ve třídě. Příklad ukazuje, jak přidat nový prvek pásu karet na stavový řádek pásu karet, přidat prvek pásu karet do rozšířené oblasti stavového řádku pásu karet, přidat oddělovač a povolit pravidelný režim pro stavový řádek pásu karet.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CmFCribbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CmFCpásový panel](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFCPásový pruh::AddDynamicElement

Přidá dynamický prvek na stavový řádek pásu karet.

```cpp
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[v] Ukazatel na dynamický prvek.

### <a name="remarks"></a>Poznámky

Na rozdíl od běžných prvků nejsou dynamické prvky přizpůsobitelné a nabídka přizpůsobení stavového řádku je nezobrazuje.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFCPásový pruh::Přidat prvek

Přidá nový prvek pásu karet na stavový řádek pásu karet.

```cpp
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[v] Ukazatel na přidaný prvek.

*popisek lpsz*<br/>
[v] Textový popisek prvku.

*bIsVisible*<br/>
[v] TRUE, pokud chcete přidat prvek jako viditelný, NEPRAVDA, pokud chcete přidat prvek jako skrytý.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement

Přidá prvek pásu karet do rozšířené oblasti stavového řádku pásu karet.

```cpp
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*pElement*<br/>
[v] Ukazatel na přidaný prvek.

*popisek lpsz*<br/>
[v] Textový popisek prvku.

*bIsVisible*<br/>
[v] TRUE, pokud chcete přidat prvek jako viditelný, NEPRAVDA, pokud chcete přidat prvek jako skrytý.

### <a name="remarks"></a>Poznámky

Rozšířená oblast je na pravé straně ovládacího prvku stavového řádku.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFCRibbonStatusBar::Oddělovač přidání

Přidá oddělovač na stavový řádek pásu karet.

```cpp
void AddSeparator();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework přidá oddělovač za metodu [CMFCRibbonStatusBar::AddElement](#addelement). vloží poslední prvek.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFCRibbonStatusBar::Vytvořit

Vytvoří stavový řádek pásu karet.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[v] Ukazatel na nadřazené okno.

*dwStyl*<br/>
[v] Logická kombinace stylů ovládacích prvků NEBO.

*Nid*<br/>
[v] ID ovládacího prvku stavového řádku.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je stavový řádek úspěšně vytvořen, false jinak.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFCRibbonStatusBar::CreateEx

Vytvoří stavový řádek pásu karet s rozšířeným stylem.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazené okno.

*dwCtrlStyl*<br/>
Logická kombinace nebo dalších stylů pro vytvoření objektu stavového řádku.

*dwStyl*<br/>
Styl ovládacího prvku stavového řádku.

*Nid*<br/>
ID ovládacího prvku stavového řádku.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je stavový řádek úspěšně vytvořen, false jinak.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonStatusBar::FindByID

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parametry

[v] *uiCmdID*<br/>
[v] *BOOL*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFCPásový pruh::FindElement

Vrátí ukazatel na prvek, který má zadané ID příkazu.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] ID prvku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který má zadané ID příkazu. NULL, pokud takový prvek neexistuje.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFCRibbonStatusBar::GetCount

Vrátí počet prvků, které se nacházejí v hlavní oblasti stavového řádku pásu karet.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které jsou umístěny v hlavní oblasti stavového řádku pásu karet.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFCPásový pruh::GetElement

Vrátí ukazatel na prvek, který je umístěn na zadaný index.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje nulový index prvku, který se nachází v hlavní oblasti ovládacího prvku stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který je umístěn na zadaný index. Null, pokud je index záporný nebo překračuje počet prvků ve stavovém řádku.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount

Vrátí počet prvků, které jsou umístěny v rozšířené oblasti stavového řádku pásu karet.

```
int GetExCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které jsou umístěny v rozšířené oblasti stavového řádku pásu karet.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFCPásový pruh::GetExElement

Vrátí ukazatel na prvek, který je umístěn na zadaný index v rozšířené oblasti stavového řádku pásu karet. Rozšířená oblast je na pravé straně ovládacího prvku stavového řádku.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
[v] Určuje nulový index prvku, který se nachází v rozšířené oblasti ovládacího prvku stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na prvek, který je umístěn na zadaný index v rozšířené oblasti stavového řádku pásu karet. NULL Pokud *nIndex* je záporná nebo překračuje počet prvků v rozšířené oblasti stavového řádku pásu karet.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

[v] *rect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFCPásový pruh::GetSpace

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomFrame

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFCRibbonStatusBar::isExtendedElement

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parametry

[v] *pElement*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFCRibbonStatusBar::Režim isinformationMode

Určuje, zda je pro stavový řádek pásu karet povolen informační režim.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud stavový řádek může fungovat v informačním režimu; jinak FALSE.

### <a name="remarks"></a>Poznámky

V informačním režimu stavový řádek skryje všechna běžná podokna a zobrazí řetězec zprávy.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFCRibbonStatusBar::OnDrawInformace

Zobrazí řetězec, který se zobrazí na stavovém řádku pásu karet, když je povolen informační režim.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*strInfo*<br/>
[v] Informační řetězec.

*rectInfo*<br/>
[v] Ohraničovací obdélník.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu v odvozené třídě, pokud chcete přizpůsobit vzhled informačního řetězce na stavovém řádku. Pomocí metody [CMFCRibbonStatusBar::SetInformation](#setinformation) přepnete stavový řádek do informačního režimu. V tomto režimu stavový řádek skryje všechna podokna a zobrazí informační řetězec určený *strInfo*.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonStatusBar::Rozložení převržení

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFCRibbonStatusBar::Removeall

Odebere všechny prvky ze stavového řádku pásu karet.

```cpp
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFCRibbonStatusBar::RemoveElement

Odebere prvek, který má zadané ID příkazu ze stavového řádku pásu karet.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] ID prvku odebrat ze stavového řádku.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je odebrán prvek se zadaným *uiID.* FALSE jinak.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFCPásový pruh::SetInformation

Povolí nebo zakáže informační režim pro stavový řádek pásu karet.

```cpp
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parametry

*lpszInfo*<br/>
[v] Informační řetězec.

### <a name="remarks"></a>Poznámky

Tato metoda slouží k přepychu stavového řádku do informačního režimu. V tomto režimu stavový řádek skryje všechna podokna a zobrazí informační řetězec určený *parametrem lpszInfo*.

Pokud je hodnota LPSzInfo null, stavový řádek se vrátí do normálního režimu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
