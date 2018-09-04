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
ms.openlocfilehash: 2b0a5c568a774d0aed05d702454664e653989401
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676833"
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
  
-   [Nápovědu a podporu Microsoftu](https://support.microsoft.com/)  
  
-   [Přehled technické články k přístupu k datům společnosti Microsoft](https://msdn.microsoft.com/en-us/library/ms810811.aspx)  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)