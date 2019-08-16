---
title: Testování zprostředkovatele
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: 722757b93d3423b02340c382b16e08a31626bc01
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501256"
---
# <a name="testing-your-provider"></a>Testování zprostředkovatele

Před vydáním zprostředkovatele byste měli provést následující testy v uvedeném pořadí. Tyto testy ukazují, že poskytovatel funguje správně pro většinu potenciálních uživatelů.

1. Otestujte poskytovatele pomocí aplikace [příjemce](../../data/oledb/creating-an-ole-db-consumer.md) napsané pomocí šablon zákazníků OLE DB. Testovací příjemce by měl pokrývat všechny funkční oblasti vašeho poskytovatele (veškerý kód, který jste přidali nebo upravili).

1. Otestujte poskytovatele pomocí aplikace příjemce napsané pomocí ADO. Většina vývojářů (zejména Microsoft Visual Basic a C# vývojářů Microsoftu) pro aplikace pro spotřebitele používá ADO nebo ADO.NET. Testovací příjemce by měl pokrývat všechny funkční oblasti vašeho poskytovatele. Příklad aplikace příjemce ADO najdete [v tématu Příklady kódů ADO v Microsoft Visual Basic](/previous-versions/ms807514(v=msdn.10)).

1. Spusťte testy shody OLE DB (včetně testů shody ADO), abyste ukázali, že poskytovatel splňuje standard úrovně 0 pro poskytovatele OLE DB. (Pro vysvětlení úrovně 0 vyhledejte **OLE DB testy shody úrovně 0** v [příručce OLE DB Programátorská příručka](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Tyto testy a přidruženou dokumentaci jsou součástí vizuálu C++ v sadě Data Access SDK. Tyto testy také pomůžou Ukázat, že váš poskytovatel je dobře spuštěný, když je agregovaný jinými [poskytovateli služeb](../../data/oledb/ole-db-resource-pooling-and-services.md) a je zvlášť užitečný, když upravíte nebo přidáte vlastnosti. Další informace o testech dodržování shody najdete v souboru Readme pro sadu SDK pro Data Access, která je umístěná na jednom z disků CD sady Visual Studio.

## <a name="see-also"></a>Viz také:

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)