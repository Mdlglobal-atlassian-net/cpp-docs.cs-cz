---
title: CRichEditView – třída
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
ms.openlocfilehash: 2d832f3cc07d39ace9e679901c5344a376cea03c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318629"
---
# <a name="cricheditview-class"></a>CRichEditView – třída

S [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) a [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), poskytuje funkce rich edit control v kontextu architektury zobrazení dokumentu knihovny MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Vytvoří `CRichEditView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRichEditView::UpravitdialogPosition](#adjustdialogposition)|Přesune dialogové okno tak, aby nezakrývalo aktuální výběr.|
|[CricheditView::CanPaste](#canpaste)|Určuje, zda schránka obsahuje data, která lze vložit do rozšířeného zobrazení úprav.|
|[CRichEditView::DoPaste](#dopaste)|Vloží položku OLE do tohoto rozšířeného zobrazení úprav.|
|[CRichEditView::FindText](#findtext)|Najde zadaný text s vyvoláním kurzorčekání.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Najde zadaný text.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Načte atributy formátování znaků pro aktuální výběr.|
|[CRichEditView::GetDocument](#getdocument)|Načte ukazatel na související [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|
|[CricheditView::GetInplaceActiveItem](#getinplaceactiveitem)|Načte položku OLE, která je aktuálně na místě aktivní v zobrazení bohaté úpravy.|
|[CRichEditView::Okraje](#getmargins)|Načte okraje pro toto rozšířené zobrazení úprav.|
|[CRichEditView::GetPageRect](#getpagerect)|Načte obdélník stránky pro toto rozšířené zobrazení úprav.|
|[CRichEditView::GetPaperSize](#getpapersize)|Načte velikost papíru pro toto rozšířené zobrazení úprav.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Načte atributy formátování odstavce pro aktuální výběr.|
|[CRichEditView::GetPrintRect](#getprintrect)|Načte obdélník tisku pro toto rozšířené zobrazení úprav.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Načte šířku tisku pro toto rozšířené zobrazení úprav.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Načte ovládací prvek rich edit.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Načte vybranou položku z bohatého zobrazení úprav.|
|[CRichEditView::GetTextLength](#gettextlength)|Načte délku textu v rozšířeném zobrazení úprav.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Načte počet znaků nebo bajtů v rozšířeném zobrazení úprav. Rozšířený seznam příznaků pro metodu určení délky.|
|[CRichEditView::InsertfileAsObject](#insertfileasobject)|Vloží soubor jako položku OLE.|
|[CRichEditView::InsertItem](#insertitem)|Vloží novou položku jako položku OLE.|
|[CricheditView::isricheditformat](#isricheditformat)|Určuje, zda schránka obsahuje data v formátu RICH edit nebo text.|
|[CricheditView::OnCharEffect](#onchareffect)|Přepíná formátování znaků pro aktuální výběr.|
|[CricheditView::OnparaAlign](#onparaalign)|Změní zarovnání odstavců.|
|[CricheditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizuje příkaz uI pro znak veřejné členské funkce.|
|[CricheditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizuje příkaz uI pro odstavce veřejné členské funkce.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Zformátuje zadaný text v daném obdélníku.|
|[CRichEditView::PrintPage](#printpage)|Zformátuje zadaný text na dané stránce.|
|[CRichEditView::SetCharFormat](#setcharformat)|Nastaví atributy formátování znaků pro aktuální výběr.|
|[CRichEditView::SetMargins](#setmargins)|Nastaví okraje pro toto rozšířené zobrazení úprav.|
|[CRichEditView::SetPaperSize](#setpapersize)|Nastaví velikost papíru pro toto rozšířené zobrazení úprav.|
|[CRichEditView::SetParaFormat](#setparaformat)|Nastaví atributy formátování odstavce pro aktuální výběr.|
|[CricheditView::Textnotfound](#textnotfound)|Obnoví stav vnitřního hledání ovládacího prvku.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Načte objekt schránky pro oblast v tomto rozšířeném zobrazení úprav.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Načte místní nabídku pro použití na pravé tlačítko myši dolů.|
|[CricheditView::Jevybrán](#isselected)|Označuje, zda je daná položka OLE vybrána či nikoli.|
|[CricheditView::OnFindNext](#onfindnext)|Najde další výskyt podřetězce.|
|[CricheditView::OnInitialUpdate](#oninitialupdate)|Aktualizuje zobrazení při prvním připojení k dokumentu.|
|[cricheditview::onpastenativeobject](#onpastenativeobject)|Načte nativní data z položky OLE.|
|[CricheditView::OnPrinterZměněn](#onprinterchanged)|Nastaví tiskové charakteristiky na dané zařízení.|
|[CricheditView::OnReplaceAll](#onreplaceall)|Nahradí všechny výskyty daného řetězce novým řetězcem.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|
|[CricheditView::ontextnotfound](#ontextnotfound)|Zpracovává oznámení uživatele, že požadovaný text nebyl nalezen.|
|[CrichEditView::QueryAcceptData](#queryacceptdata)|Dotazy k zobrazení dat na `IDataObject`.|
|[CRichEditView::WrapChanged](#wrapchanged)|Upraví cílové výstupní zařízení pro toto rozšířené zobrazení `m_nWordWrap`úprav na základě hodnoty aplikace .|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Označuje velikost odsazení pro seznamy odrážek.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Označuje omezení zalamování řádků.|

## <a name="remarks"></a>Poznámky

"Rich edit control" je okno, ve kterém může uživatel zadávat a upravovat text. Text může být přiřazen k formátování znaků a odstavců a může obsahovat vložené objekty OLE. Ovládací prvky pro úpravy rich poskytují programovací rozhraní pro formátování textu. Aplikace však musí implementovat všechny součásti uživatelského rozhraní nezbytné k tomu, aby byly operace formátování dostupné uživateli.

`CRichEditView`zachová text a formátování charakteristiky textu. `CRichEditDoc`udržuje seznam položek klienta OLE, které jsou v zobrazení. `CRichEditCntrItem`poskytuje přístup na straně kontejneru k položce klienta OLE.

Tento ovládací prvek Windows Common (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novější.

Příklad použití rozšířeného zobrazení úprav v aplikaci knihovny MFC naleznete v ukázkové aplikaci [wordpadu.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>CRichEditView::UpravitdialogPosition

Volánítéto funkce přesunout dané dialogové okno tak, aby nezakrývalo aktuální výběr.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parametry

*pDlg*<br/>
Ukazatel na `CDialog` objekt.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>CricheditView::CanPaste

Volání této funkce k určení, zda schránka obsahuje informace, které lze vložit do tohoto zobrazení bohaté úpravy.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud schránka obsahuje data ve formátu, který může toto rozšířené zobrazení úprav přijmout; jinak 0.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>CRichEditView::CRichEditView

Volání této funkce `CRichEditView` k vytvoření objektu.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>CRichEditView::DoPaste

Volání této funkce pro vložení položky OLE v *dataobj* do tohoto rozšířeného upravit dokument/zobrazení.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parametry

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md) obsahující data vložit.

*Viz*<br/>
Požadovaný formát schránky.

*hMetaPict*<br/>
Metasoubor, který představuje položku, která má být vložena.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto funkci jako součást výchozí implementace [QueryAcceptData](#queryacceptdata).

Tato funkce určuje typ pasty na základě výsledků obslužné rutiny pro Vložit jinak. Pokud *cf* je 0, nová položka používá aktuální ikonické reprezentace. Pokud *cf* je nenulová a *hMetaPict* není NULL, nová položka používá *hMetaPict* pro jeho reprezentaci.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>CRichEditView::FindText

Voláním této funkce vyhledejte zadaný text a nastavte jej jako aktuální výběr.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Obsahuje řetězec, který chcete vyhledat.

*bCase*<br/>
Označuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Označuje, zda by hledání mělo odpovídat pouze celým slovům, nikoli částem slov.

*bDalší*<br/>
Označuje směr hledání. Pokud TRUE, směr hledání je směrem ke konci vyrovnávací paměti. Pokud false, směr hledání je směrem k začátku vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je nalezen text *lpszFind;* jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce zobrazí kurzor čekání během operace hledání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>CRichEditView::FindTextSimple

Voláním této funkce vyhledejte zadaný text a nastavte jej jako aktuální výběr.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Obsahuje řetězec, který chcete vyhledat.

*bCase*<br/>
Označuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Označuje, zda by hledání mělo odpovídat pouze celým slovům, nikoli částem slov.

*bDalší*<br/>
Označuje směr hledání. Pokud TRUE, směr hledání je směrem ke konci vyrovnávací paměti. Pokud false, směr hledání je směrem k začátku vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je nalezen text *lpszFind;* jinak 0.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::FindText](#findtext).

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection

Voláním této funkce získáte atributy formátování znaků aktuálního výběru.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Návratová hodnota

Struktura [CHARFORMAT2,](/windows/win32/api/richedit/ns-richedit-charformat2w) která obsahuje atributy formátování znaků aktuálního výběru.

### <a name="remarks"></a>Poznámky

Další informace naleznete ve [zprávě EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) a struktury [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>CRichEditView::GetClipboardData

Framework volá tuto funkci jako součást zpracování [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parametry

*lpchrg*<br/>
Ukazatel na strukturu [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) určující rozsah znaků (a položek OLE), které se mají kopírovat do datového objektu určeného *lplpdataobj*.

*dwReco*<br/>
Příznak operace schránky. Může být jednou z těchto hodnot.

- RECO_COPY Copy do schránky.

- RECO_CUT Vyjmout do schránky.

- RECO_DRAG Operace přetažení (přetažení).

- RECO_DROP Drop operace (drag and drop).

- RECO_PASTE vložit ze schránky.

*lpRichDataObj*<br/>
Ukazatel na objekt [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) obsahující data schránky z ovládacího prvku rich edit ( [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Ukazatel na proměnnou ukazatele, která `IDataObject` přijímá adresu objektu představující rozsah zadaný v parametru *lpchrg.* Hodnota *lplpdataobj* je ignorována, pokud je vrácena chyba.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT vykazující úspěch operace. Další informace o hresult naleznete [v tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud vrácená hodnota `IRichEditOleCallback::GetClipboardData` označuje `IDataObject` úspěch, vrátí přístup *lplpdataobj*; v opačném případě vrátí ten, ke který přistupuje *lpRichDataObj*. Přepište tuto funkci a zadejte vlastní data schránky. Výchozí implementace této funkce vrátí E_NOTIMPL.

Tohle je pokročilé překažné.

Další informace naleznete v [tématech IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)a [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) v sadě Windows SDK a viz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) v sadě Windows SDK.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>CRichEditView::GetContextMenu

Framework volá tuto funkci jako součást zpracování [IRichEditOleCallback::GetContextContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parametry

*seltyp*<br/>
Typ výběru. Hodnoty typu výběru jsou popsány v části Poznámky.

*lpoleobj*<br/>
Ukazatel na `OLEOBJECT` strukturu určující první vybraný objekt OLE, pokud výběr obsahuje jednu nebo více položek OLE. Pokud výběr neobsahuje žádné položky, *lpoleobj* je NULL. Struktura `OLEOBJECT` obsahuje ukazatel na objekt OLE v-table.

*lpchrg*<br/>
Ukazatel na strukturu [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) obsahující aktuální výběr.

### <a name="return-value"></a>Návratová hodnota

Zpracovat místní nabídku.

### <a name="remarks"></a>Poznámky

Tato funkce je typickou součástí zpracování pravého tlačítka myši dolů.

Typ výběru může být libovolná kombinace následujících příznaků:

- SEL_EMPTY Označuje, že neexistuje žádný aktuální výběr.

- SEL_TEXT Označuje, že aktuální výběr obsahuje text.

- SEL_OBJECT Označuje, že aktuální výběr obsahuje alespoň jednu položku OLE.

- SEL_MULTICHAR Označuje, že aktuální výběr obsahuje více než jeden znak textu.

- SEL_MULTIOBJECT Označuje, že aktuální výběr obsahuje více než jeden objekt OLE.

Výchozí implementace vrátí hodnotu NULL. Tohle je pokročilé překažné.

Další informace naleznete v [tématu IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) a [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) v sadě Windows SDK.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>CRichEditView::GetDocument

Volání této funkce získat ukazatel `CRichEditDoc` na přidružené k tomuto zobrazení.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) `CRichEditView` přidružený k objektu.

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>CricheditView::GetInplaceActiveItem

Volání této funkce získat položku OLE, která je `CRichEditView` aktuálně aktivována na místě v tomto objektu.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na jeden, na místě aktivní [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objektu v tomto zobrazení rich úprav; Null, pokud není žádná položka OLE aktuálně v aktivním stavu na místě.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>CRichEditView::Okraje

Volání této funkce načíst aktuální okraje používané při tisku.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Návratová hodnota

Okraje použité při tisku, měřeno v MM_TWIPS.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>CRichEditView::GetPageRect

Voláním této funkce získáte rozměry stránky použité při tisku.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Hranice stránky použité při tisku, měřeno v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Tato hodnota je založena na velikosti papíru.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>CRichEditView::GetPaperSize

Voláním této funkce načtěte aktuální velikost papíru.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost papíru použitého při tisku měřená v MM_TWIPS.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection

Voláním této funkce získáte atributy formátování odstavce aktuálního výběru.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Návratová hodnota

Struktura [PARAFORMAT2,](/windows/win32/api/richedit/ns-richedit-paraformat2) která obsahuje atributy formátování odstavce aktuálního výběru.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) structure in the Windows SDK.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>CRichEditView::GetPrintRect

Volání této funkce načíst hranice oblasti tisku v obdélníku stránky.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Hranice oblasti obrazu použité při tisku, měřené v MM_TWIPS.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>CRichEditView::GetPrintWidth

Voláním této funkce určete šířku oblasti tisku.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka oblasti tisku měřená v MM_TWIPS.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>CRichEditView::GetRichEditCtrl

Volání této funkce načíst [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) `CRichEditView` objekt přidružený k objektu.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CRichEditCtrl` pro toto zobrazení.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::FindText](#findtext).

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>CRichEditView::GetSelectedItem

Volání této funkce k načtení `CRichEditCntrItem` položky OLE (objektu) aktuálně vybrané v tomto `CRichEditView` objektu.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) `CRichEditView` vybraný v objektu; Null, pokud není v tomto zobrazení vybrána žádná položka.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>CRichEditView::GetTextLength

Volání této funkce načíst délku `CRichEditView` textu v tomto objektu.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka textu v tomto `CRichEditView` objektu.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx

Volání této členské funkce pro výpočet délky textu v tomto `CRichEditView` objektu.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Hodnota určující metodu, která má být použita při určování délky textu. Tento člen může být jedna nebo více hodnot uvedených v členu příznaků [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) popsaného v sadě Windows SDK.

*uCodePage*<br/>
Znaková stránka pro překlad (CP_ACP pro znakovou stránku ANSI, 1200 pro Unicode).

### <a name="return-value"></a>Návratová hodnota

Počet znaků nebo bajtů v ovládacím prvku úprav. Pokud byly v *dwFlags*nastaveny nekompatibilní příznaky , vrátí tato členská funkce E_INVALIDARG.

### <a name="remarks"></a>Poznámky

`GetTextLengthEx`poskytuje další způsoby určení délky textu. Podporuje funkci Rich Edit 2.0. Další informace naleznete v [tématu O rozšířených ovládacích prvcích úprav](/windows/win32/Controls/about-rich-edit-controls) v sadě Windows SDK.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>CRichEditView::InsertfileAsObject

Volání této funkce vložit zadaný soubor (jako [cRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objekt) do zobrazení bohaté úpravy.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parametry

*název souboru lpsz*<br/>
Řetězec obsahující název souboru, který má být vložen.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>CRichEditView::InsertItem

Volání této funkce vložit [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objektu do zobrazení bohaté úpravy.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parametry

*pPoložka*<br/>
Ukazatel na položku, která má být vložena.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT označující úspěch vložení.

### <a name="remarks"></a>Poznámky

Další informace o hresult naleznete [v tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>CricheditView::isricheditformat

Volání této funkce k určení, zda *cf* je formát schránky, který je text, formát RTF nebo formátovaný text s položkami OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parametry

*Viz*<br/>
Formát schránky zájmu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud *cf* je formát rozšířené úpravy nebo textové schránky.

## <a name="cricheditviewisselected"></a><a name="isselected"></a>CricheditView::Jevybrán

Volání této funkce k určení, zda je zadaná položka OLE aktuálně vybrána v tomto zobrazení.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Ukazatel na objekt v zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt vybrán; jinak 0.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud vaše odvozené zobrazení třídy má jinou metodu pro zpracování výběru položek OLE.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent

Odsazení pro položky odrážek v seznamu; ve výchozím nastavení 720 jednotek, což je 1/2 palce.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap

Označuje typ zalamování slov pro toto rozšířené zobrazení úprav.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Poznámky

Jedna z následujících hodnot:

- `WrapNone`Označuje žádné automatické obtékání slov.

- `WrapToWindow`Označuje zalomení slova na základě šířky okna.

- `WrapToTargetDevice`Označuje zalamování řádků na základě vlastností cílového zařízení.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::WrapChanged](#wrapchanged).

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>CricheditView::OnCharEffect

Voláním této funkce přepnete efekty formátování znaků pro aktuální výběr.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Efekty formátování znaků, které chcete upravit v aktuálním výběru.

*dwEfekt*<br/>
Požadovaný seznam efektů formátování znaků, které chcete přepnout.

### <a name="remarks"></a>Poznámky

Každé volání této funkce přepíná zadané efekty formátování pro aktuální výběr.

Další informace o parametrech *dwMask* a *dwEffect* a jejich potenciálních hodnotách naleznete v odpovídajících datových členech [sady CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>CricheditView::OnFindNext

Volat rámci při zpracování příkazů z dialogového okna Najít a nahradit.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Řetězec, který se má najít.

*bDalší*<br/>
Směr hledání: PRAVDA označuje dolů; FALSE, nahoru.

*bCase*<br/>
Označuje, zda hledání má být malá a velká písmena.

*bWord*<br/>
Označuje, zda má hledání odpovídat pouze celým slovům, či nikoli.

### <a name="remarks"></a>Poznámky

Voláním této funkce vyhledejte text v rámci . `CRichEditView` Přepište tuto funkci a změňte vyhledávací charakteristiky odvozené třídy zobrazení.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>CricheditView::OnInitialUpdate

Volat rámci po zobrazení je nejprve připojen k dokumentu, ale před zobrazení je zpočátku zobrazena.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce volá členská funkci [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) bez informací nápovědy (to znamená pomocí výchozích hodnot 0 pro parametr *lHint* a NULL pro parametr *pHint).* Přepište tuto funkci a proveďte jednorázovou inicializaci, která vyžaduje informace o dokumentu. Pokud má například aplikace dokumenty pevné velikosti, můžete pomocí této funkce inicializovat omezení posouvání zobrazení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty s `OnUpdate` proměnnou velikosti, použijte k aktualizaci omezení posouvání při každé změně dokumentu.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::m_nWordWrap](#m_nwordwrap).

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>cricheditview::onpastenativeobject

Tato funkce slouží k načtení nativních dat z vložené položky.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parametry

*lpStg*<br/>
Ukazatel na objekt [IStorage.](/windows/win32/api/objidl/nn-objidl-istorage)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0;

### <a name="remarks"></a>Poznámky

Obvykle byste to provést vytvořením [COleStreamFile](../../mfc/reference/colestreamfile-class.md) `IStorage`kolem . Lze `COleStreamFile` připojit k archivu a [CObject::Serializovat](../../mfc/reference/cobject-class.md#serialize) volána k načtení dat.

Tohle je pokročilé překažné.

Další informace naleznete v [tématu IStorage](/windows/win32/api/objidl/nn-objidl-istorage) v sadě Windows SDK.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>CricheditView::OnparaAlign

Voláním této funkce změníte zarovnání odstavce pro vybrané odstavce.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parametry

*wZarovnat*<br/>
Požadované zarovnání odstavce. Jedna z následujících hodnot:

- PFA_LEFT Zarovnejte odstavce s levým okrajem.

- PFA_RIGHT Zarovnejte odstavce s pravým okrajem.

- PFA_CENTER Vystředit odstavce mezi okraji.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>CricheditView::OnPrinterZměněn

Přepsáním této funkce změníte charakteristiky tohoto rozšířeného zobrazení úprav při změně tiskárny.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parametry

*dcTiskárna*<br/>
Objekt [CDC](../../mfc/reference/cdc-class.md) pro novou tiskárnu.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví velikost papíru na fyzickou výšku a šířku výstupního zařízení (tiskárny). Pokud není k *dcPrinter*přidružen žádný kontext zařízení , nastaví výchozí implementace velikost papíru na 8,5 o 11 palců.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>CricheditView::OnReplaceAll

Volat rámci při zpracování nahradit všechny příkazy z dialogového okna Nahradit.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nahrazen.

*lpszNahradit*<br/>
Náhradní text.

*bCase*<br/>
Označuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Označuje, zda hledání musí vybrat celá slova nebo ne.

### <a name="remarks"></a>Poznámky

Volání této funkce nahradit všechny výskyty některých daný text s jiným řetězcem. Přepsáním této funkce změníte charakteristiky hledání pro toto zobrazení.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::FindText](#findtext).

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>CRichEditView::OnReplaceSel

Volat rámci při zpracování Nahradit příkazy z dialogového okna Nahradit.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který má být nahrazen.

*bDalší*<br/>
Označuje směr hledání: PRAVDA je dole; FALSE, nahoru.

*bCase*<br/>
Označuje, zda hledání rozlišuje malá a velká písmena.

*bWord*<br/>
Označuje, zda hledání musí vybrat celá slova nebo ne.

*lpszNahradit*<br/>
Náhradní text.

### <a name="remarks"></a>Poznámky

Volání této funkce nahradit jeden výskyt některých daný text s jiným řetězcem. Přepsáním této funkce změníte charakteristiky hledání pro toto zobrazení.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>CricheditView::ontextnotfound

Volat rámci při selhání hledání.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Text, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci změnit výstupní oznámení z [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Další informace naleznete v tématu [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>CricheditView::OnUpdateCharEffect

Rozhraní Framework volá tuto funkci k aktualizaci příkazu UI pro příkazy efekt znaků.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI.](../../mfc/reference/ccmdui-class.md)

*dwMask*<br/>
Označuje masku formátování znaků.

*dwEfekt*<br/>
Označuje efekt formátování znaků.

### <a name="remarks"></a>Poznámky

Maska *dwMask* určuje, které atributy formátování znaků mají být kontrolovány. Příznaky *dwEffect* seznam atributy formátování znaků nastavit/ vymazat.

Další informace o parametrech *dwMask* a *dwEffect* a jejich potenciálních hodnotách naleznete v odpovídajících datových členech [sady CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>CricheditView::OnUpdateParaAlign

Framework volá tuto funkci k aktualizaci příkazu UI pro příkazy odstavcový efekt.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI.](../../mfc/reference/ccmdui-class.md)

*wZarovnat*<br/>
Zarovnání odstavce ke kontrole. Jedna z následujících hodnot:

- PFA_LEFT Zarovnejte odstavce s levým okrajem.

- PFA_RIGHT Zarovnejte odstavce s pravým okrajem.

- PFA_CENTER Vystředit odstavce mezi okraji.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>CRichEditView::PrintInsideRect

Volání této funkce pro formátování rozsahu textu v ovládacím prvku rich edit, aby se vešly do *rectLayout* pro zařízení určené *pDC*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení pro výstupní oblast.

*rectLayout*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect) nebo [CRect,](../../atl-mfc-shared/reference/crect-class.md) který definuje výstupní oblast.

*nIndexStart*<br/>
Nulový index prvního znaku, který má být formátován.

*nIndexStop*<br/>
Nulový index posledního znaku, který má být formátován.

*bVýstup*<br/>
Označuje, zda má být text vykreslen. Pokud false, text je jen měří.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku, který se vejde do výstupní oblasti plus jeden.

### <a name="remarks"></a>Poznámky

Obvykle toto volání následuje volání [CRichEditCtrl::DisplayBand,](../../mfc/reference/cricheditctrl-class.md#displayband) který generuje výstup.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::GetPaperSize](#getpapersize).

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>CRichEditView::PrintPage

Volání této funkce pro formátování rozsahu textu v rozšířeném ovládacím prvku úprav pro výstupní zařízení určené *pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení pro výstup stránky.

*nIndexStart*<br/>
Nulový index prvního znaku, který má být formátován.

*nIndexStop*<br/>
Nulový index posledního znaku, který má být formátován.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku, který se vejde na stránku plus jeden.

### <a name="remarks"></a>Poznámky

Rozložení každé stránky je řízeno [GetPageRect](#getpagerect) a [GetPrintRect](#getprintrect). Obvykle toto volání následuje volání [CRichEditCtrl::DisplayBand,](../../mfc/reference/cricheditctrl-class.md#displayband) který generuje výstup.

Všimněte si, že okraje jsou relativní vzhledem k fyzické stránce, nikoli logické stránce. Okraje nuly tedy často oříznou text, protože mnoho tiskáren má na stránce netisknutelné oblasti. Chcete-li se vyhnout oříznutí textu, měli byste před tiskem zavolat [SetMargins](#setmargins) a nastavit přiměřené okraje.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>CrichEditView::QueryAcceptData

Volat rámci vložit objekt do bohaté upravit.

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
Ukazatel na [objekt IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) pro dotaz.

*lpcfFormat*<br/>
Ukazatel na přijatelný formát dat.

*dwReco*<br/>
Nepoužívá se.

*bOpravdu*<br/>
Označuje, zda by měla operace vložení pokračovat či nikoli.

*hMetaSoubor*<br/>
Úchyt metasouboru použitého k kreslení ikony položky.

### <a name="return-value"></a>Návratová hodnota

Hodnota HRESULT vykazující úspěch operace.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci pro zpracování různých organizací položek COM v odvozené třídě dokumentu. Tohle je pokročilé překažné.

Další informace o hresult a `IDataObject`najdete v [tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) a [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>CRichEditView::SetCharFormat

Voláním této funkce nastavte atributy formátování znaků pro `CRichEditView` nový text v tomto objektu.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parametry

*Viz*<br/>
[CharFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) struktura obsahující nové výchozí atributy formátování znaků.

### <a name="remarks"></a>Poznámky

Tato funkce změní pouze `dwMask` atributy určené členem *cf.*

Další informace naleznete [v tématu EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) message and [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) structure in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>CRichEditView::SetMargins

Voláním této funkce nastavte okraje tisku pro toto rozšířené zobrazení úprav.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parametry

*rectMarže*<br/>
Nové hodnoty okrajů pro tisk měřené v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Pokud [m_nWordWrap](#m_nwordwrap) m_nWordWrap `WrapToTargetDevice`je , měli byste volat [WrapChanged](#wrapchanged) po použití této funkce upravit tiskové charakteristiky.

Všimněte si, že okraje používané [PrintPage](#printpage) jsou relativní vzhledem k fyzické stránce, nikoli logické stránce. Okraje nuly tedy často oříznou text, protože mnoho tiskáren má na stránce netisknutelné oblasti. Chcete-li zabránit oříznutí textu, `SetMargins` měli byste před tiskem zavolat použít k nastavení přiměřených okrajů tiskárny.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::GetPaperSize](#getpapersize).

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>CRichEditView::SetPaperSize

Voláním této funkce nastavte velikost papíru pro tisk tohoto rozšířeného zobrazení úprav.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parametry

*sizePaper*<br/>
Nové hodnoty velikosti papíru pro tisk měřené v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Pokud [m_nWordWrap](#m_nwordwrap) m_nWordWrap `WrapToTargetDevice`je , měli byste volat [WrapChanged](#wrapchanged) po použití této funkce upravit tiskové charakteristiky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>CRichEditView::SetParaFormat

Voláním této funkce nastavte atributy formátování odstavce pro `CRichEditView` aktuální výběr v tomto objektu.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parametry

*Pf*<br/>
[Struktura PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) obsahující nové výchozí atributy formátování odstavce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce změní pouze `dwMask` atributy určené členem *pf.*

Další informace naleznete [v tématu EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) structure in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>CricheditView::Textnotfound

Volání této funkce obnovit stav vnitřního vyhledávání ovládacího prvku [CRichEditView](../../mfc/reference/cricheditview-class.md) po neúspěšném volání [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszNajít*<br/>
Obsahuje textový řetězec, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Doporučuje se, aby tato metoda byla volána ihned po neúspěšných voláních [FindText](#findtext) tak, aby byl správně resetován stav vnitřního hledání ovládacího prvku.

Parametr *lpszFind* by měl obsahovat stejný obsah jako řetězec poskytnutý [findtextu](#findtext). Po obnovení stavu vnitřního vyhledávání bude tato metoda volat metodu [OnTextNotFound](#ontextnotfound) s poskytnutým vyhledávacím řetězcem.

### <a name="example"></a>Příklad

  Viz příklad [cricheditview::FindText](#findtext).

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>CRichEditView::WrapChanged

Volání této funkce při změně vlastností tisku [(SetMargins](#setmargins) nebo [SetPaperSize).](#setpapersize)

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Poznámky

Přepsáním této funkce můžete upravit způsob, jakým zobrazení bohaté úpravy reaguje na změny [m_nWordWrap](#m_nwordwrap) nebo vlastností tisku ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Viz také

[MFC Ukázka WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CrichEditDoc](../../mfc/reference/cricheditdoc-class.md)<br/>
[Třída CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)
