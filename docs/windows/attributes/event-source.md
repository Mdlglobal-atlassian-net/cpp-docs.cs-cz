---
title: event_source (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.event_source
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
ms.openlocfilehash: e187e57f21e9c94068c0b3396b93deed617fef2a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167066"
---
# <a name="event_source"></a>event_source

Vytvoří zdroj události.

## <a name="syntax"></a>Syntaxe

```cpp
[ event_source(type, optimize=[speed | size], decorate=[true | false]) ]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Výčet jedné z následujících hodnot:

- `native` pro nespravovaný kódC++ C/Code (výchozí pro nespravované třídy).

- `com` pro kód COM. Pokud `type`=`com`, je nutné použít `coclass`. Tato hodnota vyžaduje, abyste zahrnuli následující hlavičkové soubory:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Pokud je *typ* `native`, můžete zadat `optimize=size`, aby bylo indikováno, že pro všechny události ve třídě nebo v `optimize=speed` (ve výchozím nastavení) existuje 4 bajty úložiště (minimální), což značí, že je 4 * (počet událostí) bajtů úložiště.

*Uprav*<br/>
Když je *typ* `native`, můžete zadat `decorate=false`, aby označoval, že rozšířený název v sloučeném souboru (. mrg) by neměl zahrnovat název ohraničující třídy. [/FX](../../build/reference/fx-merge-injected-code.md) umožňuje generovat soubory. mrg. `decorate=false`, což je výchozí nastavení, je ve sloučeném souboru výsledkem názvy plně kvalifikovaného typu.

## <a name="remarks"></a>Poznámky

Atribut **event_source** C++ určuje, že třída nebo struktura, pro kterou je použita, bude zdrojem události.

**event_source** se používá ve spojení s atributem [event_receiver](event-receiver.md) a klíčovým slovem [__event](../../cpp/event.md) . K vytvoření přijímačů událostí použijte `event_receiver`. K určení těchto metod jako událostí použijte **__event** metody v rámci zdroje událostí.

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**Třída typu coclass** při `type`=`com`|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[event_receiver](event-receiver.md)<br/>
[__event](../../cpp/event.md)<br/>
[__hook](../../cpp/hook.md)<br/>
[__unhook](../../cpp/unhook.md)<br/>
[Atributy třídy](class-attributes.md)
