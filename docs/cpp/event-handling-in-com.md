---
title: "Zpracování událostí v modelu COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3173d01898fc63327c5e4d4c6ce4f536b1245450
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="event-handling-in-com"></a>Zpracování událostí v modelu COM
Při zpracování událostí modelu COM, můžete nastavit zdroje a event přijímače událostí pomocí [event_source –](../windows/event-source.md) a [event_receiver –](../windows/event-receiver.md) atributy, zadání `type` = **com**. Tyto atributy vloží příslušný kód pro vlastní, odeslání a duální rozhraní umožňující třídám, na které se vztahují, vyvolat a zpracovat události prostřednictvím přípojných bodů modelu COM.  
  
## <a name="declaring-events"></a>Deklarace událostí  
 V třída zdroje událostí, použijte [__event](../cpp/event.md) – klíčové slovo v deklaraci rozhraní deklarovat metody tohoto rozhraní jako události. Události tohoto rozhraní jsou aktivovány, pokud je zavoláte jako metody rozhraní. Metody pro rozhraní událost může mít nula nebo více parametrů (které musí být **v** parametry). Návratový typ může být typ void nebo libovolný celočíselný typ.  
  
## <a name="defining-event-handlers"></a>Definice obslužných rutin událostí  
 V třídě příjemce události definujte obslužné rutiny událostí, což jsou metody s podpisy (návratové typy, úmluvy volání a argumenty) odpovídajícími události, kterou budou zpracovávat. Pro události COM nemají konvence volání tak, aby odpovídaly; v tématu [rozložení závislé COM události](#vcconeventhandlingincomanchorlayoutdependentcomevents) níže podrobnosti.  
  
## <a name="hooking-event-handlers-to-events"></a>Připojení obslužných rutin událostí k událostem  
 Také v třída příjemce událostí, použijete funkci vnitřní [__hook](../cpp/hook.md) pro přidružení událostí obslužné rutiny událostí a [__unhook](../cpp/unhook.md) zrušení přidružení události z obslužné rutiny událostí. Lze připojit několik událostí k obslužné rutině události nebo několik obslužných rutin událostí k události.  
  
> [!NOTE]
>  Obvykle jsou k dispozici dvě techniky umožňující příjemci události modelu COM přistupovat k definicím rozhraní zdroje událostí. Prvním, jak je uvedeno níže, je sdílet společný soubor hlaviček. Druhý je použití [#import](../preprocessor/hash-import-directive-cpp.md) s `embedded_idl` importovat kvalifikátor, tak, aby knihovny typů zdroje událostí je zapsán do souboru .tlh kódem generované atribut zachovaná.  
  
## <a name="firing-events"></a>Vyvolání událostí  
 Chcete-li vyvolat událost, jednoduše zavolejte metodu v rozhraní deklarovaném pomocí klíčového slova `__event` v třídě zdroje události. Pokud byly obslužné rutiny připojeny k této události, budou tyto obslužné rutiny zavolány.  
  
### <a name="com-event-code"></a>Kód události COM  
 Následující příklad ukazuje, jak vyvolat událost v třídě modelu COM. Chcete-li příklad zkompilovat a spustit, přečtěte si komentáře v kódu.  
  
```  
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
  
```  
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
  
```  
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
  
```  
MyHandler1 was called with value 123.  
MyHandler2 was called with value 123.  
```  
  
##  <a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a>Rozložení závislé COM události  
 Závislost na rozložení se týká pouze programování v modelu COM. Při zpracování nativních a spravovaných událostí musí podpisy (návratový typ, konvence volání a argumenty) obslužných rutin odpovídat jejich událostem, ale názvy obslužných rutin nemusí odpovídat jejich událostem.  
  
 Ale při zpracování událostí modelu COM, při nastavení *layout_dependent* parametr **event_receiver –** k **true**, název a odpovídající podpisu je vynucená. To znamená, že názvy a podpisy obslužných rutin v příjemci události musí přesně odpovídat názvům a podpisům událostí, ke kterým jsou připojeny.  
  
 Když *layout_dependent* je nastaven na **false**, volání třída konvence a úložiště (virtuální, statické a tak dále) můžete kombinaci a shodu mezi pálení metoda události a zapojených metody (jeho Delegáti). Mírně efektivnější tak, aby měl *layout_dependent*=**true**.  
  
 Předpokládejme například, že je definováno rozhraní `IEventSource` s následujícími metodami:  
  
```  
[id(1)] HRESULT MyEvent1([in] int value);  
[id(2)] HRESULT MyEvent2([in] int value);  
```  
  
 Předpokládejme, že zdroj události má následující tvar:  
  
```  
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
  
```  
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