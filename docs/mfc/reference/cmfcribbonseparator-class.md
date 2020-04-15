---
title: Třída oddělovače cmfc
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
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368841"
---
# <a name="cmfcribbonseparator-class"></a>Třída oddělovače cmfc

Implementuje oddělovač pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|[Oddělovač pásky CMFC::ODdělovač pásky CMFC](#cmfcribbonseparator)|Vytvoří `CMFCRibbonSeparator` objekt.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[Oddělovač pásu CMFC::AddToListBox](#addtolistbox)|Přidá oddělovač do seznamu **Příkazy** v dialogovém okně **Přizpůsobit.** (Přepíše [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonSeparator::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|

### <a name="protected-methods"></a>Chráněné metody

|||
|-|-|
|Name (Název)|Popis|
|[ODdělovač cmfcstuhu::CopyFrom](#copyfrom)|Metoda kopírování, která nastaví členské proměnné oddělovače z jiného objektu.|
|[CMFCOdděliva tužehotu::GetRegularSize](#getregularsize)|Vrátí velikost oddělovače.|
|[Oddělovač cmfcpásu::Oddělovač is](#isseparator)|Označuje, zda se jedná o oddělovač.|
|[Oddělovač cmfcpásu::IsTabStop](#istabstop)|Označuje, zda se jedná o zarážku tabulátoru.|
|[Oddělovač pásu CMFC::OnDraw](#ondraw)|Volána systémem k nakreslení oddělovače na pásu karet nebo panelu nástrojů Rychlý přístup.|
|[CmFCOddělivač karet::OnDrawOnList](#ondrawonlist)|Volat systémem k nakreslení oddělovače v seznamu **příkazy.**|

## <a name="remarks"></a>Poznámky

Oddělovač pásu karet je svislá nebo vodorovná čára, která logicky odděluje prvky pásu karet. Oddělovač lze nakreslit na ovládacím prvku pásu karet, v hlavní nabídce aplikace, na stavovém řádku pásu karet a na panelu nástrojů Rychlý přístup.

Chcete-li použít oddělovač v aplikaci, vytvořte nový objekt a přidejte jej do hlavní nabídky aplikace, jak je znázorněno zde:

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Volání [CMFCRibbonRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) přidat oddělovače na pás karet panelů. Oddělovače jsou přiděleny a přidány `AddSeparator` interně metodou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Oddělovač pásu CMFC](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>Oddělovač pásu CMFC::AddToListBox

Přidá oddělovač do seznamu **Příkazy** v dialogovém okně **Přizpůsobit.**

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Parametry

*pWndListBox*<br/>
[v] Ukazatel na seznam **Příkazy,** kam je oddělovač přidán.

*bHluboký*<br/>
[v] Ignorovány.

### <a name="return-value"></a>Návratová hodnota

Nulový index na řetězec v seznamu určeném *pWndListBox*.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>Oddělovač pásky CMFC::ODdělovač pásky CMFC

Vytvoří `CMFCRibbonSeparator` objekt.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Parametry

*bIsHoriz*<br/>
[v] Pokud true, oddělovač je vodorovný; pokud false, oddělovač je svislý.

### <a name="remarks"></a>Poznámky

Horizontální oddělovače se používají v nabídkách aplikací. Svislé oddělovače se používají v panelech nástrojů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonSeparator` třídy.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>ODdělovač cmfcstuhu::CopyFrom

Metoda kopírování, která nastaví členské proměnné oddělovače z jiného objektu.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

*Src*<br/>
[v] Zdrojový prvek pásu karet, ze který chcete kopírovat.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFCOdděliva tužehotu::GetRegularSize

Vrátí velikost oddělovače.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na obsah zařízení.

### <a name="return-value"></a>Návratová hodnota

Velikost oddělovače v kontextu daného zařízení.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>Oddělovač cmfcpásu::Oddělovač is

Označuje, zda se jedná o oddělovač.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy TRUE pro tuto třídu.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>Oddělovač cmfcpásu::IsTabStop

Označuje, zda se jedná o zarážku tabulátoru.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy FALSE pro tuto třídu.

### <a name="remarks"></a>Poznámky

Oddělovač pásu karet není zarážkou tabulátoru.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>Oddělovač pásu CMFC::OnDraw

Volána systémem k nakreslení oddělovače na pásu karet nebo panelu nástrojů Rychlý přístup.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CmFCOddělivač karet::OnDrawOnList

Volat systémem k nakreslení oddělovače v seznamu **příkazy.**

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
|*Pdc*|[v] Ukazatel na kontext zařízení.|
|*strText*|[v] Text zobrazený v seznamu.|
|*nTextOffset*|[v] Mezery mezi textem a levou stranou ohraničovacího obdélníku.|
|*Rect*|[v] Určuje ohraničovací obdélník.|
|*bIsVybrané*|[v] Ignorovány.|
|*bZvýrazněno*|[v] Ignorovány.|

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
