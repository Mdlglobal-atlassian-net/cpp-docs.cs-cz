---
title: CWordArray – třída
ms.date: 09/07/2019
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
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907913"
---
# <a name="cwordarray-class"></a>CWordArray – třída

Podporuje pole 16bitových slov.

## <a name="syntax"></a>Syntaxe

```
class CWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CWordArray` jsou podobné jako členské funkce třídy [CObArray](../../mfc/reference/cobarray-class.md). Z důvodu této podobnosti můžete použít `CObArray` referenční dokumentaci pro konkrétní členské funkce. Všude, kde vidíte ukazatel [CObject](../../mfc/reference/cobject-class.md) jako parametr funkce nebo návratovou hodnotu, nahraďte slovo.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CObArray:: Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole; v případě potřeby zvětší pole.|
|[CObArray:: Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli. v případě potřeby zvětší pole.|
|[CObArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje do pole jiné pole; v případě potřeby zvětší pole.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel elementu v rámci pole.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní veškerou nevyužitou paměť nad rámec aktuální horní meze.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu v daném indexu.|
|[CObArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet prvků v tomto poli.|
|[CObArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CObArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet prvků v tomto poli.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží prvek (nebo všechny prvky v jiném poli) do zadaného indexu.|
|[CObArray::-Empty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CObArray:: funkce RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere prvek v konkrétním indexu.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index. pole není povoleno zvětšit.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index. v případě potřeby zvětší pole.|
|[CObArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsaženy v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CObArray:: operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo Získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CWordArray`zahrnuje makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) pro podporu serializace a dumpingu jeho prvků. Je-li pole slov uloženo do archivu, buď pomocí přetíženého operátoru vložení, nebo pomocí členské funkce [CObject:: serializovat](../../mfc/reference/cobject-class.md#serialize) , je každý prvek následně serializován.

> [!NOTE]
>  Před použitím pole použijte `SetSize` k určení jeho velikosti a přidělení paměti pro něj. Pokud nepoužíváte `SetSize`, přidání prvků do pole způsobí, že bude často znovu přidělen a zkopírován. Časté přerozdělování a kopírování je neefektivní a může fragmentovat paměť.

Pokud potřebujete výpis paměti jednotlivých prvků v poli, je nutné nastavit hloubku kontextu výpisu na hodnotu 1 nebo vyšší.

Další informace o použití nástroje `CWordArray`najdete v článku [kolekce](../../mfc/collections.md)článků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll. h

##  <a name="icommandsource_interface"></a>Rozhraní rozhraní ICommandSource

Spravuje příkazy odesílané ze zdrojového objektu příkazu do uživatelského ovládacího prvku.

```
interface class ICommandSource
```

### <a name="remarks"></a>Poznámky

Při hostování uživatelského ovládacího prvku v zobrazení knihovny MFC, [třídy CWinFormsView](../../mfc/reference/cwinformsview-class.md) směrují příkazy a zprávy uživatelského rozhraní příkazu k ovládacímu prvku, aby umožnily zpracování příkazů MFC (například položky nabídky rámce a tlačítka panelu nástrojů). Implementací udělíte uživatelskému ovládacímu prvku odkaz na `ICommandSource` objekt.

Viz [jak: Přidejte směrování příkazů do ovládacího prvku](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) model Windows Forms, který ukazuje, jak použít. `ICommandTarget`

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>Rozhraní ICommandSource:: AddCommandHandler

Přidá obslužnou rutinu příkazu do zdrojového objektu příkazu.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu

*cmdHandler*<br/>
Popisovač metody obslužné rutiny příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda přidá obslužnou rutinu příkazu *cmdHandler* do zdrojového objektu příkazu a mapuje obslužnou rutinu na *cmdID*.

Viz [jak: Přidejte směrování příkazů do ovládacího prvku](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) model Windows Forms, který ukazuje, jak použít. `AddCommandHandler`

##  <a name="addcommandrangehandler"></a>Rozhraní ICommandSource:: AddCommandRangeHandler

Přidá skupinu obslužných rutin příkazu do zdrojového objektu příkazu.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu

*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů

*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů na jednu obslužnou rutinu zpráv a přidá ji do zdrojového objektu příkazu. Slouží ke zpracování skupiny souvisejících tlačítek s jednou metodou.

##  <a name="addcommandrangeuihandler"></a>Rozhraní ICommandSource:: AddCommandRangeUIHandler

Přidá skupinu obslužných rutin zpráv příkazu uživatelského rozhraní do zdrojového objektu příkazu.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu

*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů

*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou příkazy mapovány.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů na obslužnou rutinu zprávy příkazu jediného uživatelského rozhraní a přidá ji do zdrojového objektu příkazu. Slouží ke zpracování skupiny souvisejících tlačítek s jednou metodou.

##  <a name="addcommanduihandler"></a>Rozhraní ICommandSource:: AddCommandUIHandler

Přidá do zdrojového objektu příkazu obslužnou rutinu zprávy příkazu uživatelského rozhraní.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu

*cmdUIHandler*<br/>
Popisovač metody obslužné rutiny zprávy příkazu uživatelského rozhraní.

### <a name="remarks"></a>Poznámky

Tato metoda přidá do zdrojového objektu příkazu obslužnou rutinu zprávy příkazu uživatelského rozhraní *cmdHandler* a mapuje obslužnou rutinu na *cmdID*.

##  <a name="postcommand"></a>Rozhraní ICommandSource::P ostCommand

Odešle zprávu bez čekání na zpracování.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*systému*<br/>
ID příkazu zprávy, která má být odeslána.

### <a name="remarks"></a>Poznámky

Tato metoda asynchronně odesílá zprávu namapovanou na ID určené *příkazem*. Volá [CWnd::P ostmessage](../../mfc/reference/cwnd-class.md#postmessage) umístit zprávu do fronty zpráv v okně a pak se vrátí bez čekání na odpovídající okno ke zpracování zprávy.

##  <a name="removecommandhandler"></a>Rozhraní ICommandSource:: RemoveCommandHandler

Odebere obslužnou rutinu příkazu ze zdrojového objektu příkazu.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu

### <a name="remarks"></a>Poznámky

Tato metoda odebere obslužnou rutinu příkazu namapovanou na *cmdID* ze zdrojového objektu příkazu.

##  <a name="removecommandrangehandler"></a>Rozhraní ICommandSource:: RemoveCommandRangeHandler

Odebere skupinu obslužných rutin příkazů ze zdrojového objektu příkazu.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu

*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů

### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu obslužných rutin zpráv mapovaných na ID příkazů zadaných pomocí *cmdIDMin* a *cmdIDMax*ze zdrojového objektu příkazu.

##  <a name="removecommandrangeuihandler"></a>Rozhraní ICommandSource:: RemoveCommandRangeUIHandler

Odebere skupinu obslužných rutin zpráv příkazu uživatelského rozhraní ze zdrojového objektu příkazu.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu

*cmdIDMax*<br/>
Koncový index rozsahu ID příkazů

### <a name="remarks"></a>Poznámky

Tato metoda odebere skupinu obslužných rutin zpráv příkazu uživatelského rozhraní, které jsou mapovány na ID příkazů určené parametrem *cmdIDMin* a *cmdIDMax*, ze zdrojového objektu příkazu.

##  <a name="removecommanduihandler"></a>Rozhraní ICommandSource:: RemoveCommandUIHandler

Odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní ze zdrojového objektu příkazu.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu

### <a name="remarks"></a>Poznámky

Tato metoda odebere obslužnou rutinu zprávy příkazu uživatelského rozhraní namapovanou na *cmdID* ze zdrojového objektu příkazu.

##  <a name="sendcommand"></a>Rozhraní ICommandSource:: SendCommand

Před vrácením pošle zprávu a počká, než se zpracuje.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*systému*<br/>
ID příkazu zprávy, která se má odeslat

### <a name="remarks"></a>Poznámky

Tato metoda synchronně odesílá zprávu namapovanou na ID určené *příkazem*. Volá [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) k umístění zprávy do fronty zpráv v okně a počká, dokud tento proces okna před vrácením nezpracovává zprávu.

##  <a name="icommandtarget_interface"></a>Rozhraní ICommandTarget

Poskytuje uživatelský ovládací prvek s rozhraním pro příjem příkazů ze zdrojového objektu příkazu.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Poznámky

Při hostování uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizovat zprávy uživatelského rozhraní příkazů do uživatelského ovládacího prvku, aby mohl zpracovávat příkazy MFC (například položky nabídky rámce a tlačítka panelu nástrojů). Implementací `ICommandTarget`udělíte uživatelskému ovládacímu prvku odkaz na objekt.

Viz [jak: Přidejte směrování příkazů do ovládacího prvku](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) model Windows Forms, který ukazuje, jak použít. `ICommandTarget`

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>ICommandTarget:: Initialize

Inicializuje cílový objekt příkazu.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Popisovač zdrojového objektu příkazu.

### <a name="remarks"></a>Poznámky

Při hostování uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizovat zprávy uživatelského rozhraní příkazů do uživatelského ovládacího prvku, aby mohl zpracovávat příkazy MFC.

Tato metoda inicializuje cílový objekt příkazu a přidruží ho k zadanému zdrojovému objektu příkazu *cmdSource*. Měla by být volána v implementaci třídy uživatelského ovládacího prvku. Při inicializaci byste měli zaregistrovat obslužné rutiny příkazů u objektu zdrojového příkazu voláním [rozhraní ICommandSource:: AddCommandHandler](../../mfc/reference/icommandsource-interface.md) v `Initialize` implementaci. Viz [jak: Přidejte směrování příkazů do ovládacího prvku](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) model Windows Forms, kde můžete příklad použít `Initialize` k tomu.

##  <a name="icommandui_interface"></a>Rozhraní ICommandUI

Spravuje příkazy uživatelského rozhraní.

```
interface class ICommandUI
```

### <a name="remarks"></a>Poznámky

Toto rozhraní poskytuje metody a vlastnosti, které spravují příkazy uživatelského rozhraní. `ICommandUI`se podobá [třídě CCmdUI –](../../mfc/reference/ccmdui-class.md), s tím `ICommandUI` rozdílem, že se používá pro aplikace MFC, které spolupracují s komponentami .NET.

`ICommandUI`se používá v `ON_UPDATE_COMMAND_UI` obslužné rutině v odvozené třídě. Když se uživatel aplikace aktivuje (vybere nebo klikne) na nabídku, zobrazí se každá položka nabídky jako povolená nebo zakázaná. Cíl jednotlivých příkazů nabídky poskytuje tyto informace implementací `ON_UPDATE_COMMAND_UI` obslužné rutiny. Pro každý z objektů uživatelského rozhraní příkazu v aplikaci použijte [Průvodce třídou](mfc-class-wizard.md) nebo okno **vlastností** (v **zobrazení tříd**) k vytvoření položky mapování zpráv a prototypu funkce pro každou obslužnou rutinu.

Další informace o tom, jak `ICommandUI` se rozhraní používá při směrování příkazu, najdete [v tématu How to: Přidejte směrování příkazů do ovládacího prvku](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)model Windows Forms.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Další informace o tom, jak jsou příkazy uživatelského rozhraní spravovány v knihovně MFC, naleznete v tématu [Třída CCmdUI –](../../mfc/reference/ccmdui-class.md).

##  <a name="check"></a>ICommandUI:: check

Nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.

```
property UICheckState Check;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly. Nastavte `Check` následující hodnoty:

|Termín|Definice|
|----------|----------------|
|0|Zrušte zaškrtnutí políčka|
|1|Kontrola|
|2|Nastavit neurčitelné|

##  <a name="continuerouting"></a>ICommandUI::ContinueRouting

Oznamuje mechanismu směrování příkazů, aby pokračoval v směrování aktuální zprávy o řetězu obslužných rutin.

```
void ContinueRouting();
```

### <a name="remarks"></a>Poznámky

Toto je pokročilá členská funkce, která by se měla používat ve spojení s obslužnou rutinou [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) , která vrací hodnotu false. Další informace najdete v tématu technická Poznámka [TN006: Mapy](../../mfc/tn006-message-maps.md)zpráv.

##  <a name="enabled"></a>ICommandUI:: Enabled

Povoluje nebo zakazuje položku uživatelského rozhraní pro tento příkaz.

```
property bool Enabled;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost povoluje nebo zakazuje položku uživatelského rozhraní pro tento příkaz. Nastavte `Enabled` na hodnotu true, chcete-li povolit položku, hodnotu false pro její zakázání.

##  <a name="id"></a>ICommandUI:: ID

Získá ID objektu uživatelského rozhraní reprezentovaného `ICommandUI` objektem.

```
property unsigned int ID;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost získá ID (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiného objektu uživatelského rozhraní reprezentovaného `ICommandUI` objektem.

##  <a name="index"></a>ICommandUI:: index

Získá index objektu uživatelského rozhraní reprezentovaného `ICommandUI` objektem.

```
property unsigned int Index;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost získá index (popisovač) položky nabídky, tlačítko panelu nástrojů nebo jiný objekt uživatelského rozhraní reprezentovaný `ICommandUI` objektem.

##  <a name="radio"></a>ICommandUI:: Radio

Nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly.

```
property bool Radio;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz na příslušný stav kontroly. Nastavte `Radio` na hodnotu true, pokud chcete položku Povolit. v opačném případě false.

##  <a name="text"></a>ICommandUI:: text

Nastaví text položky uživatelského rozhraní pro tento příkaz.

```
property String^ Text;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost nastavuje text položky uživatelského rozhraní pro tento příkaz. Nastavte `Text` na popisovač textového řetězce.

##  <a name="iview_interface"></a>Rozhraní IView

Implementuje několik metod, které [CWinFormsView](../../mfc/reference/cwinformsview-class.md) používá k odesílání oznámení zobrazení spravovanému ovládacímu prvku.

```
interface class IView
```

### <a name="remarks"></a>Poznámky

`IView`implementuje několik metod, `CWinFormsView` které nástroj používá pro přeposílání běžných oznámení o zobrazení do hostovaného spravovaného ovládacího prvku. Jsou to [OnInitialUpdate](../../mfc/reference/iview-interface.md), [Update](../../mfc/reference/iview-interface.md) a [OnActivateView](../../mfc/reference/iview-interface.md).

`IView`je podobný jako [CView](../../mfc/reference/cview-class.md), ale používá se pouze se spravovanými zobrazeními a ovládacími prvky.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>IView:: OnActivateView

Volá se knihovnou MFC při aktivaci nebo deaktivaci zobrazení.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Parametry

*aktivací*<br/>
Označuje, zda se zobrazení aktivuje nebo deaktivuje.

##  <a name="oninitialupdate"></a>IView:: OnInitialUpdate

Volá se rozhraním po prvním připojení zobrazení k dokumentu, ale před tím, než se zobrazení zpočátku zobrazí.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>IView:: inupdate

Volá se knihovnou MFC po úpravě dokumentu zobrazení.

```
void OnUpdate();
```

### <a name="remarks"></a>Poznámky

Tato funkce umožňuje zobrazení aktualizovat zobrazení tak, aby odráželo úpravy.

## <a name="see-also"></a>Viz také:

[Ukázka MFC – shromáždit](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
