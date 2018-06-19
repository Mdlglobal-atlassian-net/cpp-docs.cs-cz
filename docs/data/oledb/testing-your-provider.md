---
title: Testování zprostředkovatele | Microsoft Docs
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
ms.openlocfilehash: c35b1391e5b8cbfb073255b3680b0376d19ae040
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104786"
---
# <a name="testing-your-provider"></a>Testování zprostředkovatele
Před uvolněním zprostředkovatele, měli byste provést následující testy v uvedeném pořadí. Tyto testy zajistěte, aby funkce zprostředkovatele správně pro většinu potenciální uživatelů.  
  
1.  Testování zprostředkovatele pomocí [příjemce](../../data/oledb/creating-an-ole-db-consumer.md) aplikace vytvořené s šablonami příjemců OLE DB. Testování příjemce by mělo zahrnovat všechny funkční oblasti svého poskytovatele (všechny kód, který jste přidali nebo upravit).  
  
2.  Testování zprostředkovatele pomocí aplikace příjemce vytvořené s ADO. Většina vývojářů (zejména vývojáři Microsoft Visual Basic a Microsoft C#) používat ADO nebo ADO.NET pro příjemce aplikace. Testování příjemce by mělo zahrnovat všechny funkční oblasti svého poskytovatele. Příklad příjemce aplikace rozhraní ADO, naleznete v části [ADO příklady kódu v aplikaci Microsoft Visual Basicu](https://msdn.microsoft.com/en-us/library/ms807514.aspx).  
  
3.  Spuštění testů shodnosti technologie OLE DB (včetně testů shodnosti technologie ADO) zajistit, že váš poskytovatel splňuje standardní úroveň 0 pro zprostředkovatele OLE DB. (Další informace o úrovni 0, vyhledejte "Testy shodnosti úrovně 0 technologie OLE DB" v [OLE DB – Příručka pro vývojáře](http://go.microsoft.com/fwlink/p/?linkid=121548). Tyto testy a související dokumentace jsou součástí Visual C++ v sadě Data Access SDK. Tyto testy také pomáhají zajistit, že poskytovatel funguje dobře, pokud agregovat jiná [poskytovatelů služeb](../../data/oledb/ole-db-resource-pooling-and-services.md) a jsou obzvláště užitečné, pokud změníte nebo přidáte vlastnosti. Další informace o testů shodnosti naleznete v souboru Readme pro Data Access SDK, která se nachází na jeden z disků CD Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)