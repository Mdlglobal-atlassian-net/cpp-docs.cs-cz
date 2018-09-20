---
title: Cwordarray – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: cddcf337c68908d58749623e0739f3cb5979fa91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387949"
---
# <a name="cwordarray-class"></a>Cwordarray – třída

Podporuje pole s 16bitovými slovy.

## <a name="syntax"></a>Syntaxe

```
class CWordArray : public CObject
```

## <a name="members"></a>Členové

Členské funkce `CWordArray` jsou podobné jako u členských funkcí třídy [cobarray –](../../mfc/reference/cobarray-class.md). Z důvodu podobnosti, můžete použít `CObArray` referenční dokumentaci pro konkrétní členské funkce. Po zobrazení [CObject](../../mfc/reference/cobject-class.md) ukazatele jako parametr funkce nebo návratová hodnota, nahraďte slovo.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

například se přeloží na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Vytvoří prázdné pole.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Přidá prvek na konec pole. v případě potřeby se zvětší pole.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Připojí další pole k poli; v případě potřeby se zvětší pole.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Zkopíruje jiného objektu array do pole. v případě potřeby se zvětší pole.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Vrátí dočasný odkaz na ukazatel na prvek v poli.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Uvolní všechny nevyužité paměti nad aktuální horní mez.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Vrátí hodnotu na daném indexu.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Získá počet elementů v tomto poli.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umožňuje přístup k prvkům v poli. Může mít hodnotu NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Získá počet elementů v tomto poli.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Vrátí největší platný index.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Vloží zadaný index elementu (nebo všechny prvky v jiného objektu array).|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Určuje, zda je pole prázdné.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Odebere všechny prvky z tohoto pole.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Odebere element na konkrétní indexu.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Nastaví hodnotu pro daný index; pole nesmí růst.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Nastaví hodnotu pro daný index; v případě potřeby se zvětší pole.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Nastaví počet prvků, které mají být obsažena v tomto poli.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CObArray::operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Nastaví nebo získá prvek na zadaném indexu.|

## <a name="remarks"></a>Poznámky

`CWordArray` zahrnuje [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) – makro na podporu serializace a výpis z jeho prvků. Pokud je pole slov uloženo do archivu, s operátorem vložení přetížené nebo se [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) členská funkce, každý element je, v důsledku, serializovat.

> [!NOTE]
>  Před použitím pole, použijte `SetSize` vytvoření jeho velikost a přidělit paměť pro něj. Pokud nepoužijete `SetSize`, přidání prvků pole způsobí, že ho bude často nevyčerpané a zkopírovat. Časté realokace a kopírování jsou neefektivní a může fragmentovat paměti.

Pokud potřebujete s výpisem paměti jednotlivých prvků v poli, nastavte na 1 nebo větší hloubky kontextu s výpisem paměti.

Další informace o používání `CWordArray`, najdete v článku [kolekce](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcoll.h

##  <a name="icommandsource_interface"></a>  Icommandsource – rozhraní

Spravuje příkazy, odeslané ze zdrojového objektu příkazu do uživatelského ovládacího prvku.

```
interface class ICommandSource
```

### <a name="remarks"></a>Poznámky

Když hostujete uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací, můžete poskytnout uživatelský ovládací prvek odkazu na `ICommandSource` objektu.

Zobrazit [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `ICommandTarget`.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Obslužná rutina příkazu přidá do zdrojového objektu příkazu.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

*cmdHandler*<br/>
Popisovač metody obslužné rutiny příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda přidá obslužnou rutinu příkazu *cmdHandler* do zdrojového objektu příkazu a mapuje obslužná rutina *cmdID*.

Zobrazit [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `AddCommandHandler`.

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

Přidá skupinu obslužné rutiny příkazů do zdrojového objektu příkazu.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.

*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.

*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou mapovány příkazy.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů do jedné zprávy rutiny a přidá jej do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

Přidá skupinu obslužné rutiny zpráv uživatelské rozhraní příkazů do zdrojového objektu příkazu.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.

*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.

*cmdHandler*<br/>
Popisovač metody obslužné rutiny zpráv, ke které jsou mapovány příkazy.

### <a name="remarks"></a>Poznámky

Tato metoda mapuje souvislý rozsah ID příkazů do obslužné rutiny zpráv příkaz rozhraní jednoho uživatele a přidá jej do zdrojového objektu příkazu. Používá se pro zpracování skupina tlačítek, související s jednu metodu.

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

Obslužné rutiny zpráv uživatelské rozhraní příkaz přidá do zdrojového objektu příkazu.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

*cmdUIHandler*<br/>
Popisovač pro metodu obslužné rutiny zpráv příkaz uživatelské rozhraní.

### <a name="remarks"></a>Poznámky

Tato metoda přidá popisovač zprávy uživatelské rozhraní příkaz *cmdHandler* do zdrojového objektu příkazu a mapuje obslužná rutina *cmdID*.

##  <a name="postcommand"></a>  ICommandSource::PostCommand

Odešle zprávu bez čekání na zpracování.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
Identifikátor příkazu zprávy, která se má zveřejnit.

### <a name="remarks"></a>Poznámky

Tato metoda asynchronně odešle zprávu mapovat na ID určené *příkaz*. Volá [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) umístit zprávy do fronty zpráv a vrátí v okně bez čekání na okno odpovídající zprávu.

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

Obslužná rutina příkazu odebere ze zdrojového objektu příkazu.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odstraní obslužná rutina příkazu namapované na *cmdID* ze zdrojového objektu příkazu.

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

Odebere skupinu obslužné rutiny příkazů ze zdrojového objektu příkazu.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.

*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odstraní skupinu z namapované na zadaný ID příkazu ve obslužné rutiny zpráv *cmdIDMin* a *cmdIDMax*, ze zdrojového objektu příkazu.

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

Odebere skupinu obslužné rutiny zpráv uživatelské rozhraní příkazů ze zdrojového objektu příkazu.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Počáteční index rozsahu ID příkazu.

*cmdIDMax*<br/>
Poslední index rozsahu ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odstraní skupinu uživatelské rozhraní příkaz obslužné rutiny zpráv, mapovat na ID zadaný příkaz podle *cmdIDMin* a *cmdIDMax*, ze zdrojového objektu příkazu.

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

Obslužná rutina příkazu zprávy uživatelské rozhraní se odebere ze zdrojového objektu příkazu.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

### <a name="remarks"></a>Poznámky

Tato metoda odstraní uživatelské rozhraní zpráva obslužná rutina příkazu namapované na *cmdID* ze zdrojového objektu příkazu.

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

Odešle zprávu a čeká na zpracování před vrácením.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Příkaz*<br/>
Identifikátor příkazu zprávy k odeslání.

### <a name="remarks"></a>Poznámky

Tato metoda synchronně odešle zprávu mapovat na ID určené *příkaz*. Volá [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) mají být umístěny zprávy okna fronty zpráv a počká až tuto proceduru okna zpracovala zpráva před vrácením.

##  <a name="icommandtarget_interface"></a>  Icommandtarget – rozhraní

Uživatelský ovládací prvek poskytuje rozhraní pro příjem příkazy ze zdrojového objektu příkazu.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Poznámky

Když hostujete uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC (například rámec nabídky položek a tlačítka panelu nástrojů). Implementací `ICommandTarget`, poskytnout uživatelský ovládací prvek odkazu na objekt.

Zobrazit [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `ICommandTarget`.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>  ICommandTarget::Initialize

Inicializuje objekt cílového příkazu.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Popisovač do zdrojového objektu příkazu.

### <a name="remarks"></a>Poznámky

Když hostujete uživatelského ovládacího prvku v zobrazení knihovny MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) trasy příkazy a aktualizace příkazů zpráv uživatelského rozhraní do uživatelského ovládacího prvku, aby mohla zpracovávat příkazy knihovny MFC.

Tato metoda inicializuje cílový objekt příkazu a přidruží ji k objektu zdroje zadaného příkazu *cmdSource*. By měla být volána v implementaci třídy uživatelského ovládacího prvku. Při inicializaci, byste měli zaregistrovat obslužné rutiny příkazů s zdrojového objektu příkazu voláním [ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md) v `Initialize` implementace. V tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) příklad, jak používat `Initialize` provedete to tak.

##  <a name="icommandui_interface"></a>  Icommandui – rozhraní

Slouží ke správě uživatelských rozhraní příkazů.

```
interface class ICommandUI
```

### <a name="remarks"></a>Poznámky

Toto rozhraní poskytuje metody a vlastnosti, které spravují uživatelských rozhraní příkazů. `ICommandUI` je podobný [ccmdui – třída](../../mfc/reference/ccmdui-class.md), s tím rozdílem, že `ICommandUI` se používá pro aplikace knihovny MFC, které spolupracují s komponent architektury .NET.

`ICommandUI` se používá v rámci `ON_UPDATE_COMMAND_UI` obslužná rutina-odvozené třídy. Když uživatel aplikace aktivuje (zaškrtne nebo kliknutí) nabídka, každá položka nabídky se zobrazí jako povolené nebo zakázané. Cíl každý příkaz nabídky poskytuje tyto informace implementací `ON_UPDATE_COMMAND_UI` obslužné rutiny. Pro každý z objektů příkaz uživatelského rozhraní v aplikaci použijte okno Vlastnosti vytvořit položku mapování zpráv a prototyp funkce pro každou obslužnou rutinu.

Další informace o tom, jak `ICommandUI` rozhraní se používá v směrování příkazů, naleznete v tématu [postupy: přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Další informace o jak se spravují uživatelských rozhraní příkazů v knihovně MFC, naleznete v tématu [ccmdui – třída](../../mfc/reference/ccmdui-class.md).

##  <a name="check"></a>  ICommandUI::Check

Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.

```
property UICheckState Check;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Nastavte `Check` následující hodnoty:

|Termín|Definice|
|----------|----------------|
|0|Zrušte zaškrtnutí políčka|
|1|Kontrola|
|2|Nastavte neurčitý|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

Určuje mechanismus směrování příkazu pokračujte směrování aktuální zprávu v řetězu obslužné rutiny.

```
void ContinueRouting();
```

### <a name="remarks"></a>Poznámky

To je funkce členů s pokročilým členstvím, které byste měli použít ve spojení s [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) obslužná rutina, která vrátí hodnotu FALSE. Další informace viz technická Poznámka [TN006: mapy zpráv](../../mfc/tn006-message-maps.md).

##  <a name="enabled"></a>  ICommandUI::Enabled

Povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz.

```
property bool Enabled;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost povolí nebo zakáže položku uživatelského rozhraní pro tento příkaz. Nastavte `Enabled` na hodnotu TRUE, FALSE povolíte položku, pro jeho zakázání.

##  <a name="id"></a>  ICommandUI::ID

Získá ID rozhraní objekt uživatele reprezentován `ICommandUI` objektu.

```
property unsigned int ID;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost získá ID (popisovač) položky nabídky, tlačítka panelu nástrojů nebo jiné rozhraní objekt uživatele reprezentován `ICommandUI` objektu.

##  <a name="index"></a>  ICommandUI::Index

Získá index rozhraní objekt uživatele reprezentován `ICommandUI` objektu.

```
property unsigned int Index;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost získá index položky nabídky, tlačítka panelu nástrojů (popisovač) nebo jiné rozhraní objekt uživatele reprezentován `ICommandUI` objektu.

##  <a name="radio"></a>  ICommandUI::Radio

Nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu.

```
property bool Radio;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost nastaví položku uživatelského rozhraní pro tento příkaz do příslušné kontroly stavu. Nastavte `Radio` na hodnotu TRUE pro povolení položka, jinak FALSE.

##  <a name="text"></a>  ICommandUI::Text

Nastaví text položku uživatelského rozhraní pro tento příkaz.

```
property String^ Text;
```

### <a name="remarks"></a>Poznámky

Tato vlastnost nastavuje vlastnost text položky uživatelského rozhraní pro tento příkaz. Nastavte `Text` na popisovač řetězce textu.

##  <a name="iview_interface"></a>  IView – rozhraní

Implementuje několik metod, které [CWinFormsView](../../mfc/reference/cwinformsview-class.md) používá k odesílání oznámení zobrazení spravovatelného ovládacího prvku.

```
interface class IView
```

### <a name="remarks"></a>Poznámky

`IView` implementuje několik metod, které `CWinFormsView` používá k předávání běžné zobrazení oznámení na hostované spravovatelného ovládacího prvku. Jedná se o [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) a [OnActivateView](../../mfc/reference/iview-interface.md).

`IView` je podobný [CView](../../mfc/reference/cview-class.md), ale používá se pouze s ovládacími prvky a spravované zobrazení.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>  IView::OnActivateView

Volá se v prostředí MFC, když se aktivuje nebo deaktivuje zobrazení.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Parametry

*Aktivovat*<br/>
Určuje, zda je zobrazení se aktivuje nebo deaktivuje.

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

Volá se rozhraním po zobrazení je nejprve připojen k dokumentu, ale před začátku zobrazení.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>  IView::OnUpdate

Volá se v prostředí MFC po dokumentu v zobrazení se změnila.

```
void OnUpdate();
```

### <a name="remarks"></a>Poznámky

Tato funkce umožňuje zobrazení aktualizovat zobrazení tak, aby odrážely změny.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC shromažďování](../../visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)



