---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337553"
---
# <a name="__unhook"></a>__unhook

Disociaces metodu obslužné rutiny od události.

## <a name="syntax"></a>Syntaxe

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>Parametry

**&***SourceClass* `::` *EventMethod* Ukazatel na metodu události, ze které odpojit metodu obslužné rutiny události:

- Nativní události jazyka C++: *SourceClass* je třída zdroje událostí a *EventMethod* je událost.

- Události COM: *SourceClass* je zdrojové rozhraní události a *EventMethod* je jednou z jeho metod.

- Spravované události: *SourceClass* je třída zdroje událostí a *EventMethod* je událost.

*rozhraní*<br/>
Název rozhraní, který je odpojen od *příjemce*, pouze pro příjemce událostí COM, ve kterém je **splněn** *parametr layout_dependent* atributu [event_receiver](../windows/attributes/event-receiver.md) .

*Zdroj*<br/>
Ukazatel na instanci zdroje události. V závislosti `type` na `event_receiver`kódu určeném v písmenu a) může být *zdrojem* jeden z následujících:

- Ukazatel objektu zdrojové nativní události.

- Ukazatel `IUnknown`založený na -based (zdroj COM).

- Ukazatel spravovaného objektu (pro spravované události).

**&***ReceiverClass* `::` `HandlerMethod` Ukazatel na metodu obslužné rutiny události, která má být odpojena od události. Obslužná rutina je určena jako metoda třídy nebo odkaz na stejné; Pokud nezadáte název třídy, **__unhook** předpokládá, že třída je třída, ve které je volána.

- Nativní události jazyka C++: *ReceiverClass* je třída příjemce události a `HandlerMethod` je obslužnou rutinou.

- Události COM: *ReceiverClass* je rozhraní `HandlerMethod` příjemce událostí a je jedním z jeho obslužných rutin.

- Spravované události: *ReceiverClass* je třída `HandlerMethod` příjemce události a je obslužná rutina.

*přijímač*(volitelně) Ukazatel na instanci třídy přijímače událostí. Pokud nezadáte příjemce, výchozí je třída nebo struktura příjemce, ve které je volána **__unhook.**

## <a name="usage"></a>Využití

Lze použít v libovolném oboru funkce, včetně hlavní, mimo třídu příjemce události.

## <a name="remarks"></a>Poznámky

Pomocí vnitřní funkce **__unhook** v přijímači událostí oddělit nebo "unhook" metodu obslužné rutiny z metody události.

Existují tři formy **__unhook**. Ve většině případů můžete použít první formulář (čtyř argumentů). Druhou (dvouargumentovou) formu **__unhook** můžete použít pouze pro příjemce události COM; tím se odpojí celé rozhraní události. Třetí formulář (jeden argument) můžete použít k odpojení všech delegátů ze zadaného zdroje.

Nenulová vrácená hodnota označuje, že došlo k chybě (spravované události vyvolá výjimku).

Pokud zavoláte **__unhook** na obslužnou rutinu události a obslužnou rutinu události, které ještě nejsou zahnutý, nebude mít žádný vliv.

V době kompilace kompilátor ověří, zda událost existuje, a kontroluje typ parametru pomocí zadané obslužné rutiny.

S výjimkou událostí COM lze **__hook** a **__unhook** volat mimo příjemce události.

Alternativou k použití **__unhook** je použití operátoru -=.

Informace o kódování spravovaných událostí v nové syntaxi naleznete v [tématu událost](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="example"></a>Příklad

Ukázky najdete [v tématu Zpracování událostí v nativním jazyce C++](../cpp/event-handling-in-native-cpp.md) a [zpracování událostí v modelu COM.](../cpp/event-handling-in-com.md)

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
