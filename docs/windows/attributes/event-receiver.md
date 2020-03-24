---
title: event_receiver (C++ atribut com)
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
ms.openlocfilehash: 9653a0b5c756857d92914496b9c5c6f8aee56ebb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167079"
---
# <a name="event_receiver"></a>event_receiver

Vytvoří přijímač událostí (jímka).

## <a name="syntax"></a>Syntaxe

```cpp
[ event_receiver(type
   [, layout_dependent=false]) ]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Výčet jedné z následujících hodnot:

- `native` pro nespravovaný kódC++ C/Code (výchozí pro nativní třídy).

- `com` pro kód COM. Tato hodnota vyžaduje, abyste zahrnuli následující hlavičkové soubory:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*layout_dependent*<br/>
Zadejte *layout_dependent* pouze v případě, že `type`=**com**. *layout_dependent* je logická hodnota:

- **hodnota true** znamená, že signatura delegátů v příjemci události musí přesně odpovídat tomu, ke kterým jsou zapojeny ve zdroji událostí. Názvy obslužných rutin přijímače událostí musí odpovídat názvům zadaným v příslušném zdrojovém rozhraní události. Pokud má *layout_dependent* **hodnotu true**, musíte použít `coclass`. Je poněkud efektivnější zadat **hodnotu true**.

- **false** (výchozí) znamená, že konvence volání a třída úložiště (Virtual, static a další) nemusí odpovídat metodě události a obslužným rutinám; ani názvy obslužných rutin nemusí odpovídat názvům metod zdrojového rozhraní události.

## <a name="remarks"></a>Poznámky

Atribut **event_receiver** C++ určuje, že třída nebo struktura, pro kterou je použita, bude příjemcem události pomocí modelu události Visual C++ Unified.

**event_receiver** se používá s atributem [event_source](event-source.md) a klíčovými slovy [__hook](../../cpp/hook.md) a [__unhook](../../cpp/unhook.md) . K vytvoření zdrojů událostí použijte `event_source`. Pomocí **__hook** v rámci metod přijímače událostí přidružte metody přijímače událostí přijímače k událostem zdroje události. Zrušte jejich přidružení pomocí **__unhook** .

*layout_dependent* se zadává jenom pro přijímače událostí com (`type`=**com**). Výchozí hodnota pro *layout_dependent* je **false**.

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|`coclass`, pokud *layout_dependent*=**true**|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[event_source](event-source.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atributy třídy](class-attributes.md)
