---
title: __hook | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __hook_cpp
dev_langs:
- C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f839b6c9b87bb37564951d1c15935ad573e1b46
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719287"
---
# <a name="hook"></a>__hook

Přidruží metodu obslužné rutiny události.

## <a name="syntax"></a>Syntaxe

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>Parametry

*& SourceClass::EventMethod*<br/>
Ukazatel na metodu události, ke kterému jste připojení metodu obslužné rutiny události:

- Nativní události C++: *SourceClass* je třídě zdroje události a *EventMethod* je událost.

- Události modelu COM: *SourceClass* je rozhraní zdroje událostí a *EventMethod* je jedna z jeho metod.

- Spravované události: *SourceClass* je třídě zdroje události a *EventMethod* je událost.

*interface*<br/>
Název rozhraní, které jsou připojeny k *příjemce*, pouze pro přijímače událostí modelu COM, ve kterém *layout_dependent* parametr [event_receiver](../windows/event-receiver.md) atribut je **true**.

*Zdroj*<br/>
Ukazatel na instanci zdroje událostí. V závislosti na kód `type` zadané v poli `event_receiver`, *zdroj* může být jedna z následujících akcí:

- Ukazatel objektu zdroje nativní události.

- `IUnknown`– Na základě ukazatel (zdroj COM).

- Spravovaný objekt ukazatele (pro spravované události).

*& ReceiverClass::HandlerMethod*<br/>
Ukazatel na metodu obslužné rutiny události pro připojeny k události. Obslužná rutina je zadán jako metoda třídy nebo odkaz na stejné. Pokud není zadán název třídy **__hook** předpokládá třídě může být, ve kterém je volána.

- Nativní události C++: *ReceiverClass* je přijímače událostí a `HandlerMethod` je obslužná rutina.

- Události modelu COM: *ReceiverClass* je rozhraní příjemce události a `HandlerMethod` je jedním z jeho obslužné rutiny.

- Spravované události: *ReceiverClass* je přijímače událostí a `HandlerMethod` je obslužná rutina.

*Příjemce*<br/>
(Volitelné) Ukazatel na instanci třídy příjemce událostí. Pokud nezadáte příjemce, výchozí hodnota je příjemce třídu nebo strukturu, ve kterém **__hook** je volána.

## <a name="usage"></a>Použití

Je možné použít v jakékoli oboru funkce, včetně hlavní mimo třídu příjemce událostí.

## <a name="remarks"></a>Poznámky

Použít vnitřní funkci **__hook** v přijímače událostí pro přidružení nebo zapojit obslužnou rutinu metody s metodou události. Zadaná obslužná rutina se pak volá, když zdroj vyvolá zadanou událost. Můžete připojit několik obslužných rutin pro jednu událost nebo připojit několik událostí k jedné obslužné rutině.

Existují dvě formy **__hook**. První formulář (4 argumenty) ve většině případů můžete použít konkrétně pro přijímače událostí modelu COM, ve kterém *layout_dependent* parametr [event_receiver](../windows/event-receiver.md) atribut je **false** .

V těchto případech nepotřebujete integrovat všechny metody v rozhraní než se ohlásí události v jedné z metod; pouze metody zpracování událostí musí být připojeny. Můžete použít druhý tvar (dvěma argumenty) **__hook** pouze pro příjemci události modelu COM, ve kterém *layout_dependent* **= true**.

**__hook** vrací dlouhou hodnotu. Nenulový návratová hodnota označuje, že došlo k chybě (spravované události vyvoláním výjimky).

Kompilátor zkontroluje existenci událost a že podpisu události souhlasí s delegáta.

S výjimkou událostí modelu COM **__hook** a **__unhook** lze volat mimo příjemce událostí.

O alternativu k použití **__hook** je použití operátoru +=.

Informace týkající se kódování spravované události v nové syntaxi naleznete v tématu [události](../windows/event-cpp-component-extensions.md).

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="example"></a>Příklad

Zobrazit [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md) a [zpracování událostí v modulu COM](../cpp/event-handling-in-com.md) ukázek.

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracování událostí](../cpp/event-handling.md)<br/>
[event_source](../windows/event-source.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
