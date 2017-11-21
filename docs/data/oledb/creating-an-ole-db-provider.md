---
title: "Vytvoření zprostředkovatele OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 07060be0c14adb4d509c23ab88914de4494e6862
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [UKÁZKY CATDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046)   
 [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)