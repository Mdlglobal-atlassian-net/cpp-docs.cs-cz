---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: f8935408c6e9b43347d4ad6088505a461e254ae2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366293"
---
# <a name="__event"></a>__event

Deklaruje událost.

## <a name="syntax"></a>Syntaxe

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Poznámky

Klíčové slovo **__event** lze použít pro deklaraci metody, deklaraci rozhraní nebo deklaraci datového člena. Klíčové slovo **__event** však nelze použít ke kvalifikaci člena vnořené třídy.

V závislosti na tom, zda jsou zdroj událostí a příjemce nativní C++, COM nebo spravované (rozhraní.NET Framework), můžete jako události použít následující konstrukce:

|Nativní C++|Model COM|Spravované (rozhraní.NET Framework)|
|------------------|---------|--------------------------------|
|Metoda|—|method|
|—|rozhraní|—|
|—|—|datový člen|

Pomocí [__hook](../cpp/hook.md) v příjemci událostí přidružit metodu obslužné rutiny k metodě události. Všimněte si, že po vytvoření události s klíčovým slovem **__event** budou při volání události volány všechny obslužné rutiny událostí, které jsou následně připojeny k této události.

Deklarace metody **__event** nemůže mít definici; definice je implicitně generována, takže metodu události lze volat, jako by se jednalo o běžnou metodu.

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="native-events"></a>Nativní události

Nativní události jsou metody. Návratový typ je obvykle HRESULT nebo **void**, ale může být libovolný integrální typ, včetně **výčtu**. Pokud událost používá integrální návratový typ, je definována chybová podmínka, když obslužná rutina události vrátí nenulovou hodnotu, v takovém případě bude událost, která je vyvolána, volat ostatní delegáty.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Ukázkový kód najdete [v tématu Zpracování událostí v nativním jazyce C++.](../cpp/event-handling-in-native-cpp.md)

## <a name="com-events"></a>Události COM

Události com jsou rozhraní. Parametry metody ve zdrojovém rozhraní událostí by měly být *v* parametrech (ale to není důsledně vynuceno), protože *out* parametr není užitečné při vícesměrovém vysílání. Pokud použijete parametr *out,* bude vydáno upozornění úrovně 1.

Návratový typ je obvykle HRESULT nebo **void**, ale může být libovolný integrální typ, včetně **výčtu**. Pokud událost používá integrální návratový typ a obslužná rutina události vrátí nenulovou hodnotu, je chybový stav, v takovém případě událost, která je vyvolána, přeruší volání ostatních delegátů. Všimněte si, že kompilátor automaticky označí zdrojové rozhraní události jako [zdroj](../windows/attributes/source-cpp.md) v generovaném IDL.

Klíčové slovo [__interface](../cpp/interface.md) je vždy vyžadováno po **__event** pro zdroj událostí COM.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Ukázkový kód naleznete [v tématu Zpracování událostí v com.](../cpp/event-handling-in-com.md)

## <a name="managed-events"></a>Spravované události

Informace o událostech kódování v nové syntaxi naleznete v tématu [událost](../extensions/event-cpp-component-extensions.md).

Spravované události jsou datové členy nebo metody. Při použití s událostí musí být návratový typ delegáta kompatibilní se [specifikací společného jazyka](/dotnet/standard/language-independence-and-language-independent-components). Návratový typ obslužné rutiny události musí odpovídat návratový typ delegáta. Další informace o delegátech naleznete v tématu [Delegáti a události](../dotnet/delegates-and-events.md). Pokud je spravovaná událost datovým členem, musí být jejím typem ukazatel na delegáta.

V rozhraní .NET Framework můžete zacházet s datovým členem, jako `Invoke` by se jednalo o samotnou metodu (to znamená metodu odpovídajícího delegáta). Je nutné předdefinovat typ delegáta pro deklarování datového člena spravované události. Naproti tomu metoda spravované události implicitně definuje odpovídajícího spravovaného delegáta, pokud ještě není definována. Můžete například deklarovat hodnotu události, například `OnClick` jako událost takto:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Při implicitně deklarování spravované události můžete zadat přistupující a odebrané přístupové akce, které budou volány při přidání nebo odebrání obslužných rutin událostí. Můžete také definovat metodu, která volá (vyvolává) událost z mimo třídu.

## <a name="example-native-events"></a>Příklad: Nativní události

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Příklad: Události COM

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracování událostí](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
