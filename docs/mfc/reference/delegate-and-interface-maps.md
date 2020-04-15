---
title: Makra mapování delegáta a rozhraní (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365826"
---
# <a name="delegate-and-interface-map-macros"></a>Makra map delegátů a rozhraní

Knihovna MFC podporuje tato makra pro delegáty a mapy rozhraní:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Začíná mapování delegáta.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Začíná definice mapy s rozhraním.|
|[Delegát příkazu](#commandhandler)|Registruje metody zpětného volání se zdrojem příkazů.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Ukončí mapu delegátů.|
|[END_INTERFACE_MAP](#end_interface_map)|Ukončí mapu rozhraní v souboru implementace. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Vytvoří položku v mapě delegáta.|
|[INTERFACE_PART](#interface_part)|Používá se mezi BEGIN_INTERFACE_MAP makra a makro END_INTERFACE_MAP pro každé rozhraní, které bude objekt podporovat.|
|[MAKE_DELEGATE](#make_delegate)|Připojí obslužnou rutinu události ke spravovanému ovládacímu prvku.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Začíná mapování delegáta.

### <a name="syntax"></a>Syntaxe

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parametry

*Třída*<br/>
Třída, ve které je hostovaný spravovaný ovládací prvek.

### <a name="remarks"></a>Poznámky

Toto makro označuje začátek seznamu položek delegáta, které tvoří mapu delegáta. Příklad použití tohoto makra naleznete [v tématu EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Začíná definice rozhraní mapy při použití v souboru implementace.

### <a name="syntax"></a>Syntaxe

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ve které má být definována mapa rozhraní

*Baseclass*<br/>
Třída, ze které *Class* pochází z.

### <a name="remarks"></a>Poznámky

Pro každé rozhraní, které je implementováno, je jeden nebo více INTERFACE_PART vyvolání makra. Pro každý agregace, který používá třída, je jedna INTERFACE_AGGREGATE vyvolání makra.

Další informace o mapách rozhraní naleznete v [technické poznámce 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>Delegát příkazu

Registruje metody zpětného volání se zdrojem příkazů.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

### <a name="remarks"></a>Poznámky

Tento delegát registruje metody zpětného volání se zdrojem příkazů. Když přidáte delegáta do objektu zdroje příkazů, metoda zpětného volání se stane obslužnou rutinou pro příkazy přicházející ze zadaného zdroje.

Další informace naleznete v [tématu Postup: Přidání příkazu směrování do ovládacího prvku Formuláře systému Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="commanduihandler"></a><a name="commanduihandler"></a>Komandiemaniobs

Registruje metody zpětného volání pomocí zprávy příkazu aktualizace uživatelského rozhraní.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

*cmdUI*<br/>
ID příkazové zprávy.

### <a name="remarks"></a>Poznámky

Tento delegát registruje metody zpětného volání se zprávou příkazu příkazu aktualizace uživatelského rozhraní. `CommandUIHandler`je podobný [CommandHandler](#commandhandler) s tím rozdílem, že tento delegát se používá s příkazy aktualizace objektu uživatelského rozhraní. Příkazy aktualizace uživatelského rozhraní by měly být mapovány jeden na jednoho s metodami obslužné rutiny zpráv.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

Ukončí mapu delegátů.

### <a name="syntax"></a>Syntaxe

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Poznámky

Toto makro označuje konec seznamu položek delegáta, které tvoří mapu delegáta. Příklad použití tohoto makra naleznete [v tématu EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

Ukončí mapu rozhraní v souboru implementace.

### <a name="syntax"></a>Syntaxe

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Poznámky

Další informace o mapách rozhraní naleznete [v technické poznámce 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Vytvoří položku v mapě delegáta.

### <a name="syntax"></a>Syntaxe

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parametry

*Členské*<br/>
Metoda obslužné rutiny události, která má být připojena k ovládacímu prvku.

*ARG0*<br/>
První argument metody obslužné `Object^`rutiny spravované události, například .

*ARG1*<br/>
Druhý argument metody obslužné `EventArgs^`rutiny spravované události, například .

### <a name="remarks"></a>Poznámky

Každá položka v mapě delegáta odpovídá delegátovi obslužné rutiny spravované události vytvořenému [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak použít EVENT_DELEGATE_ENTRY k vytvoření `OnClick` položky v mapě delegáta pro obslužnou rutinu události; viz také příklad kódu v MAKE_DELEGATE. Další informace naleznete v [tématu How to: Sink Windows Forms Events from Native C++ Classes](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

## <a name="interface_part"></a><a name="interface_part"></a>INTERFACE_PART

Používá se mezi BEGIN_INTERFACE_MAP makra a makro END_INTERFACE_MAP pro každé rozhraní, které bude objekt podporovat.

### <a name="syntax"></a>Syntaxe

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní.
*Iid*<br/>
IID, který má být mapován na vložené třídy.
*localClass*<br/>
Název místní třídy.

### <a name="remarks"></a>Poznámky

Umožňuje mapovat IID na člena třídy označené *class* a *localClass*.

Další informace o mapách rozhraní naleznete v [technické poznámce 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

Připojí obslužnou rutinu události ke spravovanému ovládacímu prvku.

### <a name="syntax"></a>Syntaxe

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parametry

*Delegát*<br/>
Typ delegáta obslužné rutiny spravované události, například [EventHandler](/dotnet/api/system.eventhandler).

*Členské*<br/>
Název metody obslužné rutiny události, která má být připojena k ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Toto makro vytvoří delegáta obslužné rutiny spravované události typu *DELEGATE* a názvu *MEMBER*. Delegát obslužné rutiny spravované události umožňuje nativní třídě zpracovávat spravované události.

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `MAKE_DELEGATE` jak `OnClick` volat připojení obslužné rutiny události k ovládacímu prvku `MyControl`knihovny MFC . Širší vysvětlení fungování tohoto makra v aplikaci knihovny MFC naleznete v tématu [How to: Sink Windows Forms Events from Native C++ Classes](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

## <a name="see-also"></a>Viz také

[Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Makra a globální](mfc-macros-and-globals.md)<br/>
