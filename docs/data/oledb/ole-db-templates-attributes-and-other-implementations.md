---
title: Šablony technologie OLE DB, atributy a jiné implementace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef9baf43ded1533eb7f4962db7344f9dc1def0ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB – šablony, atributy a jiné implementace technologie
## <a name="atl-ole-db-templates"></a>Šablony technologie OLE DB knihovny ATL  
 Šablony technologie OLE DB, které jsou součástí knihovny ATL (Active knihovna šablon), usnadňují použití tím, že poskytuje třídy, které implementují mnoho běžně používaných rozhraní OLE DB databázové technologie OLE DB vysoce výkonné. Knihovny společně s tuto šablonu je podpora průvodce pro vytváření aplikací OLE DB starter.  
  
 Tato knihovna šablon obsahuje dvě části:  
  
-   **Šablony příjemce technologie OLE DB** použít k implementaci aplikace klienta (příjemce) technologie OLE DB.  
  
-   **Šablony zprostředkovatele technologie OLE DB** použít k implementaci aplikace serveru (zprostředkovatel) technologie OLE DB.  
  
 Pokud chcete používat šablony technologie OLE DB, měli seznámit pomocí šablon C++, COM a rozhraní OLE DB. Pokud nejste obeznámeni s OLE DB, přečtěte si téma [referenční příručka programátora technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx).  
  
 Další informace můžete:  
  
-   Přečtěte si témata o [šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) nebo [šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
-   Vytvoření [příjemce technologie OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) nebo [zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md).  
  
-   Zobrazit seznam [třídy příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) nebo [třídy zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-reference.md).  
  
-   Zobrazit seznam [OLE DB – Ukázky šablon](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c).  
  
-   V tématu [referenční příručka programátora prostředí OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (ve Windows SDK).  
  
## <a name="ole-db-attributes"></a>Atributy technologie OLE DB  
 [Atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md) poskytují pohodlný způsob pro vytváření OLE DB. Atributy technologie OLE DB vloží kód na základě [šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) k vytvoření a zprostředkovatele OLE DB práci. Pokud budete muset zadat funkce nepodporuje atributy, můžete ve spojení s atributy šablony technologie OLE DB v kódu.  
  
## <a name="mfc-ole-db-classes"></a>Třídy MFC OLE DB  
 Knihovna MFC má jednu třídu, [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), který zobrazí záznamů databáze v ovládacích prvcích. Zobrazení je přímo připojený k zobrazení formuláře `CRowset` objektu a zobrazí pole `CRowset` objektu v ovládacích prvcích šablony dialogového okna. Také poskytuje výchozí implementaci pro přesun na první další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu aktuálně pro zobrazení. Další informace naleznete v tématu `COleDBRecordView`.  
  
## <a name="ole-db-sdk-interfaces"></a>OLE DB sady SDK rozhraní  
 V případech, kde šablony technologie OLE DB nepodporují funkce technologie OLE DB budete muset použít rozhraní OLE DB, sami. Další informace najdete v tématu [referenční příručka programátora technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – programování](../../data/oledb/ole-db-programming.md)   
 [Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)