---
title: Přepsání výchozích hodnot služby zprostředkovatele
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209797"
---
# <a name="overriding-provider-service-defaults"></a>Přepsání výchozích hodnot služby zprostředkovatele

Hodnota registru poskytovatele pro OLEDB_SERVICES je vrácena jako výchozí hodnota pro inicializační vlastnost [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) objektu zdroje dat.

Pokud existuje položka registru, objekty poskytovatele budou agregovány. Uživatel může přepsat výchozí nastavení poskytovatele pro povolené služby nastavením vlastnosti DBPROP_INIT_OLEDBSERVICES před inicializací. Chcete-li povolit nebo zakázat určitou službu, uživatel získá aktuální hodnotu vlastnosti DBPROP_INIT_OLEDBSERVICES, nastaví nebo zruší bit pro konkrétní vlastnost, která má být povolena nebo zakázána, a obnoví vlastnost. DBPROP_INIT_OLEDBSERVICES lze nastavit přímo v OLE DB nebo v připojovacím řetězci předaných do ADO nebo `IDataInitialize::GetDatasource`. Příslušné hodnoty pro povolení nebo zakázání jednotlivých služeb jsou uvedeny v následující tabulce.

|Výchozí služby povoleny|Hodnota vlastnosti DBPROP_INIT_OLEDBSERVICES|Hodnota v připojovacím řetězci|
|------------------------------|------------------------------------------------|--------------------------------|
|Všechny služby (výchozí)|DBPROPVAL_OS_ENABLEALL|"OLE DB Services =-1;"|
|Vše kromě sdružování a autozařazení|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services =-4;"|
|Vše kromě klientského kurzoru|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-5;"|
|Vše s výjimkou sdružování, reřazování a klientského kurzoru|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-7;"|
|Žádné služby|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

Pokud položka registru pro poskytovatele neexistuje, správci komponent nebudou shromažďovat objekty poskytovatele. Žádné služby nebudou zapnuté, a to ani v případě, že uživatel výslovně vyžádá.

## <a name="see-also"></a>Viz také

[Sdružování prostředků](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[Jak spotřebitelé využívají sdružování prostředků](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[Jak poskytovatelé pracují efektivně s sdružováním prostředků](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
