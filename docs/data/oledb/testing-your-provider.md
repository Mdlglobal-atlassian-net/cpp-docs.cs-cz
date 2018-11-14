---
title: Testování zprostředkovatele
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: 9bb42af69a204c88e6068444642275b59ea5bf5c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518291"
---
# <a name="testing-your-provider"></a>Testování zprostředkovatele

Ještě před vydáním zprostředkovatele byste měli dělat následující testy v uvedeném pořadí. Tyto testy ukazují, že zprostředkovatel funkce správně pro většinu potenciální uživatelů.

1. Otestujte ho pomocí [příjemce](../../data/oledb/creating-an-ole-db-consumer.md) aplikaci napsanou s šablonami příjemců OLE DB. Test příjemce by mělo zahrnovat všechny funkční oblasti svého poskytovatele (všechen kód, který jste přidali nebo upravit).

1. Otestujte ho pomocí příjemce aplikace napsané pomocí rozhraní ADO. Většina vývojářů (zejména Microsoft Visual Basic a C# Microsoft vývojářům) používá ADO nebo ADO.NET pro aplikace pro koncové uživatele. Test příjemce by mělo zahrnovat všechny funkční oblasti vašeho zprostředkovatele. Příklad aplikace ADO příjemce, naleznete v tématu [ukázky kódu ADO v aplikaci Microsoft Visual Basicu](https://msdn.microsoft.com/library/ms807514.aspx).

1. Spuštění testů shodnosti technologie OLE DB (včetně testů shodnosti ADO) Chcete-li zobrazit, že váš poskytovatel splňuje standardní úroveň 0 pro zprostředkovatele OLE DB. (Vysvětlení úroveň 0, vyhledejte **testů pro úroveň 0 shodnosti technologie OLE DB** na [Příručka programátora technologie OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Tyto testy a související dokumentace jsou součástí Visual C++ v sadě SDK pro Data Access. Tyto testy se také pomoci zobrazíte, že váš poskytovatel správně funguje, když agregované podle jiných [poskytovatelé služeb](../../data/oledb/ole-db-resource-pooling-and-services.md) a jsou zvlášť užitečné, pokud změníte nebo přidáte vlastnosti. Další informace o přizpůsobení testů naleznete v souboru Readme pro Data Access SDK, která se nachází na jeden z disků CD Visual Studio.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)