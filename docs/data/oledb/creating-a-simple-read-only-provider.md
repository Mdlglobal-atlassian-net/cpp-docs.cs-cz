---
title: Vytvoření jednoduchého zprostředkovatele pouze pro čtení
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 466530cb8c2ebca7f1c87370389309d3a0486e26
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707614"
---
# <a name="creating-a-simple-read-only-provider"></a>Vytvoření jednoduchého zprostředkovatele pouze pro čtení

::: moniker range="vs-2019"

Průvodce zprostředkovatele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Pokud jste vytvořili pomocí zprostředkovatele OLE DB **Průvodce projektem ATL** a **Průvodce zprostředkovatelem ATL OLE DB**, můžete přidat další funkce, které chcete podporovat. Začněte vytvářet poskytovatele prozkoumáním jaký druh dat, které budete odesílání příjemci a za jakých podmínek. To je obzvláště důležité určit, jestli je potřeba podporovat příkazy, transakce a další volitelné objekty. Dobrý návrh ještě před zahájením bude rychlost implementace a testování.

V příkladu se zobrazí ve dvou částech:

- V první části se dozvíte postupy [vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) , který přečte dvojice řetězců.

- Druhá část ukazuje jak [vylepšit jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md) tak, že přidáte `IRowsetLocate` rozhraní.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
