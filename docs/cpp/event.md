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
ms.openlocfilehash: d0d6d3570662cba36a606002263559246e22da57
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180053"
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

Klíčové slovo **__event** lze použít pro deklaraci metody, deklaraci rozhraní nebo deklaraci datového člena. Nemůžete však použít klíčové slovo **__event** k kvalifikování člena vnořené třídy.

V závislosti na tom, jestli je zdroj události a přijímač C++nativní, com nebo spravované (.NET Framework), můžete jako události použít následující konstrukce:

|Nativní kód C++|Model COM|Spravované (.NET Framework)|
|------------------|---------|--------------------------------|
|Metoda|—|metoda|
|—|rozhraní|—|
|—|—|datový člen|

K přidružení metody obslužné rutiny k metodě události použijte [__hook](../cpp/hook.md) v přijímači událostí. Všimněte si, že po vytvoření události s klíčovým slovem **__event** budou všechny obslužné rutiny událostí následně připojeny k této události při volání události volány.

Deklarace metody **__event** nemůže mít definici. definice je implicitně vygenerována, takže metodu události lze volat, jako by to byla jakákoli obyčejná metoda.

> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.

## <a name="native-events"></a>Nativní události

Nativní události jsou metody. Návratový typ je obvykle HRESULT nebo **void**, ale může to být libovolný integrální typ, včetně **výčtu**. Pokud událost používá celočíselný návratový typ, je při zpracování chybové podmínky definována výjimka, když obslužná rutina události vrátí nenulovou hodnotu. v takovém případě vyvolaná událost vyvolá jiné delegáty.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Viz [zpracování událostí v nativním C++ ](../cpp/event-handling-in-native-cpp.md) kódu pro ukázkový kód.

## <a name="com-events"></a>Události COM

Události COM jsou rozhraní. Parametry metody ve zdrojovém rozhraní události by měly být *v* parametrech (ale toto není přísně vynutilo), protože *výstupní* parametr není užitečný při vícesměrovém vysílání. Pokud použijete *výstupní* parametr, bude vydáno upozornění úrovně 1.

Návratový typ je obvykle HRESULT nebo **void**, ale může to být libovolný celočíselný typ, včetně **výčtu**. Když událost používá celočíselný návratový typ a obslužná rutina události vrátí nenulovou hodnotu, jedná se o chybový stav. v takovém případě událost vyvolává přerušení volání jiných delegátů. Všimněte si, že kompilátor bude automaticky označovat zdrojové rozhraní události jako [zdroj](../windows/attributes/source-cpp.md) ve vygenerovaném IDL.

Klíčové slovo [__interface](../cpp/interface.md) se vždy vyžaduje po **__event** pro zdroj události com.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Vzorový kód najdete [v tématu zpracování událostí v modelu COM](../cpp/event-handling-in-com.md) .

## <a name="managed-events"></a>Spravované události

Informace o kódování událostí v nové syntaxi naleznete v tématu [Event](../extensions/event-cpp-component-extensions.md).

Spravované události jsou datové členy nebo metody. Při použití s událostí musí být návratový typ delegáta kompatibilní se specifikací CLS ( [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components)). Návratový typ obslužné rutiny události musí odpovídat návratový typ delegátu. Další informace o delegátech naleznete v tématu [Delegáti a události](../dotnet/delegates-and-events.md). Pokud je spravovaná událost datový člen, jeho typ musí být ukazatel na delegáta.

V .NET Framework můžete s datovým členem zacházet, jako by šlo o metodu (to znamená `Invoke` metoda příslušného delegáta). Musíte předdefinovat typ delegáta pro deklaraci spravovaného datového člena události. Naproti tomu spravovaná metoda události implicitně definuje odpovídající spravovaný delegát, pokud ještě není definovaný. Například můžete deklarovat hodnotu události, například `OnClick` jako událost následujícím způsobem:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Pokud implicitně deklarujete spravovanou událost, můžete zadat přístupové objekty Add a Remove, které budou volány při přidání nebo odebrání obslužných rutin událostí. Můžete také definovat metodu, která volá (vyvolává) událost mimo třídu.

## <a name="example-native-events"></a>Příklad: nativní události

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Příklad: události COM

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
