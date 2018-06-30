---
title: Třída CWordArray | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 562f0eff1470a4754d3eaac15a94d08fefb95951
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123016"
---
# <a name="cwordarray-class"></a>CWordArray – třída
Podporuje pole 16bitové slova.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWordArray : public CObject  
```  
  
## <a name="members"></a>Členové  
 Členské funkce `CWordArray` jsou podobné funkce člena třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti, můžete použít `CObArray` referenční dokumentace pro konkrétní funkce člen. Po zobrazení [CObject](../../mfc/reference/cobject-class.md) ukazatel jako parametr funkce nebo vrací hodnotu, nahraďte slovo.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 například překládá do  
  
 `WORD CWordArray::GetAt( int <nIndex> ) const;`  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; zvětšování pole v případě potřeby.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli; zvětšování pole v případě potřeby.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje jiného pole k poli; zvětšování pole v případě potřeby.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasné odkaz na element ukazatele v rámci pole.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní všechny nevyužitou paměť nad aktuální horní mez.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet elementů v toto pole.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|  
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet elementů v toto pole.|  
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|  
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží zadaný index elementu (nebo všechny elementy v jiném poli).|  
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda pole prázdné.|  
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny elementy z tohoto pole.|  
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere element na konkrétním indexu.|  
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daného indexu; pole není povoleno zvětšovat.|  
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daného indexu; zvětšování pole v případě potřeby.|  
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků mají být obsažena v toto pole.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CObArray::operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá element v zadaném indexu.|  
  
## <a name="remarks"></a>Poznámky  
 `CWordArray` zahrnuje [implement_serial –](run-time-object-model-services.md#implement_serial) makro pro podporu serializace a vypsání jejích elementů. Pokud je pole slov uložen do archivu, a to buď operátor přetížené vložení nebo s [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) – členská funkce každý prvek se naopak serializovat.  
  
> [!NOTE]
>  Před použitím pole, použijte `SetSize` k zahájení jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidávání elementů do pole způsobí, že se často znovu přidělit a zkopírovat. Časté opakované přidělení a kopírování jsou neefektivní a může fragmentovat paměti.  
  
 Pokud potřebujete výpis jednotlivých prvků v poli, musíte nastavit hloubka kontext výpisu na 1 nebo vyšší.  
  
 Další informace o používání `CWordArray`, najdete v článku [kolekce](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CWordArray`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcoll.h  
  
##  <a name="icommandsource_interface"></a>  ICommandSource rozhraní  
 Spravuje příkazy, odeslané ze zdrojového objektu příkazu do uživatelského ovládacího prvku.  
  
```  
interface class ICommandSource  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hostitelem uživatelský ovládací prvek v zobrazení knihovny MFC [CWinFormsView třída](../../mfc/reference/cwinformsview-class.md) příkazy trasy a aktualizace příkaz zprávy uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementace, poskytnete uživatelského ovládacího prvku odkaz na `ICommandSource` objektu.  
  
 V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití `ICommandTarget`.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler  
 Obslužná rutina příkazu přidá do zdrojového objektu příkazu.  
  
```  
void AddCommandHandler(
    unsigned int cmdID,  
    CommandHandler^ cmdHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu.  
  
 *cmdHandler*  
 Popisovač metody obslužná rutina příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá obslužná rutina *cmdHandler* ke zdrojovému objektu příkazu a mapuje obslužná rutina *cmdID*.  
  
 V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití `AddCommandHandler`.  
  
##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler  
 Přidá skupinu obslužné rutiny příkazů do zdrojového objektu příkazu.  
  
```  
void AddCommandRangeHandler(
    unsigned int cmdIDMin,  
    unsigned int cmdIDMax,  
    CommandHandler^ cmdHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Index začátek rozsahu ID příkazu.  
  
 *cmdIDMax*  
 Koncová index rozsah ID příkazu.  
  
 *cmdHandler*  
 Popisovač pro metodu zpráva obslužná rutina, ke které jsou namapované příkazy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda mapuje souvislý rozsah ID příkazů do jedné zprávy rutiny a přidá ji do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.  
  
##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler  
 Přidá skupinu obslužné rutiny zpráv uživatelské rozhraní příkaz zdrojovým objektem příkaz.  
  
```  
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,   
    unsigned int cmdIDMax,   
    CommandUIHandler^ cmdUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Index začátek rozsahu ID příkazu.  
  
 *cmdIDMax*  
 Koncová index rozsah ID příkazu.  
  
 *cmdHandler*  
 Popisovač pro metodu zpráva obslužná rutina, ke které jsou namapované příkazy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda mapuje souvislý rozsah ID příkazů obslužné rutiny zpráv příkaz rozhraní jednoho uživatele a přidá ji do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.  
  
##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler  
 Obslužné rutiny zpráv uživatelské rozhraní příkaz přidá do zdrojového objektu příkazu.  
  
```  
void AddCommandUIHandler(
    unsigned int cmdID,   
    CommandUIHandler^ cmdUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu.  
  
 *cmdUIHandler*  
 Popisovač pro metodu uživatelské rozhraní příkaz zpráva obslužné rutiny.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá popisovač zpráv uživatelské rozhraní příkaz *cmdHandler* ke zdrojovému objektu příkazu a mapuje obslužná rutina *cmdID*.  
  
##  <a name="postcommand"></a>  ICommandSource::PostCommand  
 Odešle zprávu bez čekání na zpracování.  
  
```  
void PostCommand(unsigned int command);
```  
  
### <a name="parameters"></a>Parametry  
 *Příkaz*  
 Identifikátor příkazu zprávy odesílat.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda asynchronně odešle zprávu mapovat na ID určeného *příkaz*. Zavolá [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) umístit zprávy do fronty zpráv a potom vrátí okna bez čekání na okno odpovídající ke zpracování zprávy.  
  
##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler  
 Obslužná rutina příkazu odebere ze zdrojového objektu příkazu.  
  
```  
void RemoveCommandHandler(unsigned int cmdID);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere obslužná rutina namapovaná na *cmdID* ze zdrojového objektu příkazu.  
  
##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler  
 Odebere skupinu obslužné rutiny příkazů ze zdrojového objektu příkazu.  
  
```  
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,  
    unsigned int cmdIDMax);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Index začátek rozsahu ID příkazu.  
  
 *cmdIDMax*  
 Koncová index rozsah ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda Odebere skupinu obslužné rutiny zpráv mapována na projekt ID příkazu podle *cmdIDMin* a *cmdIDMax*, ze zdrojového objektu příkazu.  
  
##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler  
 Odebere skupinu obslužné rutiny zpráv uživatelské rozhraní příkaz z ke zdrojovému objektu příkazu.  
  
```  
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,  
    unsigned int cmdIDMax);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Index začátek rozsahu ID příkazu.  
  
 *cmdIDMax*  
 Koncová index rozsah ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda Odebere skupinu uživatelské rozhraní příkaz obslužné rutiny zpráv, mapována na projekt ID příkazu podle *cmdIDMin* a *cmdIDMax*, ze zdrojového objektu příkazu.  
  
##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler  
 Obslužné rutiny zpráv uživatelské rozhraní příkaz odebere ke zdrojovému objektu příkazu.  
  
```  
void RemoveCommandUIHandler(unsigned int cmdID);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 ID příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere namapované na popisovač zpráv příkaz uživatelské rozhraní *cmdID* ze zdrojového objektu příkazu.  
  
##  <a name="sendcommand"></a>  ICommandSource::SendCommand  
 Odešle zprávu a čeká na zpracování před vrácením.  
  
```  
void SendCommand(unsigned int command);
```  
  
### <a name="parameters"></a>Parametry  
 *Příkaz*  
 ID příkazu k odeslání zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda synchronně odešle zprávu mapovat na ID určeného *příkaz*. Zavolá [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) umístit zprávu fronty zpráv a čeká okno dokud okno postupu zprávu zpracovala před vrácením.  
  
##  <a name="icommandtarget_interface"></a>  Rozhraní ICommandTarget rozhraní  
 Poskytuje uživatelského ovládacího prvku rozhraní přijímají příkazy ke zdrojovému objektu příkazu.  
  
```  
interface class ICommandTarget  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hostitelem uživatelský ovládací prvek v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) příkazy trasy a aktualizace příkaz zprávy uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací `ICommandTarget`, poskytněte odkaz na objekt uživatelského ovládacího prvku.  
  
 V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití `ICommandTarget`.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="initialize"></a>  ICommandTarget::Initialize  
 Inicializuje objekt cíl příkazu.  
  
```  
void Initialize(ICommandSource^ cmdSource);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdSource*  
 Popisovač pro příkaz zdrojový objekt.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je hostitelem uživatelský ovládací prvek v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) příkazy trasy a aktualizace příkaz zprávy uživatelského rozhraní do uživatelského ovládacího prvku tak, aby ji zpracovávat příkazy knihovny MFC.  
  
 Tato metoda inicializuje cílový objekt příkazu a přidruží ji zdrojový objekt zadaný příkaz *cmdSource*. By měla být volána v implementaci třídy ovládacího prvku uživatele. Při inicializaci, byste měli zaregistrovat obslužné rutiny příkazů ke zdrojovému objektu příkaz voláním [ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md) v `Initialize` implementace. V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad použití `Initialize` k tomu.  
  
##  <a name="icommandui_interface"></a>  ICommandUI rozhraní  
 Spravovat příkazů uživatelského rozhraní.  
  
```  
interface class ICommandUI  
```  
  
### <a name="remarks"></a>Poznámky  
 Toto rozhraní poskytuje metody a vlastnosti, které spravovat příkazů uživatelského rozhraní. `ICommandUI` je podobná [CCmdUI – třída](../../mfc/reference/ccmdui-class.md)kromě toho, že `ICommandUI` se používá pro aplikace MFC, které spolupracovat s součásti rozhraní .NET.  
  
 `ICommandUI` se používá v rámci `ON_UPDATE_COMMAND_UI` obslužná rutina-odvozené třídy. Když uživatel aplikace aktivuje (vybere nebo klikne na) nabídky, každá položka nabídky se zobrazí jako povolené nebo zakázané. Cíl pro každý příkaz nabídky implementací poskytuje tyto informace `ON_UPDATE_COMMAND_UI` obslužné rutiny. Okno Vlastnosti pro každý z objektů příkaz uživatelského rozhraní v aplikaci, lze použijte k vytvoření mapy zpráv položku a funkce prototypu pro každou obslužnou rutinu.  
  
 Další informace o tom, jak `ICommandUI` rozhraní se používá v směrování příkazů najdete v tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Další informace o tom, jak se spravují příkazy uživatelského rozhraní v MFC najdete v tématu [CCmdUI – třída](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="check"></a>  ICommandUI::Check  
 Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.  
  
```  
property UICheckState Check;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Nastavit `Check` na následující hodnoty:  
  
|Termín|Definice|  
|----------|----------------|  
|0|Zrušte zaškrtnutí políčka|  
|1|Kontrola|  
|2|Nastavit neurčitém|  
  
##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting  
 Určuje příkaz mechanismus směrování pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Poznámky  
 Jedná se rozšířené – členská funkce, která se používá ve spojení s [on_command_ex –](message-map-macros-mfc.md#on_command_ex) obslužná rutina, která vrátí hodnotu FALSE. Další informace najdete v tématu technická Poznámka [TN006: mapy zpráv](../../mfc/tn006-message-maps.md).  
  
##  <a name="enabled"></a>  ICommandUI::Enabled  
 Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.  
  
```  
property bool Enabled;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato vlastnost povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz. Nastavit `Enabled` na hodnotu TRUE, FALSE povolit položky ji zakázat.  
  
##  <a name="id"></a>  ICommandUI::ID  
 Získá ID objektu uživatelské rozhraní reprezentována `ICommandUI` objektu.  
  
```  
property unsigned int ID;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato vlastnost získá ID (popisovač) položku nabídky panelu nástrojů tlačítko nebo jiných rozhraní objekt uživatele reprezentován `ICommandUI` objektu.  
  
##  <a name="index"></a>  ICommandUI::Index  
 Získá index rozhraní objekt uživatele reprezentován `ICommandUI` objektu.  
  
```  
property unsigned int Index;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato vlastnost získá index položky nabídky, tlačítka panelu nástrojů (popisovač) nebo jiných rozhraní objekt uživatele reprezentován `ICommandUI` objektu.  
  
##  <a name="radio"></a>  ICommandUI::Radio  
 Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.  
  
```  
property bool Radio;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Nastavit `Radio` na hodnotu TRUE, chcete-li povolit položky; jinak hodnota FALSE.  
  
##  <a name="text"></a>  ICommandUI::Text  
 Nastaví text položku uživatelského rozhraní pro tento příkaz.  
  
```  
property String^ Text;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato vlastnost nastaví text položku uživatelského rozhraní pro tento příkaz. Nastavit `Text` do textového řetězce popisovače.  
  
##  <a name="iview_interface"></a>  IView rozhraní  
 Implementuje několik metod, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) používá k odesílání oznámení zobrazení do ovládacího prvku spravované.  
  
```  
interface class IView  
```  
  
### <a name="remarks"></a>Poznámky  
 `IView` implementuje několik metod, `CWinFormsView` používá k předávání běžné zobrazení oznámení na hostované spravované ovládací prvek. Jedná se o [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) a [OnActivateView](../../mfc/reference/iview-interface.md).  
  
 `IView` je podobná [CView](../../mfc/reference/cview-class.md), ale se používá jenom s spravované zobrazení a ovládací prvky.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="onactivateview"></a>  IView::OnActivateView  
 Voláno rozhraním MFC, pokud je aktivace nebo deaktivace zobrazení.  
  
```  
void OnActivateView(bool activate);
```  
  
### <a name="parameters"></a>Parametry  
 *aktivovat*  
 Určuje, zda zobrazení se aktivace nebo deaktivace.  
  
##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate  
 Voláno rámcem po zobrazení je nejprve připojen k dokumentu, ale před zpočátku je zobrazeno zobrazení.  
  
```  
void OnInitialUpdate();
```  
  
##  <a name="onupdate"></a>  IView::OnUpdate  
 Voláno rozhraním MFC po zobrazení byly změny.  
  
```  
void OnUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce umožňuje zobrazit aktualizace jeho zobrazení, aby se projevily změny.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC shromažďování](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



