---
title: Povolování a zakazování služeb pro zprostředkovatele
ms.date: 07/30/2019
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: a74f8a8b099a30cf25007547e8059c77728435f9
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682353"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>Povolování a zakazování služeb pro zprostředkovatele

Pro všechny aplikace, které mají přístup k jednomu zprostředkovateli, je možné ve výchozím nastavení povolit nebo zakázat jednotlivé OLE DB služby. To uděláte tak, že do identifikátoru CLSID poskytovatele přidáte položku registru OLEDB_SERVICES s hodnotou DWORD, která určuje služby, které chcete povolit nebo zakázat, jak je znázorněno v následující tabulce.

|Výchozí služby povoleny|Hodnota DWORD|
|------------------------------|-------------------|
|Všechny služby s výjimkou klientského kurzoru a sdružování|0xfffffffa|
|Všechny služby s výjimkou klientského kurzoru|0xfffffffb|
|Všechny služby s výjimkou sdružování a automatického zařazení|0xfffffffc|
|Všechny služby s výjimkou sdružování|0xfffffffe|
|Všechny služby (výchozí)|0xffffffff|
|Žádné služby|0x00000000|
|Bez agregace, všechny služby jsou zakázané.|Žádná položka registru OLEDB_Services|

## <a name="see-also"></a>Viz také:

[Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)
