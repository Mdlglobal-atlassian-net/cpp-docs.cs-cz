---
title: CMFCRibbonSeparator – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 65321cb80c80a5f4c6b3cf9c67e85b1bfb6f9d11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445596"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator – třída

Implementuje oddělovač pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Vytvoří objekt `CMFCRibbonSeparator`.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Přidá oddělovač do seznamu **příkazy** v dialogovém okně **přizpůsobit** . (Overrides [CMFCRibbonBaseElement:: AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonSeparator::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|

### <a name="protected-methods"></a>Chráněné metody

|||
|-|-|
|Název|Popis|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopírování, která nastavuje proměnné členů oddělovače z jiného objektu.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Vrátí velikost oddělovače.|
|[CMFCRibbonSeparator:: deoddělovač](#isseparator)|Označuje, zda se jedná o oddělovač.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Označuje, zda se jedná o zarážku tabulátoru.|
|[CMFCRibbonSeparator:: Draw](#ondraw)|Volána systémem pro vykreslení oddělovače na pásu karet nebo na panelu nástrojů Rychlý přístup.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Volá se systémem, aby se vykreslil oddělovač v seznamu **příkazů** .|

## <a name="remarks"></a>Poznámky

Oddělovač pásu karet je svislá nebo vodorovná čára, která logicky odděluje prvky pásu karet. Oddělovač lze vykreslit na ovládacím prvku pásu karet, v hlavní nabídce aplikace, na stavovém řádku pásu karet a na panelu nástrojů Rychlý přístup.

Chcete-li použít oddělovač v aplikaci, sestavte nový objekt a přidejte ho do nabídky Main Application, jak je znázorněno zde:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Chcete-li přidat oddělovače do panelů pásu karet, zavolejte [CMFCRibbonPanel:: AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) . Oddělovače jsou přiděleny a interně přidány metodou `AddSeparator`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbaseribbonelement. h

##  <a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

Přidá oddělovač do seznamu **příkazy** v dialogovém okně **přizpůsobit** .

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parametry

*pWndListBox*<br/>
pro Ukazatel na seznam **příkazů** , do kterého se přidá oddělovač.

*bDeep*<br/>
pro Přeskočen.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule k řetězci v poli seznamu určeném parametrem *pWndListBox*.

##  <a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator

Vytvoří objekt `CMFCRibbonSeparator`.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parametry

*bIsHoriz*<br/>
pro Při hodnotě TRUE je oddělovač horizontální; Pokud je hodnota FALSE, oddělovač je svislý.

### <a name="remarks"></a>Poznámky

V nabídkách aplikací se používají horizontální oddělovače. Svislé oddělovače se používají na panelech nástrojů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt třídy `CMFCRibbonSeparator`.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonSeparator::CopyFrom

Metoda kopírování, která nastavuje proměnné členů oddělovače z jiného objektu.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*Src*<br/>
pro Zdrojový element pásu karet, ze kterého se má kopírovat.

##  <a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize

Vrátí velikost oddělovače.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na obsah zařízení.

### <a name="return-value"></a>Návratová hodnota

Velikost oddělovače v daném kontextu zařízení.

##  <a name="isseparator"></a>CMFCRibbonSeparator:: deoddělovač

Označuje, zda se jedná o oddělovač.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE pro tuto třídu.

##  <a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop

Označuje, zda se jedná o zarážku tabulátoru.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy NEPRAVDA pro tuto třídu.

### <a name="remarks"></a>Poznámky

Oddělovač pásu karet není zarážka tabulátoru.

##  <a name="ondraw"></a>CMFCRibbonSeparator:: Draw

Volána systémem pro vykreslení oddělovače na pásu karet nebo na panelu nástrojů Rychlý přístup.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
pro Ukazatel na kontext zařízení.

##  <a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

Volá se systémem, aby se vykreslil oddělovač v seznamu **příkazů** .

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Emulátor*|pro Ukazatel na kontext zařízení.|
|*strText*|pro Text zobrazený v seznamu|
|*nTextOffset*|pro Mezery mezi textem a levou stranou ohraničujícího obdélníku|
|*OBD*|pro Určuje ohraničující obdélník.|
|*bIsSelected*|pro Přeskočen.|
|*bHighlighted*|pro Přeskočen.|

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
