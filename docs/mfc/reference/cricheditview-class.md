---
title: CRichEditView – – třída
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: b32578cc3c9ad4f7a89b8ee76449259c0fa0b43b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741515"
---
# <a name="cricheditview-class"></a>CRichEditView – – třída

Pomocí [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) a [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)poskytuje funkce ovládacího prvku Rich Edit v rámci kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CRichEditView –:: CRichEditView –](#cricheditview)|`CRichEditView` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Přesune dialogové okno tak, že neskryje aktuální výběr.|
|[CRichEditView –:: CanPaste](#canpaste)|Určuje, zda schránka obsahuje data, která lze vložit do zobrazení pro úpravy s formátováním.|
|[CRichEditView::DoPaste](#dopaste)|Vloží položku OLE do tohoto zobrazení s bohatou úpravou.|
|[CRichEditView::FindText](#findtext)|Vyhledá zadaný text a vyvolá na něj čekací kurzor.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Vyhledá zadaný text.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Načte atributy formátování znaků pro aktuální výběr.|
|[CRichEditView::GetDocument](#getdocument)|Načte ukazatel na související [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Načte položku OLE, která je aktuálně místně aktivní v zobrazení pro úpravy.|
|[CRichEditView –:: getmarže](#getmargins)|Načte okraje pro toto zobrazení s bohatou úpravou.|
|[CRichEditView::GetPageRect](#getpagerect)|Načte rámeček stránky pro toto zobrazení s bohatou úpravou.|
|[CRichEditView::GetPaperSize](#getpapersize)|Načte velikost papíru pro toto zobrazení s bohatou úpravou.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Načte atributy formátování odstavce pro aktuální výběr.|
|[CRichEditView::GetPrintRect](#getprintrect)|Načte rámeček pro tisk pro toto zobrazení s formátováním s bohatou úpravou.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Načte šířku tisku pro toto zobrazení s formátováním RTF.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Načte ovládací prvek Rich Edit.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Načte vybranou položku z zobrazení pro úpravy s formátováním.|
|[CRichEditView::GetTextLength](#gettextlength)|Načte délku textu v zobrazení pro úpravy s formátováním.|
|[CRichEditView –:: GetTextLengthEx](#gettextlengthex)|Načte počet znaků nebo bajtů v zobrazení pro úpravy s formátováním. Rozbalený seznam příznaků pro metodu určení délky|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Vloží soubor jako položku OLE.|
|[CRichEditView –:: InsertItem](#insertitem)|Vloží novou položku jako položku OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Určuje, zda schránka obsahuje data ve formátu RTF nebo textu.|
|[CRichEditView –:: OnCharEffect](#onchareffect)|Přepíná formátování znaků pro aktuální výběr.|
|[CRichEditView::OnParaAlign](#onparaalign)|Změní zarovnání odstavců.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizuje uživatelské rozhraní příkazu pro funkce znaků Public member.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizuje uživatelské rozhraní příkazu pro veřejné členské funkce odstavce.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Zformátuje zadaný text v rámci daného obdélníku.|
|[CRichEditView::PrintPage](#printpage)|Zformátuje zadaný text v rámci dané stránky.|
|[CRichEditView –:: SetCharFormat](#setcharformat)|Nastaví atributy formátování znaků pro aktuální výběr.|
|[CRichEditView –:: SetMargins](#setmargins)|Nastaví okraje pro toto zobrazení s bohatou úpravou.|
|[CRichEditView –:: SetPaperSize](#setpapersize)|Nastaví velikost papíru pro toto zobrazení s bohatou úpravou.|
|[CRichEditView –:: SetParaFormat](#setparaformat)|Nastaví atributy formátování odstavce pro aktuální výběr.|
|[CRichEditView::TextNotFound](#textnotfound)|Obnoví vnitřní stav vyhledávání ovládacího prvku.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Načte objekt schránky pro rozsah v tomto zobrazení s bohatou úpravou.|
|[CRichEditView –::](#getcontextmenu)|Načte místní nabídku, která se má použít při stisknutí pravého tlačítka myši.|
|[CRichEditView –:: s volbou](#isselected)|Určuje, zda je zadaná položka OLE vybrána nebo ne.|
|[CRichEditView::OnFindNext](#onfindnext)|Najde další výskyt podřetězce.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Aktualizuje zobrazení, když se poprvé připojí k dokumentu.|
|[CRichEditView –:: OnPasteNativeObject](#onpastenativeobject)|Načte nativní data z položky OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Nastaví charakteristiky tisku na dané zařízení.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Nahradí všechny výskyty daného řetězce novým řetězcem.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Zpracovává oznámení uživateli, že nebyl nalezen požadovaný text.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Dotaz zobrazí informace o datech v `IDataObject`.|
|[CRichEditView –:: WrapChanged](#wrapchanged)|Upraví cílové výstupní zařízení pro toto zobrazení s bohatou úpravou na základě hodnoty `m_nWordWrap`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Určuje velikost odsazení pro seznamy odrážek.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Označuje omezení zalamování slov.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek" Rich Edit "je okno, ve kterém může uživatel text zadat a upravit. Textu lze přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Ovládací prvky s bohatým úpravou poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní, které jsou nezbytné k zpřístupnění operací formátování uživateli.

`CRichEditView`zachová text a formátuje charakteristiky textu. `CRichEditDoc`udržuje seznam položek klienta OLE, které jsou v zobrazení. `CRichEditCntrItem`poskytuje přístup na straně kontejneru k položce klienta OLE.

Tento běžný ovládací prvek systému Windows (a proto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Příklad použití bohatých zobrazení pro úpravy v aplikaci MFC naleznete v ukázkové aplikaci [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich. h

##  <a name="adjustdialogposition"></a>CRichEditView –:: AdjustDialogPosition

Voláním této funkce přesunete dané dialogové okno tak, že neskryje aktuální výběr.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parametry

*pDlg*<br/>
Ukazatel na `CDialog` objekt.

##  <a name="canpaste"></a>CRichEditView –:: CanPaste

Voláním této funkce určíte, zda schránka obsahuje informace, které mohou být vloženy do tohoto zobrazení s formátováním.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, Pokud schránka obsahuje data ve formátu, který může toto zobrazení s bohatou úpravou přijmout; v opačném případě 0.

##  <a name="cricheditview"></a>CRichEditView –:: CRichEditView –

Voláním této funkce vytvoříte `CRichEditView` objekt.

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView –::D oPaste

Voláním této funkce vložíte položku OLE do *dataobj* do tohoto dokumentu nebo zobrazení s bohatým úpravou.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parametry

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md) obsahující data, která mají být vložena.

*cf*<br/>
Požadovaný formát schránky.

*hMetaPict*<br/>
Metasoubor, který představuje položku, která má být vložena.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci jako součást výchozí implementace [QueryAcceptData](#queryacceptdata).

Tato funkce určuje typ vložení na základě výsledků obslužné rutiny pro vložení Special. Pokud je *CF* 0, nová položka používá aktuální reprezentaci ikonickým. Pokud má *CF* hodnotu nenulového a *hMetaPict* není null, nová položka pro svůj reprezentace používá *hMetaPict* .

##  <a name="findtext"></a>CRichEditView –:: hledán FindText

Voláním této funkce Najděte zadaný text a nastavte ho jako aktuální výběr.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Obsahuje řetězec, který chcete vyhledat.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Určuje, zda má hledání odpovídat celým slovům, nikoli částí slov.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE je směr hledání na konci vyrovnávací paměti. Pokud je hodnota FALSE, směr hledání je na začátku vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nalezen text *lpszFind* ; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce zobrazí během operace Find kurzor čekání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView –:: FindTextSimple

Voláním této funkce Najděte zadaný text a nastavte ho jako aktuální výběr.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Obsahuje řetězec, který chcete vyhledat.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Určuje, zda má hledání odpovídat celým slovům, nikoli částí slov.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE je směr hledání na konci vyrovnávací paměti. Pokud je hodnota FALSE, směr hledání je na začátku vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nalezen text *lpszFind* ; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: hledán FindText](#findtext).

##  <a name="getcharformatselection"></a>CRichEditView –:: GetCharFormatSelection

Voláním této funkce získáte atributy formátování znaků aktuálního výběru.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Návratová hodnota

Struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) , která obsahuje atributy formátování znaků aktuálního výběru.

### <a name="remarks"></a>Poznámky

Další informace naleznete v části zpráva [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) a struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView –:: GetClipboardData

Rozhraní volá tuto funkci jako součást zpracování [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parametry

*lpchrg*<br/>
Ukazatel na strukturu [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) , která určuje rozsah znaků (a položky OLE) pro zkopírování do datového objektu určeného parametrem *lplpdataobj*.

*dwReco*<br/>
Příznak operace schránky. Může to být jedna z těchto hodnot.

- RECO_COPY zkopírovat do schránky.

- RECO_CUT vyjmout do schránky.

- Operace přetažení RECO_DRAG (přetažení).

- RECO_DROP operace Drop (přetažení).

- RECO_PASTE vložit ze schránky.

*lpRichDataObj*<br/>
Ukazatel na objekt [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) obsahující data ze schránky z ovládacího prvku Rich Edit ( [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Ukazatel na proměnnou ukazatele, která přijímá adresu `IDataObject` objektu reprezentujícího rozsah zadaný v parametru *lpchrg* . Hodnota *lplpdataobj* se ignoruje, pokud se vrátí chyba.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT, která hlásí úspěch operace. Další informace o HRESULT naleznete v tématu [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud vrácená `IRichEditOleCallback::GetClipboardData` hodnota označuje úspěch, `IDataObject` vrátí k ní přistupované v *lplpdataobj*. v opačném případě vrátí tu, ke které se přistupovalo *lpRichDataObj*. Tuto funkci potlačíte tak, aby poskytovala vlastní data ze schránky. Výchozí implementace této funkce vrací E_NOTIMPL.

Toto je pokročilá přepsatelné.

Další informace naleznete v tématu [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)a [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) v tématu Windows SDK a viz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) v Windows SDK.

##  <a name="getcontextmenu"></a>CRichEditView –::

Rozhraní volá tuto funkci jako součást zpracování [IRichEditOleCallback::](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)getzaskladnění.

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parametry

*seltyp*<br/>
Typ výběru. Hodnoty typu výběru jsou popsány v části poznámky.

*lpoleobj*<br/>
Ukazatel na `OLEOBJECT` strukturu určující první vybraný objekt OLE, pokud výběr obsahuje jednu nebo více položek OLE. Pokud výběr neobsahuje žádné položky, *lpoleobj* má hodnotu null. `OLEOBJECT` Struktura obsahuje ukazatel na objekt OLE v tabulce.

*lpchrg*<br/>
Ukazatel na strukturu [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) obsahující aktuální výběr.

### <a name="return-value"></a>Návratová hodnota

Popisovač do kontextové nabídky.

### <a name="remarks"></a>Poznámky

Tato funkce je typická součást pravého tlačítka myši.

Typ výběru může být libovolná kombinace následujících příznaků:

- SEL_EMPTY značí, že není k dispozici žádný aktuální výběr.

- SEL_TEXT označuje, že aktuální výběr obsahuje text.

- SEL_OBJECT označuje, že aktuální výběr obsahuje alespoň jednu položku OLE.

- SEL_MULTICHAR označuje, že aktuální výběr obsahuje více než jeden znak textu.

- SEL_MULTIOBJECT značí, že aktuální výběr obsahuje více než jeden objekt OLE.

Výchozí implementace vrací hodnotu NULL. Toto je pokročilá přepsatelné.

Další informace naleznete v tématu [IRichEditOleCallback::](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) Get a [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) v Windows SDK.

##  <a name="getdocument"></a>CRichEditView –:: GetDocument

Voláním této funkce získáte ukazatel na `CRichEditDoc` přidružený k tomuto zobrazení.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) přidružený k vašemu `CRichEditView` objektu.

##  <a name="getinplaceactiveitem"></a>CRichEditView –:: GetInPlaceActiveItem

Voláním této funkce získáte položku OLE, která je aktuálně aktivována na místě v tomto `CRichEditView` objektu.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden místně aktivní objekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) v tomto zobrazení s bohatou úpravou; Hodnota NULL, pokud není aktuálně k dispozici žádná položka OLE v místním aktivním stavu.

##  <a name="getmargins"></a>CRichEditView –:: getmarže

Voláním této funkce načtete aktuální okraje použité při tisku.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Návratová hodnota

Okraje použité v tisku, měřené v MM_TWIPS.

##  <a name="getpagerect"></a>CRichEditView –:: GetPageRect

Voláním této funkce získáte rozměry stránky použité při tisku.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Hranice stránky používané při tisku, měřená v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Tato hodnota je založena na velikosti papíru.

##  <a name="getpapersize"></a>CRichEditView –:: GetPaperSize

Voláním této funkce načtete aktuální velikost papíru.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost dokumentu používaného při tisku, měřeno v MM_TWIPS.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView –:: GetParaFormatSelection

Voláním této funkce získáte atributy formátování odstavce aktuálního výběru.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Návratová hodnota

Struktura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) , která obsahuje atributy formátování odstavce aktuálního výběru.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) Structure in the Windows SDK.

##  <a name="getprintrect"></a>CRichEditView –:: GetPrintRect

Voláním této funkce načtete hranice oblasti tisku v rámci rámečku stránky.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Hranice oblasti obrázku používané při tisku měřenou v MM_TWIPS.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>CRichEditView –:: GetPrintWidth

Voláním této funkce určíte šířku oblasti tisku.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka oblasti tisku měřená v MM_TWIPS.

##  <a name="getricheditctrl"></a>CRichEditView –:: GetRichEditCtrl

Voláním této funkce načtete objekt [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) přidružený `CRichEditView` k objektu.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

`CRichEditCtrl` Objekt pro toto zobrazení

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: hledán FindText](#findtext).

##  <a name="getselecteditem"></a>CRichEditView –:: GetSelectedItem

Voláním této funkce načtete položku OLE ( `CRichEditCntrItem` objekt) aktuálně vybranou v tomto `CRichEditView` objektu.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) vybraný v `CRichEditView` objektu; Hodnota NULL, pokud v tomto zobrazení není vybrána žádná položka.

##  <a name="gettextlength"></a>CRichEditView –:: GetTextLength

Voláním této funkce načtete délku textu v tomto `CRichEditView` objektu.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka textu v tomto `CRichEditView` objektu.

##  <a name="gettextlengthex"></a>CRichEditView –:: GetTextLengthEx

Tuto členskou funkci volejte pro výpočet délky textu v tomto `CRichEditView` objektu.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Hodnota určující metodu, která se má použít při určování délky textu Tento člen může být jednou nebo více hodnotami, které jsou uvedeny v části Flags Member of [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) popsané v Windows SDK.

*uCodePage*<br/>
Znaková stránka pro překlad (CP_ACP pro znakovou stránku ANSI, 1200 pro Unicode).

### <a name="return-value"></a>Návratová hodnota

Počet znaků nebo bajtů v ovládacím prvku pro úpravy. Pokud byly v *dwFlags*nastaveny nekompatibilní příznaky, vrátí tato členská funkce E_INVALIDARG.

### <a name="remarks"></a>Poznámky

`GetTextLengthEx`poskytuje další způsoby určení délky textu. Podporuje funkci s bohatou úpravou 2,0. Další informace najdete v tématu [o ovládacích prvcích pro úpravy s formátováním](/windows/win32/Controls/about-rich-edit-controls) v Windows SDK.

##  <a name="insertfileasobject"></a>CRichEditView –:: InsertFileAsObject

Voláním této funkce vložíte zadaný soubor (jako objekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) ) do zobrazení pro úpravy s formátováním.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec obsahující název souboru, který se má vložit

##  <a name="insertitem"></a>CRichEditView –:: InsertItem

Voláním této funkce vložíte objekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) do zobrazení pro úpravy s formátováním.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položku, která má být vložena.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT označující úspěch vložení.

### <a name="remarks"></a>Poznámky

Další informace o HRESULT naleznete v tématu [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

##  <a name="isricheditformat"></a>CRichEditView –:: IsRichEditFormat

Voláním této funkce určíte, zda je *CF* formát schránky, který je text, formátovaný text nebo formátovaný text s položkami OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Formát schránky, který vás zajímá.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má *CF* formát RTF nebo textový formát schránky.

##  <a name="isselected"></a>CRichEditView –:: s volbou

Voláním této funkce určíte, zda je zadaná položka OLE aktuálně vybrána v tomto zobrazení.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Ukazatel na objekt v zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt vybrán; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud má odvozená třída zobrazení jinou metodu pro zpracování výběru položek OLE.

##  <a name="m_nbulletindent"></a>CRichEditView –:: m_nBulletIndent

Odsazení položek odrážek v seznamu; ve výchozím nastavení 720 jednotek, což je 1/2 palců.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

Určuje typ zalamování řádků pro toto zobrazení s formátováním RTF.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Poznámky

Jedna z následujících hodnot:

- `WrapNone`Indikuje, že žádné automatické zalamování slov.

- `WrapToWindow`Označuje zalamování slov na základě šířky okna.

- `WrapToTargetDevice`Označuje zalamování slov na základě charakteristik cílového zařízení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: WrapChanged](#wrapchanged).

##  <a name="onchareffect"></a>CRichEditView –:: OnCharEffect

Voláním této funkce přepnete efekty formátování znaků pro aktuální výběr.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Změny formátování znaků v aktuálním výběru.

*dwEffect*<br/>
Požadovaný seznam efektů formátování znaků, které se mají přepnout

### <a name="remarks"></a>Poznámky

Každé volání této funkce přepíná zadané efekty formátování pro aktuální výběr.

Další informace o parametrech *dwMask* a *dwEffect* a jejich potenciálních hodnotách naleznete v tématu odpovídající datové členy [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>CRichEditView –:: OnFindNext

Volá se rozhraním, když se zpracovávají příkazy z dialogového okna Najít/nahradit.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Řetězec, který se má najít

*bNext*<br/>
Směr hledání: Hodnota TRUE označuje nižší hodnotu; NEPRAVDA, nahoru.

*bCase*<br/>
Označuje, zda má hledání rozlišovat velká a malá písmena.

*bWord*<br/>
Určuje, zda má hledání odpovídat pouze celá slova, nebo nikoli.

### <a name="remarks"></a>Poznámky

Voláním této funkce získáte text v rámci `CRichEditView`. Tuto funkci potlačíte, chcete-li změnit charakteristiky hledání pro odvozenou třídu zobrazení.

##  <a name="oninitialupdate"></a>CRichEditView –:: OnInitialUpdate

Volá se rozhraním po prvním připojení zobrazení k dokumentu, ale před tím, než se zobrazení zpočátku zobrazí.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členskou funkci [CView:: proupdate](../../mfc/reference/cview-class.md#onupdate) bez informací nápovědy (tj. použití výchozích hodnot 0 pro parametr *lHint* a hodnota null pro parametr *pHint* ). Přepište tuto funkci, pokud chcete provést jednorázovou inicializaci, která vyžaduje informace o dokumentu. Například pokud má vaše aplikace dokumenty s pevnou velikostí, můžete tuto funkci použít k inicializaci omezení posouvání zobrazení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty s proměnlivou velikostí, `OnUpdate` použijte k aktualizaci limitů posouvání pokaždé, když se dokument změní.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>CRichEditView –:: OnPasteNativeObject

Pomocí této funkce lze načíst nativní data z vložené položky.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parametry

*lpStg*<br/>
Ukazatel na objekt [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0;

### <a name="remarks"></a>Poznámky

Obvykle to provedete tak, že vytvoříte [COleStreamFile](../../mfc/reference/colestreamfile-class.md) kolem `IStorage`. Pro načtení dat [](../../mfc/reference/cobject-class.md#serialize) lzepřipojitkarchivuavoláníCObject::`COleStreamFile` serializovat.

Toto je pokročilá přepsatelné.

Další informace najdete v tématu [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) v Windows SDK.

##  <a name="onparaalign"></a>CRichEditView –:: OnParaAlign

Voláním této funkce změníte zarovnání odstavce pro vybrané odstavce.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parametry

*wAlign*<br/>
Požadované zarovnání odstavce. Jedna z následujících hodnot:

- PFA_LEFT zarovnává odstavce s levým okrajem.

- PFA_RIGHT zarovnejte odstavce s pravým okrajem.

- PFA_CENTER vycentruje odstavce mezi okraji.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>CRichEditView –:: OnPrinterChanged

Tuto funkci přepište, pokud chcete změnit vlastnosti pro toto zobrazení RTF při změně tiskárny.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parametry

*dcPrinter*<br/>
Objekt [CDC](../../mfc/reference/cdc-class.md) pro novou tiskárnu.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví velikost papíru na fyzickou výšku a šířku pro výstupní zařízení (tiskárnu). Pokud k *dcPrinter*není přidružený žádný kontext zařízení, výchozí implementace nastaví velikost papíru na 8,5 a 11 palců.

##  <a name="onreplaceall"></a>CRichEditView –:: OnReplaceAll

Volá se rozhraním, když se má zpracovat příkaz nahradit všechny příkazy z dialogového okna nahradit.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který má být nahrazen.

*lpszReplace*<br/>
Nahrazující text.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Určuje, zda je nutné při hledání zvolit celá slova nebo ne.

### <a name="remarks"></a>Poznámky

Voláním této funkce nahradíte všechny výskyty daného textu jiným řetězcem. Potlačením této funkce upravíte charakteristiky hledání pro toto zobrazení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: hledán FindText](#findtext).

##  <a name="onreplacesel"></a>CRichEditView –:: OnReplaceSel

Volá se rozhraním, když se zpracovávají příkazy nahradit v dialogovém okně nahradit.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který má být nahrazen.

*bNext*<br/>
Určuje směr hledání: Hodnota TRUE je mimo provoz. NEPRAVDA, nahoru.

*bCase*<br/>
Určuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Určuje, zda je nutné při hledání zvolit celá slova nebo ne.

*lpszReplace*<br/>
Nahrazující text.

### <a name="remarks"></a>Poznámky

Voláním této funkce nahradíte jeden výskyt nějakého zadaného textu jiným řetězcem. Potlačením této funkce upravíte charakteristiky hledání pro toto zobrazení.

##  <a name="ontextnotfound"></a>CRichEditView –:: OnTextNotFound

Volá se rozhraním, když se nepovede najít.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce změníte výstupní oznámení z [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Další informace najdete v tématu [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect

Rozhraní volá tuto funkci, aby aktualizovala uživatelské rozhraní příkazu pro příkazy efektu znaků.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI –](../../mfc/reference/ccmdui-class.md) .

*dwMask*<br/>
Určuje masku formátování znaků.

*dwEffect*<br/>
Označuje efekt formátování znaků.

### <a name="remarks"></a>Poznámky

Maska *dwMask* určuje, které atributy formátování znaků se mají kontrolovat. Příznaky *dwEffect* seznam atributů formátování znaků, které se mají nastavit nebo vymazat.

Další informace o parametrech *dwMask* a *dwEffect* a jejich potenciálních hodnotách naleznete v tématu odpovídající datové členy [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView –:: OnUpdateParaAlign

Rozhraní volá tuto funkci, aby aktualizovala uživatelské rozhraní příkazu pro příkazy efektu odstavce.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI –](../../mfc/reference/ccmdui-class.md) .

*wAlign*<br/>
Zarovnání odstavce pro kontrolu. Jedna z následujících hodnot:

- PFA_LEFT zarovnává odstavce s levým okrajem.

- PFA_RIGHT zarovnejte odstavce s pravým okrajem.

- PFA_CENTER vycentruje odstavce mezi okraji.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView –::P rintInsideRect

Voláním této funkce naformátujete rozsah textu v ovládacím prvku Rich Edit tak, aby se vešel do *rectLayout* pro zařízení určené *primárním řadičem domény*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení pro výstupní oblast.

*rectLayout*<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect) nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) definující výstupní oblast.

*nIndexStart*<br/>
Nulový index prvního znaku, který má být formátován.

*nIndexStop*<br/>
Index s nulovým základem posledního znaku, který má být formátován.

*bOutput*<br/>
Určuje, zda má být vykreslen text. Je-li hodnota FALSE, text je právě změřen.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku, který se vejde do výstupní oblasti a druhý

### <a name="remarks"></a>Poznámky

Obvykle je toto volání následováno voláním [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , které generuje výstup.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: GetPaperSize](#getpapersize).

##  <a name="printpage"></a>CRichEditView –::P rintPage

Voláním této funkce naformátujete rozsah textu v ovládacím prvku Rich Edit pro výstupní zařízení určené *primárním řadičem domény*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení pro výstup stránky.

*nIndexStart*<br/>
Nulový index prvního znaku, který má být formátován.

*nIndexStop*<br/>
Index s nulovým základem posledního znaku, který má být formátován.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku, který se vejde na stránku plus jedna.

### <a name="remarks"></a>Poznámky

Rozložení každé stránky je řízeno [GetPageRect](#getpagerect) a [GetPrintRect](#getprintrect). Obvykle je toto volání následováno voláním [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , které generuje výstup.

Všimněte si, že okraje jsou relativní vzhledem k fyzické stránce, ne k logické stránce. Proto budou marže nuly často vystřihnout text, protože mnoho tiskáren má na stránce netisknutelné oblasti. Aby nedošlo k oříznutí textu, měli byste před tiskem volat [SetMargins](#setmargins) a nastavit přiměřené okraje.

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

Volá se rozhraním, aby se vložil objekt do Rich Edit.

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>Parametry

*lpdataobj*<br/>
Ukazatel na [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) pro dotaz.

*lpcfFormat*<br/>
Ukazatel na přijatelný formát dat.

*dwReco*<br/>
Nepoužívá se.

*bReally*<br/>
Určuje, zda by měla operace vložení pokračovat, nebo ne.

*hMetaFile*<br/>
Popisovač metasouboru, který se používá k vykreslení ikony položky

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT, která hlásí úspěch operace.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud chcete zpracovat různé organizace položek modelu COM v odvozené třídě dokumentu. Toto je pokročilá přepsatelné.

Další informace o HRESULT a `IDataObject`naleznete v tématu [Struktura chybových kódů com](/windows/win32/com/structure-of-com-error-codes) a [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)v uvedeném pořadí v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView –:: SetCharFormat

Voláním této funkce nastavíte atributy formátování znaků pro nový text v tomto `CRichEditView` objektu.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Struktura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) obsahující nové výchozí atributy formátování znaků.

### <a name="remarks"></a>Poznámky

Touto funkcí se změnily pouze `dwMask` atributy určené členem *CF* .

Další informace naleznete v tématu [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Message and [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) Structure in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView –:: SetMargins

Voláním této funkce nastavíte okraje pro tisk pro toto zobrazení s bohatou úpravou.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parametry

*rectMargin*<br/>
Nové hodnoty okrajů pro tisk měřené v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Pokud [](#m_nwordwrap) je `WrapToTargetDevice`m_nWordWrap, měli byste zavolat [WrapChanged](#wrapchanged) po použití této funkce pro úpravu vlastností tisku.

Všimněte si, že okraje používané v [PrintPage](#printpage) jsou relativní vzhledem k fyzické stránce, ne k logické stránce. Proto budou marže nuly často vystřihnout text, protože mnoho tiskáren má na stránce netisknutelné oblasti. Chcete-li se vyhnout oříznutí textu, měli `SetMargins` byste volat použití k nastavení přiměřených okrajů tiskárny před tiskem.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: GetPaperSize](#getpapersize).

##  <a name="setpapersize"></a>CRichEditView –:: SetPaperSize

Voláním této funkce nastavíte velikost papíru pro tisk tohoto zobrazení s bohatou úpravou.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parametry

*sizePaper*<br/>
Nové hodnoty velikosti papíru pro tisk měřené v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Pokud [](#m_nwordwrap) je `WrapToTargetDevice`m_nWordWrap, měli byste zavolat [WrapChanged](#wrapchanged) po použití této funkce pro úpravu vlastností tisku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView –:: SetParaFormat

Voláním této funkce nastavíte atributy formátování odstavce pro aktuální výběr v tomto `CRichEditView` objektu.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parametry

*pf*<br/>
[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) struktura obsahující nové výchozí atributy formátování odstavce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Touto funkcí se změnily pouze `dwMask` atributy určené členem *BF* .

Další informace naleznete v tématu [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) Structure in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>CRichEditView –:: TextNotFound

Voláním této funkce obnovíte stav interního vyhledávání ovládacího prvku [CRichEditView –](../../mfc/reference/cricheditview-class.md) po neúspěšném volání [hledán FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Obsahuje textový řetězec, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Doporučuje se, aby se tato metoda volala hned po neúspěšných voláních [hledán FindText](#findtext) , aby se správně obnovil stav interního hledání daného ovládacího prvku.

Parametr *lpszFind* by měl zahrnovat stejný obsah jako řetězec poskytnutý pro [hledán FindText](#findtext). Po resetování vnitřního stavu hledání Tato metoda zavolá metodu [OnTextNotFound](#ontextnotfound) se zadaným hledaným řetězcem.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView –:: hledán FindText](#findtext).

##  <a name="wrapchanged"></a>CRichEditView –:: WrapChanged

Tuto funkci volejte, když se změní charakteristiky tisku ( [SetMargins](#setmargins) nebo [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze změnit způsob, jakým zobrazení s bohatou úpravou reaguje na změny v [m_nWordWrap](#m_nwordwrap) nebo charakteristiky tisku ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázka knihovny MFC v programu WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc – třída](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem – třída](../../mfc/reference/cricheditcntritem-class.md)
