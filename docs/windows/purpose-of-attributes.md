---
title: Účel atributů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b34ff9641df4d102c2902e5b8ea42a80db4db50
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607097"
---
# <a name="purpose-of-attributes"></a>Účel atributů

Atributy rozšíření bez narušení classic struktura jazyka C++ v aktuálně možné směry. Atributy umožňují poskytovatelů (samostatné knihovny DLL) rozšíření funkcí jazyka dynamicky. Hlavním cílem atributy je pro zjednodušení vytváření komponent modelu COM, kromě zvýšit úroveň produktivity pro vývojáře komponenty. Atributy lze použít na téměř jakémkoli C++ konstrukce, jako jsou třídy, datové členy nebo členské funkce. Zvýraznění výhody této nové technologie je následující:

- Uvádí známé a jednoduché konvence volání.

- Používá se vložit kód, který na rozdíl od makra, je rozpoznán v ladicím programu.

- Umožňuje snadno odvození ze základních tříd bez nákladných implementace podrobnosti.

- Nahradí velké množství kódu IDL vyžadované komponenty modelu COM s několika stručné atributy.

Například implementovat jednoduché událostní jímka pro obecné třídy ATL, můžete použít [event_receiver](../windows/event-receiver.md) atribut pro konkrétní třídu jako `CMyReceiver`. `event_receiver` Atribut je potom kompilovány pomocí kompilátoru jazyka Visual C++, který vloží správný kód do souboru objektu.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Potom můžete nastavit `CMyReceiver` metody `handler1` a `handler2` zpracování událostí (použití vnitřních funkcí [__hook](../cpp/hook.md)) ze zdroje událostí, které můžete vytvořit pomocí [event_source](../windows/event-source.md).

## <a name="see-also"></a>Viz také

[Koncepty](../windows/attributed-programming-concepts.md)