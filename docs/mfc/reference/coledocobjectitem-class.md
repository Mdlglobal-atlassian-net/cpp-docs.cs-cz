---
title: Třída COleDocObjectItem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0842904ddb6e534cabc9fff8b5d2b2b4855f410
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37042206"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem – třída
Obsahování pro aktivní dokument implementuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Vytvoří `COleDocObject` položky.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Vytiskne dokument kontejneru aplikaci pomocí výchozího nastavení tiskárny.|  
|[COleDocObjectItem::ExecCommand](#execcommand)|Provede příkaz zadaný uživatelem.|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|Načte aktivní zobrazení dokumentu.|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|Počet stránek v aplikaci kontejneru dokumentu načte.|  
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Připraví dokumentu aplikace typu kontejner pro tisk.|  
|[COleDocObjectItem::OnPrint](#onprint)|Vytiskne dokument aplikace typu kontejner.|  
|[COleDocObjectItem::QueryCommand](#querycommand)|Dotazy na stav jednoho nebo více příkazů vygenerované uživatelské rozhraní události.|  
|[COleDocObjectItem::Release](#release)|Uvolní připojení k propojené položky OLE a zavře se v případě, že byla otevřena. Nezničí klientské položky.|  
  
## <a name="remarks"></a>Poznámky  
 V prostředí MFC se podobně zpracovává aktivní dokument na místě, regulární upravitelné vkládání, s následující rozdíly:  
  
-   `COleDocument`-Odvozené třídy stále udržuje seznam aktuálně vložené položky; však mohou být tyto položky `COleDocObjectItem`-odvozené položky.  
  
-   Při aktivním aktivní dokument zabírá celého klienta zobrazení, když je aktivní na místě.  
  
-   Kontejner pro aktivní dokument má plnou kontrolu nad **pomoci** nabídky.  
  
-   **Pomoci** nabídky obsahuje položky nabídky pro kontejner pro aktivní dokument i server.  
  
 Protože vlastní kontejner pro aktivní dokument **pomoci** nabídce kontejneru je zodpovědná za předávání serveru **pomoci** nabídky zprávy na server. Tato integrace se zpracovává souborem `COleDocObjectItem`.  
  
 Další informace o slučování nabídek a aktivaci aktivní dokument, najdete v části Přehled [obsahování pro aktivní dokument](../../mfc/active-document-containment.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem  
 Volání této funkce člen k chybě při inicializaci `COleDocObjectItem` objektu.  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pContainerDoc*  
 Ukazatel `COleDocument` objekt, který funguje jako kontejner pro aktivní dokument. Tento parametr musí být **NULL** povolit **IMPLEMENT_SERIALIZE**. Obvykle se vytvářejí OLE – položky s jinou hodnotu než **NULL** ukazatel dokumentu.  
  
##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting  
 Voláno rámcem do dokumentu pomocí výchozích nastavení.  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pCaller*  
 Ukazatel [CView](../../mfc/reference/cview-class.md) objekt, který odesílá příkaz pro tisk.  
  
 *pInfo*  
 Ukazatel [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) objekt, který popisuje úlohy k tisku.  
  
##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand  
 Volání této funkce člen ke spuštění příkazu specifikovaných uživatelem.  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nCmdID*  
 Identifikátor provedení příkazu. Musí být ve skupině identifikovaný *pguidCmdGroup*.  
  
 *nCmdExecOpt*  
 Určuje možnosti provedení příkazu. Ve výchozím nastavení se spustit příkaz bez výzvy pro uživatele. V tématu [OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930) seznam hodnot.  
  
 *pguidCmdGroup*  
 Jedinečný identifikátor skupiny pro příkaz. Ve výchozím nastavení **NULL**, která určuje skupiny standardní. Příkaz předaná *nCmdID* musí patřit do skupiny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěšného; jinak vrátí jeden z následující kódy chyb.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Došlo k neočekávané chybě.|  
|**E_FAIL**|Došlo k chybě.|  
|**E_NOTIMPL**|Označuje MFC samotné pokusí přeložit a odeslat příkaz.|  
|**OLECMDERR_E_UNKNOWNGROUP**|*pguidCmdGroup* jinou hodnotu než **NULL** , ale neurčuje skupinu platný příkaz.|  
|**OLECMDERR_E_NOTSUPPORTED**|*nCmdID* nerozpoznal jako platný příkaz v pGroup skupiny.|  
|**OLECMDERR_DISABLED**|Příkaz určený *nCmdID* je zakázána a nelze ho provést.|  
|**OLECMDERR_NOHELP**|Volající požádali o pomoc na příkaz identifikovaný *nCmdID* , ale je k dispozici žádná nápověda.|  
|**OLECMDERR_CANCELLED**|Uživatel stornoval provádění.|  
  
### <a name="remarks"></a>Poznámky  
 *PguidCmdGroup* a *nCmdID* parametry společně jednoznačně příkaz k vyvolání. *NCmdExecOpt* parametr určuje přesné akci provést.  
  
##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView  
 Volání této funkce člen získat ukazatel `IOleDocumentView` rozhraní aktuálně aktivního zobrazení.  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [IOleDocumentView](http://msdn.microsoft.com/library/windows/desktop/ms678455) rozhraní aktuálně aktivního zobrazení. Pokud není žádná aktuální zobrazení, vrátí **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Počet odkazů na vrácený `IOleDocumentView` ukazatel není zvýší dřív, než se vrátí pomocí této funkce.  
  
##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount  
 Volání této funkce člen načíst počet stránek v dokumentu.  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>Parametry  
 *pnFirstPage*  
 Ukazatel na číslo první stránky dokumentu. Může být **NULL**, což naznačuje volající nepotřebuje toto číslo.  
  
 *pcPages*  
 Ukazatel na celkový počet stránek v dokumentu. Může být **NULL**, což naznačuje volající nepotřebuje toto číslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting  
 Tato funkce člen je voláno rámcem Příprava dokumentu pro tisk.  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pCaller*  
 Ukazatel [CView](../../mfc/reference/cview-class.md) objekt, který odesílá příkaz pro tisk.  
  
 *pInfo*  
 Ukazatel [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) objekt, který popisuje úlohy k tisku.  
  
 *bPrintAll*  
 Určuje, zda celý dokument k tisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="onprint"></a>  COleDocObjectItem::OnPrint  
 Tato funkce člen je voláno rámcem tisk dokumentu.  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pCaller*  
 Ukazatel na CView objekt, který odesílá příkaz pro tisk.  
  
 *pInfo*  
 Ukazatel [cprintinfo –](../../mfc/reference/cprintinfo-structure.md) objekt, který popisuje úlohy k tisku.  
  
 *bPrintAll*  
 Určuje, zda celý dokument k tisku.  
  
##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand  
 Dotazy na stav jednoho nebo více příkazů vygenerované uživatelské rozhraní události.  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nCmdID*  
 identifikátor příkazu, která je dotazována pro.  
  
 *pdwStatus*  
 Ukazatel na příznaky vrátí jako výsledek dotazu. Seznam možných hodnot najdete v tématu [OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237).  
  
 *pCmdText*  
 Ukazatel na [OLECMDTEXT](http://msdn.microsoft.com/library/windows/desktop/ms693314) struktury, ve kterém k vrácení informací o název a stav pro jeden příkaz. Může být **NULL** indikující, že volající není nutné tyto informace.  
  
 *pguidCmdGroup*  
 Jedinečný identifikátor skupiny příkaz; může být **NULL** určíte standardní skupinu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplný seznam všech návratové hodnoty, najdete v části [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) metoda, jak je popsáno v sadě Windows SDK.  
  
##  <a name="release"></a>  COleDocObjectItem::Release  
 Uvolní připojení k propojené položky OLE a zavře se v případě, že byla otevřena. Nezničí klientské položky.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Parametry  
 *dwCloseOption*  
 Příznak určující, za jakých okolností je položka OLE uložena, až se obnoví načíst stav. Seznam možných hodnot najdete v tématu [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).  
  
### <a name="remarks"></a>Poznámky  
 Nezničí klientské položky.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MFCBIND](../../visual-cpp-samples.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleClientItem – třída](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem – třída](../../mfc/reference/cdocobjectserveritem-class.md)
