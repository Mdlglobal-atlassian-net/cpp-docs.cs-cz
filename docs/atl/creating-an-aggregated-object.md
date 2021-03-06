---
title: Vytvoření agregovaného objektu
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
ms.openlocfilehash: 4be8d0e852da91b58125dc01d44eed4560b2b8d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250755"
---
# <a name="creating-an-aggregated-object"></a>Vytvoření agregovaného objektu

Delegáti agregace `IUnknown` volání, poskytuje ukazatel na objekt vnější `IUnknown` na vnitřní objekt.

## <a name="to-create-an-aggregated-object"></a>Vytvoření agregovaného objektu

1. Přidat `IUnknown` ukazatel na třídu objektu a inicializovat na hodnotu NULL v konstruktoru.

1. Přepsat [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) vytvoření agregace.

1. Použití `IUnknown` ukazatel definovaný v kroku 1, jako druhý parametr [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) makra.

1. Přepsat [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) uvolnit `IUnknown` ukazatele.

> [!NOTE]
> Pokud používáte a uvolnění rozhraní z agregovaného objektu během `FinalConstruct`, měli byste přidat [DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) – makro na definici třídy objektu.

## <a name="see-also"></a>Viz také:

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)
