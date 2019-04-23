---
title: Vytvoření jednoduchého zprostředkovatele pouze pro čtení
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: a80678f6bc512c45c0df2ea5cbfc4708f1252ac0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035358"
---
# <a name="creating-a-simple-read-only-provider"></a>Vytvoření jednoduchého zprostředkovatele pouze pro čtení

Pokud jste vytvořili pomocí zprostředkovatele OLE DB **Průvodce projektem ATL** a **Průvodce zprostředkovatelem ATL OLE DB**, můžete přidat další funkce, které chcete podporovat. Začněte vytvářet poskytovatele prozkoumáním jaký druh dat, které budete odesílání příjemci a za jakých podmínek. To je obzvláště důležité určit, jestli je potřeba podporovat příkazy, transakce a další volitelné objekty. Dobrý návrh ještě před zahájením bude rychlost implementace a testování.

V příkladu se zobrazí ve dvou částech:

- V první části se dozvíte postupy [vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) , který přečte dvojice řetězců.

- Druhá část ukazuje jak [vylepšit jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md) tak, že přidáte `IRowsetLocate` rozhraní.

## <a name="see-also"></a>Viz také:

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
