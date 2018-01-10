---
title: "Šablony zprostředkovatele technologie OLE DB (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f95b32d62d964c83853025ed4e4af9b90e7a630a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-provider-templates-c"></a>Šablony zprostředkovatele OLE DB (C++)
OLE DB, je důležitou součástí strategie Microsoft Universal Data Access. OLE DB návrh umožňuje přístup k datům vysoce výkonné z jakéhokoli zdroje dat. Žádná tabulková data jsou viditelná prostřednictvím technologie OLE DB bez ohledu na to, jestli pochází z databáze. Flexibilitu poskytuje rozsáhlou napájení.  
  
 Jak je popsáno v [OLE DB příjemci a zprostředkovatelé](../../data/oledb/ole-db-consumers-and-providers.md), používá koncept příjemci a zprostředkovatelé technologie OLE DB. Příjemce vytváří požadavky na data; zprostředkovatel vrací data ve formátu tabulky k příjemce. Z hlediska programovací nejdůležitější důsledkem tohoto modelu je, že zprostředkovatel musí implementovat každé volání uplatnit.  
  
## <a name="what-is-a-provider"></a>Co je zprostředkovatel?  
 Zprostředkovatele OLE DB je sada objektů COM, které sloužící k volání rozhraní z objektu příjemce přenosu dat v tabulkovém formátu z trvanlivého zdroje (označovanou jako úložiště dat) k příjemce.  
  
 Zprostředkovatelé můžou být jednoduché nebo komplexní. Zprostředkovatel může podporovat minimální počet funkcí nebo plnohodnotného kvalitního zprostředkovatele implementací více rozhraní. Zprostředkovatele můžete vrátit tabulku, povolit klientům určit formát této tabulky a provést operace s těmito daty.  
  
 Každý poskytovatel implementuje standardní sadu objektů COM na zpracování požadavků z klienta, se standardní význam, že všechny příjemce technologie OLE DB můžete přístup k datům z kteréhokoli poskytovatele služeb, bez ohledu na jazyk (například C++ a základní).  
  
 Každý objekt COM obsahuje několik rozhraní, z nichž některé jsou vyžadovány a některé z nich jsou volitelné. Implementací povinné rozhraní poskytovatele zaručuje minimální úroveň funkcí (nazývané dodržování), které by mohli použít libovolného klienta. Zprostředkovatel může implementovat volitelné rozhraní k poskytnutí dalších funkcí. [Architektura technologie OLE DB Provider šablon](../../data/oledb/ole-db-provider-template-architecture.md) popisuje podrobně tato rozhraní. Klient vždy by měly volat `QueryInterface` k určení, zda zprostředkovatel podporuje dané rozhraní.  
  
## <a name="ole-db-specification-level-support"></a>Úroveň podpory specifikace OLE DB  
 Šablony zprostředkovatele technologie OLE DB podporuje specifikace verze 2.7 OLE DB. Pomocí šablony zprostředkovatele technologie OLE DB, můžete implementovat úroveň 0 kompatibilní zprostředkovatele. Příklad zprostředkovatele, například používá šablony k implementaci serveru non příkaz, který spouští příkaz DOS DIR k dotazování systému souborů. Příklad zprostředkovatele vrátí informaci o adresáři v sadě řádků, což je standardní mechanismus OLE DB pro vrácení tabulková data.  
  
 Nejjednodušší typ zprostředkovatele nepodporuje šablony technologie OLE DB je jen pro čtení zprostředkovatel s žádné příkazy. Zprostředkovatelé s příkazy jsou také podporovány, jako jsou schopnosti záložky a pro čtení a zápis. Vytvořením další kód můžete implementovat zprostředkovatele pro čtení a zápis. Aktuální verze nepodporuje dynamické sady řádků a transakce, ale pokud chcete, můžete je přidat.  
  
## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Pokud potřebujete k vytvoření zprostředkovatele OLE DB?  
 Není vždy nutné k vytvoření vlastního zprostředkovatele; Společnost Microsoft poskytuje několik hotových standardní zprostředkovatelů v **vlastnosti propojení dat** dialogové okno v jazyce Visual C++. Hlavním důvodem k vytvoření zprostředkovatele OLE DB je využít výhod strategie univerzální přístup k datům. Mezi výhody, patří:  
  
-   Přístup k datům přes jakýkoli jazyk například C++, Basic a Visual Basic Scripting Edition. Umožňuje různým programátorům ve vaší organizaci pro přístup ke stejným datům stejným způsobem, bez ohledu na to, jaký jazyk používají.  
  
-   Vystavení dat s jinými daty zdroje systému SQL Server, Excel a přístup. To může být velmi užitečné, pokud chcete k přenosu dat mezi různými formáty.  
  
-   Účastní operací se zdrojovým cross-data (heterogenní). To může být velmi efektivní způsob datových skladů. S použitím zprostředkovatelů OLE DB, můžete ponechat data v nativním formátu a mít pořád povolený přístup, když je jednoduchá operace.  
  
-   Přidání dalších možností pro data, jako je například zpracování dotazu.  
  
-   Zvýšení výkonu přístupu k datům v kontrole, jak je upravit.  
  
-   Zvýšení odolnosti. Pokud máte proprietární dat formát, že pouze jeden programátory přístup, jsou v ohrožení. Pomocí zprostředkovatele OLE DB, můžete otevřít speciální formát všem programátorům.  
  
## <a name="read-only-and-updatable-providers"></a>Jen pro čtení a aktualizovatelní zprostředkovatelé  
 Zprostředkovatelé může značně lišit v složitost a funkce. Je užitečné kategorizovat zprostředkovatele na zprostředkovatelé jen pro čtení a aktualizovatelní zprostředkovatelé:  
  
-   Visual C++ verze 6.0 podporované jenom zprostředkovatelé jen pro čtení. [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md) popisuje, jak vytvořit poskytovatele jen pro čtení.  
  
-   Visual C++ podporuje aktualizovatelné zprostředkovatele, které můžete aktualizovat (zapisovat na) úložišti. Informace o aktualizovatelní zprostředkovatelé najdete v tématu [vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázka je příkladem aktualizovatelného zprostředkovatele.  
  
 Další informace naleznete v tématu:  
  
-   [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)  
  
-   [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)  
  
-   [Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům](../data-access-in-cpp.md)   
 [Dokumentaci k sadě SDK OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [Referenční příručka programátora prostředí OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx)