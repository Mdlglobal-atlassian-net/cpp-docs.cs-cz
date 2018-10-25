---
title: Povolování a zakazování služeb pro zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c9b255e715a635494e3acc34124871e90ceca8f7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055369"
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