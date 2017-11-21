---
title: "Zpráva makra mapy (MFC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70f88d493ad557515cfac1f8cffeaa305c849f63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="message-map-macros-mfc"></a>Makra map zpráv (MFC)
Pro podporu mapy zpráv, MFC poskytuje následující makra:  
  
### <a name="message-map-declaration-and-demarcation-macros"></a>Mapy zpráv deklarace a Rozhraničení makra  
  
|||  
|-|-|  
|[DECLARE_MESSAGE_MAP –](#declare_message_map)|Deklaruje, že mapy zpráv se použije v třídě k mapování zpráv na funkce (musí používat v deklaraci třídy).|  
|[BEGIN_MESSAGE_MAP –](#begin_message_map)|Zahájí definici mapy zpráv (musí používat v implementaci třídy).|  
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_interface_map)|Zahájí definici mapy zpráv typ třída obsahující jednu šablonu argumentu. |
|[END_MESSAGE_MAP –](#end_message_map)|Ukončí definici mapy zpráv (musí používat v implementaci třídy).|  
  
### <a name="message-mapping-macros"></a>Makra mapování zpráv  
  
|||  
|-|-|  
|[ON_COMMAND –](#on_command)|Určuje, jaké funkce zpracuje zprávu zadaný příkaz.|  
|[ON_COMMAND_EX –](#on_command_ex)|Určuje, jaké funkce zpracuje zprávu zadaný příkaz.|  
|[ON_CONTROL –](#on_control)|Určuje, jaké funkce zpracuje zprávu zadaný oznámení ovládacího prvku.|  
|[ON_MESSAGE –](#on_message)|Označuje, funkci, která bude zpracovávat uživatelem definovaná zpráva.|  
|[ON_OLECMD –](#on_olecmd)|Určuje, které funkce zpracuje příkaz nabídky z DocObject nebo jejímu kontejneru.|  
|[ON_REGISTERED_MESSAGE –](#on_registered_message)|Označuje, funkci, která bude zpracovávat registrované uživatelem definovaná zpráva.|  
|[ON_REGISTERED_THREAD_MESSAGE –](#on_registered_thread_message)|Určuje funkci, která bude zpracovávat registrované uživatelem definovaná zpráva, když máte `CWinThread` třídy.|  
|[ON_THREAD_MESSAGE –](#on_thread_message)|Určuje funkci, která bude zpracovávat uživatelem definovaná zpráva, když máte `CWinThread` třídy.|  
|[ON_UPDATE_COMMAND_UI –](#on_update_command_ui)|Označuje, funkci, která bude zpracovávat zprávou příkazu update zadaného uživatelského rozhraní.|  
  
### <a name="message-map-range-macros"></a>Makra Map zpráv rozsahu  
  
|||  
|-|-|  
|[ON_COMMAND_RANGE –](#on_command_range)|Označuje, funkci, která bude zpracovávat rozsah ID příkazů zadaný v první dva parametry, které chcete makro.|  
|[ON_UPDATE_COMMAND_UI_RANGE –](#on_update_command_ui_range)|Určuje, které obslužná rutina aktualizace bude zpracovávat rozsah ID příkazů zadaný v první dva pa] rametry do makra.|  
|[ON_CONTROL_RANGE –](#on_control_range)|Označuje, funkci, která bude zpracovávat upozornění z rozsahu ID zadané v parametrech druhý a třetí makru ovládacích prvků. První parametr je zpráva oznámení ovládacího prvku, jako například **BN_CLICKED**.|  
  
 Další informace o mapy zpráv, map zpráv deklarace a rozhraničení makra a makra mapování zpráv najdete v tématu [mapy zpráv](../../mfc/reference/message-maps-mfc.md) a [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md). Další informace o oblasti map zpráv najdete v tématu [obslužné rutiny pro oblasti Map zpráv](../../mfc/handlers-for-message-map-ranges.md).  


## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP –
Zahájí definici mapy zpráv.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_MESSAGE_MAP( theClass, baseClass )  
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje, že je název třídy, jejichž zpráva mapování těchto.  
  
 `baseClass`  
 Určuje název základní třídu `theClass`.  
  
### <a name="remarks"></a>Poznámky  
 V souboru implementace (sada), který definuje členské funkce pro třídu, spusťte mapy zpráv s `BEGIN_MESSAGE_MAP` makro, potom můžete přidat položky makro pro jednotlivé funkce obslužné rutiny zpráv a dokončení mapy zpráv s `END_MESSAGE_MAP` makro.  
  
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
Zahájí definici mapy zpráv typ třída obsahující jednu šablonu argumentu.  
   
### <a name="syntax"></a>Syntaxe  
  ```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )  
```
### <a name="parameters"></a>Parametry  
 `theClass`  
 Určuje, že je název třídy, jejichž zpráva mapování těchto.    
 `type_name`  
 Název šablony parametr zadaný pro třídu.    
 `baseClass`  
 Určuje název základní třídu `theClass`.  
   
### <a name="remarks"></a>Poznámky  
 Je podobná této makro [begin_message_map –](message-map-macros-mfc.md#begin_message_map) makro; toto makro je však určena pro třídy obsahující jednu šablonu argumentu.  
  
 V oddíle implementation metoda vaší třídy spuštění mapy zpráv s **BEGIN_TEMPLATE_MESSAGE_MAP** makro; poté přidejte makro položky pro každou z metod vaší obslužné rutiny zpráv, stejně jako na jednu mapu standardní zprávy. Stejně jako u **begin_message_map –** makro, dokončete mapy zpráv šablony s [end_message_map –](message-map-macros-mfc.md#end_message_map) makro.  
  
 Další informace o implementaci mapy zpráv pro šablony třídy, najdete v části [postupy: vytvoření mapy zpráv pro třídu šablony](../how-to-create-a-message-map-for-a-template-class.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
 
## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP –
 Deklaruje, že třída definuje mapy zpráv. Každý `CCmdTarget`-odvozené třídy v programu musíte zadat mapy zpráv pro zpracování zprávy.  
  
### <a name="syntax"></a>Syntaxe  
  
```    
DECLARE_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `DECLARE_MESSAGE_MAP` makro na konci deklarace třídy. Potom v souboru sada, která definuje členské funkce pro třídu, použijte `BEGIN_MESSAGE_MAP` makro, makro položky pro každý z funkcí popisovač zpráv a `END_MESSAGE_MAP` makro.  
  
> [!NOTE]
>  Pokud je deklarovat kteréhokoli člena po `DECLARE_MESSAGE_MAP`, je nutné zadat nový typ přístupu (**veřejné**, `private`, nebo `protected`) pro ně.  
  
 Další informace o zpráva mapuje a `DECLARE_MESSAGE_MAP` makro, najdete v části [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Příklad  
```cpp  
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
``` 
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  


## <a name="end_message_map"></a>END_MESSAGE_MAP –
Ukončí definici mapy zpráv.  
  
### <a name="syntax"></a>Syntaxe  
  
```   
END_MESSAGE_MAP( )  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace o zpráva mapuje a `END_MESSAGE_MAP` makro, najdete v části [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  

## <a name="on_command"></a>ON_COMMAND –
Toto makro mapuje zprávou příkazu členské funkce.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_COMMAND( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 ID příkazu.  
  
 `memberFxn`  
 Název funkce popisovač zpráv, na kterou je namapovaná příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Označuje, funkci, která zpracuje zprávu příkaz z objekt příkaz uživatelského rozhraní, například položku nabídky nebo panelu nástrojů tlačítko.  
  
 Pokud příkaz cílový objekt obdrží Windows **wm_command –** zprávu se zadaným ID `ON_COMMAND` zavolá funkci člen `memberFxn` pro zpracování zprávy.  
  
 Použití `ON_COMMAND` mapovat jeden příkaz členské funkce. Použití [on_command_range –](#on_command_range) mapovat rozsah ID příkazů funkce jeden člen. Jenom jedna položka mapování zpráv může odpovídat id daného příkazu. Příkaz nelze tedy mapovat do více než jeden obslužné rutiny. Další informace a příklady naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="example"></a>Příklad  
```cpp  
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
``` 
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

 ## <a name="on_command_ex"></a>ON_COMMAND_EX –
Rozšířené funkce člen obslužná rutina příkazu.  
   
### <a name="syntax"></a>Syntaxe  
  ```  
ON_COMMAND_EX(id, memberFxn);  
```
### <a name="parameters"></a>Parametry  
 `id`  
 ID příkazu.  
  
 `memberFxn`  
 Název funkce popisovač zpráv, na kterou je namapovaná příkaz.  
   
### <a name="remarks"></a>Poznámky 
Rozšířené formu obslužné rutiny zpráv příkaz je k dispozici pro pokročilé používá. `ON_COMMAND_EX` Makro se používá pro takové obslužné rutiny zpráv a poskytuje nadmnožinou funkci [on_command –] (# on_command –).  Rozšířené obslužná rutina příkazu členské funkce trvat jeden parametr, **Celé_číslo** obsahující ID příkazu a vrátit **BOOL**. Návratová hodnota by měla být hodnota TRUE pro 

Toto makro mapuje zprávou příkazu funkce Rozšířené člen obslužná rutina příkazu.  
   
### <a name="syntax"></a>Syntaxe  
```  
ON_COMMAND_EX(id,  memberFxn);  
```
### <a name="parameters"></a>Parametry  
 `id`  
 ID příkazu.  
  
 `memberFxn`  
 Název funkce popisovač zpráv, na kterou je namapovaná příkaz.  
   
### <a name="remarks"></a>Poznámky  
 Rozšířené formu obslužné rutiny zpráv příkaz je k dispozici pro pokročilé používá. `ON_COMMAND_EX` Makro se používá pro takové obslužné rutiny zpráv a poskytuje nadmnožinou [on_command –](message-map-macros-mfc.md#on_command) funkce. Rozšířené obslužná rutina příkazu členské funkce trvat jeden parametr, **Celé_číslo** obsahující ID příkazu a vrátit **BOOL**. Návratová hodnota by měla být hodnota TRUE, mají-li znamenat, že byla zpracována příkaz; jinak směrování bude pokračovat na další objekty cíl příkazu.  
Další informace najdete v tématu Technická poznámka [TN006: mapy zpráv] tm006. zpráva maps.md).  
   
### <a name="requirements"></a>Požadavky  
 Soubor hlaviček: afxmsg_.h  
   
### <a name="see-also"></a>Viz také  
 [ON_COMMAND –](message-map-macros-mfc.md#on_command)   
 [TN006: mapy zpráv] tm006. zpráva maps.md)

  
## <a name="on_control"></a>ON_CONTROL –
Určuje, jaké funkce zpracuje zprávu oznámení vlastní ovládací prvek.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_CONTROL( wNotifyCode, id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `wNotifyCode`  
 Kód oznámení ovládacího prvku.  
  
 `id`  
 ID příkazu.  
  
 `memberFxn`  
 Název funkce popisovač zpráv, na kterou je namapovaná příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Zprávy s oznámením ovládacího prvku jsou odesílána z ovládacího prvku do jeho nadřazeného okna.  
  
 Musí být přesně jeden `ON_CONTROL` makro příkaz na mapě zprávu pro každý ovládací prvek oznámení, které musí být namapovaný na funkce obslužné rutiny zpráv.  
  
 Další informace a příklady naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  
  

## <a name="on_message"></a>ON_MESSAGE –  
Označuje, funkci, která bude zpracovávat uživatelem definovaná zpráva.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 ID zprávy.  
  
 `memberFxn`  
 Název funkce obslužné rutiny zpráv, ke které je mapován zprávy.  
  
 Typ funkce musí být `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.  
  
### <a name="remarks"></a>Poznámky  
 Uživatelem definované zprávy jsou všechny zprávy, které nejsou standardní Windows `WM_MESSAGE` zprávy. Když vyberete ID zprávy, je nutné použít hodnoty v rozsahu `WM_USER` (0x0400) k 0x7FFF nebo `WM_APP` (0x8000) k 0xBFFF. Další informace o ID zpráv najdete v tématu [WM_APP](http://msdn.microsoft.com/library/windows/desktop/ms644930).  
  
 Musí být přesně jeden `ON_MESSAGE` makro příkaz na mapě zprávu pro každý uživatelem definovaná zpráva, která musí být namapovaný na funkce obslužné rutiny zpráv.  
  
> [!NOTE]
>  Kromě zprávy uživatelem definované `ON_MESSAGE` zpracovává méně častých zpráv systému Windows. Další informace najdete v článku znalostní báze [99848: informace: použití ON_MESSAGE() makro na mapu méně běžné zprávy](http://go.microsoft.com/fwlink/?linkId=192022).  
  
 Další informace a příklady naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md) a [uživatelem definované obslužné rutiny](user-defined-handlers.md)  
  
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

## <a name="on_olecmd"></a>ON_OLECMD –  
Směrování příkazů prostřednictvím rozhraní příkazového odesílání `IOleCommandTarget`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_OLECMD( pguid, olecmdid, id )  
```  
  
### <a name="parameters"></a>Parametry  
 `pguid`  
 Identifikátor příkazu skupiny, do které patří příkaz. Použití **NULL** pro standardní skupinu.  
  
 *olecmdid*  
 Identifikátor příkazu OLE.  
  
 `id`  
 ID nabídky, panelu nástrojů ID, tlačítko ID nebo jiné ID prostředku nebo objekt vydání příkazu.  
  
### <a name="remarks"></a>Poznámky  
 `IOleCommandTarget`Umožňuje kontejner pro příjem příkazů, které pocházejí v uživatelském rozhraní DocObject a umožňuje kontejneru odeslat stejné příkazy (jako je například nový, otevřít, uložit jako a tisk v nabídce Soubor; a zkopírujte, vkládat, vrátit zpět, a tak dále v nabídce Upravit) k DocObject.  
  
 `IOleCommandTarget`je jednodušší než OLE Automation `IDispatch`. `IOleCommandTarget`využívá zcela standardní sadu příkazů to obvykle nemusí argumenty, a je zahrnuta žádné informace o typu (bezpečnost typů dojde ke snížení pro argumenty příkazu také). Pokud potřebujete odesílání příkazů s argumenty, použijte [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).  
  
 `IOleCommandTarget` Příkazy standardní nabídky je implementovaná v prostředí MFC v makrech následující:  
  
 **ON_OLECMD_CLEARSELECTION –)**  
  
 Odešle zprávu příkaz Upravit zrušte. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`  
  
 **ON_OLECMD_COPY –)**  
  
 Odešle zprávu příkaz Upravit Copy. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`  
  
 **ON_OLECMD_CUT –)**  
  
 Odešle zprávu příkaz Upravit vyjmout. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`  
  
 **ON_OLECMD_NEW –)**  
  
 Odešle zprávu příkaz Nový soubor. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`  
  
 **ON_OLECMD_OPEN –)**  
  
 Odešle zprávu příkazu Otevřít soubor. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`  
  
 **ON_OLECMD_PAGESETUP –)**  
  
 Odešle zprávu příkaz vzhledu stránky. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`  
  
 **ON_OLECMD_PASTE –)**  
  
 Odešle zprávu příkaz Upravit vložit. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`  
  
 **ON_OLECMD_PASTESPECIAL –)**  
  
 Odešle zprávu příkaz Upravit Vložit jinak. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`  
  
 **ON_OLECMD_PRINT –)**  
  
 Odešle zprávu příkaz tisku souboru. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`  
  
 **ON_OLECMD_PRINTPREVIEW –)**  
  
 Odešle zprávu příkaz Náhled souboru. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`  
  
 **ON_OLECMD_REDO –)**  
  
 Odešle zprávu příkaz upravit znovu. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`  
  
 **ON_OLECMD_SAVE –)**  
  
 Odešle zprávu příkaz Soubor uložte. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`  
  
 **ON_OLECMD_SAVE_AS –)**  
  
 Odešle zprávu příkazu Uložit jako. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`  
  
 **ON_OLECMD_SAVE_COPY_AS –)**  
  
 Odešle zprávu příkaz soubor uložit kopii jako. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`  
  
 **ON_OLECMD_SELECTALL –)**  
  
 Odešle zprávu příkaz Upravit vybrat vše. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`  
  
 **ON_OLECMD_UNDO –)**  
  
 Odešle zprávu příkaz Upravit zpět. Implementovaný jako:  
  
 `ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdocob.h  
  
### <a name="see-also"></a>Viz také  
 [COleCmdUI – třída](colecmdui-class.md)   
 [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE –
Windows **RegisterWindowMessage** funkce se používá k definování zprávu nové okno, která se musí být jedinečný v celém systému.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `nMessageVariable`  
 Proměnná ID registrované zpráv oken.  
  
 `memberFxn`  
 Název funkce obslužné rutiny zpráv, ke které je mapován zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro označuje, funkci, která bude zpracovávat registrované zprávy.  
  
 Další informace a příklady naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
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

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE –    
Určuje, které funkce zpracuje zprávu registrovaných funkce Windows RegisterWindowMessage.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `nMessageVariable`  
 Proměnná ID registrované zpráv oken.  
  
 `memberFxn`  
 Název funkce CWinThread popisovač zpráv, ke které je mapován zprávy.  
  
### <a name="remarks"></a>Poznámky  
 RegisterWindowMessage se používá k definování zprávu nové okno, která se musí být jedinečný v celém systému. On_registered_thread_message – použije místo on_registered_message – Pokud máte CWinThread – třída. 
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE –  
Označuje, funkci, která bude zpracovávat uživatelem definovaná zpráva.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_THREAD_MESSAGE( message, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `message`  
 ID zprávy.  
  
 `memberFxn`  
 Název `CWinThread`– zpráva – obslužná rutina funkce, ke které je mapován zprávy.  
  
### <a name="remarks"></a>Poznámky  
 `ON_THREAD_MESSAGE`musí být použit místo `ON_MESSAGE` Pokud máte `CWinThread` třídy. Uživatelem definované zprávy jsou všechny zprávy, které nejsou standardní Windows **WM_MESSAGE** zprávy. Musí být přesně jeden `ON_THREAD_MESSAGE` makro příkaz na mapě zprávu pro každý uživatelem definovaná zpráva, která musí být namapovaný na funkce obslužné rutiny zpráv.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI –    
Toto makro označuje funkci, která bude zpracovávat zprávou příkazu aktualizace uživatelského rozhraní.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_UPDATE_COMMAND_UI( id, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 ID zprávy.  
  
 `memberFxn`  
 Název funkce obslužné rutiny zpráv, ke které je mapován zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Musí být přesně jeden `ON_UPDATE_COMMAND_UI` makro příkaz na mapě zprávu pro každý příkaz aktualizace uživatelského rozhraní, který musí být namapovaný na funkce obslužné rutiny zpráv.  
  
 Další informace a příklady naleznete v tématu [zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
### <a name="see-also"></a>Viz také  
 [CCmdUI – třída](ccmdui-class.md)

## <a name="on_command_range"></a>ON_COMMAND_RANGE –  
Pomocí této makro mapovat souvislý rozsah ID příkazů funkci obslužné rutiny jedné zprávy.  
  
### <a name="syntax"></a>Syntaxe
  
```  
ON_COMMAND_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id1`  
 ID příkazu na začátku souvislý rozsah ID příkazů.  
  
 `id2`  
 ID příkazu na konci souvislý rozsah ID příkazů.  
  
 `memberFxn`  
 Název funkce popisovač zpráv, ke které jsou namapované příkazy.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah ID začíná `id1` a končí `id2`.  
  
 Použití `ON_COMMAND_RANGE` mapovat rozsah ID příkazů funkce jeden člen. Použití [on_command –](#on_command) mapovat jeden příkaz členské funkce. Jenom jedna položka mapování zpráv může odpovídat ID daného příkazu. Příkaz nelze tedy mapovat do více než jeden obslužné rutiny. Další informace o mapování oblasti zpráv najdete v tématu [obslužné rutiny pro oblasti Map zpráv](../../mfc/handlers-for-message-map-ranges.md).  
  
 Neexistuje žádné automatické podpory pro oblasti map zpráv, proto musíte umístit makro sami.  
  
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

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE –    
Mapuje souvislý rozsah ID příkazů funkci obslužné rutiny zpráv jednu aktualizaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `id1`  
 ID příkazu na začátku souvislý rozsah ID příkazů.  
  
 `id2`  
 ID příkazu na konci souvislý rozsah ID příkazů.  
  
 `memberFxn`  
 Název funkce aktualizace popisovač zpráv, ke které jsou namapované příkazy.  
  
### <a name="remarks"></a>Poznámky  
 Obslužné rutiny zpráv aktualizace aktualizovat stav položky nabídky a přidružený k příkazu tlačítka panelu nástrojů. Rozsah ID začíná `id1` a končí `id2`.  
  
 Neexistuje žádné automatické podpory pro oblasti map zpráv, proto musíte umístit makro sami.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  

## <a name="on_control_range"></a>ON_CONTROL_RANGE –     
Použití tohoto makra k mapování souvislý rozsah ID ovládacích prvků na jedné zprávy funkci obslužné rutiny pro zadané zprávy oznámení Windows, jako například **BN_CLICKED**.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )  
```  
  
### <a name="parameters"></a>Parametry  
 `wNotifyCode`  
 Kód oznámení, ke kterému odpovídá vaší obslužné rutiny.  
  
 `id1`  
 ID příkazu na začátku souvislý rozsah ID ovládacích prvků.  
  
 `id2`  
 ID příkazu na konci souvislý rozsah ID ovládacích prvků.  
  
 `memberFxn`  
 Název funkce popisovač zpráv, ke které jsou namapované ovládací prvky.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah ID začíná `id1` a končí `id2`. Obslužná rutina se nazývá pro zadaný oznámení z jakékoli namapované ovládací prvky.  
  
 Neexistuje žádné automatické podpory pro oblasti map zpráv, proto musíte umístit makro sami.  
  
 Další informace o implementaci obslužné rutiny funkce pro řadu ID ovládacích prvků, najdete v části [obslužné rutiny pro oblasti Map zpráv](../../mfc/handlers-for-message-map-ranges.md).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmsg_.h  
  


