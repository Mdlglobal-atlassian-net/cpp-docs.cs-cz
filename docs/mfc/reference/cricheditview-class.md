---
title: "Cricheditview – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 604e226a903b8cbb518d02cac4230d7d17cc4528
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cricheditview-class"></a>Cricheditview – třída
S [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) a [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), poskytuje funkce ovládacího prvku RichEdit v kontextu zobrazení architektury MFC na dokumentu.  
  
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
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Přesune dialogové okno, takže ho nebude skrývat aktuální výběr.|  
|[CRichEditView::CanPaste](#canpaste)|Určuje, zda schránky obsahuje data, která lze vložit do zobrazení RichEdit.|  
|[CRichEditView::DoPaste](#dopaste)|Vloží položku OLE do tohoto RichEdit zobrazení.|  
|[CRichEditView::FindText](#findtext)|Vyhledá zadaný text, vyvolání kurzor čekání.|  
|[CRichEditView::FindTextSimple](#findtextsimple)|Vyhledá zadaný text.|  
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Načte formátování atributy pro aktuální výběr znaků.|  
|[CRichEditView::GetDocument](#getdocument)|Načte ukazatel související [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|  
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Načte položku OLE, který je aktuálně místní aktivní v zobrazení RichEdit.|  
|[CRichEditView::GetMargins](#getmargins)|Načte okrajů pro toto zobrazení RichEdit.|  
|[CRichEditView::GetPageRect](#getpagerect)|Načte rámeček stránky pro toto zobrazení RichEdit.|  
|[CRichEditView::GetPaperSize](#getpapersize)|Načte velikost papíru pro toto zobrazení RichEdit.|  
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Načte atributy pro aktuální výběr formátování odstavce.|  
|[CRichEditView::GetPrintRect](#getprintrect)|Načte tiskové rámeček pro toto zobrazení RichEdit.|  
|[CRichEditView::GetPrintWidth](#getprintwidth)|Načte tiskové šířku pro toto zobrazení RichEdit.|  
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Načte prvku RichEdit.|  
|[CRichEditView::GetSelectedItem](#getselecteditem)|Načte vybranou položku ze zobrazení RichEdit.|  
|[CRichEditView::GetTextLength](#gettextlength)|Získá délku textu v zobrazení RichEdit.|  
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Načte počet znaků nebo bajtů v RichEdit zobrazení. Seznam rozšířené příznak pro metodou pro určení toho délka.|  
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Vloží soubor jako položku OLE.|  
|[CRichEditView::InsertItem](#insertitem)|Vloží novou položku jako položku OLE.|  
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Oznamuje, zda schránky obsahuje data v RTF nebo textovém formátu.|  
|[CRichEditView::OnCharEffect](#onchareffect)|Přepíná formátování pro aktuální výběr znaků.|  
|[CRichEditView::OnParaAlign](#onparaalign)|Změny zarovnání odstavcích.|  
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Aktualizuje příkaz uživatelské rozhraní pro veřejné členské funkce znak.|  
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Aktualizuje příkaz uživatelské rozhraní pro veřejné členské funkce odstavce.|  
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formátuje zadaný text v rámci dané rámeček.|  
|[CRichEditView::PrintPage](#printpage)|Formátuje zadaný text v rámci dané stránky.|  
|[CRichEditView::SetCharFormat](#setcharformat)|Nastaví formátování atributy pro aktuální výběr znaků.|  
|[CRichEditView::SetMargins](#setmargins)|Nastaví okraje pro tento bohaté upravit zobrazení.|  
|[CRichEditView::SetPaperSize](#setpapersize)|Nastaví velikost papíru pro toto zobrazení RichEdit.|  
|[CRichEditView::SetParaFormat](#setparaformat)|Nastaví atributy pro aktuální výběr formátování odstavce.|  
|[CRichEditView::TextNotFound](#textnotfound)|Obnoví stav vnitřní vyhledávání ovládacího prvku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](#getclipboarddata)|Načte objekt schránky pro rozsah v tomto zobrazení RichEdit.|  
|[CRichEditView::GetContextMenu](#getcontextmenu)|Načte z kontextové nabídky používat na pravé tlačítko myši směrem dolů.|  
|[CRichEditView::IsSelected](#isselected)|Označuje, pokud daná položka OLE vybraná nebo ne.|  
|[CRichEditView::OnFindNext](#onfindnext)|Vyhledá další výskyt dílčí řetězec.|  
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Aktualizuje zobrazení, pokud je první připojený k dokumentu.|  
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Načte nativní dat z položky OLE.|  
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Nastaví vlastnosti tiskové na dané zařízení.|  
|[CRichEditView::OnReplaceAll](#onreplaceall)|Nahradí všechny výskyty daného řetězec nového řetězce.|  
|[CRichEditView::OnReplaceSel](#onreplacesel)|Nahradí aktuální výběr.|  
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Zpracovává oznámení pro uživatele, který nebyl nalezen požadovaný text.|  
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Dotazy o data zobrazit na `IDataObject`.|  
|[CRichEditView::WrapChanged](#wrapchanged)|Upraví cílové zařízení výstup pro tento bohaté upravit zobrazení, na základě hodnoty z `m_nWordWrap`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Určuje velikost odsazení pro seznamy s odrážkami.|  
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Určuje omezení wrap slovo.|  
  
## <a name="remarks"></a>Poznámky  
 "RichEdit řízení" je okno, ve kterém může uživatel zadat a upravit text. Text se dá přiřadit znak a formátování odstavce a může obsahovat vložené objekty OLE. Ovládací prvky Rich edit zadejte programovací rozhraní pro formátování textu. Aplikace musí implementovat však potřeba zpřístupnit operací formátování uživateli žádné uživatelské rozhraní komponenty.  
  
 `CRichEditView`udržuje textu a formátování vlastnosti textu. `CRichEditDoc`udržuje seznam položek OLE klienta, které jsou v zobrazení. `CRichEditCntrItem`poskytuje kontejner straně přístup k položce OLE klienta.  
  
 Tento ovládací prvek Windows běžné (a proto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) a související třídy) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Příklad použití RichEdit zobrazení v aplikaci MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkové aplikace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrich.h  
  
##  <a name="adjustdialogposition"></a>CRichEditView::AdjustDialogPosition  
 Volání této funkce můžete přesunout dané dialogových oken, takže ji není skrývat aktuální výběr.  
  
```  
void AdjustDialogPosition(CDialog* pDlg);
```  
  
### <a name="parameters"></a>Parametry  
 *pDlg*  
 Ukazatel na `CDialog` objektu.  
  
##  <a name="canpaste"></a>CRichEditView::CanPaste  
 Volání této funkce lze zjistit, pokud schránky obsahuje informace, které můžete vložit do tohoto RichEdit zobrazení.  
  
```  
BOOL CanPaste() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud schránky obsahuje data ve formátu, který může přijmout toto zobrazení RichEdit; jinak hodnota 0.  
  
##  <a name="cricheditview"></a>CRichEditView::CRichEditView  
 Volání této funkce můžete vytvořit `CRichEditView` objektu.  
  
```  
CRichEditView();
```  
  
##  <a name="dopaste"></a>CRichEditView::DoPaste  
 Volání této funkce se vložit položky OLE v `dataobj` do této úpravy s formátováním dokument/zobrazení.  
  
```  
void DoPaste(
    COleDataObject& dataobj,  
    CLIPFORMAT cf,  
    HMETAFILEPICT hMetaPict);
```  
  
### <a name="parameters"></a>Parametry  
 `dataobj`  
 [COleDataObject](../../mfc/reference/coledataobject-class.md) obsahující data, která mají vložit.  
  
 `cf`  
 Požadovaný formát schránky.  
  
 `hMetaPict`  
 Metafile, který představuje položku vložit.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá framework jako součást výchozí implementaci [QueryAcceptData](#queryacceptdata).  
  
 Tato funkce určuje typ vložení na základě výsledků obslužné rutiny pro Vložit jinak. Pokud `cf` je 0, používá aktuální ikony reprezentace novou položku. Pokud `cf` nenulový a `hMetaPict` není **NULL**, používá nová položka `hMetaPict` pro její reprezentace.  
  
##  <a name="findtext"></a>CRichEditView::FindText  
 Volání této funkce vyhledá zadaný text a nastavte ji jako aktuální výběr.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Obsahuje řetězec pro vyhledávání.  
  
 `bCase`  
 Určuje, zda hledání velká a malá písmena.  
  
 `bWord`  
 Označuje, pokud hledání by měl Hledat celá slova, nikoli části slov.  
  
 `bNext`  
 Určuje směr hledání. Pokud **TRUE**, směr vyhledávání je na konci vyrovnávací paměti. Pokud **FALSE**, směr vyhledávání je k začátku vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `lpszFind` je nalezen text; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce zobrazí kurzor čekání během operace hledání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]  
  
##  <a name="findtextsimple"></a>CRichEditView::FindTextSimple  
 Volání této funkce vyhledá zadaný text a nastavte ji jako aktuální výběr.  
  
```  
BOOL FindTextSimple(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Obsahuje řetězec pro vyhledávání.  
  
 `bCase`  
 Určuje, zda hledání velká a malá písmena.  
  
 `bWord`  
 Označuje, pokud hledání by měl Hledat celá slova, nikoli části slov.  
  
 `bNext`  
 Určuje směr hledání. Pokud **TRUE**, směr vyhledávání je na konci vyrovnávací paměti. Pokud **FALSE**, směr vyhledávání je k začátku vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `lpszFind` je nalezen text; jinak hodnota 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).  
  
##  <a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection  
 Volání této funkce můžete získat formátování atributy aktuální výběr znaků.  
  
```  
CHARFORMAT2& GetCharFormatSelection();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura, která obsahuje znak atributy aktuálního výběru formátování.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) zprávy a [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="getclipboarddata"></a>CRichEditView::GetClipboardData  
 Tato funkce volá framework jako součást zpracování [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315).  
  
```  
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,  
    DWORD dwReco,  
    LPDATAOBJECT lpRichDataObj,  
    LPDATAOBJECT* lplpdataobj);
```  
  
### <a name="parameters"></a>Parametry  
 `lpchrg`  
 Ukazatel [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura zadání rozsahu znaky (a OLE – položky) pro kopírování na datový objekt určeného `lplpdataobj`.  
  
 `dwReco`  
 Příznak operaci schránky. Může být jedna z těchto hodnot.  
  
- **RECO_COPY** zkopírujte do schránky.  
  
- **RECO_CUT** vyjmout data do schránky.  
  
- **RECO_DRAG** přetáhněte operace (přetažení).  
  
- **RECO_DROP** vyřadit operace (přetažení).  
  
- **RECO_PASTE** vložte ze schránky.  
  
 `lpRichDataObj`  
 Ukazatel na [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) objekt obsahující data schránky z bohaté ovládacích prvků pro úpravy ( [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341)).  
  
 `lplpdataobj`  
 Ukazatel na proměnné ukazatele, která přijímá adresu `IDataObject` objektu, který představuje zadaný v rozsah `lpchrg` parametr. Hodnota `lplpdataobj` je ignorována, pokud se vrátí chyba.  
  
### <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnotu úspěch operace vytváření sestav. Další informace o `HRESULT`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud návratová hodnota označuje úspěch, **IRichEditOleCallback::GetClipboardData** vrátí `IDataObject` přístup `lplpdataobj`, jinak vrátí jeden přístup `lpRichDataObj`. Přepsání této funkci můžete zadat vlastní data ze schránky. Výchozí implementace této funkce vrátí **E_NOTIMPL**.  
  
 Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341), [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315), a [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) ve Windows SDK a najdete [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) ve Windows SDK.  
  
##  <a name="getcontextmenu"></a>CRichEditView::GetContextMenu  
 Tato funkce volá framework jako součást zpracování [IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317).  
  
```  
virtual HMENU GetContextMenu(
    WORD seltyp,  
    LPOLEOBJECT lpoleobj,  
    CHARRANGE* lpchrg);
```  
  
### <a name="parameters"></a>Parametry  
 *seltyp*  
 Výběr typu. Výběr typu hodnoty jsou popsané v oddílu Poznámky.  
  
 `lpoleobj`  
 Ukazatel na **objekt OLE** struktura určující první vybraný objekt OLE, je-li výběr obsahuje jeden nebo více položek OLE. Pokud výběr neobsahuje žádné položky `lpoleobj` je **NULL**. **Objekt OLE** struktura obsahuje ukazatel na OLE objektu v tabulku.  
  
 `lpchrg`  
 Ukazatel na [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura obsahující aktuální výběr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zpracování do kontextové nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je typické součástí pravé tlačítko myši směrem dolů zpracování.  
  
 Výběr typu může být libovolnou kombinací následující příznaky:  
  
- `SEL_EMPTY`Označuje, že neexistuje žádný aktuální výběr.  
  
- `SEL_TEXT`Určuje, že aktuální výběr obsahuje text.  
  
- `SEL_OBJECT`Určuje, že aktuální výběr obsahuje alespoň jednu položku OLE.  
  
- `SEL_MULTICHAR`Určuje, že aktuální výběr obsahuje více než jeden znak textu.  
  
- `SEL_MULTIOBJECT`Určuje, že aktuální výběr obsahuje více než jeden objekt OLE.  
  
 Výchozí implementace vrací **NULL**. Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317) a [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) ve Windows SDK.  
  
 Další informace o **objekt OLE** typu, najdete v článku OLE datové struktury a struktura přidělení v *OLE znalostní báze Knowledge Base*.  
  
##  <a name="getdocument"></a>CRichEditView::GetDocument  
 Volání této funkce můžete získat ukazatel `CRichEditDoc` přiřazeného k tomuto zobrazení.  
  
```  
CRichEditDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) objekt přidružený k vaší `CRichEditView` objektu.  
  
##  <a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem  
 Volání této funkce můžete získat OLE položku, která je aktuálně aktivovat zavedené v tomto `CRichEditView` objektu.  
  
```  
CRichEditCntrItem* GetInPlaceActiveItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na jednom, místní active [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objekt v tomto zobrazení RichEdit; **NULL** Pokud neexistuje žádná položka OLE aktuálně v aktivním stavu na místě.  
  
##  <a name="getmargins"></a>CRichEditView::GetMargins  
 Volání této funkce načíst aktuální rozpětí používaná v tisku.  
  
```  
CRect GetMargins() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozpětí používaná v tisku, měřená v `MM_TWIPS`.  
  
##  <a name="getpagerect"></a>CRichEditView::GetPageRect  
 Volání této funkce můžete získat dimenze stránky použité v tisku.  
  
```  
CRect GetPageRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hranice stránky použité v tisku, měřená v `MM_TWIPS`.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota je založena na velikost papíru.  
  
##  <a name="getpapersize"></a>CRichEditView::GetPaperSize  
 Volání této funkce načíst aktuální velikost papíru.  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost papíru použitého v tisku, měřená v `MM_TWIPS`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]  
  
##  <a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection  
 Volání této funkce můžete získat atributy aktuálního výběru formátování odstavce.  
  
```  
PARAFORMAT2& GetParaFormatSelection();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktura, která obsahuje atributy aktuálního výběru formátování odstavce.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182) zprávy a [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktura ve Windows SDK.  
  
##  <a name="getprintrect"></a>CRichEditView::GetPrintRect  
 Volání této funkce načíst hranice tisk oblasti v rámci rámeček stránky.  
  
```  
CRect GetPrintRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hranice oblasti obrázku používá v tisku, měřená v `MM_TWIPS`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]  
  
##  <a name="getprintwidth"></a>CRichEditView::GetPrintWidth  
 Volání této funkce určete šířku oblasti tisku.  
  
```  
int GetPrintWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Měřená šířka oblasti tisku v `MM_TWIPS`.  
  
##  <a name="getricheditctrl"></a>CRichEditView::GetRichEditCtrl  
 Volání této funkce můžete získat [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) objekt přidružený k `CRichEditView` objektu.  
  
```  
CRichEditCtrl& GetRichEditCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `CRichEditCtrl` Objekt pro toto zobrazení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).  
  
##  <a name="getselecteditem"></a>CRichEditView::GetSelectedItem  
 Volání této funkce k získání položky OLE ( `CRichEditCntrItem` objektu) aktuálně vybrané v tomto `CRichEditView` objektu.  
  
```  
CRichEditCntrItem* GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) v vybrán objekt `CRichEditView` objektu; **NULL** Pokud v tomto zobrazení není vybrána žádná položka.  
  
##  <a name="gettextlength"></a>CRichEditView::GetTextLength  
 Volání této funkce se načíst délku textu v tomto `CRichEditView` objektu.  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka textu v tomto `CRichEditView` objektu.  
  
##  <a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx  
 Volání této funkce člen k výpočtu Délka textu v tomto `CRichEditView` objektu.  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Hodnota, která určuje způsob, který má být použit při určování délka textu. Tento člen může mít jednu nebo více hodnot uvedených v příznaky členem [GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915) popsané v sadě Windows SDK.  
  
 `uCodePage`  
 Znaková stránka pro překlad (CP_ACP ANSI znakové stránky, 1200 pro kódování Unicode).  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků nebo bajtů v ovládacím prvku upravit. Pokud byly v nekompatibilní příznaky `dwFlags`, vrátí tato funkce člen `E_INVALIDARG`.  
  
### <a name="remarks"></a>Poznámky  
 `GetTextLengthEx`Další způsoby určování délka textu. Podporuje funkci bohaté upravit 2.0. Další informace najdete v tématu [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) ve Windows SDK.  
  
##  <a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject  
 Volání této funkce Vložit zadaný soubor (jako [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objektu) do s formátováním upravit zobrazení.  
  
```  
void InsertFileAsObject(LPCTSTR lpszFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Řetězec, který obsahuje název souboru, který má být vložen.  
  
##  <a name="insertitem"></a>CRichEditView::InsertItem  
 Volání této funkce k vložení [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objektu do RichEdit zobrazení.  
  
```  
HRESULT InsertItem(CRichEditCntrItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel na položku, která má být vložen.  
  
### <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnotu, která udává úspěch vložení.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o `HRESULT`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
##  <a name="isricheditformat"></a>CRichEditView::IsRichEditFormat  
 Volání této funkce určete, zda `cf` je formát schránky, což je text, formátovaným textem nebo RTF s OLE – položky.  
  
```  
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 Formát schránky, které vás zajímají.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `cf` je bohaté formát schránky upravit nebo text.  
  
##  <a name="isselected"></a>CRichEditView::IsSelected  
 Volání této funkce k určení, pokud zadaná položka OLE je aktuálně vybraný v tomto zobrazení.  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDocItem`  
 Ukazatel na objekt v zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je objekt vybrán; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkci přepište, pokud vaše třídy odvozené zobrazení má jinou metodu pro zpracování výběr položek OLE.  
  
##  <a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent  
 Odsazení pro odrážka položky v seznamu; ve výchozím nastavení, 720 jednotek, což je 1/2 palce.  
  
```  
int m_nBulletIndent;  
```  
  
##  <a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap  
 Určuje typ zalamování řádků pro toto zobrazení RichEdit.  
  
```  
int m_nWordWrap;  
```  
  
### <a name="remarks"></a>Poznámky  
 Jedna z následujících hodnot:  
  
- `WrapNone`Označuje žádné automatické zalamování řádků.  
  
- `WrapToWindow`Označuje zalamování řádků podle šířky okna.  
  
- `WrapToTargetDevice`Označuje zalamování řádků na základě charakteristik cílového zařízení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::WrapChanged](#wrapchanged).  
  
##  <a name="onchareffect"></a>CRichEditView::OnCharEffect  
 Volání této funkce lze přepnout formátování důsledky pro aktuální výběr znaků.  
  
```  
void OnCharEffect(
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `dwMask`  
 Chcete-li upravit v aktuálním výběru formátování znaků.  
  
 `dwEffect`  
 Požadovaný seznam formátování důsledky k přepnutí znaků.  
  
### <a name="remarks"></a>Poznámky  
 Každé volání této funkce přepne zadaný formátování důsledky pro aktuální výběr.  
  
 Další informace o `dwMask` a `dwEffect` parametry a jejich potenciální hodnoty, najdete v části odpovídající členů dat [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]  
  
##  <a name="onfindnext"></a>CRichEditView::OnFindNext  
 Voláno rámcem při zpracování příkazů z dialogového okna vyhledání a nahrazení.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Řetězec, který se má najít.  
  
 `bNext`  
 Směru vyhledávání: **TRUE** označuje; **FALSE**, až.  
  
 `bCase`  
 Určuje, zda hledání se velká a malá písmena.  
  
 `bWord`  
 Určuje, zda hledání Hledat celá slova pouze nebo ne.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce najít text v rámci `CRichEditView`. Přepsání této funkci můžete měnit vlastnosti vyhledávání pro váš třídy odvozené zobrazení.  
  
##  <a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate  
 Voláno rámcem po zobrazení je nejprve připojen k dokumentu, ale před zpočátku je zobrazeno zobrazení.  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce volá [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) – členská funkce bez pomocného parametru informací (tedy pomocí výchozích hodnot 0 pro `lHint` parametr a **NULL** pro `pHint` parametr). Přepsání této funkci můžete provést všechny jednorázové inicializace, který vyžaduje informace o dokumentu. Například pokud aplikace má pevnou velikostí dokumenty, můžete použít tuto funkci k chybě při inicializaci zobrazení posouvání omezení na základě velikosti dokumentu. Pokud vaše aplikace podporuje dokumenty proměnlivé velikosti, použijte `OnUpdate` aktualizovat posouvání omezuje pokaždé, když změny dokumentu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::m_nWordWrap](#m_nwordwrap).  
  
##  <a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject  
 Pomocí této funkce můžete načíst nativní data z vložené položky.  
  
```  
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStg*  
 Ukazatel na [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0;  
  
### <a name="remarks"></a>Poznámky  
 Obvykle byste to uděláte tak, že vytvoříte [COleStreamFile](../../mfc/reference/colestreamfile-class.md) kolem `IStorage`. `COleStreamFile` Lze připojit k archivu a [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) názvem Pokud chcete načíst data.  
  
 Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) ve Windows SDK.  
  
##  <a name="onparaalign"></a>CRichEditView::OnParaAlign  
 Volání této funkce můžete změnit zarovnání odstavce pro vybrané odstavce.  
  
```  
void OnParaAlign(WORD wAlign);
```  
  
### <a name="parameters"></a>Parametry  
 `wAlign`  
 Zarovnání požadované odstavce. Jedna z následujících hodnot:  
  
- `PFA_LEFT`Zarovnává odstavců s levým okrajem.  
  
- `PFA_RIGHT`Zarovnává odstavců s pravým okrajem.  
  
- `PFA_CENTER`Center odstavců mezi pravého okraje.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]  
  
##  <a name="onprinterchanged"></a>CRichEditView::OnPrinterChanged  
 Přepsání této funkci můžete změnit vlastnosti pro toto zobrazení RichEdit při změně tiskárny.  
  
```  
virtual void OnPrinterChanged(const CDC& dcPrinter);
```  
  
### <a name="parameters"></a>Parametry  
 `dcPrinter`  
 A [CDC](../../mfc/reference/cdc-class.md) objekt pro nové tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nastaví velikost papíru fyzické výška a šířka výstupní zařízení (tiskárny). Pokud není přidružený žádný kontext zařízení `dcPrinter`, výchozí implementace nastaví velikost papíru na 8.5 podle 11 palců.  
  
##  <a name="onreplaceall"></a>CRichEditView::OnReplaceAll  
 Voláno rámcem při zpracování nahradit všechny příkazy z dialogového okna nahradit.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, který má být nahrazen.  
  
 `lpszReplace`  
 Nahrazení textu.  
  
 `bCase`  
 Určuje, zda hledání velká a malá písmena.  
  
 `bWord`  
 Označuje, pokud vyhledávání musíte vybrat celá slova nebo ne.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce můžete nahraďte všechny výskyty daného text jiným řetězcem. Přepsání této funkci můžete měnit vlastnosti vyhledávání pro toto zobrazení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).  
  
##  <a name="onreplacesel"></a>CRichEditView::OnReplaceSel  
 Voláno rámcem při zpracování nahraďte příkazy z dialogového okna nahradit.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, který má být nahrazen.  
  
 `bNext`  
 Určuje směr hledání: **TRUE** nefunguje; **FALSE**, až.  
  
 `bCase`  
 Určuje, zda hledání velká a malá písmena.  
  
 `bWord`  
 Označuje, pokud vyhledávání musíte vybrat celá slova nebo ne.  
  
 `lpszReplace`  
 Nahrazení textu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce můžete nahradit jiným řetězcem výskytů některé daného textu. Přepsání této funkci můžete měnit vlastnosti vyhledávání pro toto zobrazení.  
  
##  <a name="ontextnotfound"></a>CRichEditView::OnTextNotFound  
 Voláno rámcem vždy, když se hledání nezdaří.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Text, který nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Funkci chcete-li změnit oznámení výstup z přepsat [MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356).  
  
 Další informace najdete v tématu [MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]  
  
##  <a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect  
 Tato funkce se aktualizovat příkaz uživatelského rozhraní pro příkazy vliv znak volá framework.  
  
```  
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,  
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Ukazatel na [CCmdUI](../../mfc/reference/ccmdui-class.md) objektu.  
  
 `dwMask`  
 Určuje formátování maska znaků.  
  
 `dwEffect`  
 Určuje formátování vliv znaků.  
  
### <a name="remarks"></a>Poznámky  
 Maska `dwMask` Určuje, který znak formátování atributy ke kontrole. V příznacích `dwEffect` seznam atributů pro sadu a Vymazat formátování znaků.  
  
 Další informace o `dwMask` a `dwEffect` parametry a jejich potenciální hodnoty, najdete v části odpovídající členů dat [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]  
  
##  <a name="onupdateparaalign"></a>CRichEditView::OnUpdateParaAlign  
 Volá rámec této funkci můžete aktualizovat příkaz uživatelského rozhraní pro příkazy vliv odstavce.  
  
```  
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,  
    WORD wAlign);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Ukazatel na [CCmdUI](../../mfc/reference/ccmdui-class.md) objektu.  
  
 `wAlign`  
 Zarovnání odstavce ke kontrole. Jedna z následujících hodnot:  
  
- `PFA_LEFT`Zarovnává odstavců s levým okrajem.  
  
- `PFA_RIGHT`Zarovnává odstavců s pravým okrajem.  
  
- `PFA_CENTER`Center odstavců mezi pravého okraje.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]  
  
##  <a name="printinsiderect"></a>CRichEditView::PrintInsideRect  
 Volání této funkce k formátování rozsah textu v ovládacím prvku RichEdit nevejde se do *rectLayout* pro zařízení určeného `pDC`.  
  
```  
long PrintInsideRect(
    CDC* pDC,  
    RECT& rectLayout,  
    long nIndexStart,  
    long nIndexStop,  
    BOOL bOutput);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext zařízení pro oblasti výstup.  
  
 *rectLayout*  
 [Rect –](../../mfc/reference/rect-structure1.md) nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) určující oblasti výstup.  
  
 `nIndexStart`  
 Index prvního znaku, který má být formátována nule.  
  
 `nIndexStop`  
 Index počítaný od nuly poslední znak, který má být ve formátu.  
  
 *bOutput*  
 Označuje, pokud má být vykreslen text. Pokud **FALSE**, právě měří text.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index poslední znak, který nejlépe odpovídá v oblasti výstup plus jedna.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání obvykle následuje volání [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) který generuje výstup.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::GetPaperSize](#getpapersize).  
  
##  <a name="printpage"></a>CRichEditView::PrintPage  
 Volání této funkce k formátování rozsah textu v ovládacím prvku RichEdit pro výstupní zařízení určeného `pDC`.  
  
```  
long PrintPage(
    CDC* pDC,  
    long nIndexStart,  
    long nIndexStop);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext zařízení pro výstup stránky.  
  
 `nIndexStart`  
 Index prvního znaku, který má být formátována nule.  
  
 `nIndexStop`  
 Index počítaný od nuly poslední znak, který má být ve formátu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index poslední znak, který nejlépe odpovídá na stránce plus jedna.  
  
### <a name="remarks"></a>Poznámky  
 Rozložení každé stránce řídí [GetPageRect](#getpagerect) a [GetPrintRect](#getprintrect). Toto volání obvykle následuje volání [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) který generuje výstup.  
  
 Všimněte si, že okraje relativně k fyzickou stránku není logické stránky. Proto okraje nula bude často oříznutí text vzhledem k tomu, že mnoho tiskárny mají oblastí nezávisí na stránce. Abyste se vyhnuli výstřižek text, by měly volat [SetMargins](#setmargins) a nastavte přiměřené okraje před tiskem.  
  
##  <a name="queryacceptdata"></a>CRichEditView::QueryAcceptData  
 Voláno rámcem vložte objekt do bohaté upravit.  
  
```  
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,  
    CLIPFORMAT* lpcfFormat,  
    DWORD dwReco,  
    BOOL bReally,  
    HGLOBAL hMetaFile);
```  
  
### <a name="parameters"></a>Parametry  
 *lpdataobj*  
 Ukazatel [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) dotazu.  
  
 *lpcfFormat*  
 Ukazatel na formát dat přijatelný.  
  
 `dwReco`  
 Nepoužívá se.  
  
 *bReally*  
 Určuje, zda se operace vložení pokračovat nebo ne.  
  
 `hMetaFile`  
 Popisovač pro metafile používá pro kreslení ikony položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnotu úspěch operace vytváření sestav.  
  
### <a name="remarks"></a>Poznámky  
 Funkci pro zpracování jiné organizaci položek COM v odvození dokumentové třídy přepište. Toto je rozšířené přepisovatelné.  
  
 Další informace o `HRESULT` a `IDataObject`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) a [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421), v uvedeném pořadí, ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]  
  
##  <a name="setcharformat"></a>CRichEditView::SetCharFormat  
 Volání této funkce nastavit formátování atributy pro nový text v tomto znaků `CRichEditView` objektu.  
  
```  
void SetCharFormat(CHARFORMAT2 cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura obsahující nové výchozí formátování atributy.  
  
### <a name="remarks"></a>Poznámky  
 Pouze atributy určeného **dwMask** členem `cf` došlo ke změně pomocí této funkce.  
  
 Další informace najdete v tématu [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) zprávy a [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="setmargins"></a>CRichEditView::SetMargins  
 Volání této funkce nastavení tisku okrajů pro toto zobrazení RichEdit.  
  
```  
void SetMargins(const CRect& rectMargin);
```  
  
### <a name="parameters"></a>Parametry  
 *rectMargin*  
 Nové hodnoty okrajů pro tisk, měřená v `MM_TWIPS`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [m_nWordWrap](#m_nwordwrap) je `WrapToTargetDevice`, by měly volat [WrapChanged](#wrapchanged) po použití této funkce upravit parametry tisku.  
  
 Všimněte si, že používané pravého okraje [PrintPage](#printpage) jsou relativní vzhledem k fyzickou stránku není logické stránky. Proto okraje nula bude často oříznutí text vzhledem k tomu, že mnoho tiskárny mají oblastí nezávisí na stránce. Abyste se vyhnuli výstřižek text, by měly volat pomocí `SetMargins` nastavení okrajů přiměřené tiskárny před tiskem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::GetPaperSize](#getpapersize).  
  
##  <a name="setpapersize"></a>CRichEditView::SetPaperSize  
 Volání této funkce můžete nastavte velikost papíru pro tisk toto RichEdit zobrazení.  
  
```  
void SetPaperSize(CSize sizePaper);
```  
  
### <a name="parameters"></a>Parametry  
 *sizePaper*  
 Nové hodnoty velikost papíru pro tisk, měřená v `MM_TWIPS`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [m_nWordWrap](#m_nwordwrap) je `WrapToTargetDevice`, by měly volat [WrapChanged](#wrapchanged) po použití této funkce upravit parametry tisku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditView::SetParaFormat  
 Volání této funkce nastavit atributy pro aktuální výběr v tomto formátování odstavce `CRichEditView` objektu.  
  
```  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>Parametry  
 `pf`  
 [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktura obsahující nový výchozí bod atributy formátování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pouze atributy určeného **dwMask** členem `pf` došlo ke změně pomocí této funkce.  
  
 Další informace najdete v tématu [EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276) zprávy a [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]  
  
##  <a name="textnotfound"></a>CRichEditView::TextNotFound  
 Volání této funkce, chcete-li obnovit stav vnitřní vyhledávání [cricheditview –](../../mfc/reference/cricheditview-class.md) řízení po nezdařeného volání do [řetězec FindText](#findtext).  
  
```  
void TextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFind`  
 Obsahuje textový řetězec, který nebyl nalezen.  
  
### <a name="remarks"></a>Poznámky  
 Doporučuje se, že se tato metoda volána hned po volání se nezdařilo [řetězec FindText](#findtext) tak, aby se správně resetuje stav vnitřní vyhledávání ovládacího prvku.  
  
 `lpszFind` Parametru by měla obsahovat stejný obsah jako řetězec poskytované [řetězec FindText](#findtext). Po obnovení stavu interní vyhledávání, bude volat tuto metodu [OnTextNotFound](#ontextnotfound) metoda s zadaný hledaný řetězec.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditView::FindText](#findtext).  
  
##  <a name="wrapchanged"></a>CRichEditView::WrapChanged  
 Volat tuto funkci při tisku charakteristiky změnily ( [SetMargins](#setmargins) nebo [SetPaperSize](#setpapersize)).  
  
```  
virtual void WrapChanged();
```  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete upravit způsob, jakým bohaté upravit zobrazení reaguje na změny v [m_nWordWrap](#m_nwordwrap) nebo tisk charakteristiky ( [OnPrinterChanged](#onprinterchanged)).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC WORDPAD](../../visual-cpp-samples.md)   
 [CCtrlView – třída](../../mfc/reference/cctrlview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc – třída](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem – třída](../../mfc/reference/cricheditcntritem-class.md)
