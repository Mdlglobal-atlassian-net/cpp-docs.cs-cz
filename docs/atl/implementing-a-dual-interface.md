---
title: Implementace duálního rozhraní (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319471"
---
# <a name="implementing-a-dual-interface"></a>Implementace duálního rozhraní

Můžete implementovat duální rozhraní pomocí třídy [IDispatchImpl,](../atl/reference/idispatchimpl-class.md) která poskytuje výchozí implementaci `IDispatch` metod v duálním rozhraní. Další informace naleznete [v tématu Implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Chcete-li použít tuto třídu:

- Definujte duální rozhraní v knihovně typů.

- Odvodit třídu `IDispatchImpl` ze specializace (předat informace o rozhraní a knihovnu typů jako argumenty šablony).

- Přidejte položku (nebo položky) do mapy `QueryInterface`com vystavit duální rozhraní prostřednictvím .

- Implementujte vtable část rozhraní ve vaší třídě.

- Ujistěte se, že knihovna typů obsahující definici rozhraní je k dispozici pro objekty za běhu.

## <a name="atl-simple-object-wizard"></a>Průvodce jednoduchým objektem ATL

Chcete-li vytvořit nové rozhraní a novou třídu k jeho implementaci, můžete použít [dialogové okno Přidat třídu knihovny ATL](../ide/add-class-dialog-box.md)a [potom Průvodce jednoduchým objektem knihovny ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní

Pokud máte existující rozhraní, můžete pomocí [Průvodce implementovat rozhraní](../atl/reference/adding-a-new-interface-in-an-atl-project.md) přidat potřebné základní třídy, položky mapy COM a kostra implementace metody do existující třídy.

> [!NOTE]
> Možná budete muset upravit vygenerovanou základní třídu tak, aby hlavní a dílčí `IDispatchImpl` čísla verzí knihovny typů byla předána jako argumenty šablony základní třídě. Průvodce implementací rozhraní nekontroluje číslo verze knihovny typů.

## <a name="implementing-idispatch"></a>Implementace IDispatchu

Základní třídu `IDispatchImpl` můžete použít k poskytnutí implementace dispinterface pouze zadáním příslušné položky v mapě COM (pomocí [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) nebo [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) makro), pokud máte knihovnu typů popisující odpovídající duální rozhraní. Je zcela běžné implementovat `IDispatch` rozhraní tímto způsobem, například. Průvodce jednoduchým objektem knihovny ATL a Průvodce `IDispatch` implementací rozhraní předpokládají, že chcete implementovat tímto způsobem, takže přidají příslušnou položku do mapy.

> [!NOTE]
> Knihovna ATL nabízí třídy [IDispEventImpl](../atl/reference/idispeventimpl-class.md) a [IDispEventSimpleImpl,](../atl/reference/idispeventsimpleimpl-class.md) které vám pomohou implementovat dispinterfaces bez nutnosti knihovny typů obsahující definici kompatibilního duálního rozhraní.

## <a name="see-also"></a>Viz také

[Duální rozhraní a knihovna ATL](../atl/dual-interfaces-and-atl.md)
