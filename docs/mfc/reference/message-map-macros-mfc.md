---
title: Zpráva makra mapy (MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
dev_langs:
- C++
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e68cdc236759776fa327b4602343ec9ac73b9bba
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338363"
---
# <a name="message-map-macros-mfc"></a>Makra map zpráv (MFC)
Pro podporu mapy zpráv, knihovna MFC poskytuje následující makra:  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>Mapování zpráv deklarace a Rozhraničení makra  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklaruje, že mapy zpráv se použije ve třídě pro mapování zpráv na funkce (musí se použít v deklaraci třídy).|  
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Začíná definici mapy zpráv (musí být použitý v implementaci třídy).|  
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_interface_map)|Začíná definici mapy zpráv na typ třídy obsahující jednu šablonu argumentu. |
|[END_MESSAGE_MAP](#end_message_map)|Ukončí definici mapy zpráv (musí být použitý v implementaci třídy).|  
  
### <a name="message-mapping-macros"></a>Makra mapování zpráv  
  
|||  
|-|-|  
|[ON_COMMAND](#on_command)|Určuje funkci, která bude zpracovávat zprávy zadaný příkaz.|  
|[ON_COMMAND_EX](#on_command_ex)|Určuje funkci, která bude zpracovávat zprávy zadaný příkaz.|  
|[ON_CONTROL](#on_control)|Určuje funkci, která bude zpracovávat zprávy zadané oznámení ovládacího prvku.|  
|[ON_MESSAGE](#on_message)|Určuje funkci, která bude zpracovávat uživatelsky definovanou zprávu.|  
|[ON_OLECMD](#on_olecmd)|Určuje funkci, která zpracuje příkaz nabídky z DocObject nebo svého kontejneru.|  
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Určuje funkci, která bude zpracovávat registrované uživatelsky definovanou zprávu.|  
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Určuje funkci, která bude zpracovávat registrované uživatelsky definovanou zprávu, když máte `CWinThread` třídy.|  
|[ON_THREAD_MESSAGE](#on_thread_message)|Určuje funkci, která bude zpracovávat uživatelsky definovanou zprávu, když máte `CWinThread` třídy.|  
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Určuje funkci, která bude zpracovávat zprávou příkazu update zadaného uživatelského rozhraní.|  
  
### <a name="message-map-range-macros"></a>Makra Map zpráv rozsahu  
  
|||  
|-|-|  
|[ON_COMMAND_RANGE](#on_command_range)|Určuje funkci, která bude zpracovávat rozsah ID příkazů zadaný v prvních dvou parametrů do makra.|  
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Určuje, které obslužná rutina aktualizace bude zpracovávat rozsah ID příkazů zadaný v prvních dvou pa] rametry do makra.|  
|[ON_CONTROL_RANGE](#on_control_range)|Určuje funkci, která bude zpracovávat upozornění z rozsahu ID zadané v druhý a třetí parametry makro ovládacích prvků. První parametr je zpráva oznámení ovládacího prvku, jako je například BN_CLICKED.|  
  
 Další informace o mapy zpráv, map zpráv deklarace a rozhraničení makra a makra mapování zpráv, najdete v části [mapy zpráv](../../mfc/reference/message-maps-mfc.md) a [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md). Další informace o oblasti map zpráv najdete v tématu [obslužné rutiny pro oblasti Map zpráv](../../mfc/handlers-for-message-map-ranges.md).  


## <a name="begin_message_map"></a> BEGIN_MESSAGE_MAP
Začíná definici mapy zpráv.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_MESSAGE_MAP( theClass, baseClass )  
```  
  
### <a name="parameters"></a>Parametry  
 *theClass*  
 Určuje, že je název třídy namapujte tento parametr jehož zprávy.  
  
 *baseClass*  
 Určuje název základní třídy *theClass*.  
  
### <a name="remarks"></a>Poznámky  
 V souboru implementace (.cpp), který definuje členské funkce třídy mapu zpráv začínat BEGIN_MESSAGE_MAP – makro pak přidat makro položky pro každý z vašich funkcí obslužná rutina zprávy a mapování zpráv END_MESSAGE_MAP dokončení makra.  
  
 Další informace o mapách zpráv najdete v tématu [mapy zpráv](message-maps-mfc.md)  
  
### <a name="example"></a>Příklad  
```cpp  
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h 

##  <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP
Začíná definici mapy zpráv na typ třídy obsahující jednu šablonu argumentu.  
   
### <a name="syntax"></a>Syntaxe  
  ```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )  
```
### <a name="parameters"></a>Parametry  
 *theClass*  
 Určuje, že je název třídy namapujte tento parametr jehož zprávy.    
 *type_name*  
 Název parametru šablony určeného pro třídu.    
 *baseClass*  
 Určuje název základní třídy *theClass*.  
   
### <a name="remarks"></a>Poznámky  
 Toto makro je podobný [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) – makro; toto makro je však určena pro třídy obsahující jednu šablonu argumentu.  
  
 V části způsob implementace třídy začněte mapu zpráv BEGIN_TEMPLATE_MESSAGE_MAP makra. pak přidejte – makro položky pro každou z metod vaše obslužná rutina zprávy, jako byste to udělali pro mapování standardní zprávy. S BEGIN_MESSAGE_MAP – makro dokončení mapu zpráv šablonu s [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) – makro.  
  
 Další informace o implementaci mapy zpráv pro šablony třídy najdete [postupy: vytvoření mapy zpráv pro třídu šablony](../how-to-create-a-message-map-for-a-template-class.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
 
## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP
 Deklaruje, že třída definuje mapy zpráv. Každý `CCmdTarget`-odvozené třídy v aplikaci musíte zadat mapy zpráv pro zpracování zpráv.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
DECLARE_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Poznámky  
 Použití DECLARE_MESSAGE_MAP – makro na konec deklarace třídy. Potom v souboru .cpp, který definuje členské funkce třídy, použijte BEGIN_MESSAGE_MAP – makro, makro položky pro každý z vašich funkcí obslužná rutina zprávy a END_MESSAGE_MAP – makro.  
  
> [!NOTE]
>  Pokud jste po DECLARE_MESSAGE_MAP deklarování jakéhokoli člena, je nutné zadat nový typ přístupu (**veřejné**, **privátní**, nebo **chráněné**) pro ně.  
  
 Další informace o mapy zpráv a DECLARE_MESSAGE_MAP – makro, naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Příklad  
```cpp  
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
``` 
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  


## <a name="end_message_map"></a>  END_MESSAGE_MAP
Ukončí definici mapy zpráv.  
  
### <a name="syntax"></a>Syntaxe  
  
```   
END_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace o mapy zpráv a END_MESSAGE_MAP – makro, naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  

## <a name="on_command"></a>  ON_COMMAND
Toto makro mapuje zprávou příkazu na členskou funkci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_COMMAND( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 ID příkazu.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke které je mapován tento příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Označuje funkci, která zpracuje příkaz zprávu od objektu uživatelského rozhraní příkaz například položka nabídky nebo panelu nástrojů tlačítko.  
  
 Wm_command – Windows zprávu se zadaným ID přijetí příkazu cílový objekt ON_COMMAND bude volat členské funkce `memberFxn` ke zpracování zprávy.  
  
 ON_COMMAND používejte k mapování jediným příkazem na členskou funkci. Použití [ON_COMMAND_RANGE](#on_command_range) mapovat celou řadu ID příkazů na jednu členskou funkci. Pouze jedna položka mapování zpráv může odpovídat id daného příkazu. Příkaz tedy nelze mapovat na více než jednu obslužnou rutinu. Další informace a příklady najdete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Příklad  
```cpp  
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
``` 
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

 ## <a name="on_command_ex"></a>  ON_COMMAND_EX
Rozšířené obslužná rutina příkazu členskou funkci.  
   
### <a name="syntax"></a>Syntaxe  
  ```  
ON_COMMAND_EX(id, memberFxn);  
```
### <a name="parameters"></a>Parametry  
 *id*  
 ID příkazu.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke které je mapován tento příkaz.  
   
### <a name="remarks"></a>Poznámky 
Vyžaduje rozšířený formát obslužné rutiny zpráv příkaz je k dispozici pro rozšířené použití. ON_COMMAND_EX – makro se používá pro tyto obslužné rutiny zpráv a nabízí nadmnožinu funkcí [ON_COMMAND] (#on_command).  Rozšířené obslužná rutina příkazu členské funkce vyžadovat jeden parametr, UINT, obsahující Identifikátor příkazu a vrátit logickou hodnotu. Návratová hodnota by měla být hodnota TRUE pro 

Toto makro mapuje zprávou příkazu rozšířené obslužná rutina příkazu členské funkce.  
   
### <a name="syntax"></a>Syntaxe  
```  
ON_COMMAND_EX(id,  memberFxn);  
```
### <a name="parameters"></a>Parametry  
 *id*  
 ID příkazu.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke které je mapován tento příkaz.  
   
### <a name="remarks"></a>Poznámky  
 Vyžaduje rozšířený formát obslužné rutiny zpráv příkaz je k dispozici pro rozšířené použití. ON_COMMAND_EX – makro se používá pro tyto obslužné rutiny zpráv a nabízí nadmnožinu [ON_COMMAND](message-map-macros-mfc.md#on_command) funkce. Rozšířené obslužná rutina příkazu členské funkce vyžadovat jeden parametr, UINT, obsahující Identifikátor příkazu a vrátit logickou hodnotu. Vrácená hodnota musí být TRUE označuje, že byla zpracována příkazu; jinak směrování bude pokračovat na další příkaz cílové objektů.  
Další informace viz technická Poznámka [TN006: mapy zpráv] tm006. zpráva maps.md).  
   
### <a name="requirements"></a>Požadavky  
 Soubor hlaviček: afxmsg_.h  
   
### <a name="see-also"></a>Viz také  
 [ON_COMMAND](message-map-macros-mfc.md#on_command)   
 [TN006: mapy zpráv] tm006. zpráva maps.md)

  
## <a name="on_control"></a>  ON_CONTROL
Určuje funkci, která bude zpracovávat zprávu oznámení na vlastní ovládací prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_CONTROL( wNotifyCode, id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *funkci wNotifyCode*  
 Kód upozornění ovládacího prvku.  
  
 *id*  
 ID příkazu.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke které je mapován tento příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Zprávy s oznámením ovládacího prvku jsou odesílána z ovládacího prvku nadřazenému oknu.  
  
 Měla by existovat právě jeden příkaz ON_CONTROL – makro v mapy zpráv pro každou zprávu oznámení ovládacího prvku, který musí být namapována na funkci obslužná rutina zprávy.  
  
 Další informace a příklady najdete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  
  

## <a name="on_message"></a>  ON_MESSAGE  
Určuje funkci, která bude zpracovávat uživatelsky definovanou zprávu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *message*  
 ID zprávy.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke kterému je namapována zprávu.  
  
 Typ funkce musí být `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.  
  
### <a name="remarks"></a>Poznámky  
 Uživatelem definované zprávy jsou všechny zprávy, které nejsou standardní zprávy Windows WM_MESSAGE. Při výběru ID zprávy, používaly k 0xBFFF hodnot v rámci rozsahu WM_USER (0x0400) 0x7FFF nebo WM_APP (0x8000). Další informace o ID zpráv, najdete v části [WM_APP](http://msdn.microsoft.com/library/windows/desktop/ms644930).  
  
 Měla by existovat právě jeden příkaz ON_MESSAGE – makro v mapy zpráv pro každou zprávu definovaný uživatelem, který musí být namapována na funkci obslužné rutiny zprávy.  
  
> [!NOTE]
>  Kromě uživatelem definované zprávy zpracovává ON_MESSAGE méně běžné zpráv Windows. Další informace najdete v článku znalostní báze Microsoft Knowledge Base [99848: INFO: použití ON_MESSAGE() makra Map zpráv méně běžné](http://go.microsoft.com/fwlink/p/?linkid=192022).  
  
 Další informace a příklady najdete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md) a [uživatelem definované obslužné rutiny](user-defined-handlers.md)  
  
### <a name="example"></a>Příklad  
```cpp  
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
 afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

 LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here. 

   return 0;
}
```   
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

## <a name="on_olecmd"></a>  ON_OLECMD  
Směrovat příkazy přes rozhraní příkazového řádku odeslání `IOleCommandTarget`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_OLECMD( pguid, olecmdid, id )  
```  
  
### <a name="parameters"></a>Parametry  
 *pguid*  
 Identifikátor příkazu skupiny, ke kterému patří tento příkaz. Použijte hodnotu NULL pro standardní skupiny.  
  
 *olecmdid*  
 Identifikátor příkazu OLE.  
  
 *id*  
 ID nabídky, ID nástrojů, tlačítko ID nebo jiné ID prostředku nebo objekt příkazu.  
  
### <a name="remarks"></a>Poznámky  
 `IOleCommandTarget` Umožňuje kontejner přijímají příkazy, které pocházejí z uživatelského rozhraní DocObject a umožňuje kontejneru odeslat stejné příkazy (jako je například nový, otevřít, uložit jako a tisk v nabídce Soubor; a zkopírujte, vložit, a tak dále zpět v nabídce Úpravy) k DocObject.  
  
 `IOleCommandTarget` je jednodušší než OLE Automation `IDispatch`. `IOleCommandTarget` spoléhá výhradně na standardní sadu příkazů, který obvykle nemusí argumenty a nepodílí žádné informace o typu (bezpečnost typů je oslabená a argumentů příkazu). Pokud potřebujete k odeslání příkazů s argumenty, použijte [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).  
  
 `IOleCommandTarget` Standardní příkazy byly implementovány v prostředí MFC v následující makra:  
  
 **ON_OLECMD_CLEARSELECTION)**  
  
 Odešle příkaz pro vymazání upravit. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`  
  
 **ON_OLECMD_COPY)**  
  
 Odešle příkaz Upravit kopii. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`  
  
 **ON_OLECMD_CUT)**  
  
 Odešle příkaz Upravit vyjmout. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`  
  
 **ON_OLECMD_NEW)**  
  
 Odešle příkaz Nový soubor. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`  
  
 **ON_OLECMD_OPEN)**  
  
 Odešle příkaz Otevřít soubor. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`  
  
 **ON_OLECMD_PAGESETUP)**  
  
 Odešle příkaz souboru nastavení stránky. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`  
  
 **ON_OLECMD_PASTE)**  
  
 Odešle příkaz Upravit vložit. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`  
  
 **ON_OLECMD_PASTESPECIAL)**  
  
 Odešle příkaz Upravit Vložit jinak. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`  
  
 **ON_OLECMD_PRINT)**  
  
 Odešle příkaz Tisk souboru. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`  
  
 **ON_OLECMD_PRINTPREVIEW)**  
  
 Odešle příkaz Náhled tisku souboru. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`  
  
 **ON_OLECMD_REDO)**  
  
 Odešle příkaz upravit znovu. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`  
  
 **ON_OLECMD_SAVE)**  
  
 Odešle zprávu příkazu soubor uložit. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`  
  
 **ON_OLECMD_SAVE_AS)**  
  
 Odešle zprávu příkazu Uložit jako. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`  
  
 **ON_OLECMD_SAVE_COPY_AS)**  
  
 Odešle zprávu příkazu soubor uložit kopii jako. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`  
  
 **ON_OLECMD_SELECTALL)**  
  
 Odešle příkaz Upravit vybrat vše. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`  
  
 **ON_OLECMD_UNDO)**  
  
 Odešle příkaz vrátit zpět úpravy. Implementovat jako:  
  
 `ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocob.h  
  
### <a name="see-also"></a>Viz také  
 [Colecmdui – třída](colecmdui-class.md)   
 [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE
Windows `RegisterWindowMessage` funkce se používá k definování novou zprávu okna, která je zaručeně jedinečná v celém systému.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *nMessageVariable*  
 Proměnná ID registrované zprávy okna.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke kterému je namapována zprávu.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro označuje funkci, která bude zpracovávat registrované zprávy.  
  
 Další informace a příklady najdete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Příklad  
```cpp  
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));


BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  
  
### <a name="see-also"></a>Viz také  
 [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947)   
 [Uživatelem definované obslužné rutiny](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>  ON_REGISTERED_THREAD_MESSAGE    
Určuje funkci, která bude zpracovávat zprávy registrovaných funkci Windows RegisterWindowMessage.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *nMessageVariable*  
 Proměnná ID registrované zprávy okna.  
  
 *memberFxn*  
 Název funkce CWinThread popisovač zpráv, ke kterému je namapována zprávu.  
  
### <a name="remarks"></a>Poznámky  
 RegisterWindowMessage slouží k definování novou zprávu okna, která je zaručeně jedinečná v celém systému. ON_REGISTERED_THREAD_MESSAGE musí použít namísto ON_REGISTERED_MESSAGE, když máte CWinThread – třída. 
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

## <a name="on_thread_message"></a>  ON_THREAD_MESSAGE  
Určuje funkci, která bude zpracovávat uživatelsky definovanou zprávu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_THREAD_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *message*  
 ID zprávy.  
  
 *memberFxn*  
 Název `CWinThread`– zpráva – obslužná rutina funkce, ke kterému je namapována zprávu.  
  
### <a name="remarks"></a>Poznámky  
 ON_THREAD_MESSAGE musí použít namísto ON_MESSAGE, když máte `CWinThread` třídy. Uživatelem definované zprávy jsou všechny zprávy, které nejsou standardní zprávy Windows WM_MESSAGE. Měla by existovat právě jeden příkaz ON_THREAD_MESSAGE – makro v mapy zpráv pro každou zprávu definovaný uživatelem, který musí být namapována na funkci obslužné rutiny zprávy.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  

## <a name="on_update_command_ui"></a>  ON_UPDATE_COMMAND_UI    
Toto makro označuje funkci, která bude zpracovávat zprávou příkazu aktualizace uživatelského rozhraní.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_UPDATE_COMMAND_UI( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 ID zprávy.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, ke kterému je namapována zprávu.  
  
### <a name="remarks"></a>Poznámky  
 Měla by existovat právě jeden příkaz ON_UPDATE_COMMAND_UI – makro v mapy zpráv pro každý příkaz aktualizace uživatelského rozhraní, které musí být namapována na funkci obslužná rutina zprávy.  
  
 Další informace a příklady najdete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
### <a name="see-also"></a>Viz také  
 [CCmdUI – třída](ccmdui-class.md)

## <a name="on_command_range"></a>  ON_COMMAND_RANGE  
Použijte toto makro mapovat souvislý rozsah ID příkazů do jedné zprávy funkce obslužné rutiny.  
  
### <a name="syntax"></a>Syntaxe
  
```  
ON_COMMAND_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *ID 1*  
 ID příkazu na začátku souvislý rozsah ID příkazů.  
  
 *s ID 2*  
 ID příkazu, na konci souvislý rozsah ID příkazů.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy, do které jsou mapovány příkazy.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah ID začíná *id1* a končí *id2*.  
  
 Umožňuje mapovat rozsah ID příkazů na jednu členskou funkci ON_COMMAND_RANGE. Použití [ON_COMMAND](#on_command) mapování jediným příkazem na členskou funkci. Pouze jedna položka mapování zpráv může odpovídat ID daného příkazu. Příkaz tedy nelze mapovat na více než jednu obslužnou rutinu. Další informace o mapování oblasti zpráv, najdete v části [obslužné rutiny pro oblasti Map zpráv](../../mfc/handlers-for-message-map-ranges.md).  
  
 Neexistuje žádné automatické podpory pro oblasti map zpráv, takže je nutné umístit makro, sami.  
  
### <a name="example"></a>Příklad  
```cpp  
// The code fragment below shows how to use ON_COMMAND_RANGE macro 
// to map a contiguous range of command IDs to a single message  
// handler function (i.e. OnRangeCmds() in the sample below). In  
// addition, it also shows how to use CheckMenuRadioItem() to check a  
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, 
      nID, MF_BYCOMMAND);
}
```
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE    
Mapuje souvislý rozsah ID příkazů funkci obslužné rutiny zpráv jednu aktualizaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *ID 1*  
 ID příkazu na začátku souvislý rozsah ID příkazů.  
  
 *s ID 2*  
 ID příkazu, na konci souvislý rozsah ID příkazů.  
  
 *memberFxn*  
 Název funkce obslužná rutina zprávy aktualizace, ke které jsou mapovány příkazy.  
  
### <a name="remarks"></a>Poznámky  
 Obslužné rutiny zpráv aktualizace aktualizovat stav položky nabídky a tlačítka panelu nástrojů, které jsou přidružené k příkazu. Rozsah ID začíná *id1* a končí *id2*.  
  
 Neexistuje žádné automatické podpory pro oblasti map zpráv, takže je nutné umístit makro, sami.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

## <a name="on_control_range"></a>  ON_CONTROL_RANGE     
Použijte toto makro pro mapování na obslužnou rutinu jedné zprávy zadané zprávy oznámení Windows, jako je například BN_CLICKED souvislý rozsah ID ovládacích prvků.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 *funkci wNotifyCode*  
 Kód upozornění, ke které je vaše obslužná rutina reagovat.  
  
 *ID 1*  
 ID příkazu na začátku souvislý rozsah ID ovládacích prvků.  
  
 *s ID 2*  
 ID příkazu, na konci souvislý rozsah ID ovládacích prvků.  
  
 *memberFxn*  
 Název funkce popisovač zpráv, ke které jsou mapovány ovládací prvky.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah ID začíná *id1* a končí *id2*. Obslužná rutina se nazývá pro zadaný oznámení pocházející z některého z namapované ovládací prvky.  
  
 Neexistuje žádné automatické podpory pro oblasti map zpráv, takže je nutné umístit makro, sami.  
  
 Další informace o implementaci funkce obslužné rutiny pro celou řadu ID ovládacích prvků naleznete [obslužné rutiny pro oblasti Map zpráv](../../mfc/handlers-for-message-map-ranges.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  
  