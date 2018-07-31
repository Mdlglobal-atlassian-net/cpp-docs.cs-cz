---
title: Vytvoření zprostředkovatele OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5de304b7a21c47af18b8b753d6de704ef2473c5f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338789"
---
# <a name="creating-an-ole-db-provider"></a>Vytvoření zprostředkovatele OLE DB
Doporučeným způsobem vytvoření zprostředkovatele OLE DB je pomocí průvodců vytvořte projekt knihovny ATL modelu COM a zprostředkovatele a potom upravte soubory pomocí šablony technologie OLE DB. Při úpravách poskytovatele, můžete Zakomentovat nežádoucí vlastnosti a přidat volitelné rozhraní.  
  
 Základní kroky jsou následující:  
  
1.  Můžete vytvořit soubor základního projektu a ATL OLE DB poskytovatele průvodce vytvořit zprostředkovatele Průvodce projektem ATL (vyberte **ATL OLE DB Provider** ze složky Visual C++ v **přidat třídu**).  
  
2.  Změňte kód v `Execute` metoda v CMyProviderRS.h. Příklad najdete v tématu [čtení řetězce do zprostředkovatele OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Mapy vlastností v souboru MyProviderDS.h souboru MyProviderSess.h a MyProviderRS.h upravte. Průvodce vytvoří mapy vlastností, které obsahují všechny vlastnosti, které poskytovatel může implementovat. Projděte si mapy vlastností a odeberte nebo Odkomentujte vlastnosti, které není potřeba poskytovatele podpory.  
  
4.  Aktualizujte Provider Column Map, který se nachází v souboru MyProviderRS.h. Příklad najdete v tématu [ukládání řetězců v OLE DB Provider](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Až budete připravení k testování zprostředkovatele, takže ji můžete otestovat tak, že zkusíte najít poskytovatele ve výčtu zprostředkovatele. Příklady testovací kód, který najde poskytovatele ve výčtu, najdete v článku [CATDB](http://msdn.microsoft.com/003d516b-2bf6-444e-8be5-4ebaa0b66046) a [DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) ukázky nebo v příkladu v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Všechna další rozhraní, které chcete přidáte. Příklad najdete v tématu [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  Ve výchozím nastavení průvodci generovat kód, který je technologie OLE DB úrovně 0 kompatibilní. Aby bylo zajištěno, že vaše aplikace zůstává na úrovni 0 kompatibilní, neodstraňujte žádné rozhraní generované v Průvodci z kódu.  
  
## <a name="see-also"></a>Viz také  
 [CATDB](http://msdn.microsoft.com/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832)