---
title: "Třída CBaseTabbedPane | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs: C++
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eaabdbbcab97366aa272e51f57d215b63a0161a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane – třída
Rozšiřuje funkce [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) pro podporu vytváření záložkách windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|Výchozí konstruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseTabbedPane::AddTab](#addtab)|Přidá novou kartu záložkách podokna.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda může být zničený záložkách podokně aplikace prázdný.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Použije nastavení karet, které se načtou z registru, do záložkách podokna.|  
|[CBaseTabbedPane::CanFloat](#canfloat)|Určuje, zda můžete v podokně float. (Přepisuje [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda má popisek pro záložkách podokně zobrazit stejný text jako aktivní karty.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Přepisuje [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|Jeden nebo více lze ukotvit podokna převede do dokumentů s kartami MDI.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Povolí nebo zakáže schopnost podokně záložkách s text popisku na kartě active synchronizovat text titulku.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Interní pořadí se obnoví do výchozího stavu.|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Vrátí podokně, který se nachází na kartě, když na kartě je identifikována pořadové číslo od nuly.|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Vrátí podokno, ve kterém je určený podle ID podokně.|  
|[CBaseTabbedPane::FloatTab](#floattab)|Obtéká podokno, ale pouze, pokud se v podokně se aktuálně nachází v odpojitelných kartě.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Vrátí výchozí pořadí karet v podokně.|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Načte ukazatel na první kartě Zobrazit.|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|Načte minimální povolená velikost podokna. (Přepisuje [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Vrátí popisovač na ikonu podokně. (Přepisuje [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Vrátí seznam hodnot podokna, které jsou obsaženy v podokně s kartami.|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Vrátí ohraničující rámečky pro horní a dolní části karty.|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Vrátí počet karty v okně Karta.|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Získá základní okno Karta (zabalená).|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Vrátí počet zobrazených karty.|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda v záložkách podokně můžete přepnout do režimu automaticky skrýt.|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Určuje, zda je v záložkách podokně skryty-li jen jedné karty se zobrazí.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Používat interně během serializace.|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Přepočítá rozložení informace o podokně. (Přepisuje [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CBaseTabbedPane::RemovePane](#removepane)|Podokno se odebere z podokna s kartami.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Používat interně během serializace.|  
|`CBaseTabbedPane::Serialize`|(Přepisuje [CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6).)|  
|`CBaseTabbedPane::SerializeTabWindow`|Používat interně během serializace.|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Určuje, zda budou záložkách ovládacích pruhů automaticky zničena.|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Přepíná mezi zobrazí v podokně ukotvení a automaticky skrýt režimu. (Přepisuje [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|  
|[CBaseTabbedPane::ShowTab](#showtab)|Zobrazí nebo skryje na kartě.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je abstraktní třída a nelze vytvořit instanci. Implementuje služby, které jsou společné pro všechny typy záložkách podokna.  
  
 V současné době knihovny zahrnuje dvě třídy odvozené podokno s kartami: [CTabbedPane třída](../../mfc/reference/ctabbedpane-class.md) a [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 A `CBaseTabbedPane` ukazatel na zabalí objekt [CMFCBaseTabCtrl třída](../../mfc/reference/cmfcbasetabctrl-class.md) objektu. [Třída CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) se pak stane podřízeného okna na kartách panelu.  
  
 Další informace o tom, jak vytvořit záložkách podokna najdete v tématu [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane třída](../../mfc/reference/ctabbedpane-class.md), a [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>CBaseTabbedPane::AddTab  
 Přidá novou kartu záložkách podokna.  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pNewBar`  
 Ukazatel na podokno přidat. Po volání této metody se může stát neplatný ukazatel this. Další informace najdete v části poznámky.  
  
 [v]`bVisible`  
 `TRUE`ke zviditelnění kartě; v opačném `FALSE`.  
  
 [v]`bSetActive`  
 `TRUE`Chcete-li na kartě kartě active; v opačném `FALSE`.  
  
 [v]`bDetachable`  
 `TRUE`Chcete-li na kartě odpojitelných; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně byl úspěšně přidán jako na kartě a nebyl zrušen v procesu. `FALSE`Pokud je objekt typu podokno přidávané `CBaseTabbedPane`. Další informace najdete v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem přidání podokna jako novou kartu v záložkách podokně. Pokud `pNewBar` odkazuje na objekt typu `CBaseTabbedPane`, všechny její karty se zkopírují do podokna s kartami a potom `pNewBar` zničena. Proto `pNewBar` stane neplatný ukazatel, které by se neměla používat.  
  
##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 Určuje, zda může být zničený záložkách podokně aplikace prázdný.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud prázdnou – záložkami může být zničený podokně; v opačném `FALSE`. Výchozí implementace vždy vrátí `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud podokně aplikace prázdný záložkách nesmí být zničený, skryje rozhraní v podokně.  
  
##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 Načte nastavení na kartě z registru a použije je na kartách podokně.  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bUseTabIndexes`  
 Tento parametr se používá interně rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána rámcem, když ho znovu načte ukotvení informace o stavu z registru. Metoda získává informace o pořadí a názvy karet pro podokno s kartami.  
  
##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 Určuje, zda lze v záložkách podokně float.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně můžete float; v opačném `FALSE`.  
  
##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 Určuje, zda má popisek pro záložkách podokně zobrazit stejný text jako aktivní karty.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud text titulku na kartách panelu je nastavený na text kartě active; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Metoda slouží k určení, zda text na duplikáty titulek záložkách podokně zobrazí popisek kartě active. Můžete povolit nebo zakázat tuto funkci voláním [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).  
  
##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 Jeden nebo více lze ukotvit podokna převede do dokumentů s kartami MDI.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bActiveTabOnly`  
 Při převodu záložkách podokně zadejte `TRUE` převést pouze aktivní karty. Zadejte `FALSE` převést všechny karty v podokně.  
  
##  <a name="detachpane"></a>CBaseTabbedPane::DetachPane  
 Umožňuje odpojit podokně z podokna s kartami.  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na podokně odpojit.  
  
 [v]`bHide`  
 Logický parametr, který určuje, zda rozhraní skryje panel po je odpojená.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud rozhraní úspěšně odpojí podokna. `FALSE` Pokud `pBar` je `NULL` nebo odkazuje na podokně, který není v podokně s kartami.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework obtéká podokně odpojit Pokud je to možné. Další informace najdete v tématu [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).  
  
##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 Povolí nebo zakáže schopnost podokně záložkách s text popisku na kartě active synchronizovat text titulku.  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Proveďte synchronizaci s active karta titulek; titulek podokno s kartami v opačném `FALSE`.  
  
##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray  
 Interní pořadí se obnoví do výchozího stavu.  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když rozhraní obnoví panel aplikace Outlook počátečního stavu.  
  
##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID  
 Vrátí podokno identifikovaný podokně ID.  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uBarID`  
 Určuje ID podokně, který se má najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na podokně, pokud bylo zjištěno; v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda Porovná všechny karty v podokně a vrátí jednu s ID určeného `uBarID` parametr.  
  
##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 Vrátí podokně, který se nachází na kartě.  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTabNum`  
 Určuje index založený na nule karty pro načtení.  
  
 [v]`bGetWrappedBar`  
 `TRUE`Chcete-li vrátit okno základní (zabalené) v podokně místo v podokně sama o sobě; v opačném případě `FALSE`. To platí jenom pro odvozený z podokna [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je nalezena v podokně, je vrácena platný ukazatel do podokna prohledávaný pro; v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem načtení podokně umístěných v kartě určeného `nTabNum` parametr.  
  
##  <a name="floattab"></a>CBaseTabbedPane::FloatTab  
 Obtéká podokno, ale pouze, pokud se v podokně se aktuálně nachází v odpojitelných kartě.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pBar`  
 Ukazatel na podokno float.  
  
 [v]`nTabID`  
 Určuje index založený na nule karty na float.  
  
 [v]`dockMethod`  
 Určuje metodu sloužící k uvolnit podokně. Další informace najdete v části poznámky.  
  
 [v]`bHide`  
 `TRUE`Chcete-li skrýt podokno před plovoucí; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně obtékané; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem podokně, který se aktuálně nachází na kartě odpojitelných float.  
  
 Pokud chcete odpojit podokno prostřednictvím kódu programu, zadejte `DM_SHOW` pro `dockMethod` parametr. Pokud chcete uvolnit podokno ve stejné pozici, kde obtékané dříve, zadejte `DM_DBL_CLICK` jako `dockMethod` parametr.  
  
##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 Vrátí výchozí pořadí karet v podokně.  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CArray` objekt, který určuje výchozí pořadí karet v podokně.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při panel aplikace Outlook se resetují na počátečního stavu.  
  
##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 Načte ukazatel na první kartě Zobrazit.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iTabNum`  
 Odkaz na celé číslo. Tato metoda zapíše index založený na nule první zobrazené karty tento parametr nebo -1, pokud ne, zobrazí je zjištěno, že karta.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ukazatel na první kartě zobrazených; v opačném `NULL`.  
  
##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 Načte minimální povolená velikost podokna.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`size`  
 A `CSize` objekt, který je vyplněn minimální povolená velikost.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktivní konzistentní zpracování podokně minimální velikostí ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` je vyplněn minimální povolená velikost active karty. V opačném `size` je vyplněn návratová hodnota [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 Načte minimální povolená velikost podokna.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`size`  
 A `CSize` objekt, který je vyplněn minimální povolená velikost.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktivní konzistentní zpracování podokně minimální velikostí ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` je vyplněn minimální povolená velikost active karty. V opačném `size` je vyplněn návratová hodnota [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 Vrátí seznam hodnot podokna, které jsou obsaženy v podokně s kartami.  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`lst`  
 A `CObList` je vyplněn podokna, které jsou obsaženy v podokně s kartami.  
  
 [v]`pRTCFilter`  
 Pokud není `NULL`, vrácený seznam obsahuje pouze podokna, které jsou zadané runtime třídy.  
  
##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 Vrátí ohraničující rámečky pro horní a dolní části karty.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rectTabAreaTop`  
 Souřadnice obrazovky oblasti horní karty obdrží.  
  
 [out]`rectTabAreaBottom`  
 Souřadnice obrazovky nižší oblast karty obdrží.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem určení ohraničující obdélníky v souřadnice obrazovky pro horní a dolní karta oblasti.  
  
##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 Vrátí počet karty v okně Karta.  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet karet v podokně s kartami.  
  
##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow  
 Získá základní okno Karta (zabalená).  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na základní okno s kartou.  
  
##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 Vrátí počet viditelné karty.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet viditelné karet, které bude větší než nebo rovna hodnotě nula.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu můžete určit počet viditelné karty v podokně s kartami.  
  
##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode  
 Určuje, zda v záložkách podokně můžete přepnout do režimu autohide –.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně můžete přepnout do režimu autohide –; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud autohide – režimu je zakázané, žádné tlačítko PIN kódu se zobrazí na titulek podokno s kartami.  
  
##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 Určuje, zda je v záložkách podokně skryty-li jen jedné karty se zobrazí.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud není okno s kartou zobrazeny po pouze jedna karta viditelná; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se v podokně se nezobrazí, protože je otevřena pouze jedna karta, můžete volat tuto metodu za účelem určení, zda v záložkách podokně pracuje správně.  
  
##  <a name="removepane"></a>CBaseTabbedPane::RemovePane  
 Podokno se odebere z podokna s kartami.  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v] [out]`pBar`  
 Ukazatel na podokno odebrat z podokna s kartami.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud v podokně byla úspěšně odebrána z podokna s kartami a v podokně s kartami je stále platný. `FALSE`Pokud podokně poslední byla odebrána z podokna s kartami a podokně záložkách je zničena. Pokud je vrácenou hodnotou `FALSE`, nepoužívejte v záložkách podokně víc.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze odebrat podokně určeného `pBar` parametr z podokna s kartami.  
  
##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 Určuje, zda budou záložkách ovládacích pruhů automaticky zničena.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bAutoDestroy`  
 `TRUE`Pokud podokno s kartami byl vytvořen dynamicky a nejsou řízení celé jeho životnosti; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Nastavit režim pro automatické zrušení `TRUE` Pokud vytvoříte záložkách podokně dynamicky a nejsou řízení celé jeho životnosti. Pokud automatické zrušení režim je `TRUE`, v podokně s kartami budou automaticky zničena rámcem.  
  
##  <a name="showtab"></a>CBaseTabbedPane::ShowTab  
 Zobrazí nebo skryje na kartě.  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pBar`  
 Ukazatel na podokně můžete zobrazit nebo skrýt.  
  
 [v]`bShow`  
 `TRUE`k zobrazení podokna. `FALSE` ke skrytí podokna.  
  
 [v]`bDelay`  
 `TRUE`zpoždění před úpravou na kartě rozložení; v opačném `FALSE`.  
  
 [v]`bActivate`  
 `TRUE`Chcete-li na kartě kartě active; v opačném `FALSE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud na kartě byla buď zobrazen nebo skryt úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Když zavoláte tuto metodu, podokno je buď zobrazen nebo skryt, v závislosti na hodnotě `bShow` parametr. Pokud skrýt na kartě a je kartě poslední viditelné v okně základní karta, v podokně s kartami je skrytá. Pokud na kartě se zobrazují, když bylo dříve žádné karty viditelné, zobrazí se podokno s kartami.  
  
##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 Přepočítá rozložení informace o podokně.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je v podokně plovoucí, tato metoda upozorní framework změnit velikost podokna aktuální velikosti zkrácená rámečku.  
  
 Pokud je ukotveno podokně, tato metoda neprovede žádnou akci.  
  
##  <a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode  
 V podokně s kartami nastaví režim automaticky skrýt pro odpojitelných podokna.  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bMode`  
 `TRUE`Pokud chcete povolit režim automaticky skrýt; `FALSE` povolení regulární ukotvení režimu.  
  
 [v]`dwAlignment`  
 Určuje zarovnání automaticky skrýt podokno, které se má vytvořit. Seznam možných hodnot najdete v tématu [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).  
  
 [v] [out]`pCurrAutoHideBar`  
 Ukazatel na panelu nástrojů aktuální automaticky skrýt. Může být `NULL`.  
  
 [v]`bUseTimer`  
 Určuje, jestli použít účinek automaticky skrýt, když uživatel přejde do režimu automaticky skrýt v podokně nebo skrýt podokno okamžitě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na panelu nástrojů automaticky skrýt, který se vytvoří při přechodu do režimu automaticky skrýt, nebo `NULL` Pokud je vytvořen bez panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework, když uživatel vybere tlačítko pin přepnout podokně záložkách automaticky skrýt režimu nebo regulární ukotvení režimu.  
  
 Automaticky skrýt režim je nastaven pro každý odpojitelných podokně, v podokně s kartami. Podokna, které jsou bez odpojitelných se ignorují. Další informace najdete v tématu [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).  
  
 Voláním této metody lze přepnout na kartách podokně automaticky skrýt režimu prostřednictvím kódu programu. V podokně musí být ukotvena hlavního okna rámce ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musí vrátit platný ukazatel [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
