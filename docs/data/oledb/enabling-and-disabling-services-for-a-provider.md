---
title: Povolování a zakazování služeb pro zprostředkovatele
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: d91f08accf1a8be69f63d6bbcaa4c620d68c1077
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175436"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Povolování a zakazování služeb pro zprostředkovatele

Jednotlivé služby rozhraní OLE DB můžete povolit nebo zakázat ve výchozím nastavení pro všechny aplikace, které přistupují k jednoho zprostředkovatele. To se provádí tak, že přidáte položku registru OLEDB_SERVICES CLSID zprostředkovatele s hodnotou DWORD určení služby, které chcete povolit nebo zakázat, jak je znázorněno v následující tabulce.

|Povolené výchozí služby|Hodnota – klíčové slovo|
|------------------------------|-------------------|
|Všechny služby (výchozí)|0xffffffff|
|Všechny s výjimkou sdružování a AutoEnlistment|0xFFFFFFFE|
|Všechny s výjimkou klientský kurzor|0xfffffffb|
|Všechny s výjimkou sdružování AutoEnlistment a klientský kurzor|0xfffffff0|
|Žádné služby.|0x00000000|
|Žádné agregace všechny služby jsou zakázány|\<chybí klíč >|

## <a name="see-also"></a>Viz také:

[Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)