---
title: event_receiver (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_receiver
helpviewer_keywords:
- event_receiver attribute
- event receivers
- events [C++], event receivers (sinks)
- event handling [C++], attributes
- event handling [C++], creating receiver
- event sinks, creating
- event sinks
ms.assetid: bf8fe770-3ea2-4128-b46b-166222ee4097
ms.openlocfilehash: 81a3ec88c336ddeb550f133e657854b3b6f89d96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409629"
---
# <a name="eventreceiver"></a>event_receiver

Vytvoří přijímače událostí (jímky).

## <a name="syntax"></a>Syntaxe

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Výčet jedné z následujících hodnot:

- `native` pro nespravovaný kód jazyka C/C++ (výchozí pro nativní třídy).

- `com` pro kód v modelu COM. Tato hodnota vyžaduje, aby následující soubory hlaviček:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Zadejte *layout_dependent* pouze tehdy, pokud `type` = **com**. *layout_dependent* je logická hodnota:

- **Hodnota TRUE** znamená, že podpis delegáty, v případě, že příjemce musí přesně odpovídat těch, ke kterým jsou připojeny události zdroje. Názvy obslužných rutin událostí příjemce musí shodovat s názvy zadané v zdrojové rozhraní relevantní události. Je nutné použít `coclass` při *layout_dependent* je **true**. Je efektivnější zadejte **true**.

- **false** (výchozí) znamená, že volání třídy konvence a úložiště (virtuální, statické a další) tak, aby odpovídaly metodu události a obslužné rutiny; nemají ani tak, aby odpovídaly názvy metod rozhraní zdroje událostí potřeba názvy obslužných rutin.

## <a name="remarks"></a>Poznámky

**Event_receiver** C++ atribut určuje, zda třídu nebo strukturu, do které se použije přijímače událostí pomocí Vizuálu C++ jednotné události modelu.

**event_receiver** se používá s [event_source](event-source.md) atribut a [__hook](../../cpp/hook.md) a [__unhook](../../cpp/unhook.md) klíčová slova. Použití `event_source` k vytvoření zdroje událostí. Použití **__hook** v rámci metod přijímače událostí k přidružení metody příjemce událostí ("připojení") na události zdroje událostí. Použití **__unhook** zrušení jejich přidružení.

*má* je určena pouze pro přijímače událostí modelu COM (`type`=**com**). Výchozí nastavení pro *layout_dependent* je **false**.

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|`coclass` Když *layout_dependent*=**true**|
|**Neplatné atributy**|Žádný|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atributy třídy](class-attributes.md)