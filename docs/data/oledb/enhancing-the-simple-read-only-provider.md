---
title: Rozšíření jednoduchého zprostředkovatele pouze pro čtení
ms.date: 10/26/2018
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
ms.openlocfilehash: d61f24a9a9abffe836a7f11bd5d1517fddf97fe7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034073"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Rozšíření jednoduchého zprostředkovatele pouze pro čtení

Tato část ukazuje, jak zvýšit [jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) vytvořili v předchozí části. `IRowsetLocateImpl` Vytvoří implementaci `IRowsetLocate` rozhraní a přidává podporu záložku za vás.

Až budete mít funkční poskytovatele, můžete ho tak, aby aktualizace poskytovatele, zpracování transakcí nebo zvýšení výkonu načítání řádků algoritmus vylepšit. Většina poskytovatele vylepšení zahrnují přidání rozhraní do existujícího objektu modelu COM.

V příkladu v následujících tématech vylepšuje mechanismus načítání řádků tak, že přidáte `IRowsetLocate` rozhraní při `CAgentRowset`. Témata ukazují, jak do:

- [Ujistěte se, RCustomRowset dědit z IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).

- [Dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Viz také:

[Vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
