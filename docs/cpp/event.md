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
ms.openlocfilehash: 3a837e30d3cd66f7caa9b44971f432e00b0917ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154422"
---
# <a name="event"></a>__event

Deklaruje událost.

## <a name="syntax"></a>Syntaxe

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Poznámky

Klíčové slovo **__event** lze použít u deklarace metody, deklarací interface nebo deklaraci členské data. Však nelze použít **__event** – klíčové slovo k vyfiltrování člena vnořené třídy.

Podle toho, zda váš zdroj událostí a příjemce se nativní kód C++, COM nebo spravovaný (.NET Framework) můžete použít následující konstrukce jako události:

|Nativní kód C++|Model COM|Spravované (.NET Framework)|
|------------------|---------|--------------------------------|
|Metoda|—|– metoda|
|—|rozhraní|—|
|—|—|datový člen|

Použití [__hook](../cpp/hook.md) v přijímače událostí k přidružení metody obslužné rutiny s metodou události. Všimněte si, že po vytvoření událost se **__event** – klíčové slovo, všechny obslužné rutiny událostí, které následně připojeny k této události, zavolá se při volání události.

**__Event** deklarace metody nemůže mít definici; definici je implicitně generují, takže lze volat metodu události, jako kdyby byly všechny běžné metody.

> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.

## <a name="native-events"></a>Nativní události

Nativní událostí jsou metody. Návratový typ je obvykle HRESULT nebo **void**, ale může být libovolný integrální typ, včetně **výčtu**. Pokud událost používá integrálních návratový typ, je definován chybový stav, když obslužnou rutinu události vrací nenulovou hodnotu, ve kterém bude volat případ událostí vyvolaných delegáty.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Zobrazit [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md) ukázkový kód.

## <a name="com-events"></a>Události COM

Události modelu COM jsou rozhraní. Parametry metody v rozhraní zdroje událostí musí být *v* parametry (ale to se nevynucuje přísně), protože *si* parametr není užitečné, když vícesměrové vysílání. Bude vydáno upozornění úrovně 1, pokud používáte *si* parametru.

Návratový typ je obvykle HRESULT nebo **void**, ale může být libovolný integrální typ, včetně **výčtu**. Při události používá integrálních návratový typ a vrací nenulovou hodnotu, obslužná rutina události, je chybový stav, ve kterém případ vyvolanou událost zruší volání delegáty. Všimněte si, že kompilátor automaticky označí jako rozhraní zdroje událostí [zdroj](../windows/attributes/source-cpp.md) v generované IDL.

[__Interface](../cpp/interface.md) – klíčové slovo je vždy vyžadován po **__event** pro zdroj události COM.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Zobrazit [zpracování událostí v modulu COM](../cpp/event-handling-in-com.md) ukázkový kód.

## <a name="managed-events"></a>Spravované události

Informace týkající se kódování události v nové syntaxi naleznete v tématu [události](../extensions/event-cpp-component-extensions.md).

Spravované události jsou datové členy a metody. Při použití s událostí, návratový typ delegáta musí být kompatibilní s [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). Návratový typ obslužné rutiny události musí odpovídat návratový typ delegáta. Další informace o delegátech naleznete v tématu [Delegáti a události](../dotnet/delegates-and-events.md). Pokud je spravovaná událost datový člen, jeho typ musí být ukazatel na konstruktor delegate.

V rozhraní .NET Framework lze považovat datový člen, jako by šlo metodu samotného (to znamená `Invoke` metoda jeho odpovídající delegáta). Typ delegáta musí předdefinovat deklarace datový člen spravované události. Metoda spravované události naproti tomu implicitně definuje odpovídající spravovaný delegáta, pokud již není definován. Například je možné deklarovat hodnotu události, jako `OnClick` jako událost následujícím způsobem:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Při deklarování implicitně spravovaných událostí, můžete přidat nebo odebrat přístupové objekty, které se má volat při přidávání nebo odebírání obslužných rutin událostí. Můžete také definovat metodu, která volá (vyvolává) událost z mimo třídu.

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

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Zpracování událostí](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)