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
ms.openlocfilehash: 16d78d590201ea637dd6153edb40a1c6d89a82c0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210338"
---
# <a name="creating-an-ole-db-provider"></a>Vytvoření zprostředkovatele OLE DB
Doporučeným způsobem vytvoření zprostředkovatele OLE DB je pomocí průvodců vytvořte projekt knihovny ATL modelu COM a zprostředkovatele a potom upravte soubory pomocí šablony technologie OLE DB. Při úpravách poskytovatele, můžete Zakomentovat nežádoucí vlastnosti a přidat volitelné rozhraní.  
  
 Základní kroky jsou následující:  
  
1.  Můžete vytvořit soubor základního projektu a ATL OLE DB poskytovatele průvodce vytvořit zprostředkovatele Průvodce projektem ATL (vyberte **ATL OLE DB Provider** ze složky Visual C++ v **přidat třídu**).  
  
2.  Změňte kód v `Execute` metoda v CMyProviderRS.h. Příklad najdete v tématu [čtení řetězce do zprostředkovatele OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Mapy vlastností v souboru MyProviderDS.h souboru MyProviderSess.h a MyProviderRS.h upravte. Průvodce vytvoří mapy vlastností, které obsahují všechny vlastnosti, které poskytovatel může implementovat. Projděte si mapy vlastností a odeberte nebo Odkomentujte vlastnosti, které není potřeba poskytovatele podpory.  
  
4.  Aktualizujte Provider Column Map, který se nachází v souboru MyProviderRS.h. Příklad najdete v tématu [ukládání řetězců v OLE DB Provider](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Až budete připravení k testování zprostředkovatele, takže ji můžete otestovat tak, že zkusíte najít poskytovatele ve výčtu zprostředkovatele. Příklady testovací kód, který najde poskytovatele ve výčtu, najdete v článku [CATDB](https://github.com/Microsoft/VCSamples) a [DBVIEWER](https://github.com/Microsoft/VCSamples) ukázky nebo v příkladu v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Všechna další rozhraní, které chcete přidáte. Příklad najdete v tématu [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  Ve výchozím nastavení průvodci generovat kód, který je technologie OLE DB úrovně 0 kompatibilní. Aby bylo zajištěno, že vaše aplikace zůstává na úrovni 0 kompatibilní, neodstraňujte žádné rozhraní generované v Průvodci z kódu.  
  
## <a name="see-also"></a>Viz také  
 [CATDB](https://github.com/Microsoft/VCSamples)   
 [DBVIEWER](https://github.com/Microsoft/VCSamples)