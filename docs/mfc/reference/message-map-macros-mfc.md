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
ms.openlocfilehash: 6e9291f0f39057403bc27c7fe4ff5ca5a82dfe3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356589"
---
# <a name="message-map-macros-mfc"></a>Makra map zpráv (MFC)

Pro podporu map zpráv poskytuje knihovna MFC následující makra:

### <a name="message-map-declaration-and-demarcation-macros"></a>Makra prohlášení o mapě zpráv a demarkační makra

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|Deklaruje, že mapa zpráv bude použita ve třídě mapovat zprávy na funkce (musí být použita v deklaraci třídy).|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|Začíná definice mapy zpráv (musí být použitv implementaci třídy).|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|Začíná definice mapy zprávy na typu třídy obsahující jeden argument šablony. |
|[END_MESSAGE_MAP](#end_message_map)|Ukončí definici mapy zpráv (musí být použit v implementaci třídy).|

### <a name="message-mapping-macros"></a>Makra mapování zpráv

|||
|-|-|
|[ON_COMMAND](#on_command)|Označuje, která funkce zpracovat zadanou příkazovou zprávu.|
|[ON_COMMAND_EX](#on_command_ex)|Označuje, která funkce zpracovat zadanou příkazovou zprávu.|
|[ON_CONTROL](#on_control)|Označuje, která funkce bude zpracovávat zadanou zprávu o oznamování ovládacího prvku.|
|[ON_MESSAGE](#on_message)|Označuje, která funkce bude zpracovávat uživatelem definovanou zprávu.|
|[ON_OLECMD](#on_olecmd)|Označuje, která funkce bude zpracovávat příkaz nabídky z DocObject nebo jeho kontejneru.|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|Označuje, která funkce bude zpracovávat registrovanou uživatelem definovanou zprávu.|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|Označuje, která funkce bude zpracovávat registrovanou `CWinThread` uživatelem definovanou zprávu, pokud máte třídu.|
|[ON_THREAD_MESSAGE](#on_thread_message)|Označuje, která funkce bude zpracovávat uživatelem `CWinThread` definovanou zprávu, když máte třídu.|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|Označuje, která funkce bude zpracovávat zadanou zprávu příkazu aktualizace uživatelského rozhraní.|

### <a name="message-map-range-macros"></a>Makra rozsahu mapy zpráv

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|Označuje, která funkce bude zpracovávat rozsah ID příkazů zadaný v prvních dvou parametrech makra.|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|Označuje, která obslužná rutina aktualizace bude zpracovávat rozsah ID příkazů zadaný v prvních dvou parametrech makra.|
|[ON_CONTROL_RANGE](#on_control_range)|Označuje, která funkce bude zpracovávat oznámení z rozsahu ID ovládacího prvku zadaných v druhém a třetím parametru do makra. První parametr je zpráva o znamaže ovládacího prvku, například BN_CLICKED.|

Další informace o mapách zpráv, marech deklarace a demarkace mapy zpráv a marech mapování zpráv naleznete v tématu [Mapy zpráv](../../mfc/reference/message-maps-mfc.md) a Témata zpracování a [mapování zpráv](../../mfc/message-handling-and-mapping.md). Další informace o rozsahech map zpráv naleznete v [tématu Obslužné rutiny pro rozsahy map zpráv](../../mfc/handlers-for-message-map-ranges.md).

## <a name="begin_message_map"></a><a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

Začíná definici mapy zpráv.

### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, jejíž mapa zpráv se jedná.

*Baseclass*<br/>
Určuje název základní třídy *Class*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce pro vaši třídu, spusťte mapu zpráv pomocí BEGIN_MESSAGE_MAP makra, přidejte položky maker pro každou z funkcí obslužné rutiny zpráv a dokončete mapu zpráv END_MESSAGE_MAP makra.

Další informace o mapách zpráv naleznete v [tématu Mapy zpráv](message-maps-mfc.md)

### <a name="example"></a>Příklad

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="begin_template_message_map"></a><a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

Začíná definice mapy zprávy na typu třídy obsahující jeden argument šablony.

### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy, jejíž mapa zpráv se jedná.

*Type_name*<br/>
Název parametru šablony zadaný pro třídu.

*Baseclass*<br/>
Určuje název základní třídy *Class*.

### <a name="remarks"></a>Poznámky

Toto makro je podobné [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map) makru; Toto makro je však určeno pro třídy obsahující jeden argument šablony.

V části implementace metody ve třídě spusťte mapu zpráv pomocí BEGIN_TEMPLATE_MESSAGE_MAP makro; potom přidejte položky maker pro každou metodu obslužné rutiny zpráv stejně jako pro standardní mapu zpráv. Stejně jako u BEGIN_MESSAGE_MAP makru vyplňte mapu zpráv šablony pomocí [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map) makru.

Další informace o implementaci map zpráv pro třídy šablon naleznete v části [Postup: Vytvoření mapy zpráv pro třídu šablony](../how-to-create-a-message-map-for-a-template-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="declare_message_map"></a><a name="declare_message_map"></a>DECLARE_MESSAGE_MAP

Deklaruje, že třída definuje mapu zpráv. Každá `CCmdTarget`odvozená třída v programu musí poskytovat mapu zpráv pro zpracování zpráv.

### <a name="syntax"></a>Syntaxe

```cpp
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_MESSAGE_MAP na konci deklarace třídy. Potom v souboru CPP, který definuje členské funkce pro třídu, použijte BEGIN_MESSAGE_MAP makro, položky maker pro každou z funkcí obslužné rutiny zprávy a END_MESSAGE_MAP makro.

> [!NOTE]
> Pokud po DECLARE_MESSAGE_MAP deklarujete některý člen, musíte pro ně zadat nový typ přístupu **(veřejný**, **soukromý**nebo **chráněný).**

Další informace o mapách zpráv a makru DECLARE_MESSAGE_MAP naleznete v [tématu Témata zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Příklad

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="end_message_map"></a><a name="end_message_map"></a>END_MESSAGE_MAP

Ukončí definici mapy zpráv.

### <a name="syntax"></a>Syntaxe

```cpp
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Poznámky

Další informace o mapách zpráv a END_MESSAGE_MAP makru naleznete v [tématu Témata zpracování a mapování zpráv](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="on_command"></a><a name="on_command"></a>ON_COMMAND

Toto makro mapuje příkazovou zprávu na členskou funkci.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Commandid*<br/>
ID příkazu.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou je příkaz mapován.

### <a name="remarks"></a>Poznámky

Označuje, která funkce bude zpracovávat příkazovou zprávu z objektu uživatelského rozhraní příkazu, například položky nabídky nebo tlačítka panelu nástrojů.

Pokud objekt cíle příkazu obdrží zprávu WM_COMMAND systému Windows se zadaným ID, ON_COMMAND zavolá členskou funkci `memberFxn` ke zpracování zprávy.

Pomocí ON_COMMAND namapujte jeden příkaz na členskou funkci. Pomocí [ON_COMMAND_RANGE](#on_command_range) namapujte rozsah ID příkazů na jednu členskou funkci. Pouze jedna položka mapy zprávy může odpovídat danému ID příkazu. To znamená, že příkaz nelze mapovat na více než jednu obslužnou rutinu. Další informace a příklady naleznete v [tématu Zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Příklad

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_.h

## <a name="on_command_ex"></a><a name="on_command_ex"></a>ON_COMMAND_EX

Rozšířená členská funkce obslužné rutiny příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>Parametry

*Commandid*<br/>
ID příkazu.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou je příkaz mapován.

### <a name="remarks"></a>Poznámky

Pro pokročilá použití je k dispozici rozšířená forma obslužných rutin zpráv příkazů. Makro ON_COMMAND_EX se používá pro tyto obslužné rutiny zpráv a poskytuje nadmnožinu [funkce ON_COMMAND.](message-map-macros-mfc.md#on_command) Rozšířené funkce člena obslužné rutiny příkazu převzít jeden parametr, UINT obsahující ID příkazu a vrátit BOOL. Vrácená hodnota by měla být TRUE označuje, že příkaz byl zpracován; v opačném případě bude směrování pokračovat na další cílové objekty příkazu.

Další informace naleznete v části Technická poznámka [TN006: Mapy zpráv]tm006-message-maps.md).

### <a name="requirements"></a>Požadavky

Soubor záhlaví: afxmsg_.h

## <a name="on_control"></a><a name="on_control"></a>ON_CONTROL

Označuje, která funkce bude zpracovávat oznámení vlastní ovládací prvek.

### <a name="syntax"></a>Syntaxe

```cpp
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kód oznámení ovládacího prvku.

*Commandid*<br/>
ID příkazu.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou je příkaz mapován.

### <a name="remarks"></a>Poznámky

Zprávy s oznámením ovládacího prvku jsou zprávy odeslané z ovládacího prvku do nadřazeného okna.

V mapě zpráv by měl být přesně jeden příkaz ON_CONTROL makro pro každou zprávu s oznámením ovládacího prvku, která musí být namapována na funkci obslužné rutiny zprávy.

Další informace a příklady naleznete v [tématu Zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_.h

## <a name="on_message"></a><a name="on_message"></a>ON_MESSAGE

Označuje, která funkce bude zpracovávat uživatelem definovanou zprávu.

### <a name="syntax"></a>Syntaxe

```cpp
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*Zprávu*<br/>
ID zprávy.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou je zpráva mapována.

Typ funkce musí být `afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`.

### <a name="remarks"></a>Poznámky

Uživatelem definované zprávy jsou všechny zprávy, které nejsou standardní mise Windows WM_MESSAGE zprávy. Při výběru ID zprávy je nutné použít hodnoty v rozsahu WM_USER (0x0400) na 0x7FFF nebo WM_APP (0x8000) až 0xBFFF. Další informace týkající se ID zpráv naleznete [v tématu WM_APP](/windows/win32/winmsg/wm-app).

V mapě zpráv by měl být přesně jeden příkaz ON_MESSAGE makro pro každou uživatelem definovanou zprávu, která musí být namapována na funkci obslužné rutiny zprávy.

> [!NOTE]
> Kromě uživatelem definovaných zpráv zpracovává ON_MESSAGE méně běžné zprávy systému Windows. Další informace naleznete v [tématu Mapy zpráv](../../mfc/tn006-message-maps.md).

Další informace a příklady naleznete v [tématu Témata zpracování zpráv a mapování](../../mfc/message-handling-and-mapping.md) a [uživatelem definované obslužné rutiny](user-defined-handlers.md)

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

## <a name="on_olecmd"></a><a name="on_olecmd"></a>ON_OLECMD

Směruje příkazy prostřednictvím `IOleCommandTarget`rozhraní pro odesílání příkazů .

### <a name="syntax"></a>Syntaxe

```cpp
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>Parametry

*skličovaný*<br/>
Identifikátor skupiny příkazů, do které příkaz patří. Pro standardní skupinu použijte hodnotu NULL.

*olecmdid*<br/>
Identifikátor příkazu OLE.

*Commandid*<br/>
ID nabídky, ID panelu nástrojů, ID tlačítka nebo jiné ID prostředku nebo objektu vydávajícího příkaz.

### <a name="remarks"></a>Poznámky

`IOleCommandTarget`Umožňuje kontejneru přijímat příkazy, které pocházejí z uživatelského rozhraní DocObject, a umožňuje kontejneru odesílat stejné příkazy (například New, Open, SaveAs a Print on the File menu; a Copy, Paste, Redo a so forth v nabídce Edit) do docobject.

`IOleCommandTarget`je jednodušší než ole `IDispatch`automatizace . `IOleCommandTarget`spoléhá zcela na standardní sadu příkazů, které mají zřídka argumenty a žádné informace o typu se jedná (bezpečnost typů je snížena pro argumenty příkazu také). Pokud potřebujete odeslat příkazy s argumenty, použijte [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd).

Standardní `IOleCommandTarget` příkazy nabídky byly implementovány knihovnou MFC v následujících makrech:

**ON_OLECMD_CLEARSELECTION( )**

Odešle příkaz Upravit vymazat. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Odešle příkaz Upravit kopii. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Odešle příkaz Upravit řez. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

Odešle příkaz Nový soubor. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

Odešle příkaz Otevřít soubor. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

Odešle příkaz Vzhled stránky souborů. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Odešle příkaz Upravit vložit. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Odešle příkaz Upravit vložit jinak. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

Odešle příkaz Tisk souborů. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

Odešle příkaz Náhled tisku souboru. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

Odešle příkaz Upravit znovu. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

Odešle příkaz Uložit soubor. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

Odešle příkaz Uložit jako soubor. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

Odešle příkaz Uložit kopii souboru jako. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Odešle příkaz Upravit vybrat vše. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

Odešle příkaz Upravit odvod. Implementováno jako:

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdocob.h

## <a name="on_registered_message"></a><a name="on_registered_message"></a>ON_REGISTERED_MESSAGE

Funkce `RegisterWindowMessage` systému Windows se používá k definování nové zprávy okna, která je zaručena jedinečná v celém systému.

### <a name="syntax"></a>Syntaxe

```cpp
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nProměnná zpráva*<br/>
Registrovaná id zprávy okna proměnné.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou je zpráva mapována.

### <a name="remarks"></a>Poznámky

Toto makro označuje, která funkce bude zpracovávat registrovanou zprávu.

Další informace a příklady naleznete v [tématu Zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).

### <a name="example"></a>Příklad

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_.h

## <a name="on_registered_thread_message"></a><a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Označuje, která funkce bude zpracovávat zprávu registrovanou funkcí Windows RegisterWindowMessage.

### <a name="syntax"></a>Syntaxe

```cpp
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>Parametry

*nProměnná zpráva*<br/>
Registrovaná id zprávy okna proměnné.

*členFxn*<br/>
Název funkce cwinthread-message-handler, na kterou je zpráva mapována.

### <a name="remarks"></a>Poznámky

RegisterWindowMessage se používá k definování nové okno zprávy, která je zaručena jedinečná v celém systému. ON_REGISTERED_THREAD_MESSAGE musí být použity místo ON_REGISTERED_MESSAGE, pokud máte CWinThread třídy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_.h

## <a name="on_thread_message"></a><a name="on_thread_message"></a>ON_THREAD_MESSAGE

Označuje, která funkce bude zpracovávat uživatelem definovanou zprávu.

### <a name="syntax"></a>Syntaxe

```cpp
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>Parametry

*Zprávu*<br/>
ID zprávy.

*členFxn*<br/>
Název `CWinThread`-message-handler funkce, na kterou je zpráva mapována.

### <a name="remarks"></a>Poznámky

ON_THREAD_MESSAGE musí být použity místo `CWinThread` ON_MESSAGE, pokud máte třídu. Uživatelem definované zprávy jsou všechny zprávy, které nejsou standardní mise Windows WM_MESSAGE zprávy. V mapě zpráv by měl být přesně jeden příkaz ON_THREAD_MESSAGE makro pro každou uživatelem definovanou zprávu, která musí být namapována na funkci obslužné rutiny zprávy.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="on_update_command_ui"></a><a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

Toto makro označuje, která funkce bude zpracovávat zprávu příkazu aktualizace uživatelského rozhraní.

### <a name="syntax"></a>Syntaxe

```cpp
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>Parametry

*Messageid*<br/>
ID zprávy.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou je zpráva mapována.

### <a name="remarks"></a>Poznámky

V mapě zpráv by měl být přesně jeden příkaz ON_UPDATE_COMMAND_UI makro pro každý příkaz aktualizace uživatelského rozhraní, který musí být mapován na funkci obslužné rutiny zprávy.

Další informace a příklady naleznete v [tématu Zpracování zpráv a mapování témata](../../mfc/message-handling-and-mapping.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="on_command_range"></a><a name="on_command_range"></a>ON_COMMAND_RANGE

Toto makro slouží k mapování souvislého rozsahu ID příkazů na jednu funkci obslužné rutiny zprávy.

### <a name="syntax"></a>Syntaxe

```cpp
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
ID příkazu na začátku souvislého rozsahu ID příkazů.

*id2*<br/>
ID příkazu na konci souvislého rozsahu ID příkazů.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Rozsah ID začíná *id1* a končí *id2*.

Pomocí ON_COMMAND_RANGE namapujte rozsah ID příkazů na jednu členskou funkci. Pomocí [ON_COMMAND](#on_command) namapujte jeden příkaz na členskou funkci. Pouze jedna položka mapy zprávy může odpovídat danému ID příkazu. To znamená, že příkaz nelze mapovat na více než jednu obslužnou rutinu. Další informace o mapových rozsahech zpráv naleznete v [tématu Obslužné rutiny pro rozsahy map zpráv](../../mfc/handlers-for-message-map-ranges.md).

Neexistuje žádná automatická podpora pro rozsahy map zpráv, takže je nutné makro umístit sami.

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

## <a name="on_update_command_ui_range"></a><a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

Mapuje souvislý rozsah ID příkazů na jednu funkci obslužné rutiny zprávy aktualizace.

### <a name="syntax"></a>Syntaxe

```cpp
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*id1*<br/>
ID příkazu na začátku souvislého rozsahu ID příkazů.

*id2*<br/>
ID příkazu na konci souvislého rozsahu ID příkazů.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy aktualizace, na kterou jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Aktualizace obslužných rutin zpráv aktualizuje stav položek nabídky a tlačítek panelu nástrojů přidružených k příkazu. Rozsah ID začíná *id1* a končí *id2*.

Neexistuje žádná automatická podpora pro rozsahy map zpráv, takže je nutné makro umístit sami.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_.h

## <a name="on_control_range"></a><a name="on_control_range"></a>ON_CONTROL_RANGE

Toto makro slouží k mapování souvislého rozsahu ID ovládacího prvku na jednu funkci obslužné rutiny zprávy pro zadanou zprávu systému Windows, například BN_CLICKED.

### <a name="syntax"></a>Syntaxe

```cpp
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>Parametry

*wNotifyCode*<br/>
Kód oznámení, na který odpovídá obslužná rutina.

*id1*<br/>
ID příkazu na začátku souvislého rozsahu ID ovládacího prvku.

*id2*<br/>
ID příkazu na konci souvislého rozsahu ID ovládacího prvku.

*členFxn*<br/>
Název funkce obslužné rutiny zprávy, na kterou jsou namapovány ovládací prvky.

### <a name="remarks"></a>Poznámky

Rozsah ID začíná *id1* a končí *id2*. Obslužná rutina je volána pro zadané oznámení pocházející z některého z mapovaných ovládacích prvků.

Neexistuje žádná automatická podpora pro rozsahy map zpráv, takže je nutné makro umístit sami.

Další informace o implementaci funkcí obslužné rutiny pro rozsah ID ovládacího prvku naleznete [v obslužné rutiny pro rozsahy map zpráv](../../mfc/handlers-for-message-map-ranges.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxmsg_.h

## <a name="see-also"></a>Viz také

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006: Mapy zpráv](../tn006-message-maps.md)<br/>
[COleCmdUI – třída](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[Uživatelem definované obslužné rutiny](user-defined-handlers.md)<br/>
[CCmdUI – třída](ccmdui-class.md)
