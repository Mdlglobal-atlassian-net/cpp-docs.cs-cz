---
title: __Event | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __event_cpp
- __event
dev_langs: C++
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2819cfbc03fc5873bd3c50138c1d0838302157d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="event"></a>__event
Deklaruje událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      __event   
      method-declarator  
      ;  
__event __interface interface-specifier;  
__event member-declarator;  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo `__event` můžete použít pro deklaraci metody, deklaraci rozhraní nebo deklaraci data člena. Však nelze použít `__event` – klíčové slovo, aby se dosáhlo nároku členem vnořené třídy.  
  
 V závislosti na tom, jestli zdroje událostí a příjemce jsou nativní C++, COM nebo spravované (rozhraní .NET Framework) můžete použít následující konstrukce jako události:  
  
|Nativní C++|Model COM|Spravované (rozhraní .NET Framework)|  
|------------------|---------|--------------------------------|  
|Metoda|—|– metoda|  
|—|rozhraní|—|  
|—|—|– datový člen|  
  
 Použití [__hook](../cpp/hook.md) v přijímače událostí pro přidružení metoda obslužná rutina s metodou události. Všimněte si, že po vytvoření událost se `__event` – klíčové slovo, následně byl zapojen na tuto událost všechny obslužné rutiny událostí bude volána, když je volána události.  
  
 `__event` Deklarace metody nemůže mít definici; definici implicitně generován, takže metoda události můžete volat, jako by šlo jakékoli běžné metody.  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="native-events"></a>Nativní události  
 Nativní události jsou metody. Návratový typ je obvykle `HRESULT` nebo `void`, ale mohou být jakéhokoli typu integrální včetně `enum`. Používá-li událost integrální návratový typ, je definována chybový stav při obslužné rutiny události vrátí nenulovou hodnotu, ve kterém bude volat případ událostí vyvolaných jiných delegáty.  
  
```  
// Examples of native C++ events:  
__event void OnDblClick();  
__event HRESULT OnClick(int* b, char* s);  
```  
  
 V tématu [zpracování událostí v nativním kódu C++](../cpp/event-handling-in-native-cpp.md) pro ukázkový kód.  
  
## <a name="com-events"></a>Události COM  
 COM události jsou rozhraní. Parametry metody v rozhraní zdroj události by měla být **v** parametry (ale tento není vynucena pečlivě), protože **out** parametr není to užitečné, pokud vícesměrového vysílání. Pokud používáte bude vydáno upozornění úrovně 1 **out** parametr.  
  
 Návratový typ je obvykle `HRESULT` nebo `void`, ale mohou být jakéhokoli typu integrální včetně `enum`. Pokud událost používá integrální návratový typ a vrátí nenulovou hodnotu, obslužné rutiny události, je chybový stav, ve kterém případ událostí vyvolaných zruší volání do jiných delegáty. Všimněte si, že kompilátor automaticky označí rozhraní jako zdroj událostí [zdroj](../windows/source-cpp.md) v generované IDL.  
  
 [__Interface](../cpp/interface.md) – klíčové slovo je vždy vyžadován po `__event` pro zdroj události COM.  
  
```  
// Example of a COM event:  
__event __interface IEvent1;  
```  
  
 V tématu [zpracování událostí v modelu COM](../cpp/event-handling-in-com.md) pro ukázkový kód.  
  
## <a name="managed-events"></a>Spravované události  
 Informace týkající se kódování události v nové syntaxi najdete v tématu [událostí](../windows/event-cpp-component-extensions.md).  
  
 Datové členy nebo metody je spravovaný události. Při použití s událost, musí být kompatibilní s návratovým typem delegáta [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). Návratový typ obslužné rutiny události musí shodovat s návratovým typem delegáta. Další informace o delegáti najdete v tématu [Delegáti a události](../dotnet/delegates-and-events.md). Pokud spravované událostí je členem data, jeho typ musí být ukazatel na delegáta.  
  
 V rozhraní .NET Framework, lze považovat datový člen, jako by šlo metodu samotné (to znamená `Invoke` metoda jeho odpovídající delegáta). Typ delegáta musí předdefinovat deklarace člena spravovaných událostí. Naproti tomu metoda spravované události implicitně definuje odpovídající spravovaného delegáta Pokud již není definován. Například můžete deklarovat hodnotu události, jako `OnClick` jako událost následujícím způsobem:  
  
```  
// Examples of managed events:  
__event ClickEventHandler* OnClick;  // data member as event  
__event void OnClick(String* s);  // method as event  
```  
  
 Když implicitně deklarace spravovaného událostí, můžete určit, přidávat a odebírat přístupové objekty, které se má volat při přidávání nebo odebírání obslužných rutin událostí. Můžete také definovat metodu, která volá (vyvolá) událost z mimo třídu.  
  
## <a name="example-native-events"></a>Příklad: Nativní události  
  
```  
// EventHandling_Native_Event.cpp  
// compile with: /c  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
```  
  
## <a name="example-com-events"></a>Příklad: COM události  
  
```  
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
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Zpracování událostí](../cpp/event-handling.md)   
 [event_source –](../windows/event-source.md)   
 [event_receiver –](../windows/event-receiver.md)   
 [__hook](../cpp/hook.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)