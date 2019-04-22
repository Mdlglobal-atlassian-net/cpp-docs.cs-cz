---
title: Zpracování událostí v nativním kódu C++
ms.date: 11/04/2016
helpviewer_keywords:
- event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: 93bfcc93c680618ea3a51eabd145548a4f47563a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772329"
---
# <a name="event-handling-in-native-c"></a>Zpracování událostí v nativním kódu C++

V nativním C++ zpracování událostí, můžete nastavit zdroj a události přijímače událostí pomocí [event_source](../windows/attributes/event-source.md) a [event_receiver](../windows/attributes/event-receiver.md) atributy, určení `type` =`native`. Tyto atributy umožňují třídy, na které se vztahují, vyvolat a zpracovat události v kontextu nativní, modelu COM.

## <a name="declaring-events"></a>Deklarace událostí

V třídě zdroje události, použijte [__event](../cpp/event.md) – klíčové slovo v deklaraci metody, chcete-li deklarovat metodu jako událost. Ujistěte se, že chcete-li deklarovat metodu, ale není definován. Provedete to tak vygeneruje chybu kompilátoru, protože kompilátor definuje metodu implicitně, když se provádí na událost. Nativní události může být nula nebo více parametrů metody. Návratový typ může být typ void nebo libovolný celočíselný typ.

## <a name="defining-event-handlers"></a>Definice obslužných rutin událostí

V třídě příjemce události definujte obslužné rutiny událostí, což jsou metody s podpisy (návratové typy, úmluvy volání a argumenty) odpovídajícími události, kterou budou zpracovávat.

## <a name="hooking-event-handlers-to-events"></a>Připojení obslužných rutin událostí k událostem

Také v třídě příjemce události, pomocí vnitřní funkce [__hook](../cpp/hook.md) pro přidružení událostí k obslužné rutiny událostí a [__unhook](../cpp/unhook.md) zrušení přidružení událostí z obslužných rutin událostí. Lze připojit několik událostí k obslužné rutině události nebo několik obslužných rutin událostí k události.

## <a name="firing-events"></a>Vyvolání událostí

Chcete-li vyvolat událost, jednoduše zavolejte metodu deklarován jako událost v případě zdrojové třídy. Pokud byly obslužné rutiny připojeny k této události, budou tyto obslužné rutiny zavolány.

### <a name="native-c-event-code"></a>Kód nativní události C++

Následující příklad ukazuje, jak vyvolat událost v nativním kódu C++. Chcete-li příklad zkompilovat a spustit, přečtěte si komentáře v kódu.

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

## <a name="see-also"></a>Viz také:

[Zpracování událostí](../cpp/event-handling.md)