---
title: Přepsání výchozích hodnot služby zprostředkovatele
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: a9f8eb1c96c40336f39f14fe1a0ee29d60efd003
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265214"
---
# <a name="overriding-provider-service-defaults"></a>Přepsání výchozích hodnot služby zprostředkovatele

Hodnota registru zprostředkovatele pro OLEDB_SERVICES se vrátí jako výchozí hodnota [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898) inicializace vlastnosti na objektu zdroje dat.

Za předpokladu, položka registru existuje, je agregován objekty daného zprostředkovatele. Uživatel může přepsat výchozí nastavení pro povolené služby tak, že nastavíte vlastnost DBPROP_INIT_OLEDBSERVICES před inicializací zprostředkovatele. Pokud chcete povolit nebo zakázat určité služby, uživatel získá aktuální hodnotu vlastnosti DBPROP_INIT_OLEDBSERVICES, nastaví nebo vymaže bit pro konkrétní vlastnost, která má být povolena nebo zakázána a obnoví vlastnost. Můžete přímo v OLE DB nebo připojovací řetězec, který je předán ADO nastavit DBPROP_INIT_OLEDBSERVICES nebo `IDataInitialize::GetDatasource`. Odpovídající hodnoty pro povolení nebo zákaz jednotlivé služby jsou uvedené v následující tabulce.

|Povolené výchozí služby|Hodnota vlastnosti DBPROP_INIT_OLEDBSERVICES|Hodnota připojovacího řetězce|
|------------------------------|------------------------------------------------|--------------------------------|
|Všechny služby (výchozí)|DBPROPVAL_OS_ENABLEALL|"Služeb OLE DB = -1;"|
|Všechny s výjimkou sdružování a AutoEnlistment|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"Služeb OLE DB = -4;"|
|Všechny s výjimkou klientský kurzor|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Služeb OLE DB = -5;"|
|Všechny s výjimkou sdružování AutoEnlistment a klientský kurzor|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Služeb OLE DB = -7;"|
|Žádné služby.|`~DBPROPVAL_OS_ENABLEALL`|"Služeb OLE DB = 0;"|

Pokud položka registru neexistuje pro zprostředkovatele, správce součástí neshromáždí objekty daného zprostředkovatele. Žádné služby zapne, i v případě, že explicitně požadavku uživatele.

## <a name="see-also"></a>Viz také

[Sdružování prostředků](/previous-versions/windows/desktop/ms713655)<br/>
[Jak zákazníci používají fondy prostředků](/previous-versions/windows/desktop/ms715907)<br/>
[Jak poskytovatelů efektivně pracovat s fondy prostředků](/previous-versions/windows/desktop/ms714906)<br/>
[Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>