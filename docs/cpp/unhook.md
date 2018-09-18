---
title: __unhook | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3efdce5bb7a9ab093a53b6a005492aecd509f560
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117293"
---
# <a name="unhook"></a>__unhook

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

**&** *SourceClass* `::` *EventMethod* ukazatel na metodu události, ze kterého vyjmutí metodu obslužné rutiny události:

- Nativní události C++: *SourceClass* je třídě zdroje události a *EventMethod* je událost.

- Události modelu COM: *SourceClass* je rozhraní zdroje událostí a *EventMethod* je jedna z jeho metod.

- Spravované události: *SourceClass* je třídě zdroje události a *EventMethod* je událost.

*interface*<br/>
Název rozhraní se unhooked z *příjemce*, pouze pro přijímače událostí modelu COM, ve kterém *layout_dependent* parametr [event_receiver](../windows/event-receiver.md) atribut je **true**.

*Zdroj*<br/>
Ukazatel na instanci zdroje událostí. V závislosti na kód `type` zadané v poli `event_receiver`, *zdroj* může být jedna z následujících akcí:

- Ukazatel objektu zdroje nativní události.

- `IUnknown`– Na základě ukazatel (zdroj COM).

- Spravovaný objekt ukazatele (pro spravované události).

**&** *ReceiverClass* `::` `HandlerMethod` ukazatel na metodu obslužné rutiny události bude unhooked z události. Obslužná rutina je zadán jako metoda třídy nebo odkaz na stejné. Pokud není zadán název třídy **__unhook** předpokládá třídě může být, ve kterém je volána.

- Nativní události C++: *ReceiverClass* je přijímače událostí a `HandlerMethod` je obslužná rutina.

- Události modelu COM: *ReceiverClass* je rozhraní příjemce události a `HandlerMethod` je jedním z jeho obslužné rutiny.

- Spravované události: *ReceiverClass* je přijímače událostí a `HandlerMethod` je obslužná rutina.

*příjemce*(volitelné) ukazatel na instanci třídy příjemce událostí. Pokud nezadáte příjemce, výchozí hodnota je příjemce třídu nebo strukturu, ve kterém **__unhook** je volána.

## <a name="usage"></a>Použití

Je možné použít v jakékoli oboru funkce, včetně hlavní mimo třídu příjemce událostí.

## <a name="remarks"></a>Poznámky

Použít vnitřní funkci **__unhook** v příjemci události zrušit přidružení nebo "vyjmutí" metodu obslužné rutiny z metody událostí.

Existují tři formy **__unhook**. Ve většině případů můžete použít první formulář (4 argumenty). Můžete použít druhý tvar (dvěma argumenty) **__unhook** pouze pro příjemce události COM; to unhooks rozhraní celá událost. Třetí formuláře (jednoargumentové) můžete použít k vyjmutí Všichni delegáti ze zadaného zdroje.

Nenulový návratová hodnota označuje, že došlo k chybě (spravované události vyvolá výjimku).

Při volání **__unhook** na události a obslužná rutina události, které již nejsou připojeny, to nebude mít žádný efekt.

V době kompilace kompilátor ověří, jestli událost existuje, nemá parametr kontrolu typu zadaného popisovače.

S výjimkou událostí modelu COM **__hook** a **__unhook** lze volat mimo příjemce událostí.

O alternativu k použití **__unhook** je použití operátoru-=.

Informace týkající se kódování spravované události v nové syntaxi naleznete v tématu [události](../windows/event-cpp-component-extensions.md).

> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.

## <a name="example"></a>Příklad

Zobrazit [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md) a [zpracování událostí v modulu COM](../cpp/event-handling-in-com.md) ukázek.

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/event-source.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)