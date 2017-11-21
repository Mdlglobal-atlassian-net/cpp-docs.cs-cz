---
title: "Třída COleClientItem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleClientItem
- AFXOLE/COleClientItem
- AFXOLE/COleClientItem::COleClientItem
- AFXOLE/COleClientItem::Activate
- AFXOLE/COleClientItem::ActivateAs
- AFXOLE/COleClientItem::AttachDataObject
- AFXOLE/COleClientItem::CanCreateFromData
- AFXOLE/COleClientItem::CanCreateLinkFromData
- AFXOLE/COleClientItem::CanPaste
- AFXOLE/COleClientItem::CanPasteLink
- AFXOLE/COleClientItem::Close
- AFXOLE/COleClientItem::ConvertTo
- AFXOLE/COleClientItem::CopyToClipboard
- AFXOLE/COleClientItem::CreateCloneFrom
- AFXOLE/COleClientItem::CreateFromClipboard
- AFXOLE/COleClientItem::CreateFromData
- AFXOLE/COleClientItem::CreateFromFile
- AFXOLE/COleClientItem::CreateLinkFromClipboard
- AFXOLE/COleClientItem::CreateLinkFromData
- AFXOLE/COleClientItem::CreateLinkFromFile
- AFXOLE/COleClientItem::CreateNewItem
- AFXOLE/COleClientItem::CreateStaticFromClipboard
- AFXOLE/COleClientItem::CreateStaticFromData
- AFXOLE/COleClientItem::Deactivate
- AFXOLE/COleClientItem::DeactivateUI
- AFXOLE/COleClientItem::Delete
- AFXOLE/COleClientItem::DoDragDrop
- AFXOLE/COleClientItem::DoVerb
- AFXOLE/COleClientItem::Draw
- AFXOLE/COleClientItem::GetActiveView
- AFXOLE/COleClientItem::GetCachedExtent
- AFXOLE/COleClientItem::GetClassID
- AFXOLE/COleClientItem::GetClipboardData
- AFXOLE/COleClientItem::GetDocument
- AFXOLE/COleClientItem::GetDrawAspect
- AFXOLE/COleClientItem::GetExtent
- AFXOLE/COleClientItem::GetIconFromRegistry
- AFXOLE/COleClientItem::GetIconicMetafile
- AFXOLE/COleClientItem::GetInPlaceWindow
- AFXOLE/COleClientItem::GetItemState
- AFXOLE/COleClientItem::GetLastStatus
- AFXOLE/COleClientItem::GetLinkUpdateOptions
- AFXOLE/COleClientItem::GetType
- AFXOLE/COleClientItem::GetUserType
- AFXOLE/COleClientItem::IsInPlaceActive
- AFXOLE/COleClientItem::IsLinkUpToDate
- AFXOLE/COleClientItem::IsModified
- AFXOLE/COleClientItem::IsOpen
- AFXOLE/COleClientItem::IsRunning
- AFXOLE/COleClientItem::OnActivate
- AFXOLE/COleClientItem::OnActivateUI
- AFXOLE/COleClientItem::OnChange
- AFXOLE/COleClientItem::OnDeactivate
- AFXOLE/COleClientItem::OnDeactivateUI
- AFXOLE/COleClientItem::OnGetClipboardData
- AFXOLE/COleClientItem::OnInsertMenus
- AFXOLE/COleClientItem::OnRemoveMenus
- AFXOLE/COleClientItem::OnSetMenu
- AFXOLE/COleClientItem::OnShowControlBars
- AFXOLE/COleClientItem::OnUpdateFrameTitle
- AFXOLE/COleClientItem::ReactivateAndUndo
- AFXOLE/COleClientItem::Release
- AFXOLE/COleClientItem::Reload
- AFXOLE/COleClientItem::Run
- AFXOLE/COleClientItem::SetDrawAspect
- AFXOLE/COleClientItem::SetExtent
- AFXOLE/COleClientItem::SetHostNames
- AFXOLE/COleClientItem::SetIconicMetafile
- AFXOLE/COleClientItem::SetItemRects
- AFXOLE/COleClientItem::SetLinkUpdateOptions
- AFXOLE/COleClientItem::SetPrintDevice
- AFXOLE/COleClientItem::UpdateLink
- AFXOLE/COleClientItem::CanActivate
- AFXOLE/COleClientItem::OnChangeItemPosition
- AFXOLE/COleClientItem::OnDeactivateAndUndo
- AFXOLE/COleClientItem::OnDiscardUndoState
- AFXOLE/COleClientItem::OnGetClipRect
- AFXOLE/COleClientItem::OnGetItemPosition
- AFXOLE/COleClientItem::OnGetWindowContext
- AFXOLE/COleClientItem::OnScrollBy
- AFXOLE/COleClientItem::OnShowItem
dev_langs: C++
helpviewer_keywords:
- COleClientItem [MFC], COleClientItem
- COleClientItem [MFC], Activate
- COleClientItem [MFC], ActivateAs
- COleClientItem [MFC], AttachDataObject
- COleClientItem [MFC], CanCreateFromData
- COleClientItem [MFC], CanCreateLinkFromData
- COleClientItem [MFC], CanPaste
- COleClientItem [MFC], CanPasteLink
- COleClientItem [MFC], Close
- COleClientItem [MFC], ConvertTo
- COleClientItem [MFC], CopyToClipboard
- COleClientItem [MFC], CreateCloneFrom
- COleClientItem [MFC], CreateFromClipboard
- COleClientItem [MFC], CreateFromData
- COleClientItem [MFC], CreateFromFile
- COleClientItem [MFC], CreateLinkFromClipboard
- COleClientItem [MFC], CreateLinkFromData
- COleClientItem [MFC], CreateLinkFromFile
- COleClientItem [MFC], CreateNewItem
- COleClientItem [MFC], CreateStaticFromClipboard
- COleClientItem [MFC], CreateStaticFromData
- COleClientItem [MFC], Deactivate
- COleClientItem [MFC], DeactivateUI
- COleClientItem [MFC], Delete
- COleClientItem [MFC], DoDragDrop
- COleClientItem [MFC], DoVerb
- COleClientItem [MFC], Draw
- COleClientItem [MFC], GetActiveView
- COleClientItem [MFC], GetCachedExtent
- COleClientItem [MFC], GetClassID
- COleClientItem [MFC], GetClipboardData
- COleClientItem [MFC], GetDocument
- COleClientItem [MFC], GetDrawAspect
- COleClientItem [MFC], GetExtent
- COleClientItem [MFC], GetIconFromRegistry
- COleClientItem [MFC], GetIconicMetafile
- COleClientItem [MFC], GetInPlaceWindow
- COleClientItem [MFC], GetItemState
- COleClientItem [MFC], GetLastStatus
- COleClientItem [MFC], GetLinkUpdateOptions
- COleClientItem [MFC], GetType
- COleClientItem [MFC], GetUserType
- COleClientItem [MFC], IsInPlaceActive
- COleClientItem [MFC], IsLinkUpToDate
- COleClientItem [MFC], IsModified
- COleClientItem [MFC], IsOpen
- COleClientItem [MFC], IsRunning
- COleClientItem [MFC], OnActivate
- COleClientItem [MFC], OnActivateUI
- COleClientItem [MFC], OnChange
- COleClientItem [MFC], OnDeactivate
- COleClientItem [MFC], OnDeactivateUI
- COleClientItem [MFC], OnGetClipboardData
- COleClientItem [MFC], OnInsertMenus
- COleClientItem [MFC], OnRemoveMenus
- COleClientItem [MFC], OnSetMenu
- COleClientItem [MFC], OnShowControlBars
- COleClientItem [MFC], OnUpdateFrameTitle
- COleClientItem [MFC], ReactivateAndUndo
- COleClientItem [MFC], Release
- COleClientItem [MFC], Reload
- COleClientItem [MFC], Run
- COleClientItem [MFC], SetDrawAspect
- COleClientItem [MFC], SetExtent
- COleClientItem [MFC], SetHostNames
- COleClientItem [MFC], SetIconicMetafile
- COleClientItem [MFC], SetItemRects
- COleClientItem [MFC], SetLinkUpdateOptions
- COleClientItem [MFC], SetPrintDevice
- COleClientItem [MFC], UpdateLink
- COleClientItem [MFC], CanActivate
- COleClientItem [MFC], OnChangeItemPosition
- COleClientItem [MFC], OnDeactivateAndUndo
- COleClientItem [MFC], OnDiscardUndoState
- COleClientItem [MFC], OnGetClipRect
- COleClientItem [MFC], OnGetItemPosition
- COleClientItem [MFC], OnGetWindowContext
- COleClientItem [MFC], OnScrollBy
- COleClientItem [MFC], OnShowItem
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ce200aa3fafcd1475e711eea79cb9c4574588a97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="coleclientitem-class"></a>COleClientItem – třída
Definuje rozhraní kontejner pro OLE – položky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleClientItem : public CDocItem  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleClientItem::COleClientItem](#coleclientitem)|Vytvoří `COleClientItem` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleClientItem::Activate](#activate)|Otevře položky OLE operace a pak spustí zadaný příkaz.|  
|[COleClientItem::ActivateAs](#activateas)|Aktivuje jako jiný typ položky.|  
|[COleClientItem::AttachDataObject](#attachdataobject)|Získá přístup k datům v objektech OLE.|  
|[COleClientItem::CanCreateFromData](#cancreatefromdata)|Určuje, zda aplikace kontejneru můžete vytvořit vložený objekt.|  
|[COleClientItem::CanCreateLinkFromData](#cancreatelinkfromdata)|Určuje, zda aplikace kontejneru můžete vytvořit propojený objekt.|  
|[COleClientItem::CanPaste](#canpaste)|Určuje, jestli schránky obsahuje položku OLE li nebo statické.|  
|[COleClientItem::CanPasteLink](#canpastelink)|Určuje, jestli schránky obsahuje položku korelovat OLE.|  
|[COleClientItem::Close](#close)|Zavře odkaz na serveru, ale nezničí položky OLE.|  
|[COleClientItem::ConvertTo](#convertto)|Převede položku k jinému typu.|  
|[COleClientItem::CopyToClipboard](#copytoclipboard)|Kopíruje položku OLE do schránky.|  
|[COleClientItem::CreateCloneFrom](#createclonefrom)|Vytvoří duplicitní stávající položku.|  
|[COleClientItem::CreateFromClipboard](#createfromclipboard)|Vytvoří položku vložené ze schránky.|  
|[COleClientItem::CreateFromData](#createfromdata)|Vytvoří embedded položku z dat objektu.|  
|[COleClientItem::CreateFromFile](#createfromfile)|Vytvoří vložené položky ze souboru.|  
|[COleClientItem::CreateLinkFromClipboard](#createlinkfromclipboard)|Vytvoří propojené položky ze schránky.|  
|[COleClientItem::CreateLinkFromData](#createlinkfromdata)|Vytvoří propojené položky z dat objektu.|  
|[COleClientItem::CreateLinkFromFile](#createlinkfromfile)|Vytvoří propojené položky ze souboru.|  
|[COleClientItem::CreateNewItem](#createnewitem)|Vytvoří novou položku embedded spuštěním serverové aplikace.|  
|[COleClientItem::CreateStaticFromClipboard](#createstaticfromclipboard)|Vytvoří položku statické ze schránky.|  
|[COleClientItem::CreateStaticFromData](#createstaticfromdata)|Vytvoří statickou položku z dat objektu.|  
|[COleClientItem::Deactivate](#deactivate)|Deaktivuje položky.|  
|[COleClientItem::DeactivateUI](#deactivateui)|Aplikace typu kontejner uživatelské rozhraní se obnoví do původního stavu.|  
|[COleClientItem::Delete](#delete)|Odstraní nebo ukončí položky OLE, pokud se jednalo o propojené položky.|  
|[COleClientItem::DoDragDrop](#dodragdrop)|Provede operaci přetažení myší.|  
|[COleClientItem::DoVerb](#doverb)|Provede zadaný příkaz.|  
|[COleClientItem::Draw](#draw)|Nakreslí položky OLE.|  
|[COleClientItem::GetActiveView](#getactiveview)|Získá zobrazení, na kterém je položka aktivována na místě.|  
|[COleClientItem::GetCachedExtent](#getcachedextent)|Vrátí hranice obdélníku položky OLE.|  
|[COleClientItem::GetClassID](#getclassid)|Získá ID existuje položka třídy.|  
|[COleClientItem::GetClipboardData](#getclipboarddata)|Získá data, která by umístit do schránky voláním `CopyToClipboard` – členská funkce.|  
|[COleClientItem::GetDocument](#getdocument)|Vrátí `COleDocument` objekt, který obsahuje položku přítomen.|  
|[COleClientItem::GetDrawAspect](#getdrawaspect)|Získá aktuální zobrazení položky pro vykreslování.|  
|[COleClientItem::GetExtent](#getextent)|Vrátí hranice obdélníku položky OLE.|  
|[COleClientItem::GetIconFromRegistry](#geticonfromregistry)|Umožňuje načíst popisovač pro přidružení k serveru konkrétní CLSID ikonu.|  
|[COleClientItem::GetIconicMetafile](#geticonicmetafile)|Získá metafile používá pro kreslení ikony položky.|  
|[COleClientItem::GetInPlaceWindow](#getinplacewindow)|Vrací ukazatel na okno Úpravy položky místní.|  
|[COleClientItem::GetItemState](#getitemstate)|Získá aktuální stav položky.|  
|[COleClientItem::GetLastStatus](#getlaststatus)|Vrátí stav poslední operace OLE.|  
|[COleClientItem::GetLinkUpdateOptions](#getlinkupdateoptions)|Vrátí režim aktualizace pro propojené položky (pokročilé funkce).|  
|[COleClientItem::GetType](#gettype)|Vrátí typ (embedded, propojené nebo statické) položky OLE.|  
|[COleClientItem::GetUserType](#getusertype)|Získá řetězec popisující typ položky.|  
|[COleClientItem::IsInPlaceActive](#isinplaceactive)|Vrátí `TRUE` Pokud je položka místní aktivní.|  
|[COleClientItem::IsLinkUpToDate](#islinkuptodate)|Vrátí **TRUE** Pokud propojené položky je aktuální jeho zdrojový dokument.|  
|[COleClientItem::IsModified](#ismodified)|Vrátí `TRUE` Pokud položka byla změněna od posledního uložení.|  
|[COleClientItem::IsOpen](#isopen)|Vrátí `TRUE` Pokud položka je aktuálně otevřený v serverové aplikace.|  
|[COleClientItem::IsRunning](#isrunning)|Vrátí `TRUE` Pokud položky serverová aplikace spuštěna.|  
|[COleClientItem::OnActivate](#onactivate)|Voláno rámcem oznámit položce, zda je aktivován.|  
|[COleClientItem::OnActivateUI](#onactivateui)|Voláno rámcem oznámit položky, aby se aktivuje a by měl zobrazit svoje uživatelské rozhraní.|  
|[COleClientItem::OnChange](#onchange)|Voláno, když server změní položky OLE. Implementace vyžaduje.|  
|[COleClientItem::OnDeactivate](#ondeactivate)|Voláno rámcem po deaktivaci položku.|  
|[COleClientItem::OnDeactivateUI](#ondeactivateui)|Voláno rámcem odebraný jeho místní uživatelské rozhraní serveru.|  
|[COleClientItem::OnGetClipboardData](#ongetclipboarddata)|Voláno rámcem získat data, která mají být zkopírován do schránky.|  
|[COleClientItem::OnInsertMenus](#oninsertmenus)|Voláno rámcem vytvořit složený nabídku.|  
|[COleClientItem::OnRemoveMenus](#onremovemenus)|Voláno rámcem odebrání kontejneru nabídky složené nabídky.|  
|[COleClientItem::OnSetMenu](#onsetmenu)|Voláno rámcem instalovat a odebírat složené nabídky.|  
|[COleClientItem::OnShowControlBars](#onshowcontrolbars)|Voláno rámcem zobrazení a skrytí ovládací pruhy.|  
|[COleClientItem::OnUpdateFrameTitle](#onupdateframetitle)|Voláno rámcem aktualizovat záhlaví rámce okna.|  
|[COleClientItem::ReactivateAndUndo](#reactivateandundo)|Znovu aktivuje položku a vrátí zpět poslední úpravy operaci na místě.|  
|[COleClientItem::Release](#release)|Uvolní připojení k propojené položky OLE a zavře se v případě, že byla otevřena. Nezničí klientské položky.|  
|[COleClientItem::Reload](#reload)|Znovu načte položku po volání `ActivateAs`.|  
|[COleClientItem::Run](#run)|Spustí aplikaci přidruženou k položce.|  
|[COleClientItem::SetDrawAspect](#setdrawaspect)|Nastaví aktuální zobrazení položky pro vykreslování.|  
|[COleClientItem::SetExtent](#setextent)|Nastaví ohraničující obdélník položky OLE.|  
|[COleClientItem::SetHostNames](#sethostnames)|Nastaví názvy serveru zobrazí při úpravě položky OLE.|  
|[COleClientItem::SetIconicMetafile](#seticonicmetafile)|Ukládá do mezipaměti metafile používá pro kreslení ikony položky.|  
|[COleClientItem::SetItemRects](#setitemrects)|Nastaví ohraničující obdélník položky.|  
|[COleClientItem::SetLinkUpdateOptions](#setlinkupdateoptions)|Nastaví režim aktualizace pro propojené položky (pokročilé funkce).|  
|[COleClientItem::SetPrintDevice](#setprintdevice)|Nastaví tiskových cílové zařízení pro tuto položku klienta.|  
|[COleClientItem::UpdateLink](#updatelink)|Aktualizuje mezipaměť prezentace položky.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleClientItem::CanActivate](#canactivate)|Voláno rámcem k určení, zda je povoleno aktivace na místě.|  
|[COleClientItem::OnChangeItemPosition](#onchangeitemposition)|Voláno rámcem, když se změní položku na pozici.|  
|[COleClientItem::OnDeactivateAndUndo](#ondeactivateandundo)|Voláno rámcem zrušit po aktivaci.|  
|[COleClientItem::OnDiscardUndoState](#ondiscardundostate)|Voláno rámcem vyřadí položky informace o stavu operace vrácení zpět.|  
|[COleClientItem::OnGetClipRect](#ongetcliprect)|Voláno rámcem získat výstřižek obdélníku souřadnice položky.|  
|[COleClientItem::OnGetItemPosition](#ongetitemposition)|Voláno rámcem získat položky pozice relativně k zobrazení.|  
|[COleClientItem::OnGetWindowContext](#ongetwindowcontext)|Voláno rámcem, pokud je aktivován položku na místě.|  
|[COleClientItem::OnScrollBy](#onscrollby)|Voláno rámcem k položce přejděte do zobrazení.|  
|[COleClientItem::OnShowItem](#onshowitem)|Voláno rámcem zobrazíte položky OLE.|  
  
## <a name="remarks"></a>Poznámky  
 OLE položky představuje data, vytvářené a udržované pomocí serverové aplikace, které lze "bezproblémově" začlenit do dokumentu tak, aby se uživateli, aby se jednotlivý dokument. Výsledkem je "složeného dokumentu" tvoří položka OLE a obsahující dokumentu.  
  
 Položky OLE lze vložené nebo propojené. Pokud je integrovaný, jeho data se ukládají jako součást složeného dokumentu. Pokud je propojena, jeho data se ukládají jako součást samostatný soubor vytvořené serverové aplikace a pouze odkaz na tento soubor je uložen v složeného dokumentu. Všechny položky OLE obsahují informace, které zadáte server aplikace, která by měla být volána upravovat je.  
  
 `COleClientItem`definuje několik přepisovatelné funkce, které se nazývají v reakci na požadavky od serverové aplikace; Tyto k přepisovatelným obvykle fungují jako oznámení. To umožňuje serveru aplikace k informování kontejneru změny, které uživatel provede při úpravě položky OLE nebo načíst informace potřebné při úpravy.  
  
 `COleClientItem`lze použít s buď [COleDocument](../../mfc/reference/coledocument-class.md), [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), nebo [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) třídy. Použít `COleClientItem`, odvození třídy z něj a implementaci [při změně](#onchange) členská funkce, která definuje, jak kontejneru reaguje na změny provedené v položce. Kvůli podpoře aktivace na místě, přepsat [OnGetItemPosition](#ongetitemposition) – členská funkce. Tato funkce poskytuje informace o zobrazené pozici položky OLE.  
  
 Další informace o používání rozhraní kontejneru, najdete v článcích [kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md) a [aktivace](../../mfc/activation-cpp.md).  
  
> [!NOTE]
>  Sada Windows SDK odkazují na vložené a propojené položky jako "objekty" a na typu položky jako "třídy." Tento odkaz používá k rozlišení OLE entity z odpovídající objekt C++ a termín "typ" k rozlišení kategorie OLE ze třídy C++ termín "položka".  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="activate"></a>COleClientItem::Activate  
 Volání této funkce provést zadaný příkaz místo [funkce DoVerb](#doverb) tak, aby můžete provést vlastní zpracováním, když je vyvolána výjimka.  
  
```  
void Activate(
    LONG nVerb,  
    CView* pView,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nVerb`  
 Určuje příkaz provést. Může být jeden z následujících akcí:  
  
|Hodnota|Význam|Symbol|  
|-----------|-------------|------------|  
|- 0|primární požadavek|`OLEIVERB_PRIMARY`|  
|- 1|Sekundární operace|(Žádný)|  
|- 1|Položka zobrazení pro úpravy|`OLEIVERB_SHOW`|  
|- 2|Upravit položku v samostatném okně.|`OLEIVERB_OPEN`|  
|- 3|Skrytí položek|`OLEIVERB_HIDE`|  
  
 Hodnota-1 je obvykle alias pro jiný příkaz. Pokud otevřete úpravy není podporován, -2 má stejný účinek jako hodnotu -1. Další hodnoty, najdete v části [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
 `pView`  
 Ukazatel myši do okna zobrazení kontejneru, který obsahuje položky OLE; aplikace serveru slouží pro aktivace na místě. Tento parametr by měl být **NULL** Pokud kontejneru nepodporuje aktivace na místě.  
  
 `lpMsg`  
 Ukazatel na zprávu, která způsobila, že položka, která má být aktivována.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je serverová aplikace byla zapsána pomocí knihovny Microsoft Foundation Class, tato funkce způsobí, že [OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb) – členská funkce k odpovídající položce `COleServerItem` objekt, který má být proveden.  
  
 Pokud je primární operace upravit a nula je uveden v `nVerb` parametr příslušnou aplikaci na server se spustí umožňující OLE položku, kterou chcete upravit. Pokud aplikace kontejner podporuje aktivace na místě, úpravy lze provést na místě. Pokud kontejner nepodporuje aktivace na místě (nebo pokud je zadán příkaz otevřený), server se spouští v samostatném okně a úpravy lze provést existuje. Obvykle, když aplikace kontejneru poklepání položku OLE, hodnota primární požadavek v `nVerb` parametr určuje akci, která uživatel může trvat. Ale pokud je server podporuje jenom jednu akci, trvá této akce, bez ohledu na to, která je zadaná hodnota v `nVerb` parametr.  
  
 Další informace najdete v tématu [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
##  <a name="activateas"></a>COleClientItem::ActivateAs  
 Používá pro OLE objekt převod možnosti aktivovat položky, jako by šlo položky v typu zadaném pomocí `clsidNew`.  
  
```  
virtual BOOL ActivateAs(
    LPCTSTR lpszUserType,  
    REFCLSID clsidOld,  
    REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszUserType*  
 Ukazatel na řetězec představující cílový typ uživatele, jako je například "Dokument aplikace Word."  
  
 *clsidOld*  
 ID odkaz na aktuální třídu položky. ID třídy by měl představovat typ objektu skutečné, jak je uložen, pokud je odkaz. V takovém případě by to být CLSID položky, na který odkazuje na odkaz. [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md) automaticky poskytuje ID správné třídy pro položku.  
  
 `clsidNew`  
 Odkaz na ID cílové třídy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tomu se říká automaticky [COleConvertDialog::DoConvert](../../mfc/reference/coleconvertdialog-class.md#doconvert). Obvykle nevolá přímo.  
  
##  <a name="attachdataobject"></a>COleClientItem::AttachDataObject  
 Volání této funkce k chybě při inicializaci [COleDataObject](../../mfc/reference/coledataobject-class.md) pro přístup k datům v položce OLE.  
  
```  
void AttachDataObject(COleDataObject& rDataObject) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rDataObject*  
 Odkaz na `COleDataObject` objekt, který umožňuje přístup k datům v položce OLE, budou inicializována.  
  
##  <a name="canactivate"></a>COleClientItem::CanActivate  
 Voláno rámcem, když uživatel požádá aktivace na místě položky OLE; Tato funkce návratová hodnota určuje, zda aktivace na místě povolena.  
  
```  
virtual BOOL CanActivate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je povolená aktivace na místě; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace umožňuje aktivace na místě, pokud kontejner má platný časové období. Potlačí tuto funkci implementovat speciální logiku pro přijetí nebo odmítnutí žádost o aktivaci. Požadavek aktivace může například zamítne, pokud položka OLE je příliš malá nebo nejsou aktuálně viditelné.  
  
 Další informace najdete v tématu [IOleInPlaceSite::CanInPlaceActivate](http://msdn.microsoft.com/library/windows/desktop/ms691236) ve Windows SDK.  
  
##  <a name="cancreatefromdata"></a>COleClientItem::CanCreateFromData  
 Kontroluje, zda aplikace kontejneru můžete vytvořit vložený objekt z danou `COleDataObject` objektu.  
  
```  
static BOOL PASCAL CanCreateFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Ukazatel [COleDataObject](../../mfc/reference/coledataobject-class.md) objekt, ze kterého má být vytvořen položky OLE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud kontejner můžete vytvořit vložený objekt z `COleDataObject` objektu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 `COleDataObject` Třída se používá v přenosech souborů pro načítání dat v různých formátech ze schránky, prostřednictvím přetažení, nebo z vložené položky OLE.  
  
 Kontejnery můžete pomocí této funkce můžete rozhodnout k povolení nebo zakázání jejich příkazy upravit vložení a upravit Vložit jinak.  
  
 Další informace najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
##  <a name="cancreatelinkfromdata"></a>COleClientItem::CanCreateLinkFromData  
 Kontroluje, zda aplikace kontejneru můžete vytvořit propojený objekt z danou `COleDataObject` objektu.  
  
```  
static BOOL PASCAL CanCreateLinkFromData(const COleDataObject* pDataObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Ukazatel [COleDataObject](../../mfc/reference/coledataobject-class.md) objekt, ze kterého má být vytvořen položky OLE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud kontejner můžete vytvořit propojený objekt z `COleDataObject` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `COleDataObject` Třída se používá v přenosech souborů pro načítání dat v různých formátech ze schránky, prostřednictvím přetažení, nebo z vložené položky OLE.  
  
 Kontejnery můžete pomocí této funkce můžete rozhodnout k povolení nebo zakázání jejich příkazy upravit Vložit jinak a upravit Vložit propojení.  
  
 Další informace najdete v článku [datové objekty a zdroje dat (OLE)](../../mfc/data-objects-and-data-sources-ole.md).  
  
##  <a name="canpaste"></a>COleClientItem::CanPaste  
 Volání této funkce, které chcete zobrazit, zda lze vložit vložené položky OLE ze schránky.  
  
```  
static BOOL PASCAL CanPaste();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vložené položky OLE lze vložit ze schránky; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OleGetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms692778) a [OleQueryCreateFromData](http://msdn.microsoft.com/library/windows/desktop/ms683739) ve Windows SDK.  
  
##  <a name="canpastelink"></a>COleClientItem::CanPasteLink  
 Volání této funkce, které chcete zobrazit, zda lze vložit propojené položky OLE ze schránky.  
  
```  
static BOOL PASCAL CanPasteLink();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud propojené položky OLE lze vložit ze schránky; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OleGetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms692778) a [OleQueryLinkFromData](http://msdn.microsoft.com/library/windows/desktop/ms690244) ve Windows SDK.  
  
##  <a name="close"></a>COleClientItem::Close  
 Volání této funkce na změnu stavu položky OLE z do stavu spuštěno načíst stav, který je načten její obslužnou rutinu v paměti, ale server není spuštěný.  
  
```  
void Close(OLECLOSE dwCloseOption = OLECLOSE_SAVEIFDIRTY);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCloseOption`  
 Příznak určující, za jakých okolností je položka OLE uložena, až se obnoví načíst stav. Může mít jednu z následujících hodnot:  
  
- `OLECLOSE_SAVEIFDIRTY`Uložte položky OLE.  
  
- `OLECLOSE_NOSAVE`Neukládejte položky OLE.  
  
- `OLECLOSE_PROMPTSAVE`Dotázat se uživatele na tom, zda je k uložení položky OLE.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce nemá žádný vliv, pokud položka OLE není spuštěna.  
  
 Další informace najdete v tématu [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) ve Windows SDK.  
  
##  <a name="coleclientitem"></a>COleClientItem::COleClientItem  
 Vytvoří `COleClientItem` objektu a přidává ji k dokumentu kontejneru kolekce položek dokumentu, který vytvoří pouze objekt C++ a neprovádí žádné inicializace technologie OLE.  
  
```  
COleClientItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pContainerDoc`  
 Ukazatel na dokument kontejneru, který bude obsahovat tuto položku. To může být libovolná [COleDocument](../../mfc/reference/coledocument-class.md) odvozených.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte **NULL** ukazatele, bez přidání Přišla žádost o dokument kontejneru. Musíte explicitně volat [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem).  
  
 Jeden z následujících členské funkce vytváření musí volat dříve, než použijete OLE položky:  
  
- [CreateFromClipboard](#createfromclipboard)  
  
- [CreateFromData](#createfromdata)  
  
- [CreateFromFile](#createfromfile)  
  
- [CreateStaticFromClipboard](#createstaticfromclipboard)  
  
- [CreateStaticFromData](#createstaticfromdata)  
  
- [CreateLinkFromClipboard](#createlinkfromclipboard)  
  
- [CreateLinkFromData](#createlinkfromdata)  
  
- [CreateLinkFromFile](#createlinkfromfile)  
  
- [CreateNewItem](#createnewitem)  
  
- [CreateCloneFrom](#createclonefrom)  
  
##  <a name="convertto"></a>COleClientItem::ConvertTo  
 Volání této funkce člen převést položky v typu zadaném pomocí `clsidNew`.  
  
```  
virtual BOOL ConvertTo(REFCLSID clsidNew);
```  
  
### <a name="parameters"></a>Parametry  
 `clsidNew`  
 ID třídy cílového typu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tomu se říká automaticky [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md). Není nutné volat přímo.  
  
##  <a name="copytoclipboard"></a>COleClientItem::CopyToClipboard  
 Volání této funkce OLE položku zkopírovat do schránky.  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bIncludeLink`  
 **Hodnota TRUE,** Pokud informace o propojení by měl být zkopírována do schránky, což propojené položky být vložených; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Při zápisu obslužné rutiny zpráv pro kopírování nebo vyjmutí příkazy v nabídce Upravit se obvykle volání této funkce. Výběr položek v aplikaci kontejneru musí implementovat, pokud chcete implementovat příkazy kopírování nebo vyjmutí.  
  
 Další informace najdete v tématu [OleSetClipboard](http://msdn.microsoft.com/library/windows/desktop/ms686623) ve Windows SDK.  
  
##  <a name="createclonefrom"></a>COleClientItem::CreateCloneFrom  
 Volání této funkce vytvoření kopie zadané položky OLE.  
  
```  
BOOL CreateCloneFrom(const COleClientItem* pSrcItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pSrcItem*  
 Ukazatel na OLE položka, která má být duplicitní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Kopie je stejný jako zdroj položek. Tuto funkci můžete použít pro podporu operací, vrácení zpět.  
  
##  <a name="createfromclipboard"></a>COleClientItem::CreateFromClipboard  
 Volání této funkce Vytvoření vložené položky z obsah schránky.  
  
```  
BOOL CreateFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle volání této funkce z popisovač zpráv pro příkaz Vložit v nabídce Upravit. (Příkaz Paste zapnutá rámcem, pokud [CanPaste](#canpaste) – členská funkce vrátí nenulové hodnoty.)  
  
 Další informace najdete v tématu [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createfromdata"></a>COleClientItem::CreateFromData  
 Volání této funkce Vytvoření vložené položky z `COleDataObject` objektu.  
  
```  
BOOL CreateFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Ukazatel [COleDataObject](../../mfc/reference/coledataobject-class.md) objekt, ze kterého má být vytvořen položky OLE.  
  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Operace přenosu dat, jako je například vložení ze schránky nebo operací přetažení myší, zadejte `COleDataObject` objekty obsahujícího informace o nabízených serverová aplikace. Obvykle se používá v přepsání z [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop).  
  
 Další informace najdete v tématu [OleCreateFromData](http://msdn.microsoft.com/library/windows/desktop/ms691211), [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createfromfile"></a>COleClientItem::CreateFromFile  
 Volání této funkce Vytvoření vložené položky OLE ze souboru.  
  
```  
BOOL CreateFromFile(
    LPCTSTR lpszFileName,  
    REFCLSID clsid = CLSID_NULL,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ukazatel na název souboru, ze kterého má být vytvořen položky OLE.  
  
 `clsid`  
 Vyhrazeno pro budoucí použití.  
  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce z volá framework [COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem) Pokud uživatel vybere OK v dialogovém okně Vložit objekt, pokud je vybrána vytvořit ze souboru tlačítko.  
  
 Další informace najdete v tématu [OleCreateFromFile](http://msdn.microsoft.com/library/windows/desktop/ms690116), [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createlinkfromclipboard"></a>COleClientItem::CreateLinkFromClipboard  
 Volání této funkce k vytvoření propojené položky z obsah schránky.  
  
```  
BOOL CreateLinkFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle volat tuto funkci z popisovač zpráv pro příkaz Vložit odkaz v nabídce Upravit. (Příkaz Vložit propojení je povoleno ve výchozím nastavení implementace [COleDocument](../../mfc/reference/coledocument-class.md) pokud obsahuje schránky OLE položku, která může být propojený.)  
  
 Další informace najdete v tématu [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createlinkfromdata"></a>COleClientItem::CreateLinkFromData  
 Volání této funkce vytvoření propojené položky z `COleDataObject` objektu.  
  
```  
BOOL CreateLinkFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Ukazatel [COleDataObject](../../mfc/reference/coledataobject-class.md) objekt, ze kterého má být vytvořen položky OLE.  
  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání to během operace odstranění, když uživatel označuje, že by měl být vytvořen odkaz. Ho lze také zpracovat příkaz Upravit vložit. Je voláno rámcem v `COleClientItem::CreateLinkFromClipboard` a v [COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem) Pokud byla vybrána možnost propojení.  
  
 Další informace najdete v tématu [OleCreateLinkFromData](http://msdn.microsoft.com/library/windows/desktop/ms680731), [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createlinkfromfile"></a>COleClientItem::CreateLinkFromFile  
 Volání této funkce vytvoření propojené položky OLE ze souboru.  
  
```  
BOOL CreateLinkFromFile(
    LPCTSTR lpszFileName,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ukazatel na název souboru, ze kterého má být vytvořen položky OLE.  
  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se uživatel rozhodne OK z dialogového okna vložení objektu, když je vybrán vytvořit ze souboru tlačítko a je zaškrtnuto políčko Propojit volá rámec této funkce. Je volána z [COleInsertDialog::CreateItem](../../mfc/reference/coleinsertdialog-class.md#createitem).  
  
 Další informace najdete v tématu [OleCreateLinkToFile](http://msdn.microsoft.com/library/windows/desktop/ms678434), [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createnewitem"></a>COleClientItem::CreateNewItem  
 Volání této funkce Vytvoření vložené položky; Tato funkce spustí serverové aplikace, která umožňuje uživatelům vytvořit položku OLE.  
  
```  
BOOL CreateNewItem(
    REFCLSID clsid,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 ID, která jednoznačně identifikuje typ položky OLE k vytvoření.  
  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto funkci, pokud uživatel vybere OK v dialogovém okně Vložit objekt, pokud je vybrána tlačítko Vytvořit nový.  
  
 Další informace najdete v tématu [OleCreate](http://msdn.microsoft.com/library/windows/desktop/ms678409), [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createstaticfromclipboard"></a>COleClientItem::CreateStaticFromClipboard  
 Volání této funkce můžete vytvořit statickou položku z obsah schránky.  
  
```  
BOOL CreateStaticFromClipboard(
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Statické položka obsahuje prezentace dat, ale ne nativní data; v důsledku toho se nedá upravit. Pokud se obvykle volání této funkce [CreateFromClipboard](#createfromclipboard) – členská funkce selže.  
  
 Další informace najdete v tématu [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="createstaticfromdata"></a>COleClientItem::CreateStaticFromData  
 Volání této funkce k vytvoření statických položky z `COleDataObject` objektu.  
  
```  
BOOL CreateStaticFromData(
    COleDataObject* pDataObject,  
    OLERENDER render = OLERENDER_DRAW,  
    CLIPFORMAT cfFormat = 0,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataObject`  
 Ukazatel [COleDataObject](../../mfc/reference/coledataobject-class.md) objekt, ze kterého má být vytvořen položky OLE.  
  
 *vykreslení*  
 Příznak určující, jak bude server zobrazovat položky OLE. Možné hodnoty, najdete v části [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507) ve Windows SDK.  
  
 `cfFormat`  
 Určuje formát dat schránky do mezipaměti při vytváření položky OLE.  
  
 `lpFormatEtc`  
 Ukazatel na [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktura použít, pokud *vykreslení* je **OLERENDER_FORMAT** nebo **OLERENDER_DRAW**. Zadejte hodnotu tohoto parametru, pouze v případě, že chcete zadat informace o dalších formátu nad rámec formát schránky určeného `cfFormat`. Pokud tento parametr vynecháte, použijí se výchozí hodnoty pro v ostatních polích **FORMATETC** struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Statické položka obsahuje prezentace dat, ale ne nativní data; v důsledku toho se nedá upravit. Je to v podstatě stejné jako [CreateStaticFromClipboard](#createstaticfromclipboard) s tím rozdílem, že statické položky lze vytvořit na libovolnou `COleDataObject`, ne jenom ze schránky.  
  
 Použít v [COlePasteSpecialDialog::CreateItem](../../mfc/reference/colepastespecialdialog-class.md#createitem) při výběru statické.  
  
 Další informace najdete v tématu [OleCreateStaticFromData](http://msdn.microsoft.com/library/windows/desktop/ms687290), [OLERENDER](http://msdn.microsoft.com/library/windows/desktop/ms691507), a [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) ve Windows SDK.  
  
##  <a name="deactivate"></a>COleClientItem::Deactivate  
 Volání této funkce můžete deaktivovat položky OLE a uvolnit všechny související prostředky.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Obvykle položku místní active OLE deaktivovat po kliknutí myší na klientské oblasti mimo hranice položky. Všimněte si, že deaktivace položek OLE zrušíte stav vrácení zpět, takže je možné volat [ReactivateAndUndo](#reactivateandundo) – členská funkce.  
  
 Pokud vaše aplikace podporuje vrácení zpět, nevolejte `Deactivate`; místo toho volat [DeactivateUI](#deactivateui).  
  
 Další informace najdete v tématu [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) ve Windows SDK.  
  
##  <a name="deactivateui"></a>COleClientItem::DeactivateUI  
 Volání této funkce, když uživatel deaktivuje položku, která se aktivovala na místě.  
  
```  
void DeactivateUI();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce obnoví uživatelské rozhraní aplikace kontejneru do původního stavu, skrytí žádné nabídky a jiných ovládacích prvků, které byly vytvořeny pro aktivace na místě.  
  
 Tato funkce není k vyprázdnění informace o stavu operace vrácení zpět pro položku. Zda informace jsou uchovány tak, aby [ReactivateAndUndo](#reactivateandundo) můžete později použít ke spuštění příkazu zpět v serverové aplikace, v případě, že je zvolen příkaz undo kontejneru ihned po deaktivaci služby položky.  
  
 Další informace najdete v tématu [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) ve Windows SDK.  
  
##  <a name="delete"></a>COleClientItem::Delete  
 Volání této funkce se odstranit položku OLE z kontejneru dokumentu.  
  
```  
void Delete(BOOL bAutoDelete = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoDelete`  
 Určuje, zda položka odebrat z dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá [verze](#release) členská funkce, která zase odstraní objekt C++ položku a trvale odebrání položky OLE z dokumentu. Pokud vložené položky OLE nativní data pro položku se odstraní. Vždy se zavře používají server; Proto pokud je položka Otevřít odkaz, tato funkce uzavře.  
  
##  <a name="dodragdrop"></a>COleClientItem::DoDragDrop  
 Volání `DoDragDrop` – členská funkce k provedení operace přetažení myší.  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpItemRect,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpItemRect`  
 Položky obdélníku na obrazovce souřadnice klienta (v pixelech).  
  
 `ptOffset`  
 Posun od `lpItemRect` kde pozice myši byl v době přetahování.  
  
 `bIncludeLink`  
 Tuto možnost nastavíte na **TRUE** Pokud data propojení by se měl zkopírovat do schránky. Nastavte ji na **FALSE** Pokud vaše serverová aplikace nepodporuje odkazy.  
  
 `dwEffects`  
 Určuje účinky, které vám umožní zdroje operace přetažení v operaci přetažení.  
  
 `lpRectStartDrag`  
 Ukazatel na obdélníku, která definuje, kde přetáhněte skutečně spustí. Další informace naleznete v následující části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DROPEFFECT` hodnotu. Pokud je `DROPEFFECT_MOVE`, měla by být odebrána původní data.  
  
### <a name="remarks"></a>Poznámky  
 Operaci přetažení myší nespustí okamžitě. Čeká, dokud myší opustí rámeček určeného `lpRectStartDrag` nebo dokud předané zadaný počet milisekund. Pokud `lpRectStartDrag` je **NULL**, velikost rámeček je jeden pixel.  
  
 Doba zpoždění je určena nastavení klíče registru. Doba zpoždění lze změnit pomocí volání [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) nebo [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Pokud nezadáte čas zpoždění, se používá výchozí hodnota je 200 MS. Doba zpoždění přetažení se ukládají následujícím způsobem:  
  
-   Doba zpoždění systému Windows NT přetáhněte je uložená v HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Doba zpoždění přetáhněte 3.x Windows je uložená v WIN. Soubor INI, části [Windows}.  
  
-   Doba zpoždění Windows 95/98 přetáhněte je uložená v mezipaměti verzi WIN. INI.  
  
 Pro další informace o tom, přetáhněte zpoždění informace jsou uloženy v registru buď nebo. Soubor INI, najdete v části [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) ve Windows SDK.  
  
##  <a name="doverb"></a>COleClientItem::DoVerb  
 Volání `DoVerb` provést zadanou operaci.  
  
```  
virtual BOOL DoVerb(
    LONG nVerb,  
    CView* pView,
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nVerb`  
 Určuje příkaz provést. Může obsahovat jednu z těchto možností:  
  
|Hodnota|Význam|Symbol|  
|-----------|-------------|------------|  
|- 0|primární požadavek|`OLEIVERB_PRIMARY`|  
|- 1|Sekundární operace|(Žádný)|  
|- 1|Položka zobrazení pro úpravy|`OLEIVERB_SHOW`|  
|- 2|Upravit položku v samostatném okně.|`OLEIVERB_OPEN`|  
|- 3|Skrytí položek|`OLEIVERB_HIDE`|  
  
 Hodnota-1 je obvykle alias pro jiný příkaz. Pokud otevřete úpravy není podporován, -2 má stejný účinek jako hodnotu -1. Další hodnoty, najdete v části [Funkce IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) ve Windows SDK.  
  
 `pView`  
 Ukazatel na okno zobrazení; používá se serverem pro aktivace na místě. Tento parametr by měl být **NULL** Pokud kontejnerové aplikace nedovoluje aktivace na místě.  
  
 `lpMsg`  
 Ukazatel na zprávu, která způsobila, že položka, která má být aktivována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud příkaz byl úspěšně proveden; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá [aktivovat](#activate) – členská funkce provést příkaz. Také zachytí výjimky a zobrazí okno se zprávou uživateli, pokud jeden je vyvolána výjimka.  
  
 Pokud je primární operace upravit a nula je uveden v `nVerb` parametr příslušnou aplikaci na server se spustí umožňující OLE položku, kterou chcete upravit. Pokud aplikace kontejner podporuje aktivace na místě, úpravy lze provést na místě. Pokud kontejner nepodporuje aktivace na místě (nebo pokud je zadán příkaz otevřený), server se spouští v samostatném okně a úpravy lze provést existuje. Obvykle, když aplikace kontejneru poklepání položku OLE, hodnota primární požadavek v `nVerb` parametr určuje akci, která uživatel může trvat. Ale pokud je server podporuje jenom jednu akci, trvá této akce, bez ohledu na to, která je zadaná hodnota v `nVerb` parametr.  
  
##  <a name="draw"></a>COleClientItem::Draw  
 Volání této funkce k vykreslení položky OLE do zadaného ohraničující obdélník pomocí kontextu zadané zařízení.  
  
```  
BOOL Draw(
    CDC* pDC,  
    LPCRECT lpBounds,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na [CDC](../../mfc/reference/cdc-class.md) objekt použitý pro vykreslení položky OLE.  
  
 `lpBounds`  
 Ukazatel na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo `RECT` struktura, která definuje ohraničující obdélník, ve kterém k položce OLE (v logických jednotkách dáno kontextu zařízení).  
  
 `nDrawAspect`  
 Určuje aspektů OLE položky, to znamená, jak by se měla zobrazit. Pokud `nDrawAspect` je -1, poslední aspekt nastavit pomocí [SetDrawAspect](#setdrawaspect) se používá. Další informace o možných hodnot pro tento příznak najdete v tématu [SetDrawAspect](#setdrawaspect).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce může používat reprezentace metafile OLE položky vytvořené [OnDraw –](../../mfc/reference/coleserveritem-class.md#ondraw) členské funkce `COleServerItem`.  
  
 Obvykle použijete **kreslení** pro zobrazení na obrazovce, předávání kontextu zařízení obrazovky jako `pDC`. V takovém případě budete muset zadat pouze první dva parametry.  
  
 `lpBounds` Parametr identifikuje obdélníku v kontextu zařízení cíl (relativní vůči aktuální mapování režim). Vykreslování může zahrnovat škálování na obrázku a použitím aplikace typu kontejner uložit zobrazení, které přizpůsobí mezi zobrazené zobrazení a finální tištěné image.  
  
 Další informace najdete v tématu [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) ve Windows SDK.  
  
##  <a name="getactiveview"></a>COleClientItem::GetActiveView  
 Vrátí zobrazení, na kterém je položka aktivaci.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zobrazení; v opačném případě **NULL** Pokud položka není aktivován na místě.  
  
##  <a name="getcachedextent"></a>COleClientItem::GetCachedExtent  
 Volání této funkce načíst velikost položky OLE.  
  
```  
BOOL GetCachedExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)-1);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSize`  
 Ukazatel na **velikost** struktura nebo [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který se zobrazí informace o velikosti.  
  
 `nDrawAspect`  
 Určuje aspektů OLE položek, jejichž hranice jsou mají být načteny. Možné hodnoty, najdete v části [SetDrawAspect](#setdrawaspect).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; 0, pokud položka OLE je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce poskytuje stejné informace jako [GetExtent](#getextent). Můžete však volat `GetCachedExtent` získat informace o rozsahu během zpracování ostatních obslužných rutin OLE, jako [při změně](#onchange). Dimenze jsou v `MM_HIMETRIC` jednotky.  
  
 To je možné, protože `GetCachedExtent` používá [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318) rozhraní, místo použití [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) rozhraní získat rozsah této položky. **IViewObject2** objektu COM ukládá do mezipaměti informace o rozsahu, použitých v předchozích volání [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655).  
  
 Další informace najdete v tématu [IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) ve Windows SDK.  
  
##  <a name="getclassid"></a>COleClientItem::GetClassID  
 Vrátí ID třídy položky do paměti, na kterou odkazuje `pClassID`.  
  
```  
void GetClassID(CLSID* pClassID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pClassID`  
 Ukazatel na identifikátor typu [CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) načíst ID třídy. Informace o **CLSID**, najdete v části Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 ID třídy je 128-bit číslo, které jednoznačně identifikuje aplikaci, která upraví položky.  
  
 Další informace najdete v tématu [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) ve Windows SDK.  
  
##  <a name="getclipboarddata"></a>COleClientItem::GetClipboardData  
 Volání této funkce můžete získat `COleDataSource` objekt obsahující všechna data, která by umístit do schránky voláním [CopyToClipboard](#copytoclipboard) – členská funkce.  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDataSource`  
 Ukazatel na [coledatasource –](../../mfc/reference/coledatasource-class.md) objektu, která bude přijímat data obsažená v položce OLE.  
  
 `bIncludeLink`  
 **Hodnota TRUE,** Pokud zahrnuté; jinak hodnota by měla být data propojení **FALSE**.  
  
 `lpOffset`  
 Posun myší z tohoto počátku objektu v pixelech.  
  
 `lpSize`  
 Velikost objektu v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 `GetClipboardData`je volána jako výchozí implementaci [OnGetClipboardData](#ongetclipboarddata). Přepsání `OnGetClipboardData` pouze v případě, že můžete chtít nabízet data formáty kromě těch, které nabízí `CopyToClipboard`. Umístěte tyto formáty v `COleDataSource` objekt před nebo po volání `CopyToClipboard`a pak `COleDataSource` do objektu [COleDataSource::SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) funkce. Například pokud chcete položku OLE pozici v jeho kontejneru dokumentu, který může doprovázet do schránky, kdybyste definovat vlastní formát pro předání těchto informací a jeho umístění `COleDataSource` před voláním `CopyToClipboard`.  
  
##  <a name="getdocument"></a>COleClientItem::GetDocument  
 Volání této funkce získání ukazatele v dokumentu, který obsahuje položky OLE.  
  
```  
COleDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na dokument, který obsahuje položky OLE. **NULL** Pokud položka není součástí dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Umožňuje přístup na tento ukazatel `COleDocument` objekt, který můžete předat jako argument k `COleClientItem` konstruktor.  
  
##  <a name="getdrawaspect"></a>COleClientItem::GetDrawAspect  
 Volání `GetDrawAspect` – členská funkce k určení aktuální "aspekt", nebo zobrazení, položky.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota z `DVASPECT` výčtu, jejichž hodnoty jsou uvedeny v dokumentaci pro [SetDrawAspect](#setdrawaspect).  
  
### <a name="remarks"></a>Poznámky  
 Daný aspekt Určuje, jak má být vykreslen položky.  
  
##  <a name="getextent"></a>COleClientItem::GetExtent  
 Volání této funkce načíst velikost položky OLE.  
  
```  
BOOL GetExtent(
    LPSIZE lpSize,  
    DVASPECT nDrawAspect = (DVASPECT)- 1);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSize`  
 Ukazatel na **velikost** struktura nebo `CSize` objekt, který se zobrazí informace o velikosti.  
  
 `nDrawAspect`  
 Určuje aspektů OLE položek, jejichž hranice jsou mají být načteny. Možné hodnoty, najdete v části [SetDrawAspect](#setdrawaspect).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; 0, pokud položka OLE je prázdný.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je serverová aplikace byla zapsána pomocí knihovny Microsoft Foundation Class, tato funkce způsobí, že [OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent) – členská funkce k odpovídající položce `COleServerItem` objekt, který má být volána. Načtený velikost může lišit od velikost poslední nastavenou [SetExtent](#setextent) – členská funkce; velikost zadaná ve `SetExtent` je považován za zlepšení. Dimenze jsou v `MM_HIMETRIC` jednotky.  
  
> [!NOTE]
>  Nevolejte `GetExtent` během zpracování obslužné rutiny OLE, jako například [při změně](#onchange). Volání [GetCachedExtent](#getcachedextent) místo.  
  
 Další informace najdete v tématu [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) ve Windows SDK.  
  
##  <a name="geticonfromregistry"></a>COleClientItem::GetIconFromRegistry  
 Volání této funkce člen načíst popisovač pro prostředek s ikonou přidružené k serveru konkrétní CLSID.  
  
```  
HICON GetIconFromRegistry() const;  
  
static HICON GetIconFromRegistry(CLSID& clsid);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Odkaz na CLSID pro server přidružený ikonu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Platný popisovač pro prostředek ikonu, nebo **NULL** Pokud ikony serveru nebo výchozí ikony, nelze nalézt.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci člen nebude spuštění serveru nebo získat ikonu dynamicky, i v případě, že server je již spuštěna. Místo toho tuto funkci člen otevře spustitelné bitové kopie serveru a načte ikonu statické přidružené k serveru, jako byl zaregistrován.  
  
##  <a name="geticonicmetafile"></a>COleClientItem::GetIconicMetafile  
 Načte metafile používá pro kreslení ikony položky.  
  
```  
HGLOBAL GetIconicMetafile();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro metafile v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není žádná aktuální ikona, je vrácen výchozí ikonu. To je volána automaticky dialogová okna MFC/OLE a není obvykle volat přímo.  
  
 Tato funkce také voláním [SetIconicMetafile](#seticonicmetafile) pro ukládání do mezipaměti metafile pro pozdější použití.  
  
##  <a name="getinplacewindow"></a>COleClientItem::GetInPlaceWindow  
 Volání `GetInPlaceWindow` – členská funkce získání ukazatele do okna, ve kterém byla položka otevřena pro úpravy na místě.  
  
```  
CWnd* GetInPlaceWindow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na položky v místě úpravy okno; **NULL** Pokud položka není aktivní nebo pokud není k dispozici její server.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána pouze pro položky, které jsou na místě aktivní.  
  
##  <a name="getitemstate"></a>COleClientItem::GetItemState  
 Volání této funkce můžete získat aktuální stav položky OLE.  
  
```  
UINT GetItemState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COleClientItem::ItemState** uvedené hodnotu, která může být jedna z následujících: `emptyState`, **loadedState**, `openState`, `activeState`, `activeUIState`. Informace o těchto stavů, najdete v článku [kontejnery: stavy klientských položek](../../mfc/containers-client-item-states.md).  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete být upozorněni, když se změní stav položky OLE, použijte [při změně](#onchange) – členská funkce.  
  
 Další informace najdete v článku [kontejnery: stavy klientských položek](../../mfc/containers-client-item-states.md).  
  
##  <a name="getlaststatus"></a>COleClientItem::GetLastStatus  
 Vrátí stavový kód poslední operaci OLE.  
  
```  
SCODE GetLastStatus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `SCODE` Hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pro člen funkce, který vrací **BOOL** hodnotu **FALSE**, nebo jiné členské funkce, který vrací **NULL**, `GetLastStatus` vrátí podrobnější informace o selhání. Upozorňujeme, že většina OLE členské funkce generování výjimek pro více závažných chyb. Konkrétní informace o výkladu `SCODE` závisí na základní OLE hovoru, který vrátila poslední `SCODE` hodnotu.  
  
 Další informace o `SCODE`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) v dokumentaci k Windows SDK.  
  
##  <a name="getlinkupdateoptions"></a>COleClientItem::GetLinkUpdateOptions  
 Volání této funkce můžete získat aktuální hodnotu možnosti propojení aktualizace pro položku OLE.  
  
```  
OLEUPDATE GetLinkUpdateOptions();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot:  
  
- `OLEUPDATE_ALWAYS`Aktualizujte propojené položky, kdykoli je to možné. Tato volba podporuje přepínač Automatické aktualizace propojení v dialogovém okně odkazy.  
  
- `OLEUPDATE_ONCALL`Aktualizovat propojené položky pouze na žádost z aplikace kontejneru (když [UpdateLink](#updatelink) – členská funkce je volána). Tato volba podporuje přepínač Ruční aktualizace propojení v dialogovém okně odkazy.  
  
### <a name="remarks"></a>Poznámky  
 Toto je pokročilá operace.  
  
 Tato funkce je volána automaticky pomocí [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md) třídy.  
  
 Další informace najdete v tématu [IOleLink::GetUpdateOptions](http://msdn.microsoft.com/library/windows/desktop/ms680100) ve Windows SDK.  
  
##  <a name="gettype"></a>COleClientItem::GetType  
 Volání této funkce k určení, zda je položka OLE vložené nebo propojené nebo statické.  
  
```  
OLE_OBJTYPE GetType() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo bez znaménka s jedním z následujících hodnot:  
  
- `OT_LINK`Položka OLE je odkaz.  
  
- `OT_EMBEDDED`Vložené položky OLE.  
  
- `OT_STATIC`Položka OLE je statická, to znamená, obsahuje pouze prezentace dat, není nativní dat a proto nelze je upravit.  
  
##  <a name="getusertype"></a>COleClientItem::GetUserType  
 Volání této funkce můžete získat zobrazovanou uživateli řetězec popisující položku OLE typu, například "Dokument aplikace Word."  
  
```  
void GetUserType(
    USERCLASSTYPE nUserClassType,  
    CString& rString);
```  
  
### <a name="parameters"></a>Parametry  
 *nUserClassType*  
 Hodnota označující požadované varianta řetězec popisující typ položky OLE. To může mít jednu z následujících hodnot:  
  
- `USERCLASSTYPE_FULL`Název typu úplné zobrazí uživateli.  
  
- `USERCLASSTYPE_SHORT`Krátký název (maximálně 15 znaků) pro použití v místní nabídky a dialogové okno Upravit propojení.  
  
- `USERCLASSTYPE_APPNAME`Název aplikace pro obsluhu třídy.  
  
 `rString`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu, na které má být vrácen řetězec s popisem typ položky OLE.  
  
### <a name="remarks"></a>Poznámky  
 Toto je často položky v databázi systému registrace.  
  
 Pokud název úplné typu je požadovaný ale není k dispozici, použije se místo toho krátký název. Pokud žádný záznam pro typ položky OLE nebyla nalezena v databázi registrace nebo pokud nejsou žádné typy uživatel zaregistrovat pro typ položky OLE, pak typ uživatele aktuálně uloženy v položce OLE se používá. Pokud tento typ uživatelské jméno je řetězec prázdný, použije se "Neznámý objekt".  
  
 Další informace najdete v tématu [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) ve Windows SDK.  
  
##  <a name="isinplaceactive"></a>COleClientItem::IsInPlaceActive  
 Volání této funkce, zda položka OLE je aktivní na místě.  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka OLE aktivní na místě; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Je běžné k provádění různých logiky v závislosti na tom, jestli je položka upravovaný na místě. Funkce zkontroluje, zda je aktuální stav položky rovná buď `activeState` nebo `activeUIState`.  
  
##  <a name="islinkuptodate"></a>COleClientItem::IsLinkUpToDate  
 Volání této funkce, zda je aktuální položky OLE.  
  
```  
BOOL IsLinkUpToDate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka OLE aktuální; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Propojené položky může být zastaralý pokud jeho zdrojový dokument byl aktualizován. Vložené položku, která obsahuje odkazy v něm se může stát podobně jako zastaralý. Funkce nepodporuje kontrolu rekurzivní položky OLE. Všimněte si, stanovení, zda je aktuální položku OLE může být jako nákladné jako ve skutečnosti provedení aktualizace.  
  
 Tomu se říká automaticky pomocí [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md) implementace.  
  
 Další informace najdete v tématu [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) ve Windows SDK.  
  
##  <a name="ismodified"></a>COleClientItem::IsModified  
 Volání této funkce, zda položka OLE je nekonzistentní (změnil od posledního uložení).  
  
```  
BOOL IsModified() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka OLE změny; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [IPersistStorage::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) ve Windows SDK.  
  
##  <a name="isopen"></a>COleClientItem::IsOpen  
 Volání této funkce zjistěte, zda položky OLE otevřete; To znamená otevřít v instanci serveru aplikace běžící v samostatném okně.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka OLE otevřete; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Slouží k určení, kdy k vykreslení objektu pomocí vzoru šrafování. Otevřete objekt by měl mít nesouvislého vzoru vykreslovat nad objekt. Můžete použít [crecttracker –](../../mfc/reference/crecttracker-class.md) objekt, který chcete dosáhnout.  
  
##  <a name="isrunning"></a>COleClientItem::IsRunning  
 Volání této funkce, zda je spuštěn položky OLE; To znamená, zda je položka načíst a spustit v serverové aplikace.  
  
```  
BOOL IsRunning() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud položka OLE běží; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OleIsRunning](http://msdn.microsoft.com/library/windows/desktop/ms688705) ve Windows SDK.  
  
##  <a name="onactivate"></a>COleClientItem::OnActivate  
 Voláno rámcem položka upozornit, že právě nebyl aktivován na místě.  
  
```  
virtual void OnActivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že tato funkce je volána k označení, že na serveru běží nechcete znamenat, že byla nainstalována jeho uživatelské rozhraní v aplikaci kontejneru. V tomto okamžiku objekt nemá aktivní uživatelské rozhraní (není `activeUIState`). Není nainstalovaná její nabídky nebo na panelu nástrojů. [OnActivateUI](#onactivateui) – členská funkce je volána, když k tomu dojde.  
  
 Výchozí implementace volá [při změně](#onchange) – členská funkce s **OLE_CHANGEDSTATE** jako parametr. Potlačí tuto funkci k provedení vlastní zpracování, když se položky stane aktivní na místě.  
  
##  <a name="onactivateui"></a>COleClientItem::OnActivateUI  
 Volání framework `OnActivateUI` při objekt zadá aktivním stavu uživatelského rozhraní.  
  
```  
virtual void OnActivateUI();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt má nyní nainstalovat jeho panelu nástrojů a nabídky.  
  
 Výchozí implementace pamatuje serveru `HWND` pro pozdější **GetServerWindow** volání.  
  
##  <a name="onchange"></a>COleClientItem::OnChange  
 Voláno rámcem, když uživatel změní, uloží nebo zavře položky OLE.  
  
```  
virtual void OnChange(
    OLE_NOTIFICATION nCode,  
    DWORD dwParam);
```  
  
### <a name="parameters"></a>Parametry  
 `nCode`  
 Z důvodu serveru změnit tuto položku. Může mít jednu z následujících hodnot:  
  
- `OLE_CHANGED`Došlo ke změně vzhledu položky OLE.  
  
- `OLE_SAVED`Položka OLE se uložila.  
  
- `OLE_CLOSED`Položka OLE bylo ukončeno.  
  
- `OLE_CHANGED_STATE`Tato položka OLE změněna z jednoho stavu do jiného.  
  
 `dwParam`  
 Pokud `nCode` je `OLE_SAVED` nebo `OLE_CLOSED`, tento parametr se nepoužívá. Pokud `nCode` je `OLE_CHANGED`, tento parametr určuje aspekt OLE položky, které se změnily. Možné hodnoty, najdete v článku `dwParam` parametr [COleClientItem::Draw](#draw). Pokud `nCode` je `OLE_CHANGED_STATE`, tento parametr je **COleClientItem::ItemState** uvedené hodnoty a popisuje stav jejich zadání. Může mít jednu z následujících hodnot: `emptyState`, **loadedState**, `openState`, `activeState`, nebo `activeUIState`.  
  
### <a name="remarks"></a>Poznámky  
 (Pokud je serverová aplikace je napsán pomocí knihovny Microsoft Foundation Class, tato funkce je volána v reakci `Notify` členské funkce `COleServerDoc` nebo `COleServerItem`.) Výchozí implementace označí dokument kontejneru jako v případě upravit `nCode` je `OLE_CHANGED` nebo `OLE_SAVED`.  
  
 Pro `OLE_CHANGED_STATE`, aktuální stav vrácená z [GetItemState](#getitemstate) bude stále starý stav, což znamená, stavu, která byla aktuální před tuto změnu stavu.  
  
 Funkci reagovat na změny ve stavu položky OLE přepište. Obvykle můžete aktualizovat položky vzhled zneplatnění oblasti, ve kterém se zobrazí položka. Na začátku přepsání volejte implementaci základní třídy.  
  
##  <a name="onchangeitemposition"></a>COleClientItem::OnChangeItemPosition  
 Voláno rámcem oznámit kontejneru OLE položky rozsah došlo ke změně během aktivace na místě.  
  
```  
virtual BOOL OnChangeItemPosition(const CRect& rectPos);
```  
  
### <a name="parameters"></a>Parametry  
 *rectPos*  
 Určuje umístění relativně ke kontejneru aplikace klientské oblasti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je úspěšně se změnilo umístění; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace Určuje nové viditelné rámeček položky OLE a volání [SetItemRects](#setitemrects) s novými hodnotami. Výchozí implementace vypočítá viditelné rámeček pro položku a předá tyto informace k serveru.  
  
 Funkci chcete použít zvláštní pravidla pro operace změny velikosti nebo přesunutí přepište. Pokud je aplikace napsaná v jazyce MFC, toto volání dochází, protože server volá [COleServerDoc::RequestPositionChange](../../mfc/reference/coleserverdoc-class.md#requestpositionchange).  
  
##  <a name="ondeactivate"></a>COleClientItem::OnDeactivate  
 Voláno rámcem při položky OLE přejde ze stavu active na místě ( `activeState`) načíst stav, což znamená, že je deaktivována po aktivace na místě.  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že tato funkce je volána k označení, že položky OLE uzavřeno, není to jeho uživatelské rozhraní byla odebrána z aplikace kontejneru. Pokud k tomu dojde, [OnDeactivateUI](#ondeactivateui) – členská funkce je volána.  
  
 Výchozí implementace volá [při změně](#onchange) – členská funkce s **OLE_CHANGEDSTATE** jako parametr. Potlačí tuto funkci k provedení vlastní zpracování při deaktivaci active položku na místě. Například pokud podporujete příkaz undo v aplikaci kontejneru, můžete přepsat této funkci můžete zrušit stavu vrácení zpět, která udává, že po deaktivaci položky nelze vrátit zpět poslední operaci provést na položce v OLE.  
  
##  <a name="ondeactivateandundo"></a>COleClientItem::OnDeactivateAndUndo  
 Voláno rámcem, když uživatel příkaz zpět vyvolá po aktivaci položky OLE na místě.  
  
```  
virtual void OnDeactivateAndUndo();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá [DeactivateUI](#deactivateui) deaktivace uživatelské rozhraní serveru. Potlačí tuto funkci při implementaci příkazu zpět v aplikaci kontejneru. V přepsání volání verzi funkce základní třídy a pak vrátit zpět poslední příkaz provést ve vaší aplikaci.  
  
 Další informace najdete v tématu [IOleInPlaceSite::DeactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms683743) ve Windows SDK.  
  
##  <a name="ondeactivateui"></a>COleClientItem::OnDeactivateUI  
 Voláno, když uživatel deaktivuje položku, která se aktivovala na místě.  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>Parametry  
 `bUndoable`  
 Určuje, zda jsou změny vrátit.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce obnoví uživatelské rozhraní aplikace kontejneru do původního stavu, skrytí žádné nabídky a jiných ovládacích prvků, které byly vytvořeny pro aktivace na místě.  
  
 Pokud `bUndoable` je **FALSE**kontejneru měli zakázat příkaz undo, platí zahození vrátit zpět stav kontejneru, protože označuje, že poslední operaci provést, server nevratná.  
  
##  <a name="ondiscardundostate"></a>COleClientItem::OnDiscardUndoState  
 Voláno rámcem, když uživatel provede akci, která zruší stavu zpět při úpravách položky OLE.  
  
```  
virtual void OnDiscardUndoState();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Potlačí tuto funkci při implementaci příkazu zpět v aplikaci kontejneru. V přepsání zruší stavu kontejneru aplikace vrácení zpět.  
  
 Pokud server byla zapsána pomocí knihovny Microsoft Foundation Class, serveru může způsobit tuto funkci, která se má volat při volání [COleServerDoc::DiscardUndoState](../../mfc/reference/coleserverdoc-class.md#discardundostate).  
  
 Další informace najdete v tématu [IOleInPlaceSite::DiscardUndoState](http://msdn.microsoft.com/library/windows/desktop/ms688642) ve Windows SDK.  
  
##  <a name="ongetclipboarddata"></a>COleClientItem::OnGetClipboardData  
 Voláno rámcem získat `COleDataSource` objekt obsahující všechna data, která by umístit do schránky voláním buď [CopyToClipboard](#copytoclipboard) nebo [metody DoDragDrop](#dodragdrop) – členská funkce.  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>Parametry  
 `bIncludeLink`  
 Tuto možnost nastavíte na **TRUE** Pokud data propojení by se měl zkopírovat do schránky. Tuto možnost nastavíte na **FALSE** Pokud vaše serverová aplikace nepodporuje odkazy.  
  
 `lpOffset`  
 Ukazatel na posun myší z tohoto počátku objektu v pixelech.  
  
 `lpSize`  
 Ukazatel na velikost objektu v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [coledatasource –](../../mfc/reference/coledatasource-class.md) objekt obsahující data ze schránky.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce volá [GetClipboardData](#getclipboarddata).  
  
##  <a name="ongetcliprect"></a>COleClientItem::OnGetClipRect  
 Volání framework `OnGetClipRect` – členská funkce se získat výstřižek obdélníku souřadnice položky, který je zpracováván na místě.  
  
```  
virtual void OnGetClipRect(CRect& rClipRect);
```  
  
### <a name="parameters"></a>Parametry  
 *rClipRect*  
 Ukazatel na objekt třídy [CRect](../../atl-mfc-shared/reference/crect-class.md) , bude obsahovat souřadnice výstřižek obdélníku položky.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou uváděny v pixelech relativně k okna aplikace kontejneru klientské oblasti.  
  
 Výchozí implementace vrací jednoduše klienta obdélník zobrazení, na kterém je položka místní aktivní.  
  
##  <a name="ongetitemposition"></a>COleClientItem::OnGetItemPosition  
 Volání framework `OnGetItemPosition` – členská funkce získat souřadnice položky, který je zpracováván na místě.  
  
```  
virtual void OnGetItemPosition(CRect& rPosition);
```  
  
### <a name="parameters"></a>Parametry  
 `rPosition`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který bude obsahovat souřadnice polohy položky.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou uváděny v pixelech relativně k okna aplikace kontejneru klientské oblasti.  
  
 Výchozí implementace této funkce neprovede žádnou akci. Aplikace, které podporují úpravy v místě vyžadují jeho implementace.  
  
##  <a name="ongetwindowcontext"></a>COleClientItem::OnGetWindowContext  
 Voláno rámcem, pokud je aktivován položku na místě.  
  
```  
virtual BOOL OnGetWindowContext(
    CFrameWnd** ppMainFrame,  
    CFrameWnd** ppDocFrame,  
    LPOLEINPLACEFRAMEINFO lpFrameInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `ppMainFrame`  
 Ukazatel na ukazatel na rámec hlavního okna.  
  
 `ppDocFrame`  
 Ukazatel na ukazatel na rámec okna dokumentu.  
  
 `lpFrameInfo`  
 Ukazatel na [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) struktura, která bude přijímat informace z rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k načtení informací o položce OLE nadřazeného okna.  
  
 Pokud je kontejner aplikace MDI, výchozí implementace vrací ukazatel na [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md) objekt v `ppMainFrame` a ukazatel na aktivní [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objekt v `ppDocFrame`. Pokud je kontejner aplikace SDI, výchozí implementace vrací ukazatel na [CFrameWnd](../../mfc/reference/cframewnd-class.md) objekt v `ppMainFrame` a vrátí **NULL** v `ppDocFrame`. Výchozí implementace také vyplní členů `lpFrameInfo`.  
  
 Funkci přepsat pouze v případě, že výchozí implementace není vyhovovaly vaší aplikace; Například pokud aplikace má zlepší uživatelského rozhraní, která se liší od SDI a MDI. Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [IOleInPlaceSite::GetWindowContext](http://msdn.microsoft.com/library/windows/desktop/ms694366) a [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) struktura ve Windows SDK.  
  
##  <a name="oninsertmenus"></a>COleClientItem::OnInsertMenus  
 Voláno rámcem během aktivace na místě vložení aplikace typu kontejner nabídky do prázdné nabídky.  
  
```  
virtual void OnInsertMenus(
    CMenu* pMenuShared,  
    LPOLEMENUGROUPWIDTHS lpMenuWidths);
```  
  
### <a name="parameters"></a>Parametry  
 `pMenuShared`  
 Odkazuje na prázdné nabídky.  
  
 `lpMenuWidths`  
 Odkazuje na pole šest **DLOUHO** hodnoty, která určuje, kolik nabídky jsou v každé z těchto skupin nabídky: souboru, upravit, kontejneru objektu, v okně nápovědy. Kontejner aplikace je zodpovědná za soubor, kontejneru a okno skupiny nabídek, odpovídající elementy 0, 2 a 4 Toto pole.  
  
### <a name="remarks"></a>Poznámky  
 Tato nabídka je předána na server, který vloží vlastní nabídky, vytváření složených nabídky. Tuto funkci jde volat opakovaně vytvořit několik složené nabídek.  
  
 Výchozí implementace vloží do `pMenuShared` kontejneru místní nabídky; to znamená, soubor, kontejneru a okno skupiny nabídek. [CDocTemplate::SetContainerInfo](../../mfc/reference/cdoctemplate-class.md#setcontainerinfo) se používá k nastavení této nabídky prostředku. Výchozí implementace také přiřadí odpovídající hodnoty na elementy 0, 2 a 4 v `lpMenuWidths`, v závislosti na prostředků nabídky. Přepíše tuto funkci, pokud výchozí implementace není vhodná pro vaši aplikaci; Například pokud vaše aplikace nepoužívá šablony dokumentů pro přidružení prostředky k typů dokumentů. Pokud funkci přepsat, měli byste také přepsat [OnSetMenu](#onsetmenu) a [OnRemoveMenus](#onremovemenus). Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [IOleInPlaceFrame::InsertMenus](http://msdn.microsoft.com/library/windows/desktop/ms683987) ve Windows SDK.  
  
##  <a name="onremovemenus"></a>COleClientItem::OnRemoveMenus  
 Voláno rámcem odebrat kontejneru nabídky z nabídky zadaný složené při ukončení aktivace na místě.  
  
```  
virtual void OnRemoveMenus(CMenu* pMenuShared);
```  
  
### <a name="parameters"></a>Parametry  
 `pMenuShared`  
 Odkazuje na složené nabídky zkonstruován pomocí volání [OnInsertMenus](#oninsertmenus) – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace odebere z `pMenuShared` kontejneru místní nabídky, které je, soubor, kontejneru a okno skupiny nabídek. Přepíše tuto funkci, pokud výchozí implementace není vhodná pro vaši aplikaci; Například pokud vaše aplikace nepoužívá šablony dokumentů pro přidružení prostředky k typů dokumentů. Pokud funkci přepsat, měli byste pravděpodobně přepsat [OnInsertMenus](#oninsertmenus) a [OnSetMenu](#onsetmenu) také. Toto je rozšířené přepisovatelné.  
  
 Dílčích na `pMenuShared` může sdílet více než jeden složený nabídky Pokud má server opakovaně volána `OnInsertMenus`. Proto byste neměli odstraňovat všechny dílčích v přepsání z `OnRemoveMenus`; měli jenom odpojit.  
  
 Další informace najdete v tématu [IOleInPlaceFrame::RemoveMenus](http://msdn.microsoft.com/library/windows/desktop/ms688685) ve Windows SDK.  
  
##  <a name="onscrollby"></a>COleClientItem::OnScrollBy  
 Voláno rámcem posun položky OLE v reakci na požadavky ze serveru.  
  
```  
virtual BOOL OnScrollBy(CSize sizeExtent);
```  
  
### <a name="parameters"></a>Parametry  
 *sizeExtent*  
 Určuje vzdálenost, v pixelech, přesuňte x a y pokynů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla položka přešli; 0, pokud položka nelze přesunut oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Například pokud je položka OLE částečně viditelná a uživatel přesune mimo oblast viditelné při provádění úprav v místě, tato funkce je volána zůstat kurzor viditelné. Výchozí implementace neprovede žádnou akci. Přepsání této funkci můžete posuňte položku se zadanou velikostí. Všimněte si, že v důsledku posouvání, viditelnou část položky OLE můžete změnit. Volání [SetItemRects](#setitemrects) aktualizovat viditelné obdélníku položky.  
  
 Další informace najdete v tématu [IOleInPlaceSite::Scroll](http://msdn.microsoft.com/library/windows/desktop/ms690291) ve Windows SDK.  
  
##  <a name="onsetmenu"></a>COleClientItem::OnSetMenu  
 Voláno rámcem dvakrát aktivace na místě zahájení a ukončení; prvním instalace složené nabídky a druhém (s `holemenu` rovna **NULL**) jeho odebrání.  
  
```  
virtual void OnSetMenu(
    CMenu* pMenuShared,  
    HOLEMENU holemenu,  
    HWND hwndActiveObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pMenuShared`  
 Ukazatel na složené nabídky zkonstruován pomocí volání [OnInsertMenus](#oninsertmenus) – členská funkce a `InsertMenu` funkce.  
  
 `holemenu`  
 Zpracování do nabídky popisovače vrácený **OleCreateMenuDescriptor** funkce, nebo **NULL** Pokud odesílající kódu, se odeberou.  
  
 *hwndActiveObject*  
 Popisovač okna pro úpravy položky OLE. Toto je okno, která bude přijímat příkazy pro úpravy z OLE.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace nainstaluje nebo odebere složené nabídku a pak zavolá [OleSetMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms692831) funkce a nainstaluje nebo odebere odesílající kódu. Tato funkce přepsání, pokud výchozí implementace není vhodná pro vaši aplikaci. Pokud funkci přepsat, měli byste pravděpodobně přepsat [OnInsertMenus](#oninsertmenus) a [OnRemoveMenus](#onremovemenus) také. Toto je rozšířené přepisovatelné.  
  
 Další informace najdete v tématu [OleCreateMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms691415), [OleSetMenuDescriptor](http://msdn.microsoft.com/library/windows/desktop/ms692831), a [IOleInPlaceFrame::SetMenu](http://msdn.microsoft.com/library/windows/desktop/ms693713) ve Windows SDK.  
  
##  <a name="onshowcontrolbars"></a>COleClientItem::OnShowControlBars  
 Voláno rámcem zobrazení a skrytí kontejnerové aplikace ovládacího prvku řádky.  
  
```  
virtual BOOL OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrameWnd`  
 Ukazatel na oken s rámečkem kontejnerové aplikace. To může být okno rámce nebo okna MDI podřízené.  
  
 `bShow`  
 Určuje, zda mají ovládací pruhy zobrazen nebo skryt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud volání funkce způsobí změnu stavu ovládací pruhy; 0 Pokud volání způsobí, že žádná změna, nebo pokud `pFrameWnd` neukazuje na oken s rámečkem kontejneru.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí hodnotu 0, pokud ovládací pruhy jsou již ve stavu určeného *bShow.* K tomu může dojít například, pokud jsou skrytý ovládací pruhy a `bShow` je **FALSE**.  
  
 Výchozí implementace odebere z okna nejvyšší úrovně rámečku panelu nástrojů.  
  
##  <a name="onshowitem"></a>COleClientItem::OnShowItem  
 Voláno rámcem zobrazíte položky OLE viditelnosti je zcela během úprav.  
  
```  
virtual void OnShowItem();
```  
  
### <a name="remarks"></a>Poznámky  
 Používá se při kontejneru aplikace podporuje odkazy na vložené položky (tj. Pokud mají odvozené třídě dokumentu z [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)). Tato funkce je volána během aktivace na místě nebo když položka OLE zdroj propojení a chce uživatel upravit. Výchozí implementace aktivuje první zobrazení v kontejneru dokumentu. Funkci pro posouvání dokumentu tak, aby položka OLE přepište.  
  
##  <a name="onupdateframetitle"></a>COleClientItem::OnUpdateFrameTitle  
 Voláno rámcem během aktivace na místě aktualizovat záhlaví rámce okna.  
  
```  
virtual BOOL OnUpdateFrameTitle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že tato funkce se úspěšně aktualizoval rámečku název, jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace se nezměnil název rámce okna. Funkci přepsat, pokud chcete název jiného snímku pro vaši aplikaci, například " *aplikace server* - *položky* v *docname*" "Microsoft (jako, Excel – tabulky v sestavě. DOC"). Toto je rozšířené přepisovatelné.  
  
##  <a name="reactivateandundo"></a>COleClientItem::ReactivateAndUndo  
 Volání této funkce a znovu aktivovat položky OLE vrátit zpět poslední akci provádí uživatel během úprav na místě.  
  
```  
BOOL ReactivateAndUndo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace kontejner podporuje příkaz undo, volejte tuto funkci, pokud uživatel vybere příkaz undo ihned po deaktivaci služby položky OLE.  
  
 Pokud je serverová aplikace napsané pomocí knihovny Microsoft Foundation tříd, tato funkce způsobí, že server volání [COleServerDoc::OnReactivateAndUndo](../../mfc/reference/coleserverdoc-class.md#onreactivateandundo).  
  
 Další informace najdete v tématu [IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) ve Windows SDK.  
  
##  <a name="release"></a>COleClientItem::Release  
 Volání této funkce vyčistěte prostředky používané položkou OLE.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCloseOption`  
 Příznak určující, za jakých okolností je položka OLE uložena, až se obnoví načíst stav. Seznam možných hodnot najdete v tématu [COleClientItem::Close](#close).  
  
### <a name="remarks"></a>Poznámky  
 **Verze** volá `COleClientItem` destruktor.  
  
 Další informace najdete v tématu [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) ve Windows SDK.  
  
##  <a name="reload"></a>COleClientItem::Reload  
 Zavře a znovu načte položku.  
  
```  
BOOL Reload();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání `Reload` funkce po aktivaci položky jako položku jiného typu voláním [ActivateAs](#activateas).  
  
##  <a name="run"></a>COleClientItem::Run  
 Spustí aplikaci přidruženou k této položce.  
  
```  
void Run();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání **spustit** – členská funkce spuštění serverové aplikace před aktivací položky. To se provádí automaticky [aktivovat](#activate) a [funkce DoVerb](#doverb), takže obvykle není nutné volání této funkce. Volání této funkce, pokud je potřeba spustit serveru, aby nastavte atribut položky, jako je třeba [SetExtent](#setextent), před provedením [funkce DoVerb](#doverb).  
  
##  <a name="setdrawaspect"></a>COleClientItem::SetDrawAspect  
 Volání `SetDrawAspect` – členská funkce nastavit "aspekt", nebo zobrazení, položky.  
  
```  
virtual void SetDrawAspect(DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>Parametry  
 `nDrawAspect`  
 Hodnota z `DVASPECT` výčtu. Tento parametr může mít jednu z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
### <a name="remarks"></a>Poznámky  
 Daný aspekt Určuje, jak je položka k vykreslení [kreslení](#draw) při výchozí hodnoty pro tuto funkci `nDrawAspect` použit argument.  
  
 Tato funkce je volána automaticky tak, že na ikonu změny (a další dialogová okna, které volají přímo dialogové okno Změnit ikonu) umožňující aspekt ikony zobrazení na žádost uživatele.  
  
##  <a name="setextent"></a>COleClientItem::SetExtent  
 Volání této funkce můžete určit, kolik místa je k dispozici pro položky OLE.  
  
```  
void SetExtent(
    const CSize& size,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje informace o velikosti.  
  
 `nDrawAspect`  
 Určuje aspektů OLE položek, jejichž hranice jsou nastavení. Možné hodnoty, najdete v části [SetDrawAspect](#setdrawaspect).  
  
### <a name="remarks"></a>Poznámky  
 Pokud je serverová aplikace byla zapsána pomocí knihovny Microsoft Foundation Class, to způsobí, že [OnSetExtent](../../mfc/reference/coleserveritem-class.md#onsetextent) – členská funkce k odpovídající položce `COleServerItem` objekt, který má být volána. Položka OLE pak můžete odpovídajícím způsobem upravit jeho zobrazení. Dimenze musí být v `MM_HIMETRIC` jednotky. Když uživatel změní velikost položky OLE nebo pokud podporujete určitou formu rozložení vyjednávání volání této funkce.  
  
 Další informace najdete v tématu [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) ve Windows SDK.  
  
##  <a name="sethostnames"></a>COleClientItem::SetHostNames  
 Volání této funkce určete název kontejneru aplikace a název kontejneru pro vložené položky OLE.  
  
```  
void SetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHost`  
 Ukazatel na zobrazovanou uživateli název kontejneru aplikace.  
  
 `lpszHostObj`  
 Ukazatel na identifikační řetězec kontejneru, který obsahuje položky OLE.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je serverová aplikace byla zapsána pomocí knihovny Microsoft Foundation Class, zavolá tato funkce [OnSetHostNames](../../mfc/reference/coleserverdoc-class.md#onsethostnames) členské funkce `COleServerDoc` dokument, který obsahuje položky OLE. Tyto informace se používá v okně názvy při úpravě položky OLE. Pokaždé, když je zavedený dokument kontejneru, volá rámec této funkce pro všechny položky OLE v dokumentu. `SetHostNames`používá se pouze pro vložené položky. Není nutné pro volání této funkce pokaždé, když se aktivuje vložené položky OLE pro úpravy.  
  
 To je také označován automaticky se název aplikace a název dokumentu při načtení objektu, nebo když se soubor uloží pod jiným názvem. Podle toho není obvykle nutné pro volání této funkce přímo.  
  
 Další informace najdete v tématu [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) ve Windows SDK.  
  
##  <a name="seticonicmetafile"></a>COleClientItem::SetIconicMetafile  
 Ukládá do mezipaměti metafile používá pro kreslení ikony položky.  
  
```  
BOOL SetIconicMetafile(HGLOBAL hMetaPict);
```  
  
### <a name="parameters"></a>Parametry  
 `hMetaPict`  
 Popisovač pro metafile používá pro kreslení ikony položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití [GetIconicMetafile](#geticonicmetafile) načíst metafile.  
  
 `hMetaPict` Parametr je zkopírován do položky; proto `hMetaPict` musí být uvolněno volajícího.  
  
##  <a name="setitemrects"></a>COleClientItem::SetItemRects  
 Volejte tuto funkci nastavit ohraničující obdélník nebo viditelné rámeček položky OLE.  
  
```  
BOOL SetItemRects(
    LPCRECT lpPosRect = NULL,  
    LPCRECT lpClipRect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lprcPosRect*  
 Ukazatel na rámeček obsahující hranice položky OLE relativně k jeho nadřazené okno, v souřadnicích klienta.  
  
 *lprcClipRect*  
 Ukazatel na rámeček obsahující hranice viditelnou část položky OLE relativně k jeho nadřazené okno, v souřadnicích klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána ve výchozí implementaci [OnChangeItemPosition](#onchangeitemposition) – členská funkce. Tato funkce by měly volat vždy, když pozici nebo viditelnou část OLE položky změny. To obvykle znamená volat z vašeho zobrazení [OnSize](../../mfc/reference/cwnd-class.md#onsize) a [OnScrollBy](../../mfc/reference/cview-class.md#onscrollby) členské funkce.  
  
 Další informace najdete v tématu [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) ve Windows SDK.  
  
##  <a name="setlinkupdateoptions"></a>COleClientItem::SetLinkUpdateOptions  
 Volání této funkce můžete nastavit možnost aktualizace propojení pro prezentaci zadané propojené položky.  
  
```  
void SetLinkUpdateOptions(OLEUPDATE dwUpdateOpt);
```  
  
### <a name="parameters"></a>Parametry  
 *dwUpdateOpt*  
 Hodnota možnosti propojení aktualizace pro tuto položku. Tato hodnota musí být jedna z následujících akcí:  
  
- `OLEUPDATE_ALWAYS`Aktualizujte propojené položky, kdykoli je to možné. Tato volba podporuje přepínač Automatické aktualizace propojení v dialogovém okně odkazy.  
  
- `OLEUPDATE_ONCALL`Aktualizovat propojené položky pouze na žádost z aplikace kontejneru (když [UpdateLink](#updatelink) – členská funkce je volána). Tato volba podporuje přepínač Ruční aktualizace propojení v dialogovém okně odkazy.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle byste neměli měnit možnosti aktualizace volená uživatelem v dialogovém okně odkazy.  
  
 Další informace najdete v tématu [IOleLink::SetUpdateOptions](http://msdn.microsoft.com/library/windows/desktop/ms680120) ve Windows SDK.  
  
##  <a name="setprintdevice"></a>COleClientItem::SetPrintDevice  
 Volání této funkce a změňte zařízení vytisknout cíl pro tuto položku.  
  
```  
BOOL SetPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL SetPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>Parametry  
 `ptd`  
 Ukazatel na [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) datová struktura, která obsahuje informace o nové tiskové cílové zařízení. Může být **NULL**.  
  
 `ppd`  
 Ukazatel na [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646940) datová struktura, která obsahuje informace o nové tiskové cílové zařízení. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce aktualizací tiskových cílové zařízení pro položku, ale neaktualizuje mezipaměť prezentace. Chcete-li aktualizovat mezipaměť prezentace pro položku, volejte [UpdateLink](#updatelink).  
  
 Argumenty, které se tato funkce obsahují informace, které používá systém OLE k identifikaci cílové zařízení. **PRINTDLG** struktura obsahuje informace, které používá systém Windows k chybě při inicializaci běžné dialogové okno tisku. Jakmile uživatel zavře dialogové okno, Windows vrací informace o výběr uživatele v této struktuře. `m_pd` Členem [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objekt **PRINTDLG** struktury.  
  
 Další informace o této struktuře naleznete v tématu [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) ve Windows SDK.  
  
 Další informace najdete v tématu [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) ve Windows SDK.  
  
##  <a name="updatelink"></a>COleClientItem::UpdateLink  
 Volání této funkce aktualizace dat prezentace položky OLE okamžitě.  
  
```  
BOOL UpdateLink();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Propojené položky vyhledá funkce zdroji odkaz k získání nového prezentace pro položku OLE. Tento proces může být vhodné spustit jeden nebo více serverové aplikace, které může být časově náročná. Funkce pro vložené položky, funguje rekurzivně, kontrola, zda vložené položky obsahuje odkazy, které mohou být zastaralé a jejich aktualizace. Uživatele můžete také ručně aktualizovat jednotlivých odkazů pomocí dialogového okna odkazy.  
  
 Další informace najdete v tématu [IOleLink::Update](http://msdn.microsoft.com/library/windows/desktop/ms692660) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MFCBIND](../../visual-cpp-samples.md)   
 [Ukázka MFC OCLIENT](../../visual-cpp-samples.md)   
 [CDocItem – třída](../../mfc/reference/cdocitem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleServerItem – třída](../../mfc/reference/coleserveritem-class.md)
