---
title: Makra map zpráv (MFC)
ms.date: 03/27/2019
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
ms.openlocfilehash: b88b745e3b70cf030f77f247ab03cd69d910109f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855487"
---
# <a name="message-map-macros-mfc"></a>Makra map zpráv (MFC)

Aby bylo možné podporovat mapy zpráv, knihovna MFC poskytuje následující makra:

### <a name="message-map-declaration-and-demarcation-macros"></a>Deklarace mapy zpráv a makra ohraničení

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklaruje, že mapa zpráv bude použita ve třídě pro mapování zpráv na funkce (musí být použita v deklaraci třídy).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Zahájí definici mapy zpráv (musí být použita v implementaci třídy).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Zahájí definici mapy zpráv u typu třídy obsahující jeden argument šablony. |
|[END_MESSAGE_MAP](#end_message_map)|Ukončí definici mapy zprávy (musí být použita v implementaci třídy).|

### <a name="message-mapping-macros"></a>Makra mapování zpráv

|||
|-|-|
|[ON_COMMAND](#on_command)|Určuje, která funkce zpracuje určenou zprávu příkazu.|
|[ON_COMMAND_EX](#on_command_ex)|Určuje, která funkce zpracuje určenou zprávu příkazu.|
|[ON_CONTROL](#on_control)|Určuje, která funkce zpracuje určenou zprávu o oznámení ovládacího prvku.|
|[ON_MESSAGE](#on_message)|Určuje, která funkce zpracuje uživatelem definovanou zprávu.|
|[ON_OLECMD](#on_olecmd)|Určuje, která funkce zpracuje příkaz nabídky z DocObject nebo jeho kontejneru.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Určuje, která funkce zpracuje registrovanou uživatelsky definovanou zprávu.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Určuje, která funkce zpracuje registrovanou uživatelsky definovanou zprávu, když máte třídu `CWinThread`.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Určuje, která funkce zpracuje uživatelem definovanou zprávu, když máte třídu `CWinThread`.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Určuje, která funkce zpracuje zadanou zprávu příkazu aktualizace uživatelského rozhraní.|

### <a name="message-map-range-macros"></a>Makra rozsahu mapy zpráv

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Určuje, která funkce zpracuje rozsah identifikátorů příkazů zadaných v prvních dvou parametrech do makra.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Určuje, která obslužná rutina aktualizace zpracuje rozsah ID příkazů zadaných v prvních dvou parametrech do makra.|
|[ON_CONTROL_RANGE](#on_control_range)|Určuje, která funkce bude zpracovávat oznámení z rozsahu identifikátorů ovládacích prvků zadaných v druhém a třetím parametru do makra. První parametr je zpráva s oznámením ovládacího prvku, například BN_CLICKED.|

Další informace o mapách zpráv, makrech mapování zpráv a deohraničeních a makrech k mapování zpráv naleznete v tématech [mapy zpráv](../../mfc/reference/message-maps-mfc.md) a [zpracování zpráv a mapování](../../mfc/message-handling-and-mapping.md). Další informace o rozsahu mapování zpráv naleznete v tématu [obslužné rutiny pro rozsahy mapování zpráv](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Zahájí definici mapy zpráv.

### <a name="syntax"></a>Syntaxe

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, jejíž rozvržení zprávy je.

*baseClass*<br/>
Určuje název základní třídy *theclass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (. cpp), který definuje členské funkce pro vaši třídu, spusťte mapu zprávy pomocí makra BEGIN_MESSAGE_MAP, pak přidejte položky makra pro každou funkci obslužné rutiny zpráv a dokončete mapu zpráv s END_MESSAGE_MAP podokně.

Další informace o mapách zpráv najdete v tématu [mapy zpráv](message-maps-mfc.md) .

### <a name="example"></a>Příklad

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Zahájí definici mapy zpráv u typu třídy obsahující jeden argument šablony.

### <a name="syntax"></a>Syntaxe

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, jejíž rozvržení zprávy je.

*type_name*<br/>
Název parametru šablony zadaného pro třídu.

*baseClass*<br/>
Určuje název základní třídy *theclass*.

### <a name="remarks"></a>Poznámky

Toto makro je podobné [BEGIN_MESSAGE_MAPmu](message-map-macros-mfc.md#begin_message_map) makru; Toto makro je však určeno pro třídy obsahující jeden argument šablony.

V části implementace metody vaší třídy spusťte mapu zpráv pomocí makra BEGIN_TEMPLATE_MESSAGE_MAP; pak přidejte položky makra pro každou z vašich metod obslužné rutiny zpráv jako pro standardní mapu zpráv. Stejně jako u makra BEGIN_MESSAGE_MAP dokončete mapování zpráv šablon pomocí makra [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) .

Další informace o implementaci map zpráv pro třídy šablon najdete v tématu [Postupy: vytvoření mapy zpráv pro třídu šablony](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Deklaruje, že třída definuje mapu zpráv. Každá třída odvozená od `CCmdTarget`v programu musí poskytovat mapu zpráv pro zpracování zpráv.

### <a name="syntax"></a>Syntaxe

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_MESSAGE_MAP na konci deklarace třídy. Poté v souboru. cpp, který definuje členské funkce pro třídu, použijte makro BEGIN_MESSAGE_MAP, položky makra pro každou funkci obslužné rutiny zpráv a makro END_MESSAGE_MAP.

> [!NOTE]
>  Pokud deklarujete některého člena po DECLARE_MESSAGE_MAP, musíte pro ně zadat nový typ přístupu (**Public**, **Private**nebo **Protected**).

Další informace o mapách zpráv a makru DECLARE_MESSAGE_MAP najdete v [tématech zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Příklad

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="end_message_map"></a>END_MESSAGE_MAP

Ukončí definici mapy zpráv.

### <a name="syntax"></a>Syntaxe

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Poznámky

Další informace o mapách zpráv a makru END_MESSAGE_MAP najdete v [tématech zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="on_command"></a>ON_COMMAND

Toto makro namapuje zprávu příkazu na členskou funkci.

### <a name="syntax"></a>Syntaxe

```
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*commandId*<br/>
ID příkazu

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, ke které je příkaz namapován.

### <a name="remarks"></a>Poznámky

Označuje, která funkce zpracuje zprávu příkazu z objektu uživatelského rozhraní, jako je například položka nabídky nebo tlačítko panelu nástrojů.

Když objekt Target příkazu obdrží zprávu Windows WM_COMMAND se zadaným ID, ON_COMMAND volat členskou funkci `memberFxn` pro zpracování zprávy.

Použijte ON_COMMAND k namapování jednoho příkazu na členskou funkci. Pomocí [ON_COMMAND_RANGE](#on_command_range) namapujte rozsah ID příkazů na jednu členskou funkci. Danému ID příkazu se může shodovat jenom jedna položka v mapě zpráv. To znamená, že nemůžete mapovat příkaz na více než jednu obslužnou rutinu. Další informace a příklady najdete v [tématech o zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Příklad

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_. h

## <a name="on_command_ex"></a>ON_COMMAND_EX

Rozšířená funkce člena obslužné rutiny příkazu.

### <a name="syntax"></a>Syntaxe

```
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parametry

*commandId*<br/>
ID příkazu

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, ke které je příkaz namapován.

### <a name="remarks"></a>Poznámky

Rozšířená forma obslužných rutin zpráv příkazu je k dispozici pro pokročilé použití. Makro ON_COMMAND_EX se používá pro tyto obslužné rutiny zpráv a poskytuje nadmnožinu funkcí [ON_COMMAND](message-map-macros-mfc.md#on_command) . Rozšířené funkce členů obslužných rutin příkazu přebírají jeden parametr, UINT obsahující ID příkazu a vrátí BOOL. Návratová hodnota by měla být TRUE, aby označovala, že příkaz byl zpracován; v opačném případě bude směrování pokračovat dalšími cílovými objekty příkazu.

Další informace najdete v tématu technická Poznámka [TN006: Message Maps] tm006-Message-maps.md).

### <a name="requirements"></a>Požadavky

Hlavičkový soubor: afxmsg_. h

## <a name="on_control"></a>ON_CONTROL

Určuje, která funkce zpracuje zprávu s oznámením vlastního ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Zapněte wnotifycode*<br/>
Kód oznámení ovládacího prvku

*commandId*<br/>
ID příkazu

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, ke které je příkaz namapován.

### <a name="remarks"></a>Poznámky

Zprávy s oznámením ovládacího prvku jsou odesílány z ovládacího prvku do svého nadřazeného okna.

V mapě zpráv by měl být přesně jeden ON_CONTROL příkaz makra pro každou zprávu oznámení ovládacího prvku, která musí být namapována na funkci obslužné rutiny zpráv.

Další informace a příklady najdete v [tématech o zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_. h

## <a name="on_message"></a>ON_MESSAGE

Určuje, která funkce zpracuje uživatelem definovanou zprávu.

### <a name="syntax"></a>Syntaxe

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*message*<br/>
ID zprávy

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, ke které je zpráva mapována

Typ funkce musí být `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Poznámky

Zprávy definované uživatelem jsou všechny zprávy, které nejsou standardní WM_MESSAGE zpráv Windows. Při výběru ID zprávy je nutné použít hodnoty v rozsahu WM_USER (0x0400) na 0x7FFF nebo WM_APP (0x8000) na 0xBFFF. Další informace o ID zpráv naleznete v tématu [WM_APP](/windows/win32/winmsg/wm-app).

V mapě zpráv by měl být přesně jeden ON_MESSAGE příkaz makra pro každou zprávu definovanou uživatelem, která musí být namapována na funkci obslužné rutiny zpráv.

> [!NOTE]
>  Kromě uživatelsky definovaných zpráv ON_MESSAGE zpracovává méně běžných zpráv Windows. Další informace najdete v tématu [mapy zpráv](../../mfc/tn006-message-maps.md).

Další informace a příklady naleznete v [tématech zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md) a [uživatelsky definované obslužné rutiny](user-defined-handlers.md) .

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

**Záhlaví:** afxmsg_. h

## <a name="on_olecmd"></a>ON_OLECMD

Směruje příkazy prostřednictvím rozhraní pro odeslání příkazu `IOleCommandTarget`.

### <a name="syntax"></a>Syntaxe

```
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parametry

*pguid*<br/>
Identifikátor skupiny příkazů, do které příkaz patří Pro skupinu Standard použijte hodnotu NULL.

*olecmdid*<br/>
Identifikátor příkazu OLE

*commandId*<br/>
ID nabídky, ID panelu nástrojů, ID tlačítka nebo jiné ID prostředku nebo objektu, který příkaz vystavil.

### <a name="remarks"></a>Poznámky

`IOleCommandTarget` umožňuje kontejneru přijímat příkazy, které pocházejí z uživatelského rozhraní DocObject, a umožňuje kontejneru odesílat stejné příkazy (například nové, otevřené, SaveAs a tisknout v nabídce soubor) a kopírovat, vkládat, vracet a tak dále v nabídce Úpravy) na DocObject.

`IOleCommandTarget` je jednodušší než `IDispatch`automatizace OLE. `IOleCommandTarget` spoléhá výhradně na standardní sadu příkazů, které mají zřídka argumenty, a nejsou zapojeny žádné informace o typu (pro argumenty příkazu se snížila bezpečnost typů). Pokud potřebujete odeslat příkazy s argumenty, použijte [COleServerDoc:: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Příkazy nabídky `IOleCommandTarget` Standard byly implementovány pomocí knihovny MFC v následujících makrech:

**ON_OLECMD_CLEARSELECTION ()**

Odešle příkaz pro úpravu Clear. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY ()**

Odešle příkaz pro úpravu kopírování. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT ()**

Odešle příkaz pro úpravu řezu. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW ()**

Odešle nový příkaz souboru. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN ()**

Odešle příkaz k otevření souboru. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP ()**

Odešle příkaz instalačního souboru stránky. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE ()**

Odešle příkaz pro úpravu vložení. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL ()**

Odešle speciální příkaz pro úpravu vložení. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT ()**

Odešle příkaz pro tisk souboru. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW ()**

Odešle příkaz k tisku souboru ve verzi Preview. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO ()**

Odešle příkaz pro úpravu opětovného provedení. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE ()**

Odešle příkaz pro uložení souboru. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS ()**

Odešle soubor uložit jako. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS ()**

Odešle soubor uložit kopii jako příkazu. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL ()**

Odešle příkaz pro úpravu výběru všechny. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO ()**

Odešle příkaz pro úpravu příkazu zpět. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Požadavky

**Záhlaví:** AfxDocOb. h

## <a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Funkce Windows `RegisterWindowMessage` slouží k definování nové zprávy okna, u které je zaručeno, že budou jedinečné v celém systému.

### <a name="syntax"></a>Syntaxe

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageVariable*<br/>
Registrovaná proměnná ID okna – zprávy.

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, ke které je zpráva mapována

### <a name="remarks"></a>Poznámky

Toto makro indikuje, která funkce zpracuje registrovanou zprávu.

Další informace a příklady najdete v [tématech o zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Příklad

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_. h

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Určuje, která funkce zpracuje zprávu zaregistrovanou funkcí Windows RegisterWindowMessage.

### <a name="syntax"></a>Syntaxe

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nMessageVariable*<br/>
Registrovaná proměnná ID okna – zprávy.

*memberFxn*<br/>
Název funkce obslužné rutiny CWinThread-Message-Handler, ke které je zpráva namapována.

### <a name="remarks"></a>Poznámky

RegisterWindowMessage se používá k definování nové zprávy okna, u které je zaručeno, že budou jedinečné v celém systému. ON_REGISTERED_THREAD_MESSAGE musí být použit místo ON_REGISTERED_MESSAGE, pokud máte třídu CWinThread.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_. h

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE

Určuje, která funkce zpracuje uživatelem definovanou zprávu.

### <a name="syntax"></a>Syntaxe

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*message*<br/>
ID zprávy

*memberFxn*<br/>
Název funkce obslužné rutiny `CWinThread`-Message-, ke které je zpráva namapovaná.

### <a name="remarks"></a>Poznámky

ON_THREAD_MESSAGE je třeba použít místo ON_MESSAGE, pokud máte třídu `CWinThread`. Zprávy definované uživatelem jsou všechny zprávy, které nejsou standardní WM_MESSAGE zpráv Windows. V mapě zpráv by měl být přesně jeden ON_THREAD_MESSAGE příkaz makra pro každou zprávu definovanou uživatelem, která musí být namapována na funkci obslužné rutiny zpráv.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

Toto makro indikuje, která funkce zpracuje zprávu příkazu aktualizace uživatelského rozhraní.

### <a name="syntax"></a>Syntaxe

```
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Parametr*<br/>
ID zprávy

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, ke které je zpráva mapována

### <a name="remarks"></a>Poznámky

V mapě zpráv by měl být přesně jeden ON_UPDATE_COMMAND_UI příkaz makra pro každý příkaz pro aktualizaci uživatelského rozhraní, který musí být namapován na funkci obslužné rutiny zpráv.

Další informace a příklady najdete v [tématech o zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

## <a name="on_command_range"></a>ON_COMMAND_RANGE

Pomocí tohoto makra lze namapovat souvislý rozsah ID příkazů na jednu funkci obslužné rutiny zpráv.

### <a name="syntax"></a>Syntaxe

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*ID1*<br/>
ID příkazu na začátku souvislého rozsahu identifikátorů příkazů.

*ID 2*<br/>
ID příkazu na konci souvislého rozsahu identifikátorů příkazů.

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, do které jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Rozsah ID začíná na *ID1* a končí na *ID 2*.

Pomocí ON_COMMAND_RANGE namapujte rozsah ID příkazů na jednu členskou funkci. Použijte [ON_COMMAND](#on_command) k namapování jednoho příkazu na členskou funkci. Danému ID příkazu se může shodovat jenom jedna položka v mapě zpráv. To znamená, že nemůžete mapovat příkaz na více než jednu obslužnou rutinu. Další informace o mapování rozsahů zpráv naleznete v tématu [obslužné rutiny pro rozsahy mapování zpráv](../../mfc/handlers-for-message-map-ranges.md).

Neexistuje žádná Automatická podpora pro rozsahy map zpráv, takže je nutné makro umístit sami.

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

**Záhlaví:** afxmsg_. h

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Mapuje souvislý rozsah ID příkazů do funkce obslužné rutiny zpráv s jednou aktualizací.

### <a name="syntax"></a>Syntaxe

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*ID1*<br/>
ID příkazu na začátku souvislého rozsahu identifikátorů příkazů.

*ID 2*<br/>
ID příkazu na konci souvislého rozsahu identifikátorů příkazů.

*memberFxn*<br/>
Název funkce obslužné rutiny zprávy aktualizace, ke které jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Aktualizace obslužných rutin zpráv aktualizují stav položek nabídky a tlačítek panelu nástrojů přidružených k příkazu. Rozsah ID začíná na *ID1* a končí na *ID 2*.

Neexistuje žádná Automatická podpora pro rozsahy map zpráv, takže je nutné makro umístit sami.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_. h

## <a name="on_control_range"></a>ON_CONTROL_RANGE

Pomocí tohoto makra lze namapovat souvislý rozsah ID ovládacího prvku na jednu funkci obslužné rutiny zpráv pro zadanou zprávu systému Windows, například BN_CLICKED.

### <a name="syntax"></a>Syntaxe

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*Zapněte wnotifycode*<br/>
Kód oznámení, na který vaše obslužná rutina reaguje.

*ID1*<br/>
ID příkazu na začátku souvislého rozsahu identifikátorů ovládacích prvků.

*ID 2*<br/>
ID příkazu na konci souvislého rozsahu ID ovládacích prvků.

*memberFxn*<br/>
Název funkce obslužné rutiny zpráv, do které jsou ovládací prvky mapovány.

### <a name="remarks"></a>Poznámky

Rozsah ID začíná na *ID1* a končí na *ID 2*. Obslužná rutina je volána pro zadané oznámení ze všech mapovaných ovládacích prvků.

Neexistuje žádná Automatická podpora pro rozsahy map zpráv, takže je nutné makro umístit sami.

Další informace o implementaci funkcí obslužných rutin pro rozsah ID ovládacích prvků naleznete v tématu [obslužné rutiny pro rozsahy mapování zpráv](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_. h

## <a name="see-also"></a>Viz také

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: Mapy zpráv](../tn006-message-maps.md)<br/>
[COleCmdUI – třída](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Uživatelem definované obslužné rutiny](user-defined-handlers.md)<br/>
[CCmdUI – třída](ccmdui-class.md)
