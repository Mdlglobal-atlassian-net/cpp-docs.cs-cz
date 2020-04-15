---
title: Rozhraní (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319391"
---
# <a name="interfaces-atl"></a>Rozhraní (ATL)

Rozhraní je způsob, jakým objekt zveřejňuje jeho funkce vnějšímu světu. V com rozhraní je tabulka ukazatelů (jako C++ vtable) na funkce implementované objektem. Tabulka představuje rozhraní a funkce, na které odkazuje, jsou metody tohoto rozhraní. Objekt může vystavit tolik rozhraní, jak se vybere.

Každé rozhraní je založeno na základním rozhraní [COM, IUnknown](../atl/iunknown.md). Metody `IUnknown` povolit navigaci do jiných rozhraní vystavených objektem.

Každé rozhraní má také jedinečné ID rozhraní (IID). Tato jedinečnost usnadňuje podporu správy verzí rozhraní. Nová verze rozhraní je jednoduše nové rozhraní s novým IID.

> [!NOTE]
> IID pro standardní rozhraní COM a OLE jsou předdefinovány.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Objekty a rozhraní modelu COM](/windows/win32/com/com-objects-and-interfaces)
