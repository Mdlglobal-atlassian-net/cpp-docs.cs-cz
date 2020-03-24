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
ms.openlocfilehash: 2a259b80b941e37e0c3040ad55894c114fe4bc82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160525"
---
# <a name="__unhook"></a>__unhook

Dissociates metodu obslužné rutiny z události.

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

**&** *SourceClass* `::` *EventMethod* ukazatel na metodu události, ze které odřadíte metodu obslužné rutiny události:

- Nativní C++ události: *SourceClass* je třída zdroje události a *EventMethod* je událost.

- Události COM: *SourceClass* je zdrojové rozhraní události a *EventMethod* je jednou z jeho metod.

- Spravované události: *SourceClass* je třída zdroje události a *EventMethod* je událost.

*interface*<br/>
Název rozhraní, který je odhlášený od *příjemce*, jenom pro přijímače událostí com, ve kterých je *layout_dependent* parametrem [event_receiver](../windows/attributes/event-receiver.md) atributu **true**.

*source*<br/>
Ukazatel na instanci zdroje události. V závislosti na kódu `type` zadaného v `event_receiver`může být *zdrojem* jedna z následujících:

- Zdrojový ukazatel objektu zdroje nativní události.

- Ukazatel založený na `IUnknown`(zdroj COM).

- Ukazatel spravovaného objektu (pro spravované události).

**&** *ReceiverClass* `::` `HandlerMethod` ukazatel na metodu obslužné rutiny události, která má být odpojování od události. Obslužná rutina je určena jako metoda třídy nebo odkaz na stejný; Pokud nezadáte název třídy, **__unhook** předpokládá, že třída bude volána.

- Nativní C++ události: *ReceiverClass* je třída přijímače událostí a `HandlerMethod` je obslužná rutina.

- Události COM: *ReceiverClass* je rozhraní přijímače událostí a `HandlerMethod` je jedním z jeho obslužných rutin.

- Spravované události: *ReceiverClass* je třída přijímače událostí a `HandlerMethod` je obslužná rutina.

*přijímač*(volitelné) ukazatel na instanci třídy přijímače událostí. Pokud nezadáte přijímač, výchozí hodnota je třída přijímače nebo struktura, ve které je volána **__unhook** .

## <a name="usage"></a>Využití

Dá se použít v jakémkoli oboru funkce, včetně Main, mimo třídu přijímače událostí.

## <a name="remarks"></a>Poznámky

Pomocí vnitřní funkce **__unhook** v přijímači událostí oddělit nebo odpojte metodu obslužné rutiny od metody události.

Existují tři formy **__unhook**. Ve většině případů můžete použít první formulář (se čtyřmi argumenty). Druhý (se dvěma argumenty) **__unhook** můžete použít jenom pro přijímač událostí com; tím odzavěsí celé rozhraní událostí. Třetí formulář (s jedním argumentem) můžete použít k odpojování všech delegátů ze zadaného zdroje.

Nenulová návratová hodnota označuje, že došlo k chybě (spravované události vyvolávají výjimku).

Pokud zavoláte **__unhook** u obslužné rutiny události a události, které ještě nejsou háčkované, nebude to mít žádný vliv.

V době kompilace kompilátor ověřuje, zda událost existuje a provede kontrolu typu parametru pomocí zadané obslužné rutiny.

S výjimkou událostí COM mohou být **__hook** a **__unhook** volány vně přijímače událostí.

Alternativou k použití **__unhook** je použití operátoru-=.

Informace o kódování spravovaných událostí v nové syntaxi naleznete v tématu [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.

## <a name="example"></a>Příklad

Ukázky najdete v tématu [zpracování C++ událostí v nativním](../cpp/event-handling-in-native-cpp.md) a [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md) .

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
