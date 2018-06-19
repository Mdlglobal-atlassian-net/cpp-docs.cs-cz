---
title: Zpracování událostí v nativním kódu C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b233c8329119753e5753e19fd641c6bea5d8e42
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414178"
---
# <a name="event-handling-in-native-c"></a>Zpracování událostí v nativním kódu C++

Při zpracování událostí nativní C++, nastavíte zdroj a event přijímače událostí pomocí [event_source –](../windows/event-source.md) a [event_receiver –](../windows/event-receiver.md) atributy, zadání `type` = `native`. Tyto atributy povolit třídy, na které se použijí k vyvolání události a zpracování události v kontextu nativní, modelu COM.

## <a name="declaring-events"></a>Deklarace událostí

V třída zdroje událostí, použijte [__event](../cpp/event.md) – klíčové slovo v deklaraci metody pro metodu jako událost deklarovat. Ujistěte se, zda jste deklarovat metodu, ale nejsou definovány. Uděláte to tak vygeneruje chybu kompilátoru protože kompilátor definuje metodu implicitně když je proveden do událost. Nativní události může být metody s nula nebo více parametrů. Návratový typ může být typ void nebo libovolný celočíselný typ.  
  
## <a name="defining-event-handlers"></a>Definice obslužných rutin událostí

V třídě příjemce události definujte obslužné rutiny událostí, což jsou metody s podpisy (návratové typy, úmluvy volání a argumenty) odpovídajícími události, kterou budou zpracovávat.  
  
## <a name="hooking-event-handlers-to-events"></a>Připojení obslužných rutin událostí k událostem  

Také v třída příjemce událostí, použijete funkci vnitřní [__hook](../cpp/hook.md) pro přidružení událostí obslužné rutiny událostí a [__unhook](../cpp/unhook.md) zrušení přidružení události z obslužné rutiny událostí. Lze připojit několik událostí k obslužné rutině události nebo několik obslužných rutin událostí k události.  
  
## <a name="firing-events"></a>Vyvolání událostí  

Chcete-li aktivovat událost, stačí zavolat metodu deklarované jako událost události třída zdroje. Pokud byly obslužné rutiny připojeny k této události, budou tyto obslužné rutiny zavolány.  
  
### <a name="native-c-event-code"></a>Kód nativní události C++  

Následující příklad ukazuje, jak aktivovat události v nativním kódu C++. Chcete-li příklad zkompilovat a spustit, přečtěte si komentáře v kódu.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```cpp  
// evh_native.cpp  
#include <stdio.h>  
  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
  
[event_receiver(native)]  
class CReceiver {  
public:  
   void MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
   }  
  
   void MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
   }  
  
   void hookEvent(CSource* pSource) {  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void unhookEvent(CSource* pSource) {  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   CSource source;  
   CReceiver receiver;  
  
   receiver.hookEvent(&source);  
   __raise source.MyEvent(123);  
   receiver.unhookEvent(&source);  
}  
```  
  
### <a name="output"></a>Výstup  
  
```Output
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## <a name="see-also"></a>Viz také

[Zpracování událostí](../cpp/event-handling.md)  

