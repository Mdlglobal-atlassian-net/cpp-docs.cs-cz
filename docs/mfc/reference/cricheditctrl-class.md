---
title: "CRichEditCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCtrl
- AFXCMN/CRichEditCtrl
- AFXCMN/CRichEditCtrl::CRichEditCtrl
- AFXCMN/CRichEditCtrl::CanPaste
- AFXCMN/CRichEditCtrl::CanRedo
- AFXCMN/CRichEditCtrl::CanUndo
- AFXCMN/CRichEditCtrl::CharFromPos
- AFXCMN/CRichEditCtrl::Clear
- AFXCMN/CRichEditCtrl::Copy
- AFXCMN/CRichEditCtrl::Create
- AFXCMN/CRichEditCtrl::CreateEx
- AFXCMN/CRichEditCtrl::Cut
- AFXCMN/CRichEditCtrl::DisplayBand
- AFXCMN/CRichEditCtrl::EmptyUndoBuffer
- AFXCMN/CRichEditCtrl::FindText
- AFXCMN/CRichEditCtrl::FindWordBreak
- AFXCMN/CRichEditCtrl::FormatRange
- AFXCMN/CRichEditCtrl::GetCharPos
- AFXCMN/CRichEditCtrl::GetDefaultCharFormat
- AFXCMN/CRichEditCtrl::GetEventMask
- AFXCMN/CRichEditCtrl::GetFirstVisibleLine
- AFXCMN/CRichEditCtrl::GetIRichEditOle
- AFXCMN/CRichEditCtrl::GetLimitText
- AFXCMN/CRichEditCtrl::GetLine
- AFXCMN/CRichEditCtrl::GetLineCount
- AFXCMN/CRichEditCtrl::GetModify
- AFXCMN/CRichEditCtrl::GetOptions
- AFXCMN/CRichEditCtrl::GetParaFormat
- AFXCMN/CRichEditCtrl::GetPunctuation
- AFXCMN/CRichEditCtrl::GetRect
- AFXCMN/CRichEditCtrl::GetRedoName
- AFXCMN/CRichEditCtrl::GetSel
- AFXCMN/CRichEditCtrl::GetSelectionCharFormat
- AFXCMN/CRichEditCtrl::GetSelectionType
- AFXCMN/CRichEditCtrl::GetSelText
- AFXCMN/CRichEditCtrl::GetTextLength
- AFXCMN/CRichEditCtrl::GetTextLengthEx
- AFXCMN/CRichEditCtrl::GetTextMode
- AFXCMN/CRichEditCtrl::GetTextRange
- AFXCMN/CRichEditCtrl::GetUndoName
- AFXCMN/CRichEditCtrl::GetWordWrapMode
- AFXCMN/CRichEditCtrl::HideSelection
- AFXCMN/CRichEditCtrl::LimitText
- AFXCMN/CRichEditCtrl::LineFromChar
- AFXCMN/CRichEditCtrl::LineIndex
- AFXCMN/CRichEditCtrl::LineLength
- AFXCMN/CRichEditCtrl::LineScroll
- AFXCMN/CRichEditCtrl::Paste
- AFXCMN/CRichEditCtrl::PasteSpecial
- AFXCMN/CRichEditCtrl::PosFromChar
- AFXCMN/CRichEditCtrl::Redo
- AFXCMN/CRichEditCtrl::ReplaceSel
- AFXCMN/CRichEditCtrl::RequestResize
- AFXCMN/CRichEditCtrl::SetAutoURLDetect
- AFXCMN/CRichEditCtrl::SetBackgroundColor
- AFXCMN/CRichEditCtrl::SetDefaultCharFormat
- AFXCMN/CRichEditCtrl::SetEventMask
- AFXCMN/CRichEditCtrl::SetModify
- AFXCMN/CRichEditCtrl::SetOLECallback
- AFXCMN/CRichEditCtrl::SetOptions
- AFXCMN/CRichEditCtrl::SetParaFormat
- AFXCMN/CRichEditCtrl::SetPunctuation
- AFXCMN/CRichEditCtrl::SetReadOnly
- AFXCMN/CRichEditCtrl::SetRect
- AFXCMN/CRichEditCtrl::SetSel
- AFXCMN/CRichEditCtrl::SetSelectionCharFormat
- AFXCMN/CRichEditCtrl::SetTargetDevice
- AFXCMN/CRichEditCtrl::SetTextMode
- AFXCMN/CRichEditCtrl::SetUndoLimit
- AFXCMN/CRichEditCtrl::SetWordCharFormat
- AFXCMN/CRichEditCtrl::SetWordWrapMode
- AFXCMN/CRichEditCtrl::StopGroupTyping
- AFXCMN/CRichEditCtrl::StreamIn
- AFXCMN/CRichEditCtrl::StreamOut
- AFXCMN/CRichEditCtrl::Undo
dev_langs: C++
helpviewer_keywords:
- CRichEditCtrl [MFC], CRichEditCtrl
- CRichEditCtrl [MFC], CanPaste
- CRichEditCtrl [MFC], CanRedo
- CRichEditCtrl [MFC], CanUndo
- CRichEditCtrl [MFC], CharFromPos
- CRichEditCtrl [MFC], Clear
- CRichEditCtrl [MFC], Copy
- CRichEditCtrl [MFC], Create
- CRichEditCtrl [MFC], CreateEx
- CRichEditCtrl [MFC], Cut
- CRichEditCtrl [MFC], DisplayBand
- CRichEditCtrl [MFC], EmptyUndoBuffer
- CRichEditCtrl [MFC], FindText
- CRichEditCtrl [MFC], FindWordBreak
- CRichEditCtrl [MFC], FormatRange
- CRichEditCtrl [MFC], GetCharPos
- CRichEditCtrl [MFC], GetDefaultCharFormat
- CRichEditCtrl [MFC], GetEventMask
- CRichEditCtrl [MFC], GetFirstVisibleLine
- CRichEditCtrl [MFC], GetIRichEditOle
- CRichEditCtrl [MFC], GetLimitText
- CRichEditCtrl [MFC], GetLine
- CRichEditCtrl [MFC], GetLineCount
- CRichEditCtrl [MFC], GetModify
- CRichEditCtrl [MFC], GetOptions
- CRichEditCtrl [MFC], GetParaFormat
- CRichEditCtrl [MFC], GetPunctuation
- CRichEditCtrl [MFC], GetRect
- CRichEditCtrl [MFC], GetRedoName
- CRichEditCtrl [MFC], GetSel
- CRichEditCtrl [MFC], GetSelectionCharFormat
- CRichEditCtrl [MFC], GetSelectionType
- CRichEditCtrl [MFC], GetSelText
- CRichEditCtrl [MFC], GetTextLength
- CRichEditCtrl [MFC], GetTextLengthEx
- CRichEditCtrl [MFC], GetTextMode
- CRichEditCtrl [MFC], GetTextRange
- CRichEditCtrl [MFC], GetUndoName
- CRichEditCtrl [MFC], GetWordWrapMode
- CRichEditCtrl [MFC], HideSelection
- CRichEditCtrl [MFC], LimitText
- CRichEditCtrl [MFC], LineFromChar
- CRichEditCtrl [MFC], LineIndex
- CRichEditCtrl [MFC], LineLength
- CRichEditCtrl [MFC], LineScroll
- CRichEditCtrl [MFC], Paste
- CRichEditCtrl [MFC], PasteSpecial
- CRichEditCtrl [MFC], PosFromChar
- CRichEditCtrl [MFC], Redo
- CRichEditCtrl [MFC], ReplaceSel
- CRichEditCtrl [MFC], RequestResize
- CRichEditCtrl [MFC], SetAutoURLDetect
- CRichEditCtrl [MFC], SetBackgroundColor
- CRichEditCtrl [MFC], SetDefaultCharFormat
- CRichEditCtrl [MFC], SetEventMask
- CRichEditCtrl [MFC], SetModify
- CRichEditCtrl [MFC], SetOLECallback
- CRichEditCtrl [MFC], SetOptions
- CRichEditCtrl [MFC], SetParaFormat
- CRichEditCtrl [MFC], SetPunctuation
- CRichEditCtrl [MFC], SetReadOnly
- CRichEditCtrl [MFC], SetRect
- CRichEditCtrl [MFC], SetSel
- CRichEditCtrl [MFC], SetSelectionCharFormat
- CRichEditCtrl [MFC], SetTargetDevice
- CRichEditCtrl [MFC], SetTextMode
- CRichEditCtrl [MFC], SetUndoLimit
- CRichEditCtrl [MFC], SetWordCharFormat
- CRichEditCtrl [MFC], SetWordWrapMode
- CRichEditCtrl [MFC], StopGroupTyping
- CRichEditCtrl [MFC], StreamIn
- CRichEditCtrl [MFC], StreamOut
- CRichEditCtrl [MFC], Undo
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03ef5135130590d142e9725e1d064b932cc7ff4d
ms.sourcegitcommit: 2aeb507a426fc7881ea59115b1d5139c0a30ba91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2018
---
# <a name="cricheditctrl-class"></a>CRichEditCtrl – třída
Poskytuje funkce ovládacího prvku RichEdit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditCtrl::CRichEditCtrl](#cricheditctrl)|Vytvoří `CRichEditCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRichEditCtrl::CanPaste](#canpaste)|Určuje, pokud lze vložit obsah schránky do tohoto ovládacího prvku RichEdit.|  
|[CRichEditCtrl::CanRedo](#canredo)|Určuje, zda jsou všechny akce ve frontě opakování ovládacího prvku.|  
|[CRichEditCtrl::CanUndo](#canundo)|Určuje, pokud se operace úprav mohou být vráceny zpět.|  
|[CRichEditCtrl::CharFromPos](#charfrompos)|Načte informace o znak, který je nejblíže k bod zadané v oblasti klienta ovládacích prvků pro úpravy.|  
|[CRichEditCtrl::Clear](#clear)|Vymaže aktuální výběr.|  
|[CRichEditCtrl::Copy](#copy)|Aktuální výběr zkopíruje do schránky.|  
|[CRichEditCtrl::Create](#create)|Vytvoří ovládacího prvku RichEdit Windows a přidruží ji to `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::CreateEx](#createex)|Vytvoří ovládacího prvku RichEdit Windows se zadaným rozšířené styly Windows a přidruží ji to `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::Cut](#cut)|Vyjme aktuální výběr do schránky.|  
|[CRichEditCtrl::DisplayBand](#displayband)|Zobrazí část obsahu tohoto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::EmptyUndoBuffer](#emptyundobuffer)|Resetování (vymaže) příznak zpět tohoto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::FindText](#findtext)|Vyhledá text v rámci to `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::FindWordBreak](#findwordbreak)|Vyhledá další dělení textu před nebo po zadaný znak na pozici nebo načítá informace o znak na dané pozici.|  
|[CRichEditCtrl::FormatRange](#formatrange)|Formátuje rozsah textu pro výstup cílové zařízení.|  
|[CRichEditCtrl::GetCharPos](#getcharpos)|Určuje umístění daného znaku v rámci to `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetDefaultCharFormat](#getdefaultcharformat)|Načte aktuální znak výchozí atributy v tomto formátování `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetEventMask](#geteventmask)|Načte maska události pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetFirstVisibleLine](#getfirstvisibleline)|Určuje nejhornější viditelné řádku v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetIRichEditOle](#getiricheditole)|Načte ukazatel `IRichEditOle` rozhraní pro toto bohaté ovládacích prvků pro úpravy.|  
|[CRichEditCtrl::GetLimitText](#getlimittext)|Získá limit na objem textu, které může uživatel zadat do této `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetLine](#getline)|Načte řádku textu z tohoto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetLineCount](#getlinecount)|Získá počet řádků v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetModify](#getmodify)|Určuje, zda obsah tohoto `CRichEditCtrl` objekt změnily od posledního uložení.|  
|[CRichEditCtrl::GetOptions](#getoptions)|Načte nastavení ovládacího prvku RichEdit.|  
|[CRichEditCtrl::GetParaFormat](#getparaformat)|Načte atributy v aktuálním výběru v tomto formátování odstavce `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetPunctuation](#getpunctuation)|Načte aktuální znaky interpunkce ovládacího prvku RichEdit. Tato zpráva je k dispozici pouze v asijské jazyky verzích operačního systému.|  
|[CRichEditCtrl::GetRect](#getrect)|Načte formátování rámeček pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetRedoName](#getredoname)|Načte typ další akce, pokud existuje, v ovládacím prvku vrátit fronty.|  
|[CRichEditCtrl::GetSel](#getsel)|Získá počáteční a koncová pozice aktuální výběr v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetSelectionCharFormat](#getselectioncharformat)|Načte atributů v aktuálním výběru v tomto formátování znaků `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetSelectionType](#getselectiontype)|Načte typ obsahu v aktuálním výběru v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::GetSelText](#getseltext)|Získá text aktuální výběr v tomto `CRichEditCtrl` objektu|  
|[CRichEditCtrl::GetTextLength](#gettextlength)|Načte délka textu v znaků v tomto `CRichEditCtrl` objektu. Nezahrnuje ukončující znak hodnoty null.|  
|[CRichEditCtrl::GetTextLengthEx](#gettextlengthex)|Načte počet znaků nebo bajtů v RichEdit zobrazení. Přijme seznam, které jsou označeny metodou pro určení toho délka textu v ovládacím prvku RichEdit|  
|[CRichEditCtrl::GetTextMode](#gettextmode)|Načte aktuální text režim a vrácení zpět úroveň ovládacího prvku RichEdit.|  
|[CRichEditCtrl::GetTextRange](#gettextrange)|Načte zadaný rozsah textu.|  
|[CRichEditCtrl::GetUndoName](#getundoname)|Načte typ další akce vrácení zpět, pokud existuje.|  
|[CRichEditCtrl::GetWordWrapMode](#getwordwrapmode)|Načte aktuální zalamování řádků a možnosti v aplikaci word ukončování řádků pro ovládací prvek RichEdit. Tato zpráva je k dispozici pouze v asijské jazyky verzích operačního systému.|  
|[CRichEditCtrl::HideSelection](#hideselection)|Zobrazí nebo skryje aktuální výběr.|  
|[CRichEditCtrl::LimitText](#limittext)|Omezuje objem textu, které může uživatel zadat do `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::LineFromChar](#linefromchar)|Určuje, které řádek obsahuje daného znaku.|  
|[CRichEditCtrl::LineIndex](#lineindex)|Načte znakový index daného řádku v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::LineLength](#linelength)|Načte délka daném řádku v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::LineScroll](#linescroll)|Posune text v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::Paste](#paste)|Vloží obsah schránky do tohoto ovládacího prvku RichEdit.|  
|[CRichEditCtrl::PasteSpecial](#pastespecial)|Vloží obsah schránky do tohoto ovládacího prvku RichEdit ve formátu zadaná data.|  
|[CRichEditCtrl::PosFromChar](#posfromchar)|Načte souřadnice oblasti klienta je zadaný znak v ovládacím prvku upravit.|  
|[CRichEditCtrl::Redo](#redo)|Znovu provede další akce ve frontě opakování ovládacího prvku.|  
|[CRichEditCtrl::ReplaceSel](#replacesel)|Nahradí aktuální výběr v tomto `CRichEditCtrl` objekt se zadaným textem.|  
|[CRichEditCtrl::RequestResize](#requestresize)|Vynutí to `CRichEditCtrl` objekt, který chcete odeslat žádost o změnu velikosti oznámení.|  
|[CRichEditCtrl::SetAutoURLDetect](#setautourldetect)|Určuje, zda je automatické zjišťování adresy URL v ovládacím prvku RichEdit aktivní.|  
|[CRichEditCtrl::SetBackgroundColor](#setbackgroundcolor)|Nastaví barvu pozadí v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetDefaultCharFormat](#setdefaultcharformat)|Nastaví aktuální znak výchozí atributy v tomto formátování `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetEventMask](#seteventmask)|Nastaví maska události pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetModify](#setmodify)|Nastaví nebo vymaže příznak úpravy pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetOLECallback](#setolecallback)|Nastaví `IRichEditOleCallback` objektu COM u tohoto ovládacího prvku RichEdit.|  
|[CRichEditCtrl::SetOptions](#setoptions)|Nastaví možnosti pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetParaFormat](#setparaformat)|Nastaví atributy v aktuálním výběru v tomto formátování odstavce `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetPunctuation](#setpunctuation)|Nastaví u ovládacího prvku RichEdit znaky interpunkce. Tato zpráva je k dispozici pouze v asijské jazyky verzích operačního systému.|  
|[CRichEditCtrl::SetReadOnly](#setreadonly)|Nastaví možnost jen pro čtení pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetRect](#setrect)|Nastaví formátování rámeček pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetSel](#setsel)|Nastaví výběru v tomto `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetSelectionCharFormat](#setselectioncharformat)|Nastaví znak, atributy v aktuálním výběru v tomto formátování `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetTargetDevice](#settargetdevice)|Nastaví cílové zařízení výstup pro tento `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetTextMode](#settextmode)|Nastaví úroveň text režimu nebo vrácení zpět ovládacího prvku RichEdit. Zpráva selže, pokud obsahuje ovládací prvek text.|  
|[CRichEditCtrl::SetUndoLimit](#setundolimit)|Nastaví maximální počet akcí, které mohou být uloženy ve frontě vrácení zpět.|  
|[CRichEditCtrl::SetWordCharFormat](#setwordcharformat)|Nastaví znak, atributy v aktuální aplikaci word v tomto formátování `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::SetWordWrapMode](#setwordwrapmode)|Nastaví možnosti-zalamování řádků a dělení slov pro bohaté ovládacích prvků pro úpravy. Tato zpráva je k dispozici pouze v asijské jazyky verzích operačního systému.|  
|[CRichEditCtrl::StopGroupTyping](#stopgrouptyping)|Zastaví řízení z shromažďování dalších psaní akce do aktuální akce vrácení zpět. Ovládací prvek ukládá další zadáním akce, pokud existuje, do nové akce ve frontě vrácení zpět.|  
|[CRichEditCtrl::StreamIn](#streamin)|Vloží text ze vstupního datového proudu do této `CRichEditCtrl` objektu.|  
|[CRichEditCtrl::StreamOut](#streamout)|Ukládá text z tohoto `CRichEditCtrl` objektu do výstupního proudu.|  
|[CRichEditCtrl::Undo](#undo)|Vrátí zpět poslední operace úprav.|  
  
## <a name="remarks"></a>Poznámky  
 "RichEdit řízení" je okno, ve kterém může uživatel zadat a upravit text. Text se dá přiřadit znak a formátování odstavce a může obsahovat vložené objekty OLE. Ovládací prvky Rich edit zadejte programovací rozhraní pro formátování textu. Aplikace musí implementovat však potřeba zpřístupnit operací formátování uživateli žádné uživatelské rozhraní komponenty.  
  
 Tento ovládací prvek Windows běžné (a proto `CRichEditCtrl` – třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším. `CRichEditCtrl` Třída podporuje verze 2.0 a 3.0 bohaté sady Windows SDK ovládacích prvků pro úpravy.  
  
> [!CAUTION]
>  Pokud používáte ovládacího prvku RichEdit v dialogovém okně (bez ohledu na to informaci, jestli vaše aplikace SDI, MDI, nebo na základě dialogové okno), musí volat [afxinitrichedit –](application-information-and-management.md#afxinitrichedit) po před dialogové okno se zobrazí pole. Je typické pro volání této funkce se ve vašem programu `InitInstance` – členská funkce. Není nutné volat pokaždé, když je zobrazit dialogové okno, pouze při prvním spuštění. Není nutné volat `AfxInitRichEdit` při práci s `CRichEditView`.  
  
 Další informace o používání `CRichEditCtrl`, najdete v části:  
  
- [Ovládací prvky](../../mfc/controls-mfc.md)  
  
- [Používání atributu CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   Článek znalostní báze Knowledge Base Q259949: informace: SetCaretPos() je není vhodný s CEdit nebo ovládací prvky CRichEditCtrl  
  
 Příklad použití ovládacího prvku RichEdit v aplikaci MFC, najdete v článku [WORDPAD](../../visual-cpp-samples.md) ukázkové aplikace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="canpaste"></a>CRichEditCtrl::CanPaste  
 Určuje, pokud zadaný formát schránky vložit ovládací prvek RichEdit.  
  
```  
BOOL CanPaste(UINT nFormat = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nFormat`  
 Formát dat schránky pro dotaz. Tento parametr může být jeden z předdefinovaných formátů schránky nebo hodnoty vrácené [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud lze vložit formát schránky; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nFormat` 0, `CanPaste` se pokusí použít na libovolném formátu aktuálně ve schránce.  
  
 Další informace najdete v tématu [EM_CANPASTE](http://msdn.microsoft.com/library/windows/desktop/bb787993) zprávy a [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkce ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#1](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_1.cpp)]  
  
##  <a name="canredo"></a>CRichEditCtrl::CanRedo  
 Určuje, zda fronty opakování akce obsahuje všechny akce.  
  
```  
BOOL CanRedo() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud obsahuje fronty opakování akce, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zjistit název operací ve frontě opakování, volejte [CRichEditCtrl::GetRedoName](#getredoname). Chcete-li znovu provést poslední operaci vrácení zpět, volejte [vrátit](#redo).  
  
 Další informace najdete v tématu [EM_CANREDO](http://msdn.microsoft.com/library/windows/desktop/bb787995) ve Windows SDK.  
  
##  <a name="canundo"></a>CRichEditCtrl::CanUndo  
 Určuje, pokud poslední operace úprav mohou být vráceny zpět.  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud poslední operace upravování můžete odvolat voláním [vrátit zpět](#undo) – členská funkce; 0, pokud ho nelze vrátit zpět.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#2](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_2.cpp)]  
  
##  <a name="charfrompos"></a>CRichEditCtrl::CharFromPos  
 Načte informace o znak, od bodu je určena parametrem `pt`.  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt obsahující souřadnice Zadaný bod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index počítaný od nuly znak znaku nejbližší Zadaný bod. Pokud se zadaný bod je nad rámec jeho poslední znak v ovládacím prvku, návratová hodnota označuje poslední znak v ovládacím prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce pracuje s ovládacího prvku RichEdit. Chcete-li získat informace pro ovládací prvek úprav, volejte [CEdit::CharFromPos](../../mfc/reference/cedit-class.md#charfrompos).  
  
 Další informace najdete v tématu [EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) ve Windows SDK.  
  
##  <a name="clear"></a>CRichEditCtrl::Clear  
 Odstraní (vymaže) aktuální výběr (pokud existuje) v bohaté ovládacích prvků pro úpravy.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Odstranění provádí **zrušte** můžete odvolat voláním [vrátit zpět](#undo) – členská funkce.  
  
 Chcete-li odstranit aktuální výběr a umístit odstraněné obsah do schránky, zavolejte [Vyjmout](#cut) – členská funkce.  
  
 Další informace najdete v tématu [WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#3](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_3.cpp)]  
  
##  <a name="copy"></a>CRichEditCtrl::Copy  
 Zkopíruje aktuální výběr (pokud existuje) v ovládacím prvku RichEdit do schránky.  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#4](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_4.cpp)]  
  
##  <a name="create"></a>CRichEditCtrl::Create  
 Vytvoří ovládacího prvku RichEdit Windows a přidruží ji to `CRichEditCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládací prvek upravit. Použít kombinaci styly oken uvedené v **poznámky** části níže, a [upravit styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775464), které jsou popsány v sadě Windows SDK.  
  
 `rect`  
 Určuje velikost a umístění textové pole. Může být [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura.  
  
 `pParentWnd`  
 Určuje textové pole nadřazeného okna (často [CDialog](../../mfc/reference/cdialog-class.md)). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládací prvek upravit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného; inicializace jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CRichEditCtrl` objektu ve dvou krocích. Nejprve volání [CRichEditCtrl](#cricheditctrl) konstruktor, pak zavolají **vytvořit**, který vytvoří ovládacího prvku úprav Windows a připojí jej k `CRichEditCtrl` objekt.  
  
 Když vytvoříte pomocí této funkce ovládacího prvku RichEdit, je nutné nejdřív načíst potřebné knihovny běžných ovládacích prvků. Chcete-li načíst knihovnu, zavolejte funkci globální [afxinitrichedit –](application-information-and-management.md#afxinitrichedit), která zase inicializuje knihovny běžných ovládacích prvků. Je třeba volat `AfxInitRichEdit` jen jednou v procesu.  
  
 Když **vytvořit** provede, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), a [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy pro ovládací prvek upravit.  
  
 Tyto zprávy jsou zpracovávány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Rozšíření zpracování zpráv výchozí, odvození třídy z `CRichEditCtrl`, přidejte mapy zpráv do nové třídy a přepsat výše členské funkce obslužné rutiny zpráv. Přepsání `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na ovládací prvek upravit.  
  
- **Ws_child –** vždy.  
  
- **Ws_visible –** obvykle.  
  
- **Ws_disabled –** zřídka.  
  
- **Ws_group –** k seskupování ovládacích prvků.  
  
- **Ws_tabstop –** zahrnout ovládacích prvků pro úpravy v pořadí, dají se procházet tabulátorem.  
  
 Další informace o styly oken najdete v tématu [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#5](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_5.cpp)]  
  
##  <a name="createex"></a>CRichEditCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CRichEditCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje styl ovládací prvek upravit. Použít kombinaci styly oken uvedené v **poznámky** části [vytvořit](#create) a [upravit styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775464), které jsou popsány v sadě Windows SDK.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo **vytvořit** použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="cricheditctrl"></a>CRichEditCtrl::CRichEditCtrl  
 Vytvoří `CRichEditCtrl` objektu.  
  
```  
CRichEditCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [vytvořit](#create) vytvořit Windows bohaté ovládacích prvků pro úpravy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#6](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_6.cpp)]  
  
##  <a name="cut"></a>CRichEditCtrl::Cut  
 Odstranit (kusy) aktuální výběr (pokud existuje) v bohaté ovládacích prvků pro úpravy a zkopíruje odstraněný text do schránky.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Poznámky  
 Odstranění provádí **Vyjmout** můžete odvolat voláním [vrátit zpět](#undo) – členská funkce.  
  
 Chcete-li odstranit aktuální výběr bez umístění odstraněný text do schránky, zavolejte [zrušte](#clear) – členská funkce.  
  
 Další informace najdete v tématu [WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#7](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_7.cpp)]  
  
##  <a name="displayband"></a>CRichEditCtrl::DisplayBand  
 Zobrazí část obsah ovládacího prvku RichEdit (text a OLE – položky), jako dříve formátován pomocí [FormatRange](#formatrange).  
  
```  
BOOL DisplayBand(LPRECT pDisplayRect);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisplayRect`  
 Ukazatel na [Rect –](../../mfc/reference/rect-structure1.md) nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) určující oblasti zařízení k zobrazení textu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li zobrazení formátovaný text úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Text a OLE – položky jsou oříznuto oblasti určeného ukazatele `pDisplayRect`.  
  
 Další informace najdete v tématu [EM_DISPLAYBAND](http://msdn.microsoft.com/library/windows/desktop/bb787997) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditCtrl::FormatRange](#formatrange).  
  
##  <a name="emptyundobuffer"></a>CRichEditCtrl::EmptyUndoBuffer  
 Obnoví příznak zpět tohoto ovládacího prvku RichEdit (Vymazat).  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek bude nyní nelze vrátit zpět poslední operace úprav. Příznak vrácení zpět je nastaven při každém operace v rámci prvku RichEdit mohou být vráceny zpět.  
  
 Příznak vrácení zpět je automaticky vymazán vždy, když zavoláte [CWnd](../../mfc/reference/cwnd-class.md) – členská funkce [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
 Další informace najdete v tématu [EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#8](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_8.cpp)]  
  
##  <a name="findtext"></a>CRichEditCtrl::FindText  
 Vyhledá text v rámci prvku RichEdit.  
  
```  
long FindText(
    DWORD dwFlags,  
    FINDTEXTEX* pFindText) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Seznam možných hodnot najdete v tématu `wParam` v [EM_FINDTEXTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788011) ve Windows SDK.  
  
 *pFindText*  
 Ukazatel [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) struktury poskytnutí parametrů pro vyhledání a vrácení rozsahu, kde byla nalezena shoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice znaku nule další shody; -1, pokud nejsou žádné shody.  
  
### <a name="remarks"></a>Poznámky  
 Můžete hledat buď nahoru nebo dolů podle nastavení v parametrech správné rozsah [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktury v rámci **FINDTEXTEX** struktury.  
  
 Další informace najdete v tématu [EM_FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb788011) zprávy a [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#9](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_9.cpp)]  
  
##  <a name="findwordbreak"></a>CRichEditCtrl::FindWordBreak  
 Vyhledá další dělení textu před nebo po pozice určeného `nStart`.  
  
```  
DWORD FindWordBreak(
    UINT nCode,  
    DWORD nStart) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nCode`  
 Určuje akci provést. Seznamu možných hodnot, naleznete v popisu parametru `code` v **EM_FINDWORDBREAK** ve Windows SDK.  
  
 `nStart`  
 Pozice znaku nule ze kterého má začít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Na základě parametru `nCode`. Další informace najdete v tématu [EM_FINDWORDBREAK](http://msdn.microsoft.com/library/windows/desktop/bb788018) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce slouží k načtení informací o znak na dané pozici.  
  
##  <a name="formatrange"></a>CRichEditCtrl::FormatRange  
 Formátuje rozsah textu v ovládacím prvku RichEdit pro konkrétní zařízení.  
  
```  
long FormatRange(
    FORMATRANGE* pfr,  
    BOOL bDisplay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *PFR*  
 Ukazatel [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) struktura, která obsahuje informace o zařízení výstup. **NULL** označuje, že může být uvolněno informace uložené v mezipaměti v rámci prvku RichEdit.  
  
 *bDisplay*  
 Označuje, pokud má být vykreslen text. Pokud **FALSE**, právě měří text.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index poslední znak, který nejlépe odpovídá v oblasti plus jedna.  
  
### <a name="remarks"></a>Poznámky  
 Toto volání obvykle následuje volání [DisplayBand](#displayband).  
  
 Další informace najdete v tématu [EM_FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb788020) zprávy a [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#10](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_10.cpp)]  
  
##  <a name="getcharpos"></a>CRichEditCtrl::GetCharPos  
 Načte pozici (levého horního rohu) daného znaku v rámci to `CRichEditCtrl` objektu.  
  
```  
CPoint GetCharPos(long lChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lChar`  
 Index nule znaku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění levého horního rohu určeného znaku `lChar`.  
  
### <a name="remarks"></a>Poznámky  
 Znak, který je zadán tím, že její hodnota index o základu 0. Pokud `lChar` je větší než index poslední znak v tomto `CRichEditCtrl` objektu návratovou hodnotu určuje souřadnice znak na pozici právě za jeho poslední znak v tomto `CRichEditCtrl` objektu.  
  
 Další informace najdete v tématu [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) ve Windows SDK.  
  
##  <a name="getdefaultcharformat"></a>CRichEditCtrl::GetDefaultCharFormat  
 Získá výchozí znakovou atributy tohoto formátování `CRichEditCtrl` objektu.  
  
```  
DWORD GetDefaultCharFormat(CHARFORMAT& cf) const;  DWORD GetDefaultCharFormat(CHARFORMAT2& cf) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 V první verzi, odkazy **CHARFORMAT** struktura, která uchovává výchozí znakovou atributů formátování.  
  
 V druhé verzi ukazatel na **CHARFORMAT2** struktura, což je rozšíření bohaté upravit 2.0 na **CHARFORMAT** struktura, která uchovává výchozí znakovou atributů formátování.  
  
### <a name="return-value"></a>Návratová hodnota  
 **DwMask** data členem `cf`. Není zadán výchozí znakovou atributů formátování.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu **EM_GETCHARFORMAT** zprávy a **CHARFORMAT** a **CHARFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [SetDefaultCharFormat](#setdefaultcharformat).  
  
##  <a name="geteventmask"></a>CRichEditCtrl::GetEventMask  
 Získá maska události pro tento `CRichEditCtrl` objektu.  
  
```  
long GetEventMask() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maska události pro tento `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Maska události Určuje, které zprávy oznámení `CRichEditCtrl` objekt odešle do jeho nadřazeného okna.  
  
 Další informace najdete v tématu [EM_GETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb788032) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditCtrl::SetEventMask](#seteventmask).  
  
##  <a name="getfirstvisibleline"></a>CRichEditCtrl::GetFirstVisibleLine  
 Určuje nejhornější viditelné řádku v tomto `CRichEditCtrl` objektu.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index řádku nejvyšší viditelné v tomto nule `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#11](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_11.cpp)]  
  
##  <a name="getiricheditole"></a>CRichEditCtrl::GetIRichEditOle  
 Přistupuje **IRichEditOle** rozhraní pro toto `CRichEditCtrl` objektu.  
  
```  
IRichEditOle* GetIRichEditOle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) rozhraní, které je možné získat přístup k této `CRichEditCtrl` objektu OLE funkce; **NULL** Pokud rozhraní není přístupná.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí tohoto rozhraní pro přístup k: `CRichEditCtrl` funkce OLE objektu.  
  
 Další informace najdete v tématu [EM_GETOLEINTERFACE](http://msdn.microsoft.com/library/windows/desktop/bb788041) zprávy a [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) rozhraní v sadě Windows SDK.  
  
##  <a name="getlimittext"></a>CRichEditCtrl::GetLimitText  
 Získá limit text pro tento `CRichEditCtrl` objektu.  
  
```  
long GetLimitText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální text limit, v bajtech pro tento `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Limit textu je maximální objem textu v bajtech prvku RichEdit může přijmout.  
  
 Další informace najdete v tématu [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#12](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_12.cpp)]  
  
##  <a name="getline"></a>CRichEditCtrl::GetLine  
 Načte řádku textu z tohoto `CRichEditCtrl` objektu.  
  
```  
int GetLine(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
int GetLine(
    int nIndex,  
    LPTSTR lpszBuffer,  
    int nMaxLength) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index řádku k načtení nule.  
  
 `lpszBuffer`  
 Odkazuje na vyrovnávací paměť pro příjem text. První slovo vyrovnávací paměti, musíte zadat maximální počet bajtů, které je možné zkopírovat do vyrovnávací paměti.  
  
 `nMaxLength`  
 Maximální počet znaků, které je možné zkopírovat do `lpszBuffer`. O druhou podobu `GetLine` umístí tuto hodnotu do první slovo vyrovnávací paměti určeného `lpszBuffer`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků, které jsou zkopírovány do `lpszBuffer`.  
  
### <a name="remarks"></a>Poznámky  
 Zkopírovaného řádku neobsahuje ukončovací znak hodnoty null.  
  
> [!NOTE]
>  Vzhledem k tomu, že první slovo vyrovnávací paměti ukládá počet znaků, které se mají zkopírovat, ujistěte se, že vaše vyrovnávací paměť je minimálně 4 bajtů.  
  
 Další informace najdete v tématu [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>CRichEditCtrl::GetLineCount  
 Získá počet řádků v `CRichEditCtrl` objektu.  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků v tomto `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#13](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_13.cpp)]  
  
##  <a name="getmodify"></a>CRichEditCtrl::GetModify  
 Určuje, zda obsah tohoto `CRichEditCtrl` objekt byly upraveny.  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě text v tomto `CRichEditCtrl` objektu se změnila; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Windows udržuje interní příznak označující, zda obsah ovládacího prvku RichEdit se změnily. Tento příznak není zaškrtnuto, když je poprvé vytvořen textové pole a lze také vymazat voláním [SetModify](#setmodify) – členská funkce.  
  
 Další informace najdete v tématu [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#14](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_14.cpp)]  
  
##  <a name="getoptions"></a>CRichEditCtrl::GetOptions  
 Načte aktuálně nastavené pro ovládací prvek RichEdit možnosti.  
  
```  
UINT GetOptions() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kombinace aktuální hodnoty příznak možnosti. Seznam těchto hodnot, najdete v článku *fOptions* parametr ve [EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getparaformat"></a>CRichEditCtrl::GetParaFormat  
 Získá formátování odstavce atributy aktuální výběr.  
  
```  
DWORD GetParaFormat(PARAFORMAT& pf) const;  DWORD GetParaFormat(PARAFORMAT2& pf) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pf`  
 V první verzi, odkazy [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura k uchování atributy aktuálního výběru formátování odstavce.  
  
 V druhé verzi ukazatel na [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktura, což je rozšíření bohaté upravit 2.0 na **PARAFORMAT** struktura, která uchovává výchozí znakovou atributů formátování.  
  
### <a name="return-value"></a>Návratová hodnota  
 **DwMask** data členem `pf`. Určuje atributy, které jsou konzistentní v rámci aktuální výběr formátování odstavce.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vybrána více než jeden odstavec, `pf` obdrží atributy vybrané odstavce. Návratová hodnota Určuje atributy, které jsou konzistentní v rámci výběr.  
  
 Další informace najdete v tématu [EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182) zprávy a **PARAFORMAT** a **PARAFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditCtrl::SetParaFormat](#setparaformat).  
  
##  <a name="getpunctuation"></a>CRichEditCtrl::GetPunctuation  
 Získá aktuální znaky interpunkce v ovládacím prvku RichEdit.  
  
```  
BOOL GetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `fType`  
 Příznak typ interpunkční znaménka, jak je popsáno v `fType` parametr [EM_GETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774184) ve Windows SDK.  
  
 `lpPunc`  
 Ukazatel [INTERPUNKCE](http://msdn.microsoft.com/library/windows/desktop/bb787944) struktury, jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud operace byla úspěšná, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je k dispozici pouze v asijské jazyky verzích operačního systému.  
  
##  <a name="getrect"></a>CRichEditCtrl::GetRect  
 Načte formátování rámeček pro tento `CRichEditCtrl` objektu.  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo ukazatel na [Rect –](../../mfc/reference/rect-structure1.md) přijímat formátování obdélník `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Formátování rámeček je ohraničující obdélník text. Tato hodnota je nezávislé na velikost `CRichEditCtrl` objektu.  
  
 Další informace najdete v tématu [EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [LimitText](#limittext).  
  
##  <a name="getredoname"></a>CRichEditCtrl::GetRedoName  
 Načte typ další dostupné akce ve frontě znovu, pokud existuje.  
  
```  
UNDONAMEID GetRedoName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `GetRedoName` vrátí [UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365) typ výčtu označující typ další akce ve frontě opakování ovládacího prvku. Pokud je znovu fronta prázdná, nebo pokud není opakování akce ve frontě neznámého typu, `GetRedoName` vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Typy akcí, které můžete odvolat nebo znovu patří zadáte, odstranění, přetáhněte, vyjmutí a operace vložení. Tato informace může být užitečné pro aplikace, které poskytují rozšířené uživatelské rozhraní pro operace zpět a znovu, např. rozevírací seznam redoable akcí.  
  
##  <a name="getsel"></a>CRichEditCtrl::GetSel  
 Načte rozsah aktuální výběr v tomto `CRichEditCtrl` objektu.  
  
```  
void GetSel(CHARRANGE& cr) const;  
  
void GetSel(
    long& nStartChar,  
    long& nEndChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `cr`  
 Odkaz na [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura přijímat hranice aktuální výběr.  
  
 `nStartChar`  
 Index prvního znaku v aktuálním výběru nule.  
  
 `nEndChar`  
 Index počítaný od nuly poslední znak v aktuálním výběru.  
  
### <a name="remarks"></a>Poznámky  
 Dvě formy této funkce zadejte alternativní způsoby, jak získat hranice pro výběr. Stručný popis těchto formulářů podle:  
  
- **GetSel (** `cr` **)** používá tento formulář **CHARRANGE** struktury s jeho **cpMin** a **cpMax** členy vrátit hranice.  
  
- **GetSel (** `nStartChar` **,** `nEndChar` **)** tento formulář vrátí hranice v parametrech `nStartChar` a `nEndChar`.  
  
 Výběr zahrnuje vše, pokud začátku ( **cpMin** nebo `nStartChar`) je 0 a end ( **cpMax** nebo `nEndChar`) je - 1.  
  
 Další informace najdete v tématu [EM_EXGETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788001) zprávy a [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#15](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_15.cpp)]  
  
##  <a name="getselectioncharformat"></a>CRichEditCtrl::GetSelectionCharFormat  
 Získá znak atributy aktuálního výběru formátování.  
  
```  
DWORD GetSelectionCharFormat(CHARFORMAT& cf) const;  DWORD GetSelectionCharFormat(CHARFORMAT2& cf) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 V první verzi, odkazy [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura přijímat formátování atributy aktuální výběr znaků.  
  
 V druhé verzi ukazatel na [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura, což je rozšíření bohaté upravit 2.0 na **CHARFORMAT** struktura přijímat formátování atributy aktuální výběr znaků.  
  
### <a name="return-value"></a>Návratová hodnota  
 **DwMask** data členem `cf`. Určuje formátování atributy, které jsou konzistentní v rámci aktuální výběr znaků.  
  
### <a name="remarks"></a>Poznámky  
 `cf` Parametr obdrží atributy první znak v aktuálním výběru. Návratová hodnota Určuje atributy, které jsou konzistentní v rámci výběr.  
  
 Další informace najdete v tématu [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) zprávy a **CHARFORMAT** a **CHARFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [SetSelectionCharFormat](#setselectioncharformat).  
  
##  <a name="getselectiontype"></a>CRichEditCtrl::GetSelectionType  
 Určuje typ výběru v tomto `CRichEditCtrl` objektu.  
  
```  
WORD GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Příznaky udávající obsah aktuální výběr. Kombinace následující příznaky:  
  
- `SEL_EMPTY`Označuje, že neexistuje žádný aktuální výběr.  
  
- `SEL_TEXT`Určuje, že aktuální výběr obsahuje text.  
  
- `SEL_OBJECT`Určuje, že aktuální výběr obsahuje alespoň jednu položku OLE.  
  
- `SEL_MULTICHAR`Určuje, že aktuální výběr obsahuje více než jeden znak textu.  
  
- `SEL_MULTIOBJECT`Určuje, že aktuální výběr obsahuje více než jeden objekt OLE.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_SELECTIONTYPE](http://msdn.microsoft.com/library/windows/desktop/bb774223) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#16](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_16.cpp)]  
  
##  <a name="getseltext"></a>CRichEditCtrl::GetSelText  
 Načte text z aktuálního výběru v tomto `CRichEditCtrl` objektu.  
  
```  
long GetSelText(LPSTR lpBuf) const;  CString GetSelText() const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel na vyrovnávací paměť pro příjem text v aktuálním výběru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Závisí na formuláři:  
  
- **GetSelText (** `lpBuf` **)** počet znaků, které jsou zkopírovány do `lpBuf`, není včetně ukončení hodnotu null.  
  
- **(GetSelText)** řetězec obsahující aktuální výběr.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte první formulář **GetSelText (** `lpBuf` **)**, ujistěte se, že vyrovnávací paměť je dostatečně velký pro text se zobrazí. Volání [GetSel](#getsel) můžete určit počet znaků v aktuálním výběru.  
  
 Další informace najdete v tématu [EM_GETSELTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774190) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CRichEditCtrl::GetSelectionType](#getselectiontype).  
  
##  <a name="gettextlength"></a>CRichEditCtrl::GetTextLength  
 Načte délka textu v znaků v tomto `CRichEditCtrl` objektu, včetně není ukončující znak hodnoty null.  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka textu v tomto `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [WM_GETTEXTLENGTH](http://msdn.microsoft.com/library/windows/desktop/ms632628) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#17](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_17.cpp)]  
  
##  <a name="gettextlengthex"></a>CRichEditCtrl::GetTextLengthEx  
 Vypočítá délku textu v ovládacím prvku RichEdit.  
  
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
 `GetTextLengthEx`Další způsoby určování délka textu. Podporuje funkci bohaté upravit 2.0. V tématu [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) v systému Windows SDKfor Další informace.  
  
##  <a name="gettextmode"></a>CRichEditCtrl::GetTextMode  
 Načte aktuální text režim a vrácení zpět úroveň ovládacího prvku RichEdit.  
  
```  
UINT GetTextMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Sadu bitové příznaky z [v textovém režimu](http://msdn.microsoft.com/library/windows/desktop/bb774364) typ výčtu, jak je popsáno v sadě Windows SDK. V příznacích označuje aktuální režim textové a vrátit zpět úroveň ovládacího prvku.  
  
##  <a name="gettextrange"></a>CRichEditCtrl::GetTextRange  
 Získá zadaný rozsah znaků.  
  
```  
int GetTextRange(
    int nFirst,  
    int nLast,  
    CString& refString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nFirst`  
 Znak na pozici indexu bezprostředně před první znak v rozsahu.  
  
 `nLast`  
 Pozice znaku hned za jeho poslední znak v rozsahu.  
  
 `refString`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který se zobrazí text.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků, kopírovat, není včetně ukončující znak hodnoty null.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETTEXTRANGE](http://msdn.microsoft.com/library/windows/desktop/bb774199) ve Windows SDK.  
  
 `GetTextRange`podporuje funkci bohaté upravit 2.0. V tématu [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) v systému Windows SDKfor Další informace.  
  
##  <a name="getundoname"></a>CRichEditCtrl::GetUndoName  
 Načte typ další dostupné akce ve frontě vrácení zpět, pokud existuje.  
  
```  
UNDONAMEID GetUndoName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je akce vrácení zpět do ovládacího prvku vrácení zpět fronty, `GetUndoName` vrátí [UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365) typ výčtu označující typ další akce ve frontě. Pokud vrácení zpět fronty je prázdný, nebo pokud je akce vrácení zpět ve frontě neznámého typu, `GetUndoName` vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Typy akcí, které můžete odvolat nebo znovu patří zadáte, odstranění, přetáhněte, vyjmutí a operace vložení. Tato informace může být užitečné pro aplikace, které poskytují rozšířené uživatelské rozhraní pro operace zpět a znovu, např. rozevírací seznam akcí, které mohou být vráceny zpět.  
  
##  <a name="getwordwrapmode"></a>CRichEditCtrl::GetWordWrapMode  
 Načte aktuální zalamování řádků a možnosti v aplikaci word ukončování řádků pro ovládací prvek RichEdit.  
  
```  
UINT GetWordWrapMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zalamování řádků a možnosti dělení slov. Tyto možnosti jsou popsané v [EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je k dispozici pouze pro verze asijské jazyky operačního systému.  
  
##  <a name="hideselection"></a>CRichEditCtrl::HideSelection  
 Změní viditelnost výběru.  
  
```  
void HideSelection(
    BOOL bHide,  
    BOOL bPerm);
```  
  
### <a name="parameters"></a>Parametry  
 `bHide`  
 Určuje, pokud by měl výběr zobrazen nebo skryt, **TRUE** Skrýt výběr.  
  
 `bPerm`  
 Určuje, pokud má být tato změna v viditelnost pro výběr trvalé.  
  
### <a name="remarks"></a>Poznámky  
 Když `bPerm` je **TRUE**, změní `ECO_NOHIDESEL` možnost pro tento `CRichEditCtrl` objektu. Stručný popis této možnosti najdete v tématu [SetOptions](#setoptions). Tato funkce slouží k nastavení všech možností pro toto `CRichEditCtrl` objektu.  
  
 Další informace najdete v tématu [EM_HIDESELECTION](http://msdn.microsoft.com/library/windows/desktop/bb774210) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#18](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_18.cpp)]  
  
##  <a name="limittext"></a>CRichEditCtrl::LimitText  
 Omezení délky textu, který může uživatel zadat do ovládacího prvku úprav.  
  
```  
void LimitText(long nChars = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nChars`  
 Určuje text, který může uživatel zadat délku (v bajtech). Pokud má parametr hodnotu 0 (výchozí hodnota), délka textu je nastavená na 64 kB.  
  
### <a name="remarks"></a>Poznámky  
 Změna textu limit omezuje pouze text, který může uživatel zadat. Je již nemá žádný vliv na jakýkoli text v textovém poli ani neovlivní délku textu zkopírovat do ovládacího prvku upravit podle [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) – členská funkce v `CWnd`. Pokud aplikace používá `SetWindowText` umístit další text do ovládacího prvku úprav, než je zadaný ve volání funkce `LimitText`, uživatel může odstraní všechny textu v rámci ovládací prvek upravit. Text limit však bude brání uživateli, nahradí existující text novým textem, pokud odstraňování aktuální výběr způsobí, že text, který má klesnou pod text limit.  
  
> [!NOTE]
>  Pro text limit jednotlivých položek OLE počítá jako jeden znak.  
  
 Další informace najdete v tématu [EM_EXLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788003) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#19](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_19.cpp)]  
  
##  <a name="linefromchar"></a>CRichEditCtrl::LineFromChar  
 Načte číslo řádku řádek, který obsahuje index zadaný znak.  
  
```  
long LineFromChar(long nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje hodnotu index o základu 0 pro požadovaný znak v textu ovládacích prvků pro úpravy, nebo obsahuje hodnotu -1. Pokud `nIndex` je -1, určuje aktuálního řádku, tedy řádek, který obsahuje pomocí kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků od nuly řádek obsahující znakový index určeného `nIndex`. Pokud `nIndex` je -1, vrátí se číslo řádku, který obsahuje první znak výběru. Pokud není nic vybráno, bude vrácena aktuální číslo řádku.  
  
### <a name="remarks"></a>Poznámky  
 Znakový index je počet znaků od začátku prvku RichEdit. Pro počítání znaků, položku OLE se počítá jako jeden znak.  
  
 Další informace najdete v tématu [EM_EXLINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb788005) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#20](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_20.cpp)]  
  
##  <a name="lineindex"></a>CRichEditCtrl::LineIndex  
 Načte znakový index řádku v rámci to `CRichEditCtrl` objektu.  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nLine`  
 Obsahuje hodnotu indexu pro požadovaný řádek v textu ovládacích prvků pro úpravy nebo -1. Pokud `nLine` je -1, určuje aktuálního řádku, tedy řádek, který obsahuje pomocí kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Znakový index řádku zadaný v `nLine` nebo -1, pokud je zadané číslo řádku větší a počet řádků v ovládacím prvku upravit.  
  
### <a name="remarks"></a>Poznámky  
 Znakový index je počet znaků od začátku prvku RichEdit, který má zadaný řádek.  
  
 Další informace najdete v tématu [EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#21](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_21.cpp)]  
  
##  <a name="linelength"></a>CRichEditCtrl::LineLength  
 Načte délka řádku v ovládacím prvku RichEdit.  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nLine`  
 Určuje znakový index znaku v řádku, jehož délka má být načtena. Pokud tento parametr hodnotu -1, se vrátí délku aktuálního řádku (řádek, který obsahuje vsuvka), není včetně Délka libovolného vybraný text v řádku. Když `LineLength` je volána pro jednořádkové textové pole, je tento parametr ignorován.  
  
### <a name="return-value"></a>Návratová hodnota  
 Když `LineLength` je volána pro ovládací prvek upravit více řádků, je vrácenou hodnotu délka (v `TCHAR`) řádku určeného `nLine`.  Nebude obsahovat znak návratu na konec řádku. Když `LineLength` je volána pro jednořádkové textové pole, je vrácenou hodnotu délka (v `TCHAR`) textu v textovém poli. Pokud je vyšší než počet znaků v ovládacím prvku využívat, je vrácenou hodnotu nula.
  
### <a name="remarks"></a>Poznámky  
 Použití [LineIndex](#lineindex) – členská funkce načíst znakový index pro daný řádek číslo v rámci to `CRichEditCtrl` objektu.  
  
 Další informace najdete v tématu [EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [LineIndex](#lineindex).  
  
##  <a name="linescroll"></a>CRichEditCtrl::LineScroll  
 Posune text ovládacích prvků pro úpravy více řádků.  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nLines`  
 Určuje počet řádků posunu svisle.  
  
 `nChars`  
 Určuje počet pozic znak, který má vodorovný posun. Tato hodnota je ignorována, pokud má prvku RichEdit buď **es_right –** nebo **es_center –** stylu. [Styly pro úpravy](../../mfc/reference/styles-used-by-mfc.md#edit-styles) jsou určené v [vytvořit](#create).  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek upravit neposouvá svisle za poslední řádek textu v textovém poli. Pokud aktuální řádek plus počet řádků určeného `nLines` větší než celkový počet řádků v ovládacím prvku úprav, hodnota se nastaví tak, aby poslední řádek ovládacích prvků pro úpravy je přechod na horní části okna textové pole.  
  
 `LineScroll`slouží k vodorovnému posouvání za jeho poslední znak kterýkoli řádek.  
  
 Další informace najdete v tématu [EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetFirstVisibleLine](#getfirstvisibleline).  
  
##  <a name="paste"></a>CRichEditCtrl::Paste  
 Vloží data ze schránky do `CRichEditCtrl` na pozici kurzoru, umístění pomocí kurzoru.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Poznámky  
 Pouze v případě, že schránky obsahuje data v rozpoznaném formátu, vloží se data.  
  
 Další informace najdete v tématu [WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#22](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_22.cpp)]  
  
##  <a name="pastespecial"></a>CRichEditCtrl::PasteSpecial  
 Vloží data v konkrétním formátu schránky do této `CRichEditCtrl` objektu.  
  
```  
void PasteSpecial(
    UINT nClipFormat,  
    DWORD dvAspect = 0,  
    HMETAFILE hMF = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *nClipFormat*  
 Formát schránky vložit do této `CRichEditCtrl` objektu.  
  
 *dvAspect*  
 Aspekt zařízení pro data, která mají být načtena ze schránky.  
  
 *hMF*  
 Popisovač metafile obsahující ikony zobrazení objekt, který chcete vložit.  
  
### <a name="remarks"></a>Poznámky  
 Nové materiály vložen na pozici kurzoru, umístění pomocí kurzoru.  
  
 Další informace najdete v tématu [EM_PASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/bb774214) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#23](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_23.cpp)]  
  
##  <a name="posfromchar"></a>CRichEditCtrl::PosFromChar  
 Načte souřadnice oblasti klienta je zadaný znak v ovládacím prvku upravit.  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nChar`  
 Index založený na nule znaku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice znaku, (x, y). Pro ovládací prvek upravit jeden řádek souřadnici y je vždy nula.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) ve Windows SDK.  
  
##  <a name="redo"></a>CRichEditCtrl::Redo  
 Znovu provede další akce ve frontě opakování ovládacího prvku.  
  
```  
BOOL Redo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_REDO](http://msdn.microsoft.com/library/windows/desktop/bb774218) ve Windows SDK.  
  
##  <a name="replacesel"></a>CRichEditCtrl::ReplaceSel  
 Nahradí aktuální výběr v tomto `CRichEditCtrl` objekt se zadaným textem.  
  
```  
void ReplaceSel(
    LPCTSTR lpszNewText,  
    BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewText`  
 Ukazatel na obsahující text, kterým řetězce ukončené hodnotou null.  
  
 `bCanUndo`  
 Chcete-li určit, že tato funkce může být vrátit zpět, nastavte hodnotu tohoto parametru k **TRUE**. Výchozí hodnota je **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li nahradit veškerého textu v tomto `CRichEditCtrl` objektu, použijte [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
 Pokud není žádná aktuální výběr, text, kterým je vložen na pozici kurzoru, který je aktuální umístění pomocí kurzoru.  
  
 Tato funkce bude formát vložený text s existující formátování znaků. Při nahrazování celý rozsah text (voláním `SetSel`(0, -1) před voláním `ReplaceSel`), je konci znak odstavce, který uchovává v předchozím odstavci formátování, které v zdědí nově vložený text.  
  
 Další informace najdete v tématu [EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [LineIndex](#lineindex).  
  
##  <a name="requestresize"></a>CRichEditCtrl::RequestResize  
 Vynutí to `CRichEditCtrl` objekt, který chcete odeslat **EN_REQUESTRESIZE** zpráv s oznámením do jeho nadřazeného okna.  
  
```  
void RequestResize();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná během [CWnd::OnSize](../../mfc/reference/cwnd-class.md#onsize) zpracování neomezené `CRichEditCtrl` objektu.  
  
 Další informace najdete v tématu [EM_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb774220) zprávy a **ovládací prvky pro úpravy neomezené bohaté** části [o bohaté upravit ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb787873) ve Windows SDK.  
  
##  <a name="setautourldetect"></a>CRichEditCtrl::SetAutoURLDetect  
 Nastaví ovládacího prvku RichEdit automaticky zjišťovat adresu URL.  
  
```  
BOOL SetAutoURLDetect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Určuje, zda je ovládací prvek nastaven automaticky zjišťovat adresu URL. Pokud **TRUE**, je povoleno. Pokud **FALSE**, je zakázaná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud úspěšný, jinak nenulové hodnoty. Například zpráva může selhat z důvodu nedostatku paměti.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je povoleno, prvku RichEdit vyhledá text k určení, jestli odpovídá standardní formát adresy URL. Seznam těchto formátech adres URL, najdete v části [EM_AUTOURLDETECT](http://msdn.microsoft.com/library/windows/desktop/bb787991) ve Windows SDK.  
  
> [!NOTE]
>  Nenastavujte `SetAutoURLDetect` k **TRUE** pokud používá ovládacích prvků pro úpravy **CFE_LINK** vliv text než adresy URL. `SetAutoURLDetect`Umožňuje tento efekt pro adresy URL a zakáže pro všechny další text. V tématu [EN_LINK](http://msdn.microsoft.com/library/windows/desktop/bb787970) Další informace o **CFE_LINK** vliv.  
  
##  <a name="setbackgroundcolor"></a>CRichEditCtrl::SetBackgroundColor  
 Nastaví barvu pozadí pro tento `CRichEditCtrl` objektu.  
  
```  
COLORREF SetBackgroundColor(
    BOOL bSysColor,  
    COLORREF cr);
```  
  
### <a name="parameters"></a>Parametry  
 `bSysColor`  
 Označuje, pokud barvu pozadí je třeba nastavit na hodnotu systému. Pokud je tato hodnota **TRUE**, `cr` je ignorována.  
  
 `cr`  
 Barva pozadí požadovaný. Použít pouze v případě `bSysColor` je **FALSE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí barva pozadí pro tento `CRichEditCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Barva pozadí lze nastavit na hodnotu systému nebo na zadané [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu.  
  
 Další informace najdete v tématu [EM_SETBKGNDCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774228) zprávy a [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#24](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_24.cpp)]  
  
##  <a name="setdefaultcharformat"></a>CRichEditCtrl::SetDefaultCharFormat  
 Nastaví znak, formátování atributy pro nový text v tomto `CRichEditCtrl` objektu.  
  
```  
BOOL SetDefaultCharFormat(CHARFORMAT& cf);  
BOOL SetDefaultCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 V první verzi, odkazy [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura obsahující nové výchozí formátování atributy.  
  
 V druhé verzi ukazatel na [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura, což je rozšíření bohaté upravit 2.0 na **CHARFORMAT** struktura, obsahující znak výchozí formátování atributy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pouze atributy určeného **dwMask** členem `cf` došlo ke změně pomocí této funkce.  
  
 Další informace najdete v tématu [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) zprávy a **CHARFORMAT** a **CHARFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#25](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_25.cpp)]  
  
##  <a name="seteventmask"></a>CRichEditCtrl::SetEventMask  
 Nastaví maska události pro tento `CRichEditCtrl` objektu.  
  
```  
DWORD SetEventMask(DWORD dwEventMask);
```  
  
### <a name="parameters"></a>Parametry  
 *dwEventMask*  
 Nové maska události pro tento `CRichEditCtrl` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí maska událostí.  
  
### <a name="remarks"></a>Poznámky  
 Maska události Určuje, které zprávy oznámení `CRichEditCtrl` objekt odešle do jeho nadřazeného okna.  
  
 Další informace najdete v tématu [EM_SETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb774238) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#26](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_26.cpp)]  
  
##  <a name="setmodify"></a>CRichEditCtrl::SetModify  
 Nastaví nebo vymaže příznak upravené pro ovládací prvek upravit.  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Hodnota **TRUE** byla změněna text a hodnota **FALSE** označuje je beze změny. Ve výchozím nastavení je upravený nastavený příznak.  
  
### <a name="remarks"></a>Poznámky  
 Příznak upravené označuje, zda byla změněna textu v rámci ovládací prvek upravit. Bude automaticky nastavena vždy, když uživatel změní text. Jeho hodnota se dá načíst pomocí [GetModify](#getmodify) – členská funkce.  
  
 Další informace najdete v tématu [EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetModify](#getmodify).  
  
##  <a name="setolecallback"></a>CRichEditCtrl::SetOLECallback  
 To dává `CRichEditCtrl` objektu **IRichEditOleCallback** objekt, který chcete používat pro přístup k prostředkům související s rozhraním OLE a informace.  
  
```  
BOOL SetOLECallback(IRichEditOleCallback* pCallback);
```  
  
### <a name="parameters"></a>Parametry  
 `pCallback`  
 Ukazatel na [IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308) objekt které tento `CRichEditCtrl` objekt se používá k udržení materiály související s rozhraním OLE a informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 To `CRichEditCtrl` bude volat objekt [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) se zvýší počet použití pro objekt COM určeného `pCallback`.  
  
 Další informace najdete v tématu [EM_SETOLECALLBACK](http://msdn.microsoft.com/library/windows/desktop/bb774252) zprávy a [IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308) rozhraní v sadě Windows SDK.  
  
##  <a name="setoptions"></a>CRichEditCtrl::SetOptions  
 Nastaví možnosti pro tento `CRichEditCtrl` objektu.  
  
```  
void SetOptions(
    WORD wOp,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 *wOp*  
 Určuje typ operace. Jedna z následujících hodnot:  
  
- `ECOOP_SET`Nastavit na uvedenými v `dwFlags`.  
  
- `ECOOP_OR`Aktuální možnosti sloučit s uvedenými v `dwFlags`.  
  
- `ECOOP_AND`Zachovat pouze aktuální možnosti, které jsou také určené `dwFlags`.  
  
- `ECOOP_XOR`Logicky exkluzivní OR aktuální možnosti s uvedenými v `dwFlags`.  
  
 `dwFlags`  
 Bohaté možnosti úprav. Příznak hodnoty jsou uvedené v oddílu Poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Možnosti může být kombinací následujícího:  
  
- `ECO_AUTOWORDSELECTION`Dvakrát klikněte na automatický výběr slova na.  
  
- `ECO_AUTOVSCROLL`Když uživatel zadá znak na konci řádku automaticky posune text doprava 10 znaky. Po stisknutí klávesy ENTER, ovládacího prvku posune veškerý text zpět na pozici nula.  
  
- `ECO_AUTOHSCROLL`Automaticky posune text jednu stránku po stisknutí klávesy ENTER na posledním řádku.  
  
- `ECO_NOHIDESEL`Neguje výchozí chování pro ovládací prvek upravit. Výchozí chování skryje výběr při řízení ztratí zaměření pro vstup a zobrazuje výběr zaměření pro vstup přijetí ovládacího prvku. Pokud zadáte `ECO_NOHIDESEL`, obrácený vybraný text, i v případě, že ovládací prvek nemá fokus.  
  
- `ECO_READONLY`Zabrání uživatelům zadání nebo úpravě textu v textovém poli.  
  
- `ECO_WANTRETURN`Určuje, že návrat vložit při stisknutí klávesy ENTER při zadávání textu do ovládacího prvku RichEdit více řádků v dialogovém okně. Pokud nezadáte tento styl, stisknutím klávesy ENTER odešle příkaz do nadřazeného okna pro ovládací prvek RichEdit, která napodobuje kliknutím na tlačítko výchozí nadřazeného okna (například na tlačítko OK v dialogovém okně). Tento styl nemá žádný vliv na jeden řádek ovládacích prvků pro úpravy.  
  
- `ECO_SAVESEL`Při deaktivaci ovládacího prvku se zachovají výběr. Standardně jsou vybrané celý obsah ovládacího prvku když získá fokus.  
  
- `ECO_VERTICAL`Kreslení textu a objekty ve svislém směru. K dispozici pro pouze asijské jazyky.  
  
 Další informace najdete v tématu [EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#27](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_27.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditCtrl::SetParaFormat  
 Nastaví atributy pro aktuální výběr v tomto formátování odstavce `CRichEditCtrl` objektu.  
  
```  
BOOL SetParaFormat(PARAFORMAT& pf);  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>Parametry  
 `pf`  
 V první verzi, odkazy [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) struktura obsahující nový výchozí bod atributy formátování.  
  
 V druhé verzi ukazatel na [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) struktura, což je rozšíření bohaté upravit 2.0 na **PARAFORMAT** struktura, která uchovává výchozí znakovou atributů formátování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pouze atributy určeného **dwMask** členem `pf` došlo ke změně pomocí této funkce.  
  
 Další informace najdete v tématu [EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276) zprávy a **PARAFORMAT** a **PARAFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#28](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_28.cpp)]  
  
##  <a name="setpunctuation"></a>CRichEditCtrl::SetPunctuation  
 Nastaví na řádek v ovládacím prvku RichEdit.  
  
```  
BOOL SetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc);
```  
  
### <a name="parameters"></a>Parametry  
 `fType`  
 Příznak interpunkce. Seznam možných hodnot najdete v tématu `fType` parametr pro [EM_SETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774278) ve Windows SDK.  
  
 `lpPunc`  
 Ukazatel [INTERPUNKCE](http://msdn.microsoft.com/library/windows/desktop/bb787944) struktury, jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je k dispozici pouze asijské jazyky verze operačního systému.  
  
##  <a name="setreadonly"></a>CRichEditCtrl::SetReadOnly  
 Změny `ECO_READONLY` možnost pro tento `CRichEditCtrl` objektu.  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bReadOnly`  
 Určuje, pokud `CRichEditCtrl` objektu by měla jen pro čtení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Stručný popis této možnosti najdete v tématu [SetOptions](#setoptions). Tato funkce slouží k nastavení všech možností pro toto `CRichEditCtrl` objektu.  
  
 Další informace najdete v tématu [EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#29](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_29.cpp)]  
  
##  <a name="setrect"></a>CRichEditCtrl::SetRect  
 Nastaví formátování rámeček pro tento `CRichEditCtrl` objektu.  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo ukazatel na [Rect –](../../mfc/reference/rect-structure1.md) určující nové hranice pro formátování rámeček.  
  
### <a name="remarks"></a>Poznámky  
 Formátování rámeček je limitující rámeček pro text. Omezení rámeček je nezávislá na velikosti okna ovládacího prvku RichEdit. Pokud to `CRichEditCtrl` nejprve vytvořit objekt, formátování rámeček se stejnou velikost jako klientské oblasti okna. Použití `SetRect` provést formátování rámeček větší nebo menší než okno RichEdit.  
  
 Další informace najdete v tématu [EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#30](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_30.cpp)]  
  
##  <a name="setsel"></a>CRichEditCtrl::SetSel  
 Nastaví výběr v rámci to `CRichEditCtrl` objektu.  
  
```  
void SetSel(
    long nStartChar,  
    long nEndChar);  
  
void SetSel(CHARRANGE& cr);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartChar`  
 Index prvního znaku pro výběr nule.  
  
 `nEndChar`  
 Index počítaný od nuly poslední znak pro výběr.  
  
 `cr`  
 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura, která obsahuje hranice aktuální výběr.  
  
### <a name="remarks"></a>Poznámky  
 Dvě formy této funkce zadejte alternativní způsoby, jak nastavit rozsah pro výběr. Stručný popis těchto formulářů podle:  
  
- **SetSel (** `cr` **)** používá tento formulář **CHARRANGE** struktury s jeho **cpMin** a **cpMax** členy nastavit rozsah.  
  
- **SetSel (** `nStartChar` **,** `nEndChar` **)** tento formulář použijte parametry `nStartChar` a `nEndChar` nastavit rozsah.  
  
 Na konci výběr indikován větší spouštění je umístěn pomocí kurzoru ( **cpMin** nebo `nStartChar`) a end ( **cpMax** nebo `nEndChar`) indexy. Tato funkce se posouvá společně obsah `CRichEditCtrl` tak, aby pomocí kurzoru.  
  
 Vyberte veškerý text v tomto `CRichEditCtrl` objektu, volání `SetSel` s počáteční index 0 a end index - 1.  
  
 Další informace najdete v tématu [EM_EXSETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788007) zprávy a [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetSel](#getsel).  
  
##  <a name="setselectioncharformat"></a>CRichEditCtrl::SetSelectionCharFormat  
 Nastaví znak, formátování atributy pro text v aktuálním výběru v tomto `CRichEditCtrl` objektu.  
  
```  
BOOL SetSelectionCharFormat(CHARFORMAT& cf);  
BOOL SetSelectionCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 V první verzi, odkazy [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura obsahující bude nové formátování atributy pro aktuální výběr.  
  
 V druhé verzi ukazatel na [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura, což je rozšíření bohaté upravit 2.0 na **CHARFORMAT** struktura, která obsahuje nové atributy pro aktuální formátování výběr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pouze atributy určeného **dwMask** členem `cf` došlo ke změně pomocí této funkce.  
  
 Další informace najdete v tématu [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) a **CHARFORMAT** a **CHARFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#31](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_31.cpp)]  
  
##  <a name="settargetdevice"></a>CRichEditCtrl::SetTargetDevice  
 Nastaví cíl zařízení a řádku šířku, která používá pro WYSIWYG (zobrazené je můžete získat) formátování v tomto `CRichEditCtrl` objektu.  
  
```  
BOOL SetTargetDevice(
    HDC hDC,  
    long lLineWidth);

 
BOOL SetTargetDevice(
    CDC& dc,  
    long lLineWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `hDC`  
 Popisovač kontext zařízení pro nové cílové zařízení.  
  
 *lLineWidth*  
 Šířka čáry pro formátování.  
  
 `dc`  
 [CDC](../../mfc/reference/cdc-class.md) pro nové cílové zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je tato funkce je úspěšné, zařízení vlastní ovládací prvek RichEdit kontext je předán jako parametr. V takovém případě by neměl volání funkce zrušte kontextu zařízení.  
  
 Další informace najdete v tématu [EM_SETTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/bb774282) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#32](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_32.cpp)]  
  
##  <a name="settextmode"></a>CRichEditCtrl::SetTextMode  
 Nastaví úroveň text režimu nebo zpět a znovu ovládacího prvku RichEdit.  
  
```  
BOOL SetTextMode(UINT fMode);
```  
  
### <a name="parameters"></a>Parametry  
 *fmode –*  
 Určuje nové nastavení pro ovládací prvek text režim a vrácení zpět úrovně parametry. Seznam možných hodnot najdete v tématu parametr režimu pro [EM_SETTEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774286) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula. Pokud úspěšný, jinak nenulové hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Popis režimů text naleznete v tématu **EM_SETTEXTMODE** ve Windows SDK.  
  
 Tato funkce člen selže, pokud obsahuje ovládací prvek text. Pokud chcete mít jistotu ovládací prvek je prázdný, odeslání [WM_SETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632644) zprávu s prázdný řetězec.  
  
##  <a name="setundolimit"></a>CRichEditCtrl::SetUndoLimit  
 Nastaví maximální počet akcí, které mohou být uloženy ve frontě vrácení zpět.  
  
```  
UINT SetUndoLimit(UINT nLimit);
```  
  
### <a name="parameters"></a>Parametry  
 *nLimit*  
 Určuje maximální počet akcí, které mohou být uloženy ve frontě vrácení zpět. Vrátit zpět na hodnotu 0 zakážete.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové maximální počet akce vrácení zpět pro bohaté ovládacích prvků pro úpravy.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení je maximální počet akce ve frontě vrácení zpět 100. Pokud tento počet zvýšíte, musí být k dispozici dostatek paměti k uložení nové číslo. Lepší výkon omezit na nejnižší možná hodnota.  
  
##  <a name="setwordcharformat"></a>CRichEditCtrl::SetWordCharFormat  
 Nastaví znak, formátování atributy pro aktuálně vybrané aplikace word v tomto `CRichEditCtrl` objektu.  
  
```  
BOOL SetWordCharFormat(CHARFORMAT& cf);  
BOOL SetWordCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 V první verzi, odkazy [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura obsahující bude nové formátování atributy pro aktuálně vybrané aplikace word.  
  
 V druhé verzi ukazatel na [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) struktura, což je rozšíření bohaté upravit 2.0 na **CHARFORMAT** struktura, obsahující bude nové formátování atributy pro aktuálně vybrané aplikace word.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pouze atributy určeného **dwMask** členem `cf` došlo ke změně pomocí této funkce.  
  
 Další informace najdete v tématu [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) zprávy a **CHARFORMAT** a **CHARFORMAT2** struktury v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#33](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_33.cpp)]  
  
##  <a name="setwordwrapmode"></a>CRichEditCtrl::SetWordWrapMode  
 Nastaví možnosti-zalamování řádků a dělení slov pro bohaté ovládacích prvků pro úpravy.  
  
```  
UINT SetWordWrapMode(UINT uFlags) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uFlags`  
 Možnosti nastavit pro zabalení aplikace word a dělení slov. Seznam možných možnosti najdete v tématu [EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální-zalamování řádků a dělení slov možnosti.  
  
### <a name="remarks"></a>Poznámky  
 Tato zpráva je k dispozici pouze v asijské jazyky verzích operačního systému.  
  
##  <a name="stopgrouptyping"></a>CRichEditCtrl::StopGroupTyping  
 Zastaví řízení z shromažďování dalších psaní akce do aktuální akce vrácení zpět.  
  
```  
void StopGroupTyping();
```  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek ukládá další zadáním akce, pokud existuje, do nové akce ve frontě vrácení zpět.  
  
 Další informace najdete v tématu [EM_STOPGROUPTYPING](http://msdn.microsoft.com/library/windows/desktop/bb774300) ve Windows SDK.  
  
##  <a name="streamin"></a>CRichEditCtrl::StreamIn  
 Nahradí text v tomto `CRichEditCtrl` objekt s text ze zadaného vstupního datového proudu.  
  
```  
long StreamIn(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>Parametry  
 `nFormat`  
 Příznaky určující vstupní data formátů. Další informace naleznete v části Poznámky.  
  
 `es`  
 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) struktura určení vstupního datového proudu. Další informace naleznete v části Poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků pro čtení ze vstupního datového proudu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota `nFormat` musí mít jednu z následujících akcí:  
  
- `SF_TEXT`Označuje pouze text čtení.  
  
- `SF_RTF`Označuje čtení textu a formátování.  
  
 Některé z těchto hodnot je možné kombinovat s `SFF_SELECTION`. Pokud `SFF_SELECTION` není zadaný, `StreamIn` nahradí aktuální výběr vstupního datového proudu obsahu. Pokud není zadaný, `StreamIn` nahradí celý obsah této `CRichEditCtrl` objektu.  
  
 V **EDITSTREAM** parametr `es`, zadejte funkce zpětného volání, které doplní vyrovnávací paměť s textem. Tato funkce zpětného volání je volána opakovaně, dokud vyčerpá vstupního datového proudu.  
  
 Další informace najdete v tématu [EM_STREAMIN](http://msdn.microsoft.com/library/windows/desktop/bb774302) zprávy a [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#34](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_34.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl#35](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_35.cpp)]  
  
##  <a name="streamout"></a>CRichEditCtrl::StreamOut  
 Zapíše obsah tohoto `CRichEditCtrl` objekt do zadané výstupní datový proud.  
  
```  
long StreamOut(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>Parametry  
 `nFormat`  
 Příznaky určující formáty dat výstup. Další informace naleznete v části Poznámky.  
  
 `es`  
 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) struktura určení výstupního datového proudu. Další informace naleznete v části Poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků, které jsou zapsány do výstupního datového proudu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota `nFormat` musí mít jednu z následujících akcí:  
  
- `SF_TEXT`Označuje pouze text zápis.  
  
- `SF_RTF`Označuje zápis textu a formátování.  
  
- `SF_RTFNOOBJS`Označuje zápis textu a formátování, nahradí OLE – položky mezerami.  
  
- `SF_TEXTIZED`Označuje zápis textu a formátování s textové reprezentace OLE – položky.  
  
 Všechny tyto hodnoty mohou být kombinovány s `SFF_SELECTION`. Pokud `SFF_SELECTION` není zadaný, `StreamOut` zapíše na aktuální výběr do výstupního datového proudu. Pokud není zadaný, `StreamOut` zapíše se celý obsah této `CRichEditCtrl` objektu.  
  
 V **EDITSTREAM** parametr `es`, zadejte funkce zpětného volání, které doplní vyrovnávací paměť s textem. Tato funkce zpětného volání je volána opakovaně, až do vyčerpání do výstupního datového proudu.  
  
 Další informace najdete v tématu [EM_STREAMOUT](http://msdn.microsoft.com/library/windows/desktop/bb774304) zprávy a [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) struktura ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CRichEditCtrl#36](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_36.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl#37](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_37.cpp)]  
  
##  <a name="undo"></a>CRichEditCtrl::Undo  
 Vrátí zpět poslední operaci v ovládacím prvku RichEdit.  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je operace vrácení zpět úspěšně; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Operace vrácení zpět může být také vrátit zpět. Například můžete obnovit odstraněné textu s prvním volání **vrátit zpět**. Také neprobíhá žádná použité operace upravit, můžete odebrat text znovu s druhé volání **vrátit zpět**.  
  
 Další informace najdete v tématu [EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CanUndo](#canundo).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC WORDPAD](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [CRichEditView – třída](../../mfc/reference/cricheditview-class.md)
