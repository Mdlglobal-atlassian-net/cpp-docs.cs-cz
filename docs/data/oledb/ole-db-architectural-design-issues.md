---
title: Problémy s návrhem technologie OLE DB | Microsoft Docs
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
ms.openlocfilehash: 75d996416e92ded920f45d3352c6478dd8c67a86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-architectural-design-issues"></a>Problémy s návrhem technologie OLE DB
Před zahájením aplikaci OLE DB, je třeba zvážit následující problémy:  
  
 **Jaké programovací implementace použijete k zápisu aplikaci OLE DB?**  
 Společnost Microsoft nabízí několik knihoven k tomuto účelu: knihovny šablony technologie OLE DB, atributy technologie OLE DB a raw rozhraní OLE DB v SDK technologie OLE DB. Kromě toho existují průvodců, snadněji tak můžete psát vašeho programu. Tato implementace jsou popsané v [šablony technologie OLE DB, atributy a jiné implementace](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **Potřebujete napsat vlastního zprostředkovatele?**  
 Většina vývojářů, není nutné napsat vlastní zprostředkovatele. Společnost Microsoft poskytuje několik poskytovatelů. Vždy, když vytvoříte připojení dat (například když přidáte do projektu pomocí průvodce příjemcem knihovny ATL technologie OLE DB příjemce), **vlastnosti propojení dat** dialogové okno obsahuje seznam všech dostupných zprostředkovatelů registrovaných v systému. Pokud jeden z těchto poskytovatelů je vhodné pro vaše vlastní datové úložiště a data aplikace přístup, je nejjednodušší cesta použít jeden z nich. Ale pokud data store nevejde jedné z těchto kategorií, budete muset vytvořit vlastního poskytovatele. Informace o vytváření poskytovatelů najdete v tématu [šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **Jakou úroveň podpory potřebujete pro vaše příjemce?**  
 Někteří příjemci mohou být velmi základní; zatímco jiné může být velmi složité. Funkce objektů OLE DB je určena vlastnostmi. Pokud použijete průvodce příjemcem knihovny ATL technologie OLE DB k vytvoření příjemce a v průvodci zprostředkovatele databáze, které slouží k vytvoření poskytovatele, nastaví příslušné objekt vlastnosti vám poskytuje standardní sada funkcí. Ale pokud příjemce nebo zprostředkovatele třídy generované v Průvodci všechno, co potřebujete, aby se nepodporují, musíte k odkazování na rozhraní pro tyto třídy v [knihovny šablony technologie OLE DB](../../data/oledb/ole-db-templates.md). Tato rozhraní zabalit nezpracovaná rozhraní OLE DB, poskytuje další implementace usnadnění jejich používání za vás.  
  
 Například pokud chcete aktualizovat data v sadě řádků, ale zapomněli jste na tuto verzi uveďte při vytváření příjemce pomocí průvodce, můžete zadat funkce ve skutečnosti nastavení **DBPROP_IRowsetChange** a  **DBPROP_UPDATABILITY** vlastnosti v objektu command. Poté, když je vytvořen sadu řádků, má `IRowsetChange` rozhraní.  
  
 **Máte starší kódu pomocí jiné technologie přístup data (ADO, rozhraní ODBC a DAO)?**  
 Zadána možných kombinací technologie (například pomocí součásti ADO součásti OLE DB a migrace kód rozhraní ODBC do OLE DB) zahrnující všechny situace je nad rámec dokumentace Visual C++. Mnoho článků týkajících se různé scénáře jsou však k dispozici na následujících webech společnosti Microsoft:  
  
-   [Nápovědu a podporu Microsoftu](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Přehled technických článcích přístupu k datům společnosti Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Centrum řešení Visual Studio](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [Hledání Microsoft.com](http://search.microsoft.com/)  
  
 Při hledání, zadejte kombinaci klíčová slova, která nejlépe odpovídá vašemu scénáři; například: Pokud jste používali objektů ADO pomocí zprostředkovatele OLE DB, zkuste logické vyhledávání s **ADO a "Technologie OLE DB"**. Pokud jste chtěli migrovat starší rozhraní DAO kódu do rozhraní ODBC, vyberte "všechna slova" a zadejte řetězce, jako například **migrace DAO**.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)