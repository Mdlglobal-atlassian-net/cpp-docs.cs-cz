---
title: Zpracování událostí v nativním kódu C++ | Dokumentace Microsoftu
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
ms.openlocfilehash: 89f6ab1bd378309750984a466c30c224bee89ca7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060028"
---
# <a name="event-handling-in-native-c"></a>Zpracování událostí v nativním kódu C++

V nativním C++ zpracování událostí, nastavíte událost zdroj a příjemce události pomocí [event_source](../windows/event-source.md) a [event_receiver](../windows/event-receiver.md) atributy, určení `type` = `native`. Tyto atributy umožňují třídy, na které se vztahují, vyvolat a zpracovat události v kontextu nativní, modelu COM.

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