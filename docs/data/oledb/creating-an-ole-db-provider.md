---
title: Vytvoření zprostředkovatele OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: b6e59dba375e78878d13a6014ce75edf2a21758b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611195"
---
# <a name="creating-an-ole-db-provider"></a>Vytvoření zprostředkovatele OLE DB

Doporučeným způsobem vytvoření zprostředkovatele OLE DB je pomocí průvodců vytvořte projekt knihovny ATL modelu COM a zprostředkovatele a potom upravte soubory pomocí šablony technologie OLE DB. Při úpravách poskytovatele, můžete Zakomentovat nežádoucí vlastnosti a přidat volitelné rozhraní.

Základní kroky jsou následující:

1. Použití **Průvodce projektem ATL** vytvořit soubor základního projektu a **Průvodce zprostředkovatelem ATL OLEDB** vytvořit zprostředkovatele (vyberte **zprostředkovatele služeb OLEDB knihovny ATL** z **Nainstalováno** > **Visual C++** > **ATL** složky **přidat novou položku**).

   > [!NOTE]
   > Projekt musí obsahovat podporu knihovny MFC před přidáním **zprostředkovatele služeb OLEDB knihovny ATL**.

1. Změňte kód v `Execute` metoda [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Příklad najdete v tématu [čtení řetězce do zprostředkovatele OLE DB](../../data/oledb/reading-strings-into-the-ole-db-provider.md).

1. Upravit vlastnost mapy v [CustomDS.h](cmyprovidersource-myproviderds-h.md), [CustomSess.h](cmyprovidersession-myprovidersess-h.md), a [CustomRS.h](cmyproviderrowset-myproviderrs-h.md). Průvodce vytvoří mapy vlastností, které obsahují všechny vlastnosti, které poskytovatel může implementovat. Projděte si mapy vlastností a odeberte nebo Odkomentujte vlastnosti, které není potřeba poskytovatele podpory.

1. Aktualizovat Provider Column Map, který se nachází v [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md). Příklad najdete v tématu [ukládání řetězců v OLE DB Provider](../../data/oledb/storing-strings-in-the-ole-db-provider.md).

1. Až budete připravení k testování zprostředkovatele, takže ji můžete otestovat tak, že zkusíte najít poskytovatele ve výčtu zprostředkovatele. Příklady testovací kód, který najde poskytovatele ve výčtu, najdete v článku [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb) a [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) ukázky nebo v příkladu v [Implementace jednoduchého příjemce](../../data/oledb/implementing-a-simple-consumer.md).

1. Všechna další rozhraní, které chcete přidáte. Příklad najdete v tématu [rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md).

   > [!NOTE]
   > Ve výchozím nastavení průvodci generovat kód, který je technologie OLE DB úrovně 0 kompatibilní. Aby bylo zajištěno, že vaše aplikace zůstává na úrovni 0 kompatibilní, neodstraňujte žádné rozhraní generované v Průvodci z kódu.

## <a name="see-also"></a>Viz také

[Ukázka CatDB: Prohlížeč schématu zdroje dat](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[Ukázka DBViewer: Databáze prohlížeče](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
