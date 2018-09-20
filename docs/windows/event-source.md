---
title: event_source | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.event_source
dev_langs:
- C++
helpviewer_keywords:
- event handling, attributes
- event logs, event source
- event sources, creating
- event_source attribute
- event sources
- event handling, creating event source
ms.assetid: 0983e36a-6127-4fbb-8a22-8dfec6564c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d2dfcf61ced958519e7255bd241d3c0ea911824e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408918"
---
# <a name="eventsource"></a>event_source

Vytvoří zdroj událostí.

## <a name="syntax"></a>Syntaxe

```cpp
[ event_source(
   type,
   optimize=[speed | size],
   decorate=[true | false]
) ]
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Výčet jedné z následujících hodnot:

- `native` pro nespravovaný kód jazyka C/C++ (výchozí nastavení pro nespravované třídy).

- `com` pro kód v modelu COM. Je nutné použít `coclass` při `type` = `com`. Tato hodnota vyžaduje, aby následující soubory hlaviček:

    ```cpp
    #define _ATL_ATTRIBUTES
    #include <atlbase.h>
    #include <atlcom.h>
    ```

*optimize*<br/>
Když *typ* je `native`, můžete zadat `optimize=size`, pro indikaci, že je 4 bajty úložiště (minimum) pro všechny události v třídě nebo `optimize=speed` (výchozí), že je 4 * (počet událostí) bajtů úložiště.

*vyplnění*<br/>
Když *typ* je `native`, můžete zadat `decorate=false`, pro indikaci, že rozbalený název souboru sloučeného (.mrg) by neměla obsahovat název nadřazené třídy. [/FX](../build/reference/fx-merge-injected-code.md) umožňuje generovat soubory .mrg. `decorate=false`, což je výchozí nastavení, výsledkem názvy typů plně kvalifikovaný v sloučený soubor.

## <a name="remarks"></a>Poznámky

**Event_source** C++ atribut určuje, zda třídu nebo strukturu, do které se použije zdroj událostí.

**event_source** se používá ve spojení s [event_receiver](../windows/event-receiver.md) atribut a [__event](../cpp/event.md) – klíčové slovo. Použití `event_receiver` vytvoření přijímače událostí. Použití **__event** pro metody v rámci zdroje událostí k určení těchto metod jako události.

> [!NOTE]
> Třída šablony nebo struktura nemohou obsahovat události.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass** při `type`=`com`|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](../windows/compiler-attributes.md)<br/>
[event_receiver](../windows/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[Atributy třídy](../windows/class-attributes.md)  