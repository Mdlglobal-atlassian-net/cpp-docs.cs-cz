---
title: "Testování zprostředkovatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1c97db59b88672f390fc88b78f8d5f843ca7099
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="testing-your-provider"></a>Testování zprostředkovatele
Před uvolněním zprostředkovatele, měli byste provést následující testy v uvedeném pořadí. Tyto testy zajistěte, aby funkce zprostředkovatele správně pro většinu potenciální uživatelů.  
  
1.  Testování zprostředkovatele pomocí [příjemce](../../data/oledb/creating-an-ole-db-consumer.md) aplikace vytvořené s šablonami příjemců OLE DB. Testování příjemce by mělo zahrnovat všechny funkční oblasti svého poskytovatele (všechny kód, který jste přidali nebo upravit).  
  
2.  Testování zprostředkovatele pomocí aplikace příjemce vytvořené s ADO. Většina vývojářů (zejména vývojáři Microsoft Visual Basic a Microsoft C#) používat ADO nebo ADO.NET pro příjemce aplikace. Testování příjemce by mělo zahrnovat všechny funkční oblasti svého poskytovatele. Příklad příjemce aplikace rozhraní ADO, naleznete v části [ADO příklady kódu v aplikaci Microsoft Visual Basicu](https://msdn.microsoft.com/en-us/library/ms807514.aspx).  
  
3.  Spuštění testů shodnosti technologie OLE DB (včetně testů shodnosti technologie ADO) zajistit, že váš poskytovatel splňuje standardní úroveň 0 pro zprostředkovatele OLE DB. (Další informace o úrovni 0, vyhledejte "Testy shodnosti úrovně 0 technologie OLE DB" v [OLE DB – Příručka pro vývojáře](http://go.microsoft.com/fwlink/?linkid=121548). Tyto testy a související dokumentace jsou součástí Visual C++ v sadě Data Access SDK. Tyto testy také pomáhají zajistit, že poskytovatel funguje dobře, pokud agregovat jiná [poskytovatelů služeb](../../data/oledb/ole-db-resource-pooling-and-services.md) a jsou obzvláště užitečné, pokud změníte nebo přidáte vlastnosti. Další informace o testů shodnosti naleznete v souboru Readme pro Data Access SDK, která se nachází na jeden z disků CD Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)