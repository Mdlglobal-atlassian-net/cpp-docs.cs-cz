---
title: "Třída COleServerDoc | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
dev_langs: C++
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81b3b8d4c3f25e1c443d5fbcaeddb7b587216d69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="coleserverdoc-class"></a>COleServerDoc – třída
Základní třída pro OLE – dokumenty na serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Vytvoří `COleServerDoc` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Aktivuje přidružené DocObject dokumentu.|  
|[COleServerDoc::ActivateInPlace](#activateinplace)|Aktivuje v dokumentu úpravy na místě.|  
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Deaktivuje uživatelské rozhraní serveru.|  
|[COleServerDoc::DiscardUndoState](#discardundostate)|Odstraní informace o stavu operace vrácení zpět.|  
|[COleServerDoc::GetClientSite](#getclientsite)|Načte ukazatel základní `IOleClientSite` rozhraní.|  
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Vrací ukazatel na položku představující celý dokument.|  
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Vrátí aktuální výstřižek rámeček pro úpravy na místě.|  
|[COleServerDoc::GetItemPosition](#getitemposition)|Vrátí aktuální rámeček pozice relativně ke kontejneru aplikace klientské oblasti pro úpravy na místě.|  
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Vrátí na faktor zvětšování v pixelech.|  
|[COleServerDoc::IsDocObject](#isdocobject)|Určuje, zda dokument DocObject.|  
|[COleServerDoc::IsEmbedded](#isembedded)|Určuje, zda je dokument vložený v kontejneru dokumentu nebo spuštění samostatné.|  
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Vrátí `TRUE` Pokud položka je právě aktivována na místě.|  
|[COleServerDoc::NotifyChanged](#notifychanged)|Upozorní kontejnery, že uživatel změnil dokumentu.|  
|[COleServerDoc::NotifyClosed](#notifyclosed)|Upozorní kontejnery, že uživatel zavřel dokumentu.|  
|[COleServerDoc::NotifyRename](#notifyrename)|Upozorní kontejnery, že uživatel má přejmenovat dokumentu.|  
|[COleServerDoc::NotifySaved](#notifysaved)|Upozorní kontejnery, že má uživatel uloží dokument.|  
|[COleServerDoc::OnDeactivate](#ondeactivate)|Voláno rámcem, když uživatel deaktivuje položku, která se aktivovala na místě.|  
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Voláno rámcem ke zničení ovládacích prvků a další prvky uživatelského rozhraní, které jsou vytvořené pro aktivace na místě.|  
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Voláno rámcem, pokud je aktivace nebo deaktivace kontejneru dokumentu rámce okna.|  
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Voláno rámcem při změně velikosti oken s rámečkem aplikace typu kontejner nebo okna dokumentu.|  
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Voláno rámcem zobrazíte nebo skryjete ovládací pruhy pro úpravy na místě.|  
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Voláno rámcem při uložení dokumentu serveru, který je vložený položku aktualizace kopie kontejneru položky.|  
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Změní umístění úpravy rámečkem na místě.|  
|[COleServerDoc::SaveEmbedding](#saveembedding)|Informuje kontejnerové aplikace k uložení dokumentu.|  
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Posune dokument kontejneru.|  
|[COleServerDoc::UpdateAllItems](#updateallitems)|Upozorní kontejnery, že uživatel změnil dokumentu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Voláno rámcem vytvoření rámce okna pro úpravy na místě.|  
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Voláno rámcem zrušení rámce okna pro úpravy na místě.|  
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Funkci pro vytvoření nového přepsat `CDocObjectServer` objektu a označení, že tento dokument je kontejner DocObject.|  
|[COleServerDoc::OnClose](#onclose)|Voláno rámcem, když kontejner požaduje zavřete dokument.|  
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Provede zadaný příkaz nebo zobrazuje nápovědu pro příkaz.|  
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Voláno rámcem, pokud je aktivace nebo deaktivace oken s rámečkem kontejneru.|  
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Voláno k získání `COleServerItem` , představuje celý dokument; použít k získání vložené položky. Implementace vyžaduje.|  
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Voláno rámcem vrátit zpět změny provedené v průběhu úpravy na místě.|  
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Voláno rámcem, pokud kontejner nastaví záhlaví okna pro vložený objekt.|  
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Voláno rámcem na pozici okno úprav rámečkem na místě v rámci časového období aplikace typu kontejner.|  
|[COleServerDoc::OnShowDocument](#onshowdocument)|Voláno rámcem zobrazit nebo skrýt dokumentu.|  
  
## <a name="remarks"></a>Poznámky  
 Dokument serveru může obsahovat [COleServerItem](../../mfc/reference/coleserveritem-class.md) objekty, které představují rozhraní serveru na vložené nebo propojené položky. Při aplikaci server je spuštěn kontejner k úpravě vložené položky, položka je načtena jako svůj vlastní dokument serveru; `COleServerDoc` objekt obsahuje pouze jeden `COleServerItem` objekt, který se skládá z celý dokument. Při spuštění aplikace server podle kontejner upravit propojené položky stávající dokument je načten z disku; část obsah dokumentu je označený k označení propojené položky.  
  
 `COleServerDoc`objekty může také obsahovat položky [COleClientItem](../../mfc/reference/coleclientitem-class.md) třídy. Umožňuje vytvořit kontejner serverových aplikací. Rozhraní framework poskytuje funkce správně ukládat `COleClientItem` položky během obsluhy `COleServerItem` objekty.  
  
 Pokud vaše serverová aplikace nepodporuje odkazy, server dokumentu vždycky obsahovat pouze jednu položku serveru, která představuje celou vložený objekt jako dokument. Pokud vaše serverová aplikace podporuje odkazy, musí vytvořit položku server pokaždé, když je výběr zkopírován do schránky.  
  
 Chcete-li použít `COleServerDoc`, odvození třídy z něj a implementaci [OnGetEmbeddedItem](#ongetembeddeditem) členská funkce, která umožňuje serveru pro podporu vložené položky. Odvození třídy z `COleServerItem` implementace položek v dokumentech a vrátit objekty třídy z `OnGetEmbeddedItem`.  
  
 Pro podporu propojené položky `COleServerDoc` poskytuje [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) – členská funkce. Můžete použít výchozí implementace nebo přepsat, pokud máte vlastní způsob správy položky dokumentů.  
  
 Budete potřebovat `COleServerDoc`-odvozené třídy, pro každý typ serveru dokumentu vaše aplikace podporuje. Například pokud vaše serverová aplikace podporuje listů a grafy, je třeba dva `COleServerDoc`-odvozených třídách.  
  
 Další informace o serverech najdete v článku [servery: implementace serveru](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject  
 Aktivuje přidružené DocObject dokumentu.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `COleServerDoc` nepodporuje aktivní dokumenty (také označované jako DocObjects). Chcete-li povolit tuto podporu, najdete v části [GetDocObjectServer](#getdocobjectserver) a třída [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).  
  
##  <a name="activateinplace"></a>COleServerDoc::ActivateInPlace  
 Aktivuje položka pro úpravy na místě.  
  
```  
BOOL ActivateInPlace();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; v opačném případě 0, která označuje, že položka je plně otevřené.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce provede všechny operace, které jsou nezbytné pro aktivace na místě. Se vytvoří okno s rámečkem na místě, se aktivuje a velikosti na položku, nastaví sdílené nabídek a jiných ovládacích prvků, posune položky do zobrazení a nastaví fokus do okna s rámečkem na místě.  
  
 Tato funkce je volána ve výchozí implementaci [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Volání této funkce, pokud vaše aplikace podporuje jiný příkaz Aktivace na místě (například Play).  
  
##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc  
 Vytvoří `COleServerDoc` objektu bez připojení k systému OLE knihovny DLL.  
  
```  
COleServerDoc();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) otevřete komunikace s OLE. Pokud používáte [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) ve vaší aplikaci, `COleLinkingDoc::Register` je volána pro vám `COleLinkingDoc`na implementaci `OnNewDocument`, `OnOpenDocument`, a `OnSaveDocument`.  
  
##  <a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame  
 Tato funkce se vytvořit okno rámce pro místní úpravy volá framework.  
  
```  
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel do nadřazeného okna aplikace typu kontejner.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel do okna s rámečkem na místě nebo **NULL** Pokud neúspěšně.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace používá k vytvoření rámečku informace zadané v šabloně. Zobrazení použít je první zobrazení vytvořené pro dokument. Toto zobrazení je dočasně odpojený od původního rámečku a připojit k nově vytvořený rámečku.  
  
 Toto je rozšířené přepisovatelné.  
  
##  <a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo  
 Pokud vaše aplikace podporuje vrátit zpět a uživatel zvolí vrácení zpět po aktivaci položku, ale před jeho úpravou volání této funkce.  
  
```  
BOOL DeactivateAndUndo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace kontejneru je napsán pomocí knihovny Microsoft Foundation Class, volání této funkce způsobí, že [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) k volání, které deaktivuje uživatelské rozhraní serveru.  
  
##  <a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame  
 Tato funkce zničit okno s rámečkem na místě a vrátit server do stavu před aktivace na místě okna dokumentu aplikace volá framework.  
  
```  
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrameWnd`  
 Ukazatel do okna s rámečkem na místě zničení.  
  
### <a name="remarks"></a>Poznámky  
 Toto je rozšířené přepisovatelné.  
  
##  <a name="discardundostate"></a>COleServerDoc::DiscardUndoState  
 Pokud uživatel provede úpravy operace, která nelze vrátit zpět, volejte tuto funkci vynutit aplikace kontejneru vyřadí informací o stavu operace vrácení zpět.  
  
```  
BOOL DiscardUndoState();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je poskytována tak, aby servery, které podporují operace vrácení zpět můžete uvolnit prostředky, které by jinak využívat informace o vrácení zpět stavu, která se nedá použít.  
  
##  <a name="getclientsite"></a>COleServerDoc::GetClientSite  
 Načte ukazatel základní `IOleClientSite` rozhraní.  
  
```  
LPOLECLIENTSITE GetClientSite() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte ukazatel základní [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706) rozhraní.  
  
##  <a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer  
 Funkci pro vytvoření nového přepsat `CDocObjectServer` položku a vrátí ukazatel na ni.  
  
```  
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```  
  
### <a name="parameters"></a>Parametry  
 `pDocSite`  
 Ukazatel `IOleDocumentSite` rozhraní, které bude tento dokument připojit k serveru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CDocObjectServer`; **NULL** Pokud operace se nezdařila.  
  
### <a name="remarks"></a>Poznámky  
 Když se aktivuje DocObject server, návrat jinou hodnotu než **NULL** ukazatele ukazuje, že klient může podporovat DocObjects. Výchozí implementace vrací **NULL**.  
  
 Typické implementace pro dokument, který podporuje DocObjects jednoduše přidělit nový `CDocObjectServer` objektu a obnoví v něm volajícímu. Příklad:  
  
 [!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]  
  
##  <a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem  
 Volání této funkce získání ukazatele k položce představující celý dokument.  
  
```  
COleServerItem* GetEmbeddedItem();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na položku představující celý dokument; **NULL** Pokud operace se nezdařila.  
  
### <a name="remarks"></a>Poznámky  
 Zavolá [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), virtuální funkce s žádné výchozí implementace.  
  
##  <a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect  
 Volání `GetItemClipRect` – členská funkce se získat výstřižek obdélníku souřadnice položky, který je zpracováván na místě.  
  
```  
void GetItemClipRect(LPRECT lpClipRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpClipRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt, který chcete přijímat souřadnice výstřižek obdélníku položky.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou uváděny v pixelech relativně k okna aplikace kontejneru klientské oblasti.  
  
 Kreslení by nemělo dojít mimo výstřižek rámeček. Obvykle je automaticky omezen kreslení. Tato funkce slouží k určení, zda má uživatel přešli mimo viditelnou část dokumentu. Pokud ano, posuňte dokument kontejneru podle potřeby prostřednictvím volání [ScrollContainerBy](#scrollcontainerby).  
  
##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition  
 Volání `GetItemPosition` – členská funkce získat souřadnice položky upravovaný na místě.  
  
```  
void GetItemPosition(LPRECT lpPosRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt, který chcete přijímat souřadnice položky.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou uváděny v pixelech relativně k okna aplikace kontejneru klientské oblasti.  
  
 Umístění můžete porovnat s aktuální rámeček výstřižek k určení rozsahu, který položka viditelné (nebo nejsou viditelné) na obrazovce.  
  
##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor  
 `GetZoomFactor` – Členská funkce určuje "faktor zvětšování" položky, kterou byla aktivována pro úpravy na místě.  
  
```  
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,  
    LPSIZE lpSizeDenom = NULL,  
    LPCRECT lpPosRect = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpSizeNum*  
 Ukazatel na objekt třídy `CSize` , bude obsahovat na faktor zvětšování čítači. Může být **NULL**.  
  
 *lpSizeDenom*  
 Ukazatel na objekt třídy `CSize` , bude obsahovat na faktor zvětšování jmenovatel. Může být **NULL**.  
  
 `lpPosRect`  
 Ukazatel na objekt třídy `CRect` , který popisuje nové umístění. Pokud tento argument je **NULL**, funkce, která používá aktuální umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka aktivována pro místní úpravy a jeho faktor zvětšování je než 100 % (1:1); jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Na faktor zvětšování v pixelech, je poměr velikost položky na aktuální velikost. Pokud aplikace kontejneru nebyla nastavena položky rozsah, jeho přirozené rozsah (počítáno od [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) se používá.  
  
 Funkce nastaví její první dva argumenty čítači a jmenovatel položky "faktor zvětšování." Pokud položka není upravovaný na místě, funkce tyto argumenty nastaví na výchozí hodnotu 100 % (nebo 1:1) a vrátí hodnotu 0. Další informace najdete v tématu technické Poznámka 40 [změny velikosti na místě MFC/OLE a Zooming](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
##  <a name="isdocobject"></a>COleServerDoc::IsDocObject  
 Určuje, zda dokument DocObject.  
  
```  
BOOL IsDocObject() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud dokument je DocObject; v opačném případě **FALSE**.  
  
##  <a name="isembedded"></a>COleServerDoc::IsEmbedded  
 Volání `IsEmbedded` členské funkce k určení, zda dokument reprezentuje objektu vloženého v kontejneru.  
  
```  
BOOL IsEmbedded() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `COleServerDoc` objekt je dokument, který představuje objekt, vložené v kontejneru; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Dokument načtený ze souboru není vložených, i když může být používán kontejneru aplikaci jako odkaz. Dokument, který je vložený v kontejneru dokumentu je považován za vložit.  
  
##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive  
 Volání `IsInPlaceActive` – členská funkce k určení, zda je položka v současné době v aktivním stavu na místě.  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `COleServerDoc` objekt je v místní aktivní; jinak hodnota 0.  
  
##  <a name="notifychanged"></a>COleServerDoc::NotifyChanged  
 Volání této funkce upozornit všechny propojené položky, které jsou připojené k dokumentu, který dokument byl změněn.  
  
```  
void NotifyChanged();
```  
  
### <a name="remarks"></a>Poznámky  
 Poté, co uživatel změní některé globální atribut třeba dimenze dokumentu na serveru se obvykle volání této funkce. Pokud položku OLE je propojený s automatické propojení dokumentu, položku aktualizovat tak, aby odrážely změny. V kontejneru aplikací vytvořených pomocí knihovny Microsoft Foundation Class [při změně](../../mfc/reference/coleclientitem-class.md#onchange) členské funkce `COleClientItem` je volána.  
  
> [!NOTE]
>  Tato funkce je zahrnuté pro kompatibilitu s OLE 1. Nové aplikace by měly používat [UpdateAllItems](#updateallitems).  
  
##  <a name="notifyclosed"></a>COleServerDoc::NotifyClosed  
 Volání této funkce zřetelně oznámit, že byla uzavřena dokumentu.  
  
```  
void NotifyClosed();
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel vybere příkaz Zavřít z nabídky Soubor `NotifyClosed` volá `COleServerDoc`na implementaci [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) – členská funkce. V kontejneru aplikací vytvořených pomocí knihovny Microsoft Foundation Class [při změně](../../mfc/reference/coleclientitem-class.md#onchange) členské funkce `COleClientItem` je volána.  
  
##  <a name="notifyrename"></a>COleServerDoc::NotifyRename  
 Jakmile uživatel přejmenuje dokumentu na serveru, volání této funkce.  
  
```  
void NotifyRename(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewName`  
 Ukazatel na řetězec určující název nového dokumentu na serveru; Obvykle se jedná o plně kvalifikovanou cestu.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel vybere příkazu Uložit jako z nabídky Soubor `NotifyRename` volá `COleServerDoc`na implementaci [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) – členská funkce. Tato funkce upozorní OLE systémové knihovny DLL, které pak oznámit kontejnerů. V kontejneru aplikací vytvořených pomocí knihovny Microsoft Foundation Class [při změně](../../mfc/reference/coleclientitem-class.md#onchange) členské funkce `COleClientItem` je volána.  
  
##  <a name="notifysaved"></a>COleServerDoc::NotifySaved  
 Jakmile uživatel uloží dokument serveru, volání této funkce.  
  
```  
void NotifySaved();
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel vybere příkaz Uložit z nabídky Soubor `NotifySaved` je volána pro vám `COleServerDoc`na implementaci [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Tato funkce upozorní OLE systémové knihovny DLL, které pak oznámit kontejnerů. V kontejneru aplikací vytvořených pomocí knihovny Microsoft Foundation Class [při změně](../../mfc/reference/coleclientitem-class.md#onchange) členské funkce `COleClientItem` je volána.  
  
##  <a name="onclose"></a>COleServerDoc::OnClose  
 Voláno rámcem, když kontejner požaduje, aby dokumentu na serveru je třeba ukončit.  
  
```  
virtual void OnClose(OLECLOSE dwCloseOption);
```  
  
### <a name="parameters"></a>Parametry  
 `dwCloseOption`  
 Hodnota z výčtu `OLECLOSE`. Tento parametr může mít jednu z následujících hodnot:  
  
- `OLECLOSE_SAVEIFDIRTY`Soubor zůstane uložen, pokud se změnila.  
  
- `OLECLOSE_NOSAVE`Soubor se zavřel bez uložení.  
  
- `OLECLOSE_PROMPTSAVE`Pokud soubor byl upraven, bude uživatel vyzván o uložení.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá `CDocument::OnCloseDocument`.  
  
 Další informace a další hodnoty, najdete v části [OLECLOSE](http://msdn.microsoft.com/library/windows/desktop/ms680623) ve Windows SDK.  
  
##  <a name="ondeactivate"></a>COleServerDoc::OnDeactivate  
 Voláno rámcem, když uživatel deaktivuje vložené nebo propojené položky, která je aktuálně místní aktivní.  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se obnoví do původního stavu kontejneru aplikace uživatelské rozhraní a zničí všechny nabídky a jiných ovládacích prvků, které byly vytvořeny pro aktivace na místě.  
  
 Informace o stavu operace vrácení zpět by měly být uvolněny bezpodmínečně v tomto okamžiku.  
  
 Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md)...  
  
##  <a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI  
 Voláno, když uživatel deaktivuje položku, která se aktivovala na místě.  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>Parametry  
 `bUndoable`  
 Určuje, zda mohou být změny vrátit zpět.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce obnoví uživatelské rozhraní aplikace kontejneru do původního stavu, skrytí žádné nabídky a jiných ovládacích prvků, které byly vytvořeny pro aktivace na místě.  
  
 Rozhraní framework vždy nastaví `bUndoable` k **FALSE**. Pokud je server podporuje vrácení zpět a operace, která lze vrátit zpět, volat základní třídy implementaci s `bUndoable` nastavena na **TRUE**.  
  
##  <a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate  
 Rozhraní framework volá tuto funkci aktivovat nebo deaktivovat okna dokumentu pro úpravy na místě.  
  
```  
virtual void OnDocWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 `bActivate`  
 Určuje, zda okna dokumentu je aktivace nebo deaktivace.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace odebere nebo ho přidá elementy rámce úrovni uživatelského rozhraní podle potřeby. Tato funkce přepsání, pokud chcete provádět další akce, pokud je aktivace nebo deaktivace dokument obsahující položky.  
  
 Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md)...  
  
##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd  
 Volá rámec této funkci můžete provést zadaný příkaz nebo zobrazit nápovědu pro příkaz.  
  
```  
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,  
    DWORD nCmdID,  
    DWORD nCmdExecOpt,  
    VARIANTARG* pvarargIn,  
    VARIANTARG* pvarargOut);
```  
  
### <a name="parameters"></a>Parametry  
 `pguidCmdGroup`  
 Ukazatel na identifikátor GUID, který identifikuje sadu příkazů. Může být **NULL** udávajících do výchozí skupiny příkaz.  
  
 `nCmdID`  
 Příkaz k provedení. Musí být ve skupině identifikovaný `pguidCmdGroup`.  
  
 *nCmdExecOut*  
 Způsob, jakým objekt by měla spustit příkaz, jeden nebo více z následujících hodnot z **OLECMDEXECOPT** výčtu:  
  
 **OLECMDEXECOPT_DODEFAULT**  
  
 **OLECMDEXECOPT_PROMPTUSER**  
  
 **OLECMDEXECOPT_DONTPROMPTUSER**  
  
 **OLECMDEXECOPT_SHOWHELP**  
  
 `pvarargIn`  
 Ukazatel na **VARIANTARG** obsahující vstupní argumenty pro příkaz. Může být **NULL**.  
  
 `pvarargOut`  
 Ukazatel na **VARIANTARG** přijímat vrácené hodnoty výstupu z příkazu. Může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` Pokud úspěšné, jinak hodnota jednu z následujících kódů chyb:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Došlo k neočekávané chybě|  
|**E_FAIL**|Došlo k chybě|  
|**E_NOTIMPL**|Označuje MFC samotné pokusí přeložit a odeslat příkaz|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`jinou hodnotu než **NULL** , ale neurčuje platný příkaz skupiny|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`nerozpoznal jako platný příkaz ve skupině`pguidCmdGroup`|  
|**OLECMDERR_DISABLED**|Příkaz určený `nCmdID` je zakázané a nelze provést|  
|**OLECMDERR_NOHELP**|Volající požádali o pomoc na příkaz identifikovaný `nCmdID` , ale je k dispozici žádná Nápověda|  
|**OLECMDERR_CANCELED**|Uživatel stornoval provádění|  
  
### <a name="remarks"></a>Poznámky  
 `COleCmdUI`slouží k povolení, aktualizovat a nastavit další vlastnosti příkazy DocObject uživatelského rozhraní. Po inicializaci jsou příkazy, můžete provést pomocí `OnExecOleCmd`.  
  
 Rozhraní framework volání funkce dřív, než se převede a odeslat příkaz OLE dokumentu. Nemusíte přepsat tuto funkci pro zpracování standardní příkazy OLE dokumentu, ale je nutné zadat přepsání pro tuto funkci, pokud chcete zpracovávat vlastních příkazů nebo zpracování příkazy, které přijímají parametry, nebo může vracet výsledky.  
  
 Většina příkazů, nezadávejte trvat argumenty nebo návratové hodnoty. Pro většinu příkazů můžete předat volající **NULL**s pro `pvarargIn` a `pvarargOut`. Pro příkazy, které očekávají vstupní hodnoty, volající deklarace a inicializace **VARIANTARG** proměnné a předejte ukazatel na proměnné v `pvarargIn`. Pro příkazy, které vyžadují jednu hodnotu, může být argument přímo v uložená **VARIANTARG** a předaný funkci. Více argumentů musí být zabalené v rámci **VARIANTARG** pomocí jedné z podporovaných typů (jako například `IDispatch` a **SAFEARRAY** ).  
  
 Podobně, pokud příkaz vrátí argumenty volající musí deklarovat **VARIANTARG**, inicializujte ho, aby `VT_EMPTY`a předejte adresy v `pvarargOut`. Pokud příkaz vrátí jednu hodnotu, objekt můžete uložit hodnotu přímo v `pvarargOut`. Více hodnot výstup musí být zabalené nějakým způsobem vhodné pro **VARIANTARG**.  
  
 Provede implementace třídy base této funkce **OLE_COMMAND_MAP** struktury související s cíl příkazu a zkuste odeslat příkaz pro příslušnou obslužnou rutinu. Implementace třídy base pracuje pouze s příkazy, které přijímají argumenty nebo návratové hodnoty. Pokud potřebujete pro zpracování příkazy, které přijímají argumenty nebo návratové hodnoty, musíte funkci přepsat a pracovat `pvarargIn` a `pvarargOut` parametry sami.  
  
##  <a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate  
 Pokud je aktivace nebo deaktivace oken s rámečkem kontejnerové aplikace volá rámec této funkce.  
  
```  
virtual void OnFrameWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 `bActivate`  
 Určuje, zda okně s rámečkem na aktivace nebo deaktivace.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace zruší všechny režimy nápovědy okně s rámečkem může být v. Tato funkce přepsání, pokud chcete provést zvláštní zpracování, pokud je aktivace nebo deaktivace rámce okna.  
  
 Další informace najdete v článku [aktivace](../../mfc/activation-cpp.md)...  
  
##  <a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem  
 Voláno rámcem, pokud aplikace kontejneru volá aplikaci server k vytvoření nebo úpravě vložené položky.  
  
```  
virtual COleServerItem* OnGetEmbeddedItem() = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na položku představující celý dokument; **NULL** Pokud operace se nezdařila.  
  
### <a name="remarks"></a>Poznámky  
 Neexistuje žádný výchozí implementace. Je nutné přepsat této funkci vrátíte položku, která představuje celý dokument. Tato návratová hodnota by měla být objekt `COleServerItem`-odvozené třídy.  
  
##  <a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo  
 Rozhraní framework volá tuto funkci, když uživatel vybere možnost vrátit zpět změny provedené v položku, která se aktivuje na místě, změnit a následně deaktivováno.  
  
```  
virtual BOOL OnReactivateAndUndo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace se nic nestane. kromě vrátit **FALSE** označující selhání.  
  
 Tato funkce přepsání, pokud vaše aplikace podporuje vrácení zpět. Obvykle provést operaci vrácení zpět a potom aktivovat položka voláním `ActivateInPlace`. Pokud je aplikace kontejneru napsané pomocí knihovny Microsoft Foundation Class, volání `COleClientItem::ReactivateAndUndo` způsobí, že tuto funkci, která se má volat.  
  
##  <a name="onresizeborder"></a>COleServerDoc::OnResizeBorder  
 Při změně velikosti okna s rámečkem kontejnerové aplikace volá rámec této funkce.  
  
```  
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,  
    LPOLEINPLACEUIWINDOW lpUIWindow,  
    BOOL bFrame);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRectBorder`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt, který určuje souřadnice ohraničení.  
  
 `lpUIWindow`  
 Ukazatel na objekt třídy **IOleInPlaceUIWindow** , který je vlastníkem aktuální relace úprav na místě.  
  
 *bFrame*  
 **Hodnota TRUE,** Pokud `lpUIWindow` odkazuje na oken s rámečkem nejvyšší úrovně aplikace typu kontejner, nebo **FALSE** Pokud `lpUIWindow` odkazuje na kontejner aplikace oken s rámečkem úrovni dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce změní a upraví panely nástrojů a další prvky uživatelského rozhraní v souladu s novou velikost okna.  
  
 Další informace najdete v tématu [IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716) ve Windows SDK.  
  
 Toto je rozšířené přepisovatelné.  
  
##  <a name="onsethostnames"></a>COleServerDoc::OnSetHostNames  
 Voláno rámcem při kontejneru nastaví změny nebo změny názvy hostitelů pro tento dokument.  
  
```  
virtual void OnSetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHost`  
 Ukazatel na řetězec, který určuje název aplikace kontejneru.  
  
 `lpszHostObj`  
 Ukazatel na řetězec, který určuje název kontejneru pro dokument.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace změní název dokumentu pro všechna zobrazení odkazující na tento dokument.  
  
 Funkci přepište, pokud je vaše aplikace nastaví názvy přes jiný mechanismus.  
  
##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Této funkci můžete umístění okna úpravy rámečkem na místě v okně s rámečkem kontejnerové aplikace volá framework.  
  
```  
virtual void OnSetItemRects(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt, který určuje pozici okna rámečkem na místě relativně ke kontejneru aplikace klientské oblasti.  
  
 `lpClipRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt, který určuje okno rámečkem na místě výstřižek obdélník relativní vzhledem k aplikaci kontejneru klientské oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete aktualizovat faktoru zvětšení zobrazení, v případě potřeby.  
  
 Tato funkce je volána obvykle v reakci `RequestPositionChange` zavolat, i když je možné volat kdykoli v kontejneru požadavek na změnu pozice pro položku na místě.  
  
##  <a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars  
 Volá rámec této funkci můžete zobrazit nebo skrýt ovládací pruhy serverová aplikace přidružené k rámce okna identifikovaný `pFrameWnd`.  
  
```  
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrameWnd`  
 Ukazatel na rámec okna jejichž ovládací pruhy by měla být skrytý nebo vidět.  
  
 `bShow`  
 Určuje, zda jsou ovládací pruhy zobrazen nebo skryt.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vytvoří výčet všech ovládací pruhy vlastníkem této oken s rámečkem a skryje nebo zobrazí je.  
  
##  <a name="onshowdocument"></a>COleServerDoc::OnShowDocument  
 Volání framework `OnShowDocument` kdy dokumentu na serveru musí být skrytý nebo vidět.  
  
```  
virtual void OnShowDocument(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Určuje, zda uživatelské rozhraní v dokumentu je zobrazen nebo skryt.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bShow` je **TRUE**, výchozí implementaci serverové aplikace, aktivuje se v případě potřeby a způsobí, že aplikace kontejneru posuňte jeho okna tak, aby položka. Pokud `bShow` je **FALSE**, výchozí implementace deaktivuje položky prostřednictvím volání `OnDeactivate`, ničí nebo skryje všechna okna s rámečkem vytvořené pro dokument, s výjimkou první z nich. Pokud žádné viditelné dokumenty zůstanou, skryje výchozí implementaci serverové aplikace.  
  
##  <a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument  
 Voláno rámcem při ukládání dokumentu, který je vložený položku v složeného dokumentu.  
  
```  
virtual BOOL OnUpdateDocument();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla úspěšně aktualizována v dokumentu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá [COleServerDoc::NotifySaved](#notifysaved) a [COleServerDoc::SaveEmbedding](#saveembedding) členské funkce a pak označí dokumentu jako vyčistit. Tato funkce přepsání, pokud chcete provést zvláštní zpracování při aktualizaci vložené položky.  
  
##  <a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange  
 Volání této funkce člen tak, aby měl kontejner aplikace změnit umístění.  
  
```  
void RequestPositionChange(LPCRECT lpPosRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt obsahující nové umístění.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle (ve spojení s `UpdateAllItems`) změny dat v aktivní položku na místě. Následující toto volání kontejner může nebo nemusí provést změnu voláním `OnSetItemRects`. Výsledný pozice se může lišit od požadované.  
  
##  <a name="saveembedding"></a>COleServerDoc::SaveEmbedding  
 Volání této funkce říct aplikace kontejner pro uložení vložený objekt.  
  
```  
void SaveEmbedding();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je automaticky volána z `OnUpdateDocument`. Všimněte si, že tato funkce způsobí položka, která má být aktualizován na disk, proto se obvykle označuje jako pouze v důsledku akce konkrétního uživatele.  
  
##  <a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy  
 Volání `ScrollContainerBy` členskou funkci pro posouvání kontejneru dokumentu o vzdálenost v pixelech indikován `sizeScroll`.  
  
```  
BOOL ScrollContainerBy(CSize sizeScroll);
```  
  
### <a name="parameters"></a>Parametry  
 `sizeScroll`  
 Určuje, jak daleko je dokument kontejneru posun.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Kladné hodnoty stanovují posouvání dolů a doprava; záporné hodnoty znamenat posouvání nahoru a doleva.  
  
##  <a name="updateallitems"></a>COleServerDoc::UpdateAllItems  
 Volání této funkce upozornit všechny propojené položky, které jsou připojené k dokumentu, který dokument byl změněn.  
  
```  
void UpdateAllItems(
    COleServerItem* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parametry  
 `pSender`  
 Ukazatel na položku upravit dokumentu nebo **NULL** všechny položky mají-li aktualizovat.  
  
 `lHint`  
 Obsahuje informace o této úpravy.  
  
 `pHint`  
 Ukazatel na objekt ukládání informací o úpravy.  
  
 `nDrawAspect`  
 Určuje, jak má být odeslána položky. Je to hodnota z `DVASPECT` výčtu. Tento parametr může mít jednu z následujících hodnot:  
  
- `DVASPECT_CONTENT`Položka je reprezentována tak, že lze zobrazit jako vložený objekt uvnitř jeho kontejneru.  
  
- `DVASPECT_THUMBNAIL`Položka je vykreslen v znázornění "miniaturu" tak, aby ji bylo možné zobrazit v nástroji procházení.  
  
- `DVASPECT_ICON`Položka je reprezentována ikonu.  
  
- `DVASPECT_DOCPRINT`Položka je reprezentována jako kdyby byly vytisknout, pomocí příkazu Tisk z nabídky soubor.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se obvykle volání, poté, co uživatel změní dokumentu na serveru. Pokud položku OLE je propojený s automatické propojení dokumentu, položku aktualizovat tak, aby odrážely změny. V kontejneru aplikací vytvořených pomocí knihovny Microsoft Foundation Class [při změně](../../mfc/reference/coleclientitem-class.md#onchange) členské funkce `COleClientItem` je volána.  
  
 Tato funkce volá `OnUpdate` – členská funkce pro všechny položky dokumentu s výjimkou odesílání položek, předávání `pHint`, `lHint`, a `nDrawAspect`. Použijte tyto parametry k předání informací k položkám o změny provedené v dokumentu. Můžete kódovat pomocí informace `lHint` nebo můžete definovat `CObject`-odvozené třídy k ukládání informací o změny a předat objekt této třídy pomocí `pHint`. Přepsání `OnUpdate` členské funkce ve vaší `COleServerItem`-odvozené třídy za účelem optimalizace, aktualizuje se každou položku v závislosti na tom, zda došlo ke změně jeho prezentaci.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [COleLinkingDoc – třída](../../mfc/reference/colelinkingdoc-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDocument – třída](../../mfc/reference/coledocument-class.md)   
 [COleLinkingDoc – třída](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer – třída](../../mfc/reference/coletemplateserver-class.md)
