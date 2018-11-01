---
title: Cricheditview – třída
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
ms.openlocfilehash: 2eebfe18275aa63ac26c0c898a5d796300860db8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476608"
---
# <a name="cricheditview-class"></a>Cricheditview – třída

S [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md) a [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md), poskytuje funkce pro ovládací prvek RTF v rámci kontextu architektury zobrazení dokumentu MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Vytvoří `CRichEditView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Přesune dialogovému oknu, takže ho nebude skryl aktuálního výběru.|
|[CRichEditView::CanPaste](#canpaste)|Určuje, zda schránky obsahuje data, která lze vložit do zobrazení RichEdit.|
|[CRichEditView::DoPaste](#dopaste)|Vloží položku OLE. v tomto zobrazení RichEdit.|
|[CRichEditView::FindText](#findtext)|Vyhledá zadaný text vyvolání kurzor pro čekání.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Vyhledá zadaný text.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Načte formátování atributy pro aktuální výběr.|
|[CRichEditView::GetDocument](#getdocument)|Načte ukazatel na související [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md).|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Načte položky OLE, který je aktuálně v místě aktivní v zobrazení RichEdit.|
|[CRichEditView::GetMargins](#getmargins)|Načte rozpětí pro toto zobrazení RichEdit.|
|[CRichEditView::GetPageRect](#getpagerect)|Načte obdélník stránky pro toto zobrazení RichEdit.|
|[CRichEditView::GetPaperSize](#getpapersize)|Načte papíru pro toto zobrazení RichEdit.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Získá atributy pro aktuální výběr formátování odstavce.|
|[CRichEditView::GetPrintRect](#getprintrect)|Načte obdélník tisku pro toto zobrazení RichEdit.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Načte tisku šířku pro toto zobrazení RichEdit.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Načte ovládací prvek RichEdit.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Načte vybranou položku ze zobrazení RichEdit.|
|[CRichEditView::GetTextLength](#gettextlength)|Získá délku textu v zobrazení RichEdit.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Získá počet znaků nebo bajtů v zobrazení RichEdit. Seznam rozšířené příznak pro metodu určující délku.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Vloží soubor jako položka OLE.|
|[CRichEditView::InsertItem](#insertitem)|Vloží novou položku jako položka OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Informuje, zda schránky obsahuje data ve formátu textu nebo RichEdit.|
|[CRichEditView::OnCharEffect](#onchareffect)|Přepíná formátování pro aktuální výběr.|
|[CRichEditView::OnParaAlign](#onparaalign)|Změní zarovnání odstavce.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizace uživatelského rozhraní příkaz pro znak veřejné členské funkce.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizace uživatelského rozhraní příkaz pro odstavec veřejné členské funkce.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formátuje zadaný text v rámci dané obdélník.|
|[CRichEditView::PrintPage](#printpage)|Formátuje text zadaný v rámci dané stránky.|
|[CRichEditView::SetCharFormat](#setcharformat)|Nastaví formátování atributy pro aktuální výběr.|
|[CRichEditView::SetMargins](#setmargins)|Nastaví okraje tohoto bohaté možnosti Upravit zobrazení.|
|[CRichEditView::SetPaperSize](#setpapersize)|Nastaví velikost papíru pro toto zobrazení RichEdit.|
|[CRichEditView::SetParaFormat](#setparaformat)|Nastaví atributy pro aktuální výběr formátování odstavce.|
|[CRichEditView::TextNotFound](#textnotfound)|Obnoví stav vnitřní vyhledávání ovládacího prvku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Načte objekt Clipboard pro rozsah v tomto zobrazení RichEdit.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Načte místní nabídku pro použití na pravé tlačítko myši dolů.|
|[CRichEditView::IsSelected](#isselected)|Označuje, pokud je daná položka OLE vybraná nebo ne.|
|[CRichEditView::OnFindNext](#onfindnext)|Najde další výskyt podřetězce.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Aktualizace zobrazení při prvním připojené k dokumentu.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Načte nativní data z položky OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Nastaví tiskové charakteristiky na dané zařízení.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Nový řetězec nahradí všechny výskyty daného řetězce.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Zpracovává oznámení pro uživatele, který nebyl nalezen požadovaný text.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Dotazy na najdete v článku o datech `IDataObject`.|
|[CRichEditView::WrapChanged](#wrapchanged)|Nastaví cílové výstupní zařízení pro zobrazení, založené na hodnotě pro úpravy s formátováním tento `m_nWordWrap`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Určuje velikost odsazení pro seznamy s odrážkami.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Určuje omezení zalamování slov.|

## <a name="remarks"></a>Poznámky

"Ovládacího prvku rich edit" je okno, ve kterém můžete uživatele zadat a upravit text. Text je možné přiřadit formátování znaků a odstavců a může obsahovat vložené objekty OLE. Bohaté ovládacích prvcích pro úpravy poskytují programovací rozhraní pro formátování textu. Však musí aplikace implementovat součásti potřebné k zajištění operací formátování pro uživatele k dispozici žádné uživatelského rozhraní.

`CRichEditView` udržuje textu a formátování vlastnosti textu. `CRichEditDoc` udržuje seznam klientské položky OLE, které jsou v zobrazení. `CRichEditCntrItem` poskytuje kontejner straně přístup k klientskou položku OLE.

Tento ovládací prvek Windows běžné (a tedy [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Příklad použití zobrazení RichEdit v aplikaci knihovny MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkovou aplikaci.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cctrlview –](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrich.h

##  <a name="adjustdialogposition"></a>  CRichEditView::AdjustDialogPosition

Voláním této funkce dané dialogové okno přesunout tak, aby se skryl není aktuální výběr.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parametry

*pDlg*<br/>
Ukazatel `CDialog` objektu.

##  <a name="canpaste"></a>  CRichEditView::CanPaste

Voláním této funkce lze zjistit, jestliže schránky obsahuje informace, které můžete vložit do toto zobrazení RichEdit.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud obsahuje data ve formátu, který může přijmout toto zobrazení RichEdit; do schránky jinak 0.

##  <a name="cricheditview"></a>  CRichEditView::CRichEditView

Volání této funkce můžete vytvořit `CRichEditView` objektu.

```
CRichEditView();
```

##  <a name="dopaste"></a>  CRichEditView::DoPaste

Voláním této funkce vložení položky OLE v *dataobj* do tohoto ovládacího prvku rich edit dokument/zobrazení.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parametry

*dataobj*<br/>
[Coledataobject –](../../mfc/reference/coledataobject-class.md) obsahující dat vložte.

*CF*<br/>
Požadovaný formát schránky.

*hMetaPict*<br/>
Tento metasoubor, která představuje položku, kterou chcete vložit.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci, jako součást výchozí implementace [QueryAcceptData](#queryacceptdata).

Tato funkce určuje typ vložit na základě výsledků obslužné rutiny pro Vložit jinak. Pokud *cf* je 0, nová položka používá reprezentaci aktuální ikony. Pokud *cf* je nenulová a *hMetaPict* nemá hodnotu NULL, použije nová položka *hMetaPict* její znázornění.

##  <a name="findtext"></a>  CRichEditView::FindText

Voláním této funkce najít zadaný text a nastavit aktuální výběr.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Obsahuje hledaný řetězec.

*bCase*<br/>
Určuje, zda je hledání malá a velká písmena.

*bWord*<br/>
Označuje, pokud by měl odpovídat hledat pouze celá slova, nikoli částí slova.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE se ke konci vyrovnávací paměti je směr hledání. Pokud má hodnotu FALSE, je směr hledání směrem k začátku vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud *lpszFind* text nalezen; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce zobrazí kurzor pro čekání během operace find.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>  CRichEditView::FindTextSimple

Voláním této funkce najít zadaný text a nastavit aktuální výběr.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Obsahuje hledaný řetězec.

*bCase*<br/>
Určuje, zda je hledání malá a velká písmena.

*bWord*<br/>
Označuje, pokud by měl odpovídat hledat pouze celá slova, nikoli částí slova.

*bNext*<br/>
Určuje směr hledání. Při hodnotě TRUE se ke konci vyrovnávací paměti je směr hledání. Pokud má hodnotu FALSE, je směr hledání směrem k začátku vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud *lpszFind* text nalezen; jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).

##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection

Voláním této funkce získáte formátování atributy aktuálního výběru.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Návratová hodnota

A [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktura, která obsahuje formátování atributy aktuálního výběru.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_GETCHARFORMAT](/windows/desktop/Controls/em-getcharformat) zprávu a [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktura v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData

Rozhraní volá tuto funkci, jako součást zpracování [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parametry

*lpchrg*<br/>
Ukazatel [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktura zadání rozsahu znaků (a položky OLE) ke kopírování dat objektu určeného parametrem *lplpdataobj*.

*dwReco*<br/>
Příznak operaci schránky. Může být jedna z těchto hodnot.

- RECO_COPY kopírování do schránky.

- RECO_CUT vyjmout data do schránky.

- Přetáhněte RECO_DRAG operace (přetažení).

- Vyřadit RECO_DROP operace (přetažení).

- RECO_PASTE vložení ze schránky.

*lpRichDataObj*<br/>
Ukazatel [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) objekt, který obsahuje data schránky z získáte bohaté ovládacích prvků pro úpravy ( [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Ukazatel na ukazatel proměnné, která bude přijímat adresy `IDataObject` představující rozsah zadaný v objektu *lpchrg* parametru. Hodnota *lplpdataobj* se ignoruje, pokud je vrácena chyba.

### <a name="return-value"></a>Návratová hodnota

Oznamuje se úspěch operace hodnotu HRESULT. Další informace o HRESULT, naleznete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Pokud vrácená hodnota označuje úspěch, `IRichEditOleCallback::GetClipboardData` vrátí `IDataObject` přistupuje *lplpdataobj*; v opačném případě vrátí jeden přistupuje *lpRichDataObj*. Přepište tato funkce slouží k poskytování dat schránky. Výchozí implementace této funkce vrátí E_NOTIMPL.

To je moderní overridable.

Další informace najdete v tématu [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata), a [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) v sadě Windows SDK a viz [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) ve Windows SDK.

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

Rozhraní volá tuto funkci, jako součást zpracování [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parametry

*seltyp*<br/>
Typ výběru. Výběr typu hodnoty jsou popsány v části poznámky.

*lpoleobj*<br/>
Ukazatel `OLEOBJECT` struktura zadáním prvního vybraného objektu OLE, pokud výběr obsahuje jeden nebo více položek OLE. Pokud výběr neobsahuje žádné položky *lpoleobj* má hodnotu NULL. `OLEOBJECT` Struktura obsahuje ukazatel v-table objektu OLE.

*lpchrg*<br/>
Ukazatel [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktury obsahující aktuální výběr.

### <a name="return-value"></a>Návratová hodnota

Zpracování do kontextové nabídky.

### <a name="remarks"></a>Poznámky

Tato funkce je typické součástí stisknutí pravého tlačítka myši dolů zpracování.

Typ výběru může obsahovat libovolnou kombinaci následujících příznaků:

- SEL_EMPTY označuje, že nebyla vybrána žádná aktuální položka.

- SEL_TEXT znamená, že aktuální výběr obsahuje text.

- SEL_OBJECT znamená, že aktuální výběr obsahuje alespoň jednu položku OLE.

- SEL_MULTICHAR znamená, že aktuální výběr obsahuje více než jeden znak textu.

- SEL_MULTIOBJECT znamená, že aktuální výběr obsahuje více než jeden objekt OLE.

Výchozí implementace vrací hodnotu NULL. To je moderní overridable.

Další informace najdete v tématu [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu) a [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) v sadě Windows SDK.

##  <a name="getdocument"></a>  CRichEditView::GetDocument

Volání této funkce získáte ukazatel `CRichEditDoc` spojeného s tímto zobrazením.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cricheditdoc –](../../mfc/reference/cricheditdoc-class.md) objekt přidružený k vaší `CRichEditView` objektu.

##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem

Volání této funkce získáte OLE položku, která je aktuálně aktivovaná na místě v tomto `CRichEditView` objektu.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní jeden, místní [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md) objekt v tomto zobrazení RichEdit; Hodnota NULL, pokud neexistuje žádná položka OLE aktuálně ve stavu aktivní na místě.

##  <a name="getmargins"></a>  CRichEditView::GetMargins

Volání této funkce načtete aktuální rozpětí používaná v tisku.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Návratová hodnota

Okraje používaných pro tisk, se měří v MM_TWIPS.

##  <a name="getpagerect"></a>  CRichEditView::GetPageRect

Voláním této funkce získáte rozměry stránky používaných pro tisk.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Hranice stránky použité v tisku, se měří v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Tato hodnota je založena na papír.

##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize

Volání této funkce načtete aktuální velikosti papíru.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Formát papíru používaných pro tisk, se měří v MM_TWIPS.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection

Voláním této funkce se získat atributy aktuálního výběru formátování odstavce.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Návratová hodnota

A [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) struktura, která obsahuje atributy aktuálního výběru formátování odstavce.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_GETPARAFORMAT](/windows/desktop/Controls/em-getparaformat) zprávu a [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) struktura v sadě Windows SDK.

##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect

Volání této funkce načtete rozsah tisku oblasti v rámci stránky obdélník.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Hranice oblasti image použité v tisku, se měří v MM_TWIPS.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth

Voláním této funkce určuje šířku oblasti tisku.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka oblasti Tisk měřeno v MM_TWIPS.

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

Voláním této funkce načtete [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) objekt přidružený k `CRichEditView` objektu.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Návratová hodnota

`CRichEditCtrl` Objektu pro toto zobrazení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

Voláním této funkce načtete položky OLE. ( `CRichEditCntrItem` objekt) aktuálně vybraného v tomto `CRichEditView` objektu.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md) objektu vybraného v `CRichEditView` objektu Hodnota NULL, pokud není vybrána žádná položka v tomto zobrazení.

##  <a name="gettextlength"></a>  CRichEditView::GetTextLength

Voláním této funkce načtete délka textu v tomto `CRichEditView` objektu.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka textu v tomto `CRichEditView` objektu.

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

Voláním této členské funkce pro výpočet délka textu v tomto `CRichEditView` objektu.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Hodnota, která určuje metodu, který se má použít při určování délka textu. Tento člen může být jedna nebo více hodnot uvedených v členu příznaky [GETTEXTLENGTHEX](/windows/desktop/api/richedit/ns-richedit-_gettextlengthex) je popsáno v sadě Windows SDK.

*uCodePage*<br/>
Znaková stránka pro překlad (CP_ACP pro znakovou stránku ANSI, 1200 pro Unicode).

### <a name="return-value"></a>Návratová hodnota

Počet znaků nebo bajtů v textovém poli. Pokud byly v nekompatibilní příznaky *dwFlags*, tato členská funkce vrátí E_INVALIDARG.

### <a name="remarks"></a>Poznámky

`GetTextLengthEx` Další způsoby určení délka textu. Podporuje funkce Upravit 2.0 ve formátu RTF. Další informace najdete v tématu [o bohaté upravit ovládací prvky](/windows/desktop/Controls/about-rich-edit-controls) v sadě Windows SDK.

##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject

Voláním této funkce Vložit zadaný soubor (jako [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md) objekt) do bohaté upravit zobrazení.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec obsahující název souboru, který má být vložen.

##  <a name="insertitem"></a>  CRichEditView::InsertItem

Voláním této funkce Vložit [cricheditcntritem –](../../mfc/reference/cricheditcntritem-class.md) objektu do zobrazení RichEdit.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Ukazatel na položky, která má být vložen.

### <a name="return-value"></a>Návratová hodnota

Hodnotu HRESULT udávající úspěch vložení.

### <a name="remarks"></a>Poznámky

Další informace o HRESULT, naleznete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes) v sadě Windows SDK.

##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat

Voláním této funkce určete, jestli *cf* je formát schránky, což je text, formátovaný text nebo formátovaný text položky OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parametry

*CF*<br/>
Formát schránky, které vás zajímají.

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud *cf* bohaté formát schránky úpravy nebo text.

##  <a name="isselected"></a>  CRichEditView::IsSelected

Voláním této funkce k určení, pokud zadaná položka OLE je aktuálně vybrána v tomto zobrazení.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Ukazatel na objekt v zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt vybrán; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud vaše třída odvozená zobrazení má jinou metodu pro zpracování výběr položek OLE.

##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent

Odsazení odrážek položek v seznamu. ve výchozím nastavení, 720 jednotek, což je 1/2 palce.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

Určuje typ zalamování řádků pro toto zobrazení RichEdit.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Poznámky

Jeden z následujících hodnot:

- `WrapNone` Označuje žádné automatické zalamování.

- `WrapToWindow` Označuje zalamování založené na šířku okna.

- `WrapToTargetDevice` Označuje zalamování založený na ukazatelích na cílové zařízení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::WrapChanged](#wrapchanged).

##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect

Voláním této funkce lze přepnout formátování efektů pro aktuální výběr.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Formátování efektů upravit v aktuálním výběru znaků.

*dwEffect*<br/>
Požadovaný seznam formátování efektů, chcete-li přepnout.

### <a name="remarks"></a>Poznámky

Každé volání této funkce přepne zadaný formátování efektů pro aktuální výběr.

Další informace o *dwMask* a *dwEffect* parametry a jejich možných hodnot, najdete v části odpovídající datové členy [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>  CRichEditView::OnFindNext

Volá se rozhraním při zpracování příkazů z dialogového okna Najít a nahradit.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Řetězec, který se má najít.

*bNext*<br/>
Směr hledání: hodnota TRUE označuje; FALSE provoz.

*bCase*<br/>
Označuje, zda hledání rozlišovat velikost písmen.

*bWord*<br/>
Označuje, zda je hledání Hledat celá slova pouze nebo ne.

### <a name="remarks"></a>Poznámky

Voláním této funkce hledání textu v rámci `CRichEditView`. Přepsání této funkce můžete měnit vlastnosti hledání pro vaše zobrazení odvozené třídy.

##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate

Volá se rozhraním po zobrazení je nejprve připojen k dokumentu, ale před začátku zobrazení.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Poznámky

Volá výchozí implementaci této funkce [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) členská funkce se žádné informace nápovědy (to znamená, že použití výchozí hodnoty 0 pro *lHint* parametru a hodnota NULL pro *pHint* parametr). Přepsání této funkce provedla jednorázová inicializace, která vyžaduje informace o dokumentu. Například pokud vaše aplikace má pevnou velikostí dokumenty, můžete použít tuto funkci inicializace umožňující posouvání omezení zobrazení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty proměnlivé velikosti, použijte `OnUpdate` aktualizovat posouvání omezuje pokaždé, když změny dokumentu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject

Pomocí této funkce můžete načíst nativní data z vložené položky.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parametry

*lpStg*<br/>
Ukazatel [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0;

### <a name="remarks"></a>Poznámky

Obvykle by to provedete tak, že vytvoříte [colestreamfile –](../../mfc/reference/colestreamfile-class.md) kolem `IStorage`. `COleStreamFile` Lze připojit k archivu a [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) volá se, aby se načetla data.

To je moderní overridable.

Další informace najdete v tématu [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) v sadě Windows SDK.

##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign

Voláním této funkce, chcete-li změnit zarovnání odstavce vybrané odstavce.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parametry

*wAlign*<br/>
Požadované zarovnání odstavce. Jeden z následujících hodnot:

- PFA_LEFT zarovnání odstavce se na levém okraji.

- PFA_RIGHT zarovnání odstavce se na pravém okraji.

- PFA_CENTER Datacentra odstavců mezi okraje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged

Potlačí tuto funkci chcete-li změnit vlastnosti pro toto zobrazení RichEdit, když se změní na tiskárnu.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parametry

*dcPrinter*<br/>
A [CDC](../../mfc/reference/cdc-class.md) objekt pro nové tiskárně.

### <a name="remarks"></a>Poznámky

Výchozí implementace nastaví velikost papíru na fyzické výšku a šířku pro výstupní zařízení (tiskárna). Pokud není přidružený žádný kontext zařízení *dcPrinter*, nastaví výchozí implementace papíru 8.5 podle 11 palců.

##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll

Volá se rozhraním při zpracování nahradit všechny příkazy z dialogového okna nahradit.

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
Nahrazovací text.

*bCase*<br/>
Určuje, zda je hledání malá a velká písmena.

*bWord*<br/>
Označuje, pokud hledání musíte vybrat celá slova nebo ne.

### <a name="remarks"></a>Poznámky

Voláním této funkce, aby nahradil všechny výskyty daného text jiným řetězcem. Přepsání této funkce můžete měnit vlastnosti hledání pro toto zobrazení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).

##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel

Volá se rozhraním při zpracování příkazů nahraďte z dialogového okna nahradit.

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
Určuje směr hledání: je TRUE. FALSE provoz.

*bCase*<br/>
Určuje, zda je hledání malá a velká písmena.

*bWord*<br/>
Označuje, pokud hledání musíte vybrat celá slova nebo ne.

*lpszReplace*<br/>
Nahrazovací text.

### <a name="remarks"></a>Poznámky

Voláním této funkce nahraďte jiným řetězcem jeden výskyt některé daného textu. Přepsání této funkce můžete měnit vlastnosti hledání pro toto zobrazení.

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

Volá se rozhraním, pokaždé, když se hledání nezdaří.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Text, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Tuto funkci chcete-li změnit oznámení výstup z přepsat [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep).

Další informace najdete v tématu [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect

Rozhraní volá tuto funkci k aktualizaci příkaz uživatelského rozhraní pro příkazy vliv znak.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel [ccmdui –](../../mfc/reference/ccmdui-class.md) objektu.

*dwMask*<br/>
Určuje formátování masky.

*dwEffect*<br/>
Určuje formátování vliv.

### <a name="remarks"></a>Poznámky

Maska *dwMask* Určuje, které znak atributů formátování ke kontrole. Příznaky *dwEffect* seznam atributů, které mají set/Vymazat formátování.

Další informace o *dwMask* a *dwEffect* parametry a jejich možných hodnot, najdete v části odpovídající datové členy [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign

Rozhraní volá tuto funkci k aktualizaci příkaz uživatelského rozhraní pro příkazy vliv odstavce.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel [ccmdui –](../../mfc/reference/ccmdui-class.md) objektu.

*wAlign*<br/>
Zarovnání odstavce ke kontrole. Jeden z následujících hodnot:

- PFA_LEFT zarovnání odstavce se na levém okraji.

- PFA_RIGHT zarovnání odstavce se na pravém okraji.

- PFA_CENTER Datacentra odstavců mezi okraje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect

Voláním této funkce formátovat rozsah textu v ovládacím prvku RichEdit, aby vyhovovaly *rectLayout* pro zařízení určeného *primárního řadiče domény*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Ukazatel na kontext zařízení pro výstupní oblasti.

*rectLayout*<br/>
[Rect –](../../mfc/reference/rect-structure1.md) nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) určující výstupní oblasti.

*nIndexStart*<br/>
Z nuly vycházející index prvního znaku, který má být formátováno.

*nIndexStop*<br/>
Z nuly vycházející index posledního znaku, který má být formátováno.

*bOutput*<br/>
Označuje, pokud má být vykreslen text. Pokud má hodnotu FALSE, se měří pouze text.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku, který se vejde do oblasti výstup plus jedna.

### <a name="remarks"></a>Poznámky

Obvykle je toto volání a potom voláním [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) které generují výstup.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::GetPaperSize](#getpapersize).

##  <a name="printpage"></a>  CRichEditView::PrintPage

Voláním této funkce pro formátování textu v ovládacím prvku RichEdit, pro výstupní zařízení určeného rozsahu *primárního řadiče domény*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Ukazatel na kontext zařízení pro výstup stránky.

*nIndexStart*<br/>
Z nuly vycházející index prvního znaku, který má být formátováno.

*nIndexStop*<br/>
Z nuly vycházející index posledního znaku, který má být formátováno.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku, který se vejde na stránku plus jedna.

### <a name="remarks"></a>Poznámky

Rozložení jednotlivých stránek je řízen [GetPageRect](#getpagerect) a [GetPrintRect](#getprintrect). Obvykle je toto volání a potom voláním [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) které generují výstup.

Všimněte si, že okraje vzhledem k fyzické stránce, ne logické stránky. Proto okraje nula bude často Galerie textu od mnoha tiskárny mají málo častého netisknutelného oblasti na stránce. Chcete-li zabránit oříznutí textu, měli byste zavolat [SetMargins](#setmargins) a nastavení přiměřené okrajů před tiskem.

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

Volá se rozhraním, k vložení objektu do bohaté možnosti úprav.

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
Ukazatel [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) dotazu.

*lpcfFormat*<br/>
Ukazatel na formát dat přijatelné.

*dwReco*<br/>
Nepoužívá se.

*bReally*<br/>
Určuje, zda operace vložení pokračovat nebo ne.

*hMetaFile*<br/>
Popisovač pro tento metasoubor použitý pro vykreslení položky ikonu.

### <a name="return-value"></a>Návratová hodnota

Oznamuje se úspěch operace hodnotu HRESULT.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci pro zpracování jiné organizaci COM položek ve třídě odvozené dokumentu. To je moderní overridable.

Další informace o HRESULT a `IDataObject`, naleznete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes) a [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)v uvedeném pořadí, v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat

Voláním této funkce nastavit atributy pro nový text v tomto formátování `CRichEditView` objektu.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parametry

*CF*<br/>
[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktury obsahující nové výchozí formátování atributy.

### <a name="remarks"></a>Poznámky

Pouze atributy určené `dwMask` členem *cf* změní tuto funkci.

Další informace najdete v tématu [EM_SETCHARFORMAT](/windows/desktop/Controls/em-setcharformat) zprávu a [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) struktura v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>  CRichEditView::SetMargins

Voláním této funkce nastavit okraje pro tisk pro toto zobrazení RichEdit.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parametry

*rectMargin*<br/>
Nové hodnoty vlastnosti okraj pro tisk, se měří v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Pokud [m_nWordWrap](#m_nwordwrap) je `WrapToTargetDevice`, měli byste zavolat [WrapChanged](#wrapchanged) po použití této funkce Upravit tiskové charakteristiky.

Všimněte si, že používá okraje [PrintPage](#printpage) jsou relativní vzhledem k fyzické stránky, ne logické stránky. Proto okraje nula bude často Galerie textu od mnoha tiskárny mají málo častého netisknutelného oblasti na stránce. Chcete-li zabránit oříznutí textu, měli byste zavolat použití `SetMargins` nastavit okraje přiměřené tiskáren před tiskem.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::GetPaperSize](#getpapersize).

##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize

Voláním této funkce nastavte velikost papíru pro tisk toto zobrazení RichEdit.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parametry

*sizePaper*<br/>
Nové hodnoty velikosti papíru pro tisk, se měří v MM_TWIPS.

### <a name="remarks"></a>Poznámky

Pokud [m_nWordWrap](#m_nwordwrap) je `WrapToTargetDevice`, měli byste zavolat [WrapChanged](#wrapchanged) po použití této funkce Upravit tiskové charakteristiky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat

Voláním této funkce nastavit atributy pro aktuální výběr v tomto formátování odstavce `CRichEditView` objektu.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parametry

*PF*<br/>
[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) atributů formátování odstavce struktury obsahující nové výchozí nastavení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pouze atributy určené `dwMask` členem *pf* změní tuto funkci.

Další informace najdete v tématu [EM_SETPARAFORMAT](/windows/desktop/Controls/em-setparaformat) zprávu a [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) struktura v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>  CRichEditView::TextNotFound

Voláním této funkce, chcete-li obnovit stav vnitřní hledání [cricheditview –](../../mfc/reference/cricheditview-class.md) ovládacího prvku po selhání volání [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Obsahuje textový řetězec, který nebyl nalezen.

### <a name="remarks"></a>Poznámky

Doporučuje se, že tuto metodu volat ihned po neúspěšnými voláními [FindText](#findtext) tak, aby se správně Vynuluje stav vnitřní vyhledávání ovládacího prvku.

*LpszFind* parametr by měl obsahovat obsah jako řetězec poskytnuté [FindText](#findtext). Po obnovení stav vnitřní hledání, zavolá tato metoda [OnTextNotFound](#ontextnotfound) metodu s zadaný hledaný řetězec.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).

##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged

Voláním této funkce, pokud jste změnili vlastnosti tisku ( [SetMargins](#setmargins) nebo [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete upravit způsob zobrazení pro úpravy s formátováním, jsou reaguje na změny v [m_nWordWrap](#m_nwordwrap) nebo tiskové charakteristiky ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[CCtrlView – třída](../../mfc/reference/cctrlview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc – třída](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem – třída](../../mfc/reference/cricheditcntritem-class.md)
