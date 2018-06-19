---
title: Vytvoření zprostředkovatele OLE DB | Microsoft Docs
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
ms.openlocfilehash: f649b5b4c79c4148d0aed026b044485ca2b1eaa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097104"
---
# <a name="creating-an-ole-db-provider"></a>Vytvoření zprostředkovatele OLE DB
Doporučený způsob vytvoření zprostředkovatele OLE DB je použít Průvodce pro vytvoření projektu knihovny ATL COM a zprostředkovatele a potom upravte soubory pomocí šablony technologie OLE DB. Jako nastavení vlastního zprostředkovatele, můžete Zakomentovat nežádoucí vlastnosti a přidat volitelné rozhraní.  
  
 Základní kroky jsou následující:  
  
1.  Průvodce projektem ATL použít k vytvoření základních souborů projektu a ATL průvodce OLE DB Provider pro vytvoření zprostředkovatele (vyberte **ATL zprostředkovatele technologie OLE DB** ze složky Visual C++ v **přidat třídu**).  
  
2.  Změňte kód v `Execute` metoda v CMyProviderRS.h. Příklad, naleznete v části [čtení řetězců do zprostředkovatele OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).  
  
3.  Mapy vlastností v souboru MyProviderDS.h, MyProviderSess.h a MyProviderRS.h upravte. Průvodce vytvoří mapy vlastností, které obsahují všechny vlastnosti, které může implementovat zprostředkovatele. Projít mapy vlastností a odeberte nebo komentář vlastnosti, které váš poskytovatel nemusí podporovat.  
  
4.  Aktualizujte Provider Column Map, který naleznete v souboru MyProviderRS.h. Příklad, naleznete v části [ukládání řetězců v OLE DB poskytovatel](../../data/oledb/storing-strings-in-the-ole-db-provider.md).  
  
5.  Jakmile budete připraveni k testování zprostředkovatele, můžete ji otestovat tak, že zkusíte se najít poskytovatele ve výčtu zprostředkovatele. Příklady testovací kód, který najde poskytovatele v výčet najdete v tématu [ukázky CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046) a [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ukázky nebo příklad v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).  
  
6.  Taková rozhraní, které chcete přidáte. Příklad, naleznete v části [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
    > [!NOTE]
    >  Ve výchozím nastavení průvodců generovat kód, který je technologie OLE DB úrovně 0 kompatibilní. Aby se zajistilo, že vaše aplikace zůstává na úrovni 0 kompatibilní, neodebírejte žádné rozhraní vygenerované průvodcem z kódu.  
  
## <a name="see-also"></a>Viz také  
 [CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)