---
title: Vytvoření jednoduchého zprostředkovatele pouze pro čtení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c8fd4e5eb25ab1e8e6b20b576a0688da7b5aa2ef
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216393"
---
# <a name="creating-a-simple-read-only-provider"></a>Vytvoření jednoduchého zprostředkovatele pouze pro čtení

Pokud jste vytvořili pomocí zprostředkovatele OLE DB **Průvodce projektem ATL** a **Průvodce zprostředkovatelem ATL OLE DB**, můžete přidat další funkce, které chcete podporovat. Začněte vytvářet poskytovatele prozkoumáním jaký druh dat, které budete odesílání příjemci a za jakých podmínek. To je obzvláště důležité určit, jestli je potřeba podporovat příkazy, transakce a další volitelné objekty. Dobrý návrh ještě před zahájením bude rychlost implementace a testování.

V příkladu se zobrazí ve dvou částech:

- V první části se dozvíte postupy [vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) , který přečte dvojice řetězců.

- Druhá část ukazuje jak [vylepšit jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md) tak, že přidáte `IRowsetLocate` rozhraní.

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
