---
title: Testování zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c99a881dd90d94c87de98239a7de1a2b49be020
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060219"
---
# <a name="testing-your-provider"></a>Testování zprostředkovatele

Ještě před vydáním zprostředkovatele, měli byste provést následující testy v uvedeném pořadí. Tyto testy Ujistěte se, že zprostředkovatel funkce správně pro většinu potenciální uživatelů.

1. Otestujte ho pomocí [příjemce](../../data/oledb/creating-an-ole-db-consumer.md) aplikaci napsanou s šablonami příjemců OLE DB. Test příjemce by mělo zahrnovat všechny funkční oblasti svého poskytovatele (všechen kód, který jste přidali nebo upravit).

1. Otestujte ho pomocí příjemce aplikace napsané pomocí rozhraní ADO. Většina vývojářů (zejména Microsoft Visual Basic a C# Microsoft vývojářům) používá ADO nebo ADO.NET pro aplikace pro koncové uživatele. Test příjemce by mělo zahrnovat všechny funkční oblasti vašeho zprostředkovatele. Příklad aplikace ADO příjemce, naleznete v tématu [ukázky kódu ADO v aplikaci Microsoft Visual Basicu](https://msdn.microsoft.com/library/ms807514.aspx).

1. Spuštění testů shodnosti technologie OLE DB (včetně testů shodnosti ADO) jestli splňuje standardní úroveň 0 pro zprostředkovatele OLE DB poskytovatele. (Vysvětlení úroveň 0, vyhledejte "Testů shodnosti úroveň 0 technologie OLE DB" v [Příručka programátora technologie OLE DB](/previous-versions/windows/desktop/ms713643). Tyto testy a související dokumentace jsou součástí Visual C++ v sadě SDK pro Data Access. Tyto testy také pomáhají zajistit, že váš poskytovatel funguje dobře, když se agregují jiná [poskytovatelé služeb](../../data/oledb/ole-db-resource-pooling-and-services.md) a jsou zvlášť užitečné, pokud změníte nebo přidáte vlastnosti. Další informace o přizpůsobení testů naleznete v souboru Readme pro Data Access SDK, která se nachází na jeden z disků CD Visual Studio.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)