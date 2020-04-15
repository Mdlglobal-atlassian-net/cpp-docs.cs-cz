---
title: Zpracování událostí v modelu COM
ms.date: 11/04/2016
helpviewer_keywords:
- event handling [C++], COM
- event handling [C++], about event handling
- declaring events
- event handlers [C++], COM
- event handlers
- COM, events
- event receivers, in event handling
- event handling [C++]
- hooking events
- event receivers, name and signature matching
- event sources, in event handling
- declaring events, in COM
- declaring events, event handling in COM
ms.assetid: 6b4617d4-a58e-440c-a8a6-1ad1c715b2bb
ms.openlocfilehash: 756fb6f17aa02fda9a19d501395c39a0b1f602f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366307"
---
# <a name="event-handling-in-com"></a>Zpracování událostí v modelu COM

Při zpracování událostí com nastavit zdroj událostí a příjemce událostí pomocí [atributů event_source](../windows/attributes/event-source.md) `type` = `com`a [event_receiver,](../windows/attributes/event-receiver.md) v uvedeném pořadí, určení . Tyto atributy vloží příslušný kód pro vlastní, odeslání a duální rozhraní umožňující třídám, na které se vztahují, vyvolat a zpracovat události prostřednictvím přípojných bodů modelu COM.

## <a name="declaring-events"></a>Deklarace událostí

Ve třídě zdroje událostí použijte klíčové slovo [__event](../cpp/event.md) v deklaraci rozhraní k deklarování metod tohoto rozhraní jako událostí. Události tohoto rozhraní jsou aktivovány, pokud je zavoláte jako metody rozhraní. Metody na rozhraní událostí může mít nula nebo více parametrů (které by měly být *všechny v* parametrech). Návratový typ může být typ void nebo libovolný celočíselný typ.

## <a name="defining-event-handlers"></a>Definice obslužných rutin událostí

V třídě příjemce události definujte obslužné rutiny událostí, což jsou metody s podpisy (návratové typy, úmluvy volání a argumenty) odpovídajícími události, kterou budou zpracovávat. U událostí com nemusí odpovídat konvence volání; Podrobnosti naleznete níže v části [Události com závislé na rozložení.](#vcconeventhandlingincomanchorlayoutdependentcomevents)

## <a name="hooking-event-handlers-to-events"></a>Připojení obslužných rutin událostí k událostem

Také ve třídě příjemce událostí použít vnitřní funkce [__hook](../cpp/hook.md) k přidružení událostí s obslužnými rutinami událostí a [__unhook](../cpp/unhook.md) k odlučování událostí od obslužných rutin událostí. Lze připojit několik událostí k obslužné rutině události nebo několik obslužných rutin událostí k události.

> [!NOTE]
> Obvykle jsou k dispozici dvě techniky umožňující příjemci události modelu COM přistupovat k definicím rozhraní zdroje událostí. Prvním, jak je uvedeno níže, je sdílet společný soubor hlaviček. Druhým je použití [#import](../preprocessor/hash-import-directive-cpp.md) `embedded_idl` s kvalifikátorem importu, aby byla knihovna typu zdroje událostí zapsána do souboru TLH se zachovaným kódem generovaným atributem.

## <a name="firing-events"></a>Vyvolání událostí

Chcete-li vyvolat událost, jednoduše zavolejte metodu v rozhraní deklarovaném s klíčovým slovem **__event** ve třídě zdroje událostí. Pokud byly obslužné rutiny připojeny k této události, budou tyto obslužné rutiny zavolány.

### <a name="com-event-code"></a>Kód události COM

Následující příklad ukazuje, jak vyvolat událost v třídě modelu COM. Chcete-li příklad zkompilovat a spustit, přečtěte si komentáře v kódu.

```cpp
// evh_server.h
#pragma once

[ dual, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IEvents {
   [id(1)] HRESULT MyEvent([in] int value);
};

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT FireEvent();
};

class DECLSPEC_UUID("530DF3AD-6936-3214-A83B-27B63C7997C4") CSource;
```

A potom tento server:

```cpp
// evh_server.cpp
// compile with: /LD
// post-build command: Regsvr32.exe /s evh_server.dll
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include "evh_server.h"

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[coclass, event_source(com), uuid("530DF3AD-6936-3214-A83B-27B63C7997C4")]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      __raise MyEvent(123);
      return S_OK;
   }
};
```

A potom klienta:

```cpp
// evh_client.cpp
// compile with: /link /OPT:NOREF
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <stdio.h>
#include "evh_server.h"

[ module(name="EventReceiver") ];

[ event_receiver(com) ]
class CReceiver {
public:
   HRESULT MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
      return S_OK;
   }

   HRESULT MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
      return S_OK;
   }

   void HookEvent(IEventSource* pSource) {
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void UnhookEvent(IEventSource* pSource) {
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   // Create COM object
   CoInitialize(NULL);
   {
      IEventSource* pSource = 0;
      HRESULT hr = CoCreateInstance(__uuidof(CSource), NULL,         CLSCTX_ALL, __uuidof(IEventSource), (void **) &pSource);
      if (FAILED(hr)) {
         return -1;
      }

      // Create receiver and fire event
      CReceiver receiver;
      receiver.HookEvent(pSource);
      pSource->FireEvent();
      receiver.UnhookEvent(pSource);
   }
   CoUninitialize();
   return 0;
}
```

### <a name="output"></a>Výstup

```Output
MyHandler1 was called with value 123.
MyHandler2 was called with value 123.
```

## <a name="layout-dependent-com-events"></a><a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a>Události COM závislé na rozložení

Závislost na rozložení se týká pouze programování v modelu COM. Při zpracování nativních a spravovaných událostí musí podpisy (návratový typ, konvence volání a argumenty) obslužných rutin odpovídat jejich událostem, ale názvy obslužných rutin nemusí odpovídat jejich událostem.

Při zpracování událostí com při nastavení *parametru* `event_receiver` layout_dependent na **hodnotu true**je však vynuceno párování názvů a podpisů. To znamená, že názvy a podpisy obslužných rutin v příjemci události musí přesně odpovídat názvům a podpisům událostí, ke kterým jsou připojeny.

Pokud *je layout_dependent* nastavena na **hodnotu false**, může být třída konvence volání a úložiště (virtuální, statická a tak dále) smíchána a spárována mezi metodou události vypalování a metodami hákování (jeho delegáti). Je o něco efektivnější mít *layout_dependent*=**pravda**.

Předpokládejme například, že je definováno rozhraní `IEventSource` s následujícími metodami:

```cpp
[id(1)] HRESULT MyEvent1([in] int value);
[id(2)] HRESULT MyEvent2([in] int value);
```

Předpokládejme, že zdroj události má následující tvar:

```cpp
[coclass, event_source(com)]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      MyEvent1(123);
      MyEvent2(123);
      return S_OK;
   }
};
```

Poté v příjemci události musí kterákoli obslužná rutina připojená k metodě v rozhraní `IEventSource` odpovídat jejímu názvu a podpisu následovně:

```cpp
[coclass, event_receiver(com, true)]
class CReceiver {
public:
   HRESULT MyEvent1(int nValue) {  // name and signature matches MyEvent1
      ...
   }
   HRESULT MyEvent2(E c, char* pc) {  // signature doesn't match MyEvent2
      ...
   }
   HRESULT MyHandler1(int nValue) {  // name doesn't match MyEvent1 (or 2)
      ...
   }
   void HookEvent(IEventSource* pSource) {
      __hook(IFace, pSource);  // Hooks up all name-matched events
                               // under layout_dependent = true
      __hook(&IFace::MyEvent1, pSource, &CReceive::MyEvent1);   // valid
      __hook(&IFace::MyEvent2, pSource, &CSink::MyEvent2);   // not valid
      __hook(&IFace::MyEvent1, pSource, &CSink:: MyHandler1); // not valid
   }
};
```

## <a name="see-also"></a>Viz také

[Zpracování událostí](../cpp/event-handling.md)
