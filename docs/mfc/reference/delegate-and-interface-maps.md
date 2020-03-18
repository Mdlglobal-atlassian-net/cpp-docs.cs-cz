---
title: Makra mapování delegátů a rozhraní (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421392"
---
# <a name="delegate-and-interface-map-macros"></a>Makra map delegátů a rozhraní

Knihovna MFC podporuje tato makra pro mapování delegátů a rozhraní:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Spustí mapu delegáta.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Zahájí definici mapy s rozhraním.|
|[CommandHandler – delegát](#commandhandler)|Registruje metody zpětného volání se zdrojem příkazů.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Ukončí mapu delegáta.|
|[END_INTERFACE_MAP](#end_interface_map)|Ukončí mapu rozhraní v implementačním souboru. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Vytvoří položku v mapě delegáta.|
|[INTERFACE_PART](#interface_part)|Používá se mezi makrem BEGIN_INTERFACE_MAP a makrem END_INTERFACE_MAP pro každé rozhraní, které bude váš objekt podporovat.|
|[MAKE_DELEGATE](#make_delegate)|Připojí obslužnou rutinu události ke spravovanému ovládacímu prvku.|

## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Spustí mapu delegáta.

### <a name="syntax"></a>Syntaxe

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parametry

*Deník*<br/>
Třída, ve které je spravovaný ovládací prvek hostován.

### <a name="remarks"></a>Poznámky

Toto makro označuje začátek seznamu položek delegátů, které tvoří mapu delegáta. Příklad toho, jak se toto makro používá, najdete v tématu [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Zahájí definici mapy rozhraní při použití v implementačním souboru.

### <a name="syntax"></a>Syntaxe

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ve které má být definována mapa rozhraní

*baseClass*<br/>
Třída, ze které je odvozeno *theclass* .

### <a name="remarks"></a>Poznámky

Pro každé rozhraní, které je implementováno, existuje jedno nebo více INTERFACE_PART volání makra. Pro každou agregaci, kterou třída používá, je k dispozici jedno INTERFACE_AGGREGATE vyvolání makra.

Další informace o mapách rozhraní najdete v části [Technická poznámka 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="commandhandler"></a>CommandHandler – delegát

Registruje metody zpětného volání se zdrojem příkazů.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu

### <a name="remarks"></a>Poznámky

Tento delegát registruje metody zpětného volání se zdrojem příkazů. Když přidáte delegáta do zdrojového objektu příkazu, bude metoda zpětného volání převedena do obslužné rutiny pro příkazy přicházející ze zadaného zdroje.

Další informace najdete v tématu [Postupy: Přidání směrování příkazů do ovládacího prvku model Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

##  <a name="commanduihandler"></a>Commanduihandler –

Registruje metody zpětného volání pomocí zprávy příkazu Update v uživatelském rozhraní.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu

*cmdUI*<br/>
ID zprávy příkazu

### <a name="remarks"></a>Poznámky

Tento delegát registruje metody zpětného volání pomocí zprávy příkazu Update v uživatelském rozhraní. `CommandUIHandler` se podobá [CommandHandler –](#commandhandler) s tím rozdílem, že tento delegát se používá pro příkazy aktualizace objektu uživatelského rozhraní. Příkazy pro aktualizaci uživatelského rozhraní by měly být mapovány pomocí metod obslužné rutiny zpráv One-to-One.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Ukončí mapu delegáta.

### <a name="syntax"></a>Syntaxe

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Poznámky

Toto makro označuje konec seznamu položek delegáta, které tvoří mapu delegáta. Příklad toho, jak se toto makro používá, najdete v tématu [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Ukončí mapu rozhraní v implementačním souboru.

### <a name="syntax"></a>Syntaxe

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Poznámky

Další informace o mapách rozhraní najdete v části [Technická poznámka 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Vytvoří položku v mapě delegáta.

### <a name="syntax"></a>Syntaxe

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parametry

*ČLEN*<br/>
Metoda obslužné rutiny události, která má být připojena k ovládacímu prvku.

*ARG0*<br/>
První argument metody obslužné rutiny spravované události, například `Object^`.

*ARG1*<br/>
Druhý argument metody obslužné rutiny spravované události, například `EventArgs^`.

### <a name="remarks"></a>Poznámky

Každá položka v mapě delegáta odpovídá delegátovi spravované obslužné rutiny události, kterou vytvořila [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak použít EVENT_DELEGATE_ENTRY k vytvoření položky v mapě delegáta pro obslužnou rutinu události `OnClick`; Podívejte se také na příklad kódu v MAKE_DELEGATE. Další informace naleznete v tématu [How to: jímka model Windows Forms Events z nativních C++ tříd](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

Používá se mezi makrem BEGIN_INTERFACE_MAP a makrem END_INTERFACE_MAP pro každé rozhraní, které bude váš objekt podporovat.

### <a name="syntax"></a>Syntaxe

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní.
*identifikátor*<br/>
Identifikátor IID, který má být namapován na vloženou třídu.
*localClass*<br/>
Název místní třídy.

### <a name="remarks"></a>Poznámky

Umožňuje mapovat IID na člena třídy označené *theclass* a *localClass*.

Další informace o mapách rozhraní najdete v části [Technická poznámka 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Připojí obslužnou rutinu události ke spravovanému ovládacímu prvku.

### <a name="syntax"></a>Syntaxe

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parametry

*DOSTÁVAL*<br/>
Typ delegáta spravované události, jako je například [obslužná](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True)rutina.

*ČLEN*<br/>
Název metody obslužné rutiny události, která má být připojena k ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Toto makro vytvoří delegáta spravované obslužné rutiny události typu *delegát* a *člena*Name. Delegát obslužné rutiny spravované události umožňuje nativní třídě zpracovávat spravované události.

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak volat `MAKE_DELEGATE` pro připojení obslužné rutiny události `OnClick` k ovládacímu prvku MFC `MyControl`. Širší vysvětlení, jak toto makro funguje v aplikaci knihovny MFC, naleznete v tématu [How to: jímka model Windows Forms Events z nativních C++ tříd](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

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
[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
