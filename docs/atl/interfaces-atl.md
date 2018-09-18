---
title: Rozhraní (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef93476e669b923d642f79f480c602229d6a4322
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071156"
---
# <a name="interfaces-atl"></a>Rozhraní (ATL)

Rozhraní je způsob, ve kterém objekt zpřístupňuje jeho funkce zvnějšku. V modelu COM rozhraní je tabulka ukazatelů (třeba C++ vtable) na funkce, které jsou implementovány v objektu. V tabulce představuje rozhraní a metody rozhraní jsou funkce, na které odkazuje. Objekt lze vystavit libovolný počet rozhraní jako zvolí.

Každé rozhraní je založená na základní rozhraní modelu COM, [IUnknown](../atl/iunknown.md). Metody `IUnknown` povolit navigaci na další vystavených objektem.

Každé rozhraní je rovněž jedinečné ID rozhraní (IID). Tuto jedinečnost usnadňuje podporu rozhraní správy verzí. Jednoduše na nové rozhraní s novou IID je nová verze rozhraní.

> [!NOTE]
>  IID pro rozhraní COM a OLE standard jsou předdefinovány.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Objekty COM a rozhraní](/windows/desktop/com/com-objects-and-interfaces)

