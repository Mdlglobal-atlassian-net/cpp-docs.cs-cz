---
title: Rozšíření jednoduchého zprostředkovatele pouze pro čtení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dc899314070f10c0b10cd959af57a7230a406ac3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069708"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Rozšíření jednoduchého zprostředkovatele pouze pro čtení

Tato část ukazuje, jak zvýšit [jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) vytvořili v předchozí části. `IRowsetLocateImpl` Vytvoří implementaci `IRowsetLocate` rozhraní a přidává podporu záložku za vás.

Až budete mít funkční poskytovatele, můžete ho tak, aby aktualizace poskytovatele, zpracování transakcí nebo zvýšení výkonu načítání řádků algoritmus vylepšit. Většina poskytovatele vylepšení zahrnují přidání rozhraní do existujícího objektu modelu COM.

V příkladu v následujících tématech vylepšuje mechanismus načítání řádků tak, že přidáte `IRowsetLocate` rozhraní při `CAgentRowset`. Témata ukazují, jak do:

- [Ujistěte se, RCustomRowset dědit z IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).

- [Dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Viz také

[Vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/creating-a-simple-read-only-provider.md)