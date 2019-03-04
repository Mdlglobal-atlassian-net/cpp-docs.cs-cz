---
title: Implementace duálního rozhraní (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: ecd6a0cc90ca4175c4ae898f2e9aa8bf00508a3e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287333"
---
# <a name="implementing-a-dual-interface"></a>Implementace duálního rozhraní

Můžete implementovat duální rozhraní pomocí [třídou IDispatchImpl](../atl/reference/idispatchimpl-class.md) třídu, která poskytuje výchozí implementaci třídy `IDispatch` metody duální rozhraní. Další informace najdete v tématu [implementace rozhraní IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Chcete-li použít tuto třídu:

- Definujte duální rozhraní v knihovně typů.

- Odvodit třídu z specializací `IDispatchImpl` (předávání informací o knihovně rozhraní a typ jako argumenty šablony).

- Přidat položku (nebo položky) do mapy modelu COM vystavení duální rozhraní prostřednictvím `QueryInterface`.

- Implementace vtable součástí rozhraní ve své třídě.

- Ujistěte se, že knihovnu typů obsahující definice rozhraní dostupná k objektům v době běhu.

## <a name="atl-simple-object-wizard"></a>Průvodce jednoduchým objektem ATL

Pokud chcete vytvořit nové rozhraní a novou třídu pro implementaci, můžete použít [dialogové okno Přidat třídu ATL](../ide/add-class-dialog-box.md)a pak [Průvodce jednoduchý objekt knihovny ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Průvodce implementací rozhraní

Pokud máte existující rozhraní, můžete použít [Průvodce implementací rozhraní](../atl/reference/adding-a-new-interface-in-an-atl-project.md) přidejte nezbytné základní třídy, položek mapování modelu COM a implementace kostru metody do existující třídy.

> [!NOTE]
>  Budete muset upravit základní třídy generované tak, aby čísla hlavní verze a podverze knihovny typů jsou předány jako argumenty šablony pro vaše `IDispatchImpl` základní třídy. Průvodce implementací rozhraní není zkontrolujte číslo verze knihovny typů.

## <a name="implementing-idispatch"></a>Implementace rozhraní IDispatch

Můžete použít `IDispatchImpl` základní třídu na: zajišťovat implementaci rozhraní dispinterface jenom tak, že zadáte odpovídající položku v objektu map COM (pomocí [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) nebo [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) – makro), dokud máte knihovnu typů popisující odpovídající duální rozhraní. Je celkem běžné k implementaci `IDispatch` tímto způsobem, například rozhraní. Průvodce jednoduchý objekt knihovny ATL a implementovat rozhraní Průvodce obojí se předpokládá, že máte v úmyslu implementovat `IDispatch` tímto způsobem, takže se přidávají na příslušnou položku do mapy.

> [!NOTE]
>  ATL – nabízí [IDispEventImpl](../atl/reference/idispeventimpl-class.md) a [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md) třídy, které vám pomůže implementovat odesílacích rozhraních bez nutnosti knihovnu typů obsahující definice kompatibilní duální rozhraní.

## <a name="see-also"></a>Viz také:

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)
