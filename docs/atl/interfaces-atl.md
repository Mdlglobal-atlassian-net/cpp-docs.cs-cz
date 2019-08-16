---
title: Rozhraní (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492127"
---
# <a name="interfaces-atl"></a>Rozhraní (ATL)

Rozhraní je způsob, jakým objekt zpřístupňuje svou funkci na vnějším světě. V modelu COM je rozhraní tabulkou ukazatelů (jako je C++ vtable) na funkce implementované objektem. Tabulka představuje rozhraní a funkce, na které odkazuje, jsou metody tohoto rozhraní. Objekt může vystavit tolik rozhraní, kolik jich zvolí.

Každé rozhraní je založeno na základním rozhraní modelu COM, [IUnknown](../atl/iunknown.md). Metody pro `IUnknown` povolení navigace jiným rozhraním vystaveným objektem.

Každé rozhraní je také přiděleno jedinečné ID rozhraní (IID). Tato jedinečnost usnadňuje podporu verzí rozhraní. Nová verze rozhraní je jednoduše nové rozhraní s novým identifikátorem IID.

> [!NOTE]
>  IID pro standardní rozhraní COM a rozhraní OLE jsou předdefinovaná.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Objekty modelu COM a rozhraní](/windows/win32/com/com-objects-and-interfaces)
