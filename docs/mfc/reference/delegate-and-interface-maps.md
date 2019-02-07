---
title: Delegát a Interface makra mapy (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850200"
---
# <a name="delegate-and-interface-map-macros"></a>Makra map delegátů a rozhraní

MFC podporuje tato makra map delegátů a rozhraní:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Začne mapování delegáta.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Začíná definici připojený mapy.|
|[Commandhandler – delegát](#commandhandler)|Zaregistruje zpětné volání metody se zdrojem příkazu.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Ukončí mapu delegáta.|
|[END_INTERFACE_MAP](#end_interface_map)|Ukončí mapy rozhraní v souboru implementace. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Vytvoří položku v objektu map delegátů.|
|[INTERFACE_PART](#interface_part)|Použít mezi – makro BEGIN_INTERFACE_MAP a END_INTERFACE_MAP – makro pro každé rozhraní, které bude váš objekt podporovat.|
|[MAKE_DELEGATE](#make_delegate)|Připojí obslužnou rutinu události spravovatelného ovládacího prvku.|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

Začne mapování delegáta.

### <a name="syntax"></a>Syntaxe

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parametry

*TŘÍDA*<br/>
Třída, ve kterém je hostovaný spravovatelného ovládacího prvku.

### <a name="remarks"></a>Poznámky

Toto makro označuje konec seznamu položek delegáta, které tvoří mapu delegáta. Příklad toho, jak se toto makro používá, najdete v části [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Začíná definici připojený mapy při použití v souboru implementace.

### <a name="syntax"></a>Syntaxe

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ve kterém má definovat mapa rozhraní

*baseClass*<br/>
Třída, ze které *theClass* odvozena.

### <a name="remarks"></a>Poznámky

Pro každé rozhraní, která je implementována je jeden nebo více vyvoláním makra INTERFACE_PART. Pro každou agregaci, která používá třídu je jedna volání makra INTERFACE_AGGREGATE.

Další informace o mapy rozhraní najdete v tématu [technická Poznámka: 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="commandhandler"></a>Commandhandler – delegát

Zaregistruje zpětné volání metody se zdrojem příkazu.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

### <a name="remarks"></a>Poznámky

Tento delegát zaregistruje zpětné volání metody se zdrojem příkazu. Když do zdrojového objektu příkazu přidáte delegáta, stane se metoda zpětného volání obslužné rutiny pro příkazy pocházející ze zadaného zdroje.

Další informace najdete v tématu [jak: Příkaz přidat ovládací prvek směrování Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)

##  <a name="commanduihandler"></a>Commanduihandler –

Zaregistruje zpětné volání metody zpráva příkaz aktualizace uživatelského rozhraní.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu.

*cmdUI*<br/>
Identifikátor příkazu zprávy

### <a name="remarks"></a>Poznámky

Tento delegát registruje metody zpětného volání příkazu zpráva aktualizace uživatelského rozhraní. `CommandUIHandler` je podobný [commandhandler –](#commandhandler) s tím rozdílem, že tento delegát je použít s příkazy aktualizace objektů uživatelského rozhraní. Příkazy aktualizace uživatelského rozhraní by měly být namapované 1: 1 se metody obslužné rutiny zpráv.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Ukončí mapu delegáta.

### <a name="syntax"></a>Syntaxe

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Poznámky

Toto makro označuje konec seznamu položek delegáta, které tvoří mapu delegáta. Příklad toho, jak se toto makro používá, najdete v části [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Ukončí mapy rozhraní v souboru implementace.

### <a name="syntax"></a>Syntaxe

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Poznámky

Další informace o mapy rozhraní najdete v tématu [technická Poznámka: 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Vytvoří položku v objektu map delegátů.

### <a name="syntax"></a>Syntaxe

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parametry

*ČLEN*<br/>
Metoda obslužné rutiny události bude připojený k ovládacímu prvku.

*ARG0*<br/>
Prvním argumentem funkce spravované obslužná rutina události, jako například `Object^`.

*ARG1*<br/>
Druhý argument spravované obslužná rutina události, jako například `EventArgs^`.

### <a name="remarks"></a>Poznámky

Každá položka v mapě delegáta odpovídá obslužné rutiny delegáta spravované události vytvořené [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak můžete vytvořit položku v objektu map delegátů pro EVENT_DELEGATE_ENTRY `OnClick` obslužné rutiny události; také naleznete v příkladu kódu v MAKE_DELEGATE. Další informace najdete v tématu [jak: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

Použít mezi – makro BEGIN_INTERFACE_MAP a END_INTERFACE_MAP – makro pro každé rozhraní, které bude váš objekt podporovat.

### <a name="syntax"></a>Syntaxe

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní.
*iid*<br/>
Identifikátor IID, který se má namapovat na vloženou třídu.
*localClass*<br/>
Název místní třídy.

### <a name="remarks"></a>Poznámky

Umožňuje mapovat IID ke členovi třídy podle *theClass* a *localClass*.

Další informace o mapy rozhraní najdete v tématu [technická Poznámka: 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Připojí obslužnou rutinu události spravovatelného ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parametry

*DELEGÁT*<br/>
Typu spravované obslužné rutiny delegáta, například [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).

*ČLEN*<br/>
Název metody obslužné rutiny události bude připojený k ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Toto makro vytvoří delegát obslužné rutiny spravovaná událost typu *delegovat* a názvu *člen*. Delegát obslužné rutiny události spravované umožňuje nativních tříd pro zpracování spravované události.

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak volat `MAKE_DELEGATE` připojit `OnClick` obslužnou rutinu události pro ovládací prvek MFC `MyControl`. Širší vysvětlení fungování toto makro v aplikaci knihovny MFC, najdete v článku [jak: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

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

## <a name="see-also"></a>Viz také:

[Postupy: Zpracování jímky událostí modelu Windows Forms z nativních tříd jazyka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Postupy: Přidání směrování příkazů do ovládacího prvku modelu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
