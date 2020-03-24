---
title: Zpracování událostí v nativním kódu C++
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: cc9265cd3f9f400e2880405019e4d2c9a934f10a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180079"
---
# <a name="event-handling-in-native-c"></a>Zpracování událostí v nativním kódu C++

V případě C++ nativního zpracování událostí nastavíte zdroj události a přijímač událostí pomocí atributů [event_source](../windows/attributes/event-source.md) a [event_receiver](../windows/attributes/event-receiver.md) , v uvedeném pořadí určíte `type`=`native`. Tyto atributy umožňují třídám, které jsou aplikovány na události požáru a zpracovávat události v nativním kontextu, který nepatří do modelu COM.

## <a name="declaring-events"></a>Deklarace událostí

Ve třídě zdroje události použijte klíčové slovo [__event](../cpp/event.md) v deklaraci metody k deklaraci metody jako události. Ujistěte se, že jste metodu deklarovali, ale nedefinujete ji. k tomu dojde, když kompilátor vygeneruje chybu kompilátoru, protože kompilátor implicitně definuje metodu, když se provede v události. Nativní události mohou být metody s nulovým nebo více parametry. Návratový typ může být typ void nebo libovolný celočíselný typ.

## <a name="defining-event-handlers"></a>Definice obslužných rutin událostí

V třídě příjemce události definujte obslužné rutiny událostí, což jsou metody s podpisy (návratové typy, úmluvy volání a argumenty) odpovídajícími události, kterou budou zpracovávat.

## <a name="hooking-event-handlers-to-events"></a>Připojení obslužných rutin událostí k událostem

Také v třídě přijímače událostí použijete vnitřní funkci [__hook](../cpp/hook.md) k přidružení událostí k obslužným rutinám událostí a [__unhook](../cpp/unhook.md) k oddálení událostí z obslužných rutin událostí. Lze připojit několik událostí k obslužné rutině události nebo několik obslužných rutin událostí k události.

## <a name="firing-events"></a>Vyvolání událostí

Chcete-li vyvolat událost, jednoduše zavolejte metodu deklarovanou jako událost ve třídě zdroje události. Pokud byly obslužné rutiny připojeny k této události, budou tyto obslužné rutiny zavolány.

### <a name="native-c-event-code"></a>Nativní C++ kód události

Následující příklad ukazuje, jak vyvolat událost v nativním režimu C++. Chcete-li příklad zkompilovat a spustit, přečtěte si komentáře v kódu.

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
