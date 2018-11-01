---
title: Povolování a zakazování služeb pro zprostředkovatele
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: ca621b005dd0bad60c70298e4d49abce6fb8d1d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665449"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Povolování a zakazování služeb pro zprostředkovatele

Jednotlivé služby rozhraní OLE DB můžete povolit nebo zakázat ve výchozím nastavení pro všechny aplikace, které přistupují k jednoho zprostředkovatele. To se provádí tak, že přidáte položku registru OLEDB_SERVICES CLSID zprostředkovatele s `DWORD` hodnota určuje služby, které chcete povolit nebo zakázat, jak je znázorněno v následující tabulce.

|Povolené výchozí služby|Hodnota – klíčové slovo|
|------------------------------|-------------------|
|Všechny služby (výchozí)|0xFFFFFFFF|
|Všechny s výjimkou sdružování a AutoEnlistment|0xFFFFFFFE|
|Všechny s výjimkou klientský kurzor|0xfffffffb|
|Všechny s výjimkou sdružování AutoEnlistment a klientský kurzor|0xfffffff0|
|Žádné služby.|0x00000000|
|Žádné agregace všechny služby jsou zakázány|\<chybí klíč >|

## <a name="see-also"></a>Viz také

[Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)