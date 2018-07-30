---
title: Problémy s návrhem technologie OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b080945309732bec06c63eb665bbf6dd5f4acb5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340560"
---
# <a name="ole-db-architectural-design-issues"></a>Problémy s návrhem technologie OLE DB
Před zahájením aplikaci OLE DB, je třeba zvážit následující problémy:  
  
 **Jaké programovací implementace použijete k zápisu aplikaci OLE DB?**  
 Společnost Microsoft nabízí několik knihoven jak toho dosáhnout: knihovny šablon technologie OLE DB, atributy technologie OLE DB a raw rozhraní OLE DB v SDK technologie OLE DB. Kromě toho existují průvodců, snadněji napsat program. Tato implementace jsou popsány v [šablony technologie OLE DB, atributy a jiné implementace](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **Je třeba napsat vlastního zprostředkovatele?**  
 Většina vývojářů není nutné napsat vlastní zprostředkovatele. Společnost Microsoft poskytuje několik poskytovatelů. Při vytváření datového připojení (například když přidáte do projektu pomocí průvodce příjemcem ATL OLE DB příjemce), **vlastnosti propojení dat** dialogové okno zobrazí seznam všech dostupných zprostředkovatelů registrované ve vašem systému. Pokud jeden z těchto poskytovatelů je vhodné pro vaše vlastní aplikace pro přístup k ukládání dat a dat data, je nejjednodušší cesta použijte jeden z nich. Nicméně pokud vaše úložiště dat není vhodná pro jednu z těchto kategorií, budete muset vytvořit vlastního zprostředkovatele. Informace o vytváření poskytovatelů najdete v tématu [šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **Jaké úroveň podpory je potřeba pro vaše?**  
 Některé příjemce může být velmi základní; zatímco ostatní mohou být velmi složité. Funkce pro objekty OLE DB je zadána vlastností. Když použijete průvodce příjemcem ATL OLE DB k vytvoření příjemce nebo Průvodce zprostředkovatelem databázi vytvořit zprostředkovatele, nastaví vlastnosti příslušný objekt pro vám umožní poskytovat standardní sadu funkcí. Ale pokud příjemce nebo zprostředkovatele třídy generované v Průvodci nepodporují všechno, co budete potřebovat udělat, musíte odkazovat na rozhraní pro tyto třídy v [knihovny šablon technologie OLE DB](../../data/oledb/ole-db-templates.md). Tato rozhraní zabalit nezpracovaná rozhraní technologie OLE DB poskytují dodatečné implementace pro usnadnění jejich používání za vás.  
  
 Například pokud chcete aktualizovat data v sadě řádků, ale zapomněli zadat při vytváření příjemce pomocí průvodce, můžete zadat funkce po jejich výskytu tak, že nastavíte `DBPROP_IRowsetChange` a `DBPROP_UPDATABILITY` vlastnosti v objektu command. Poté, když se v sadě řádků, má `IRowsetChange` rozhraní.  
  
 **Máte starší kód pomocí jiné technologie přístup data (ADO, ODBC a DAO)?**  
 Je to možné kombinace technologií (jako jsou komponenty technologie OLE DB pomocí komponenty ADO a migrace kód rozhraní ODBC do technologie OLE DB), zahrnující všechny situace je nad rámec dokumentace k Visual C++. Řada článků pokrývajících různé scénáře jsou však k dispozici na následujících webech Microsoftu:  
  
-   [Nápovědu a podporu Microsoftu](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Přehled technické články k přístupu k datům společnosti Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Středisko řešení sady Visual Studio](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [Hledat na webu Microsoft.com](http://search.microsoft.com/)  
  
 Při vyhledávání, zadejte kombinace klíčových slov, která nejlépe vyhovuje vaší situaci; Příklad: Pokud jste používali objektů ADO pomocí zprostředkovatele OLE DB, zkuste logického hledání s **ADO a "OLE DB"**. Pokud jste chtěli migrovat starší rozhraní DAO kód k rozhraní ODBC, vyberte "všech slov" a zadejte řetězce, jako například **migrace DAO**.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)