---
title: "Získávání metadat pomocí sad řádků schématu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a2a57fd92183c60e245ecdd1ba237da74c9e575b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Získávání metadat pomocí sad řádků schématu
V některých případech budete muset získat informace o zprostředkovateli, řádků, tabulky, sloupce nebo Další informace o databázi bez otevření sady řádků. Data o struktuře databáze se nazývá metadata a můžete si ho načíst několik různých metod. Jednou z možností je použití sad řádků schématu.  
  
 Šablony OLE DB poskytují sadu tříd pro načtení informací o schématu; Tyto třídy vytvoří předdefinované sady řádků schématu a jsou uvedeny v [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
> [!NOTE]
>  Pokud používáte OLAP a některé vaší sady řádků nejsou podporovány třídy sady řádků schématu (například máte proměnný počet sloupců), měli byste zvážit použití `CManualAccessor` nebo `CDynamicAccessor`. Můžete procházet sloupci a pomocí příkazu case zpracovávat všechny možné datové typy pro každý sloupec.  
  
## <a name="catalogschema-model"></a>Model katalogu nebo schématu  
 ANSI SQL definuje model katalogu nebo schématu pro úložiště dat; Tento model používá technologie OLE DB. V tomto modelu katalogy (databáze) obsahují schémata a schémata obsahují tabulky.  
  
-   **Katalog** katalog je jiný název databáze. Je kolekce souvisejících schémat. K zobrazení seznamu katalogy (databáze), které patří ke zdroji dat, použijte [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Protože mnoho databází má pouze jeden katalog, metadata někdy jednoduše nazývá informace o schématu.  
  
-   **Schéma** schéma je kolekce databázové objekty, které jsou ve vlastnictví nebo byly vytvořeny konkrétním uživatelem. K zobrazení seznamu schémata vlastníkem daného uživatele, použijte [CSchemata](../../data/oledb/cschemata-cschematainfo.md).  
  
     V systému Microsoft SQL Server a rozhraní ODBC 2.x podmínky, schéma je vlastníkem (například dbo je název typické schématu). Také ukládá metadata v sadu tabulek systému SQL Server: jedna tabulka obsahuje seznam všech tabulek a jiná tabulka obsahuje seznam všech sloupců. Není žádný ekvivalent schéma v databázi Microsoft Access.  
  
-   **Tabulka** tabulky jsou kolekce sloupců uspořádány v určitých pořadích. K zobrazení seznamu tabulek definovaných v daném katalogu (databáze) a informace o těchto tabulkách použijte [CTables](../../data/oledb/ctables-ctableinfo.md)).  
  
## <a name="restrictions"></a>Omezení  
 Při dotazu na informace schématu, můžete určit typ informací, která vás zajímá omezení. Si můžete představit omezení jako filtr nebo kvalifikátor v dotazu. Například v dotazu:  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name`je však omezení. To je velmi jednoduchý příklad s pouze jedním z omezení; třídy sady řádků schématu podporují několik omezení.  
  
 [Typedef třídy sady řádků schématu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) zapouzdřují všechny sady řádků schématu OLE DB, abyste vytváření instancí a otevřením dostanete sada řádků schématu stejně jako ostatní sady řádků. Například třída typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) je definován jako:  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md) třída poskytuje podporu omezení. Po vytvoření instance sady řádků schématu volat [CRestrictions::Open](../../data/oledb/crestrictions-open.md). Tato metoda vrátí sadu výsledků na základě omezení, které zadáte.  
  
 Zadat omezení, najdete v tématu [sad řádků schématu příloha B:](http://go.microsoft.com/fwlink/?linkid=64681) a vyhledání řádků, který používáte. Například **CColumns** odpovídá [řádků sloupců](http://go.microsoft.com/fwlink/?linkid=64682); Toto téma uvádí omezení sloupce v dané sadě řádků sloupců: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME. Postupujte podle tohoto pořadí v určování vašich omezení.  
  
 Ano, například pokud chcete omezit tak, že název tabulky, Všimněte si, že TABLE_NAME je třetí sloupec omezení a pak zavolají **otevřete**, zadáte název požadované tabulky jako třetí parametr omezení, jak je znázorněno v následujícím příkladu.  
  
#### <a name="to-use-schema-rowsets"></a>Použití sady řádků schématu  
  
1.  Musíte zahrnout soubor hlaviček Atldbsch.h (samozřejmě, potřebujete také Atldbcli.h pro podporu příjemce).  
  
2.  Vytvoření instance objektu sady řádků schématu v příjemce nebo dokumentu soubor hlaviček. Pokud chcete informace o tabulce, deklarovat **CTables** objektu; Pokud chcete informace o sloupci, deklarovat **CColumns** objektu. Tento příklad ukazuje, jak načíst sloupců v tabulce Autoři:  
  
    ```  
    CDataSource ds;  
    ds.Open();  
    CSession ss;  
    ss.Open();  
    CColumns ColumnSchemaRowset;  
    // TABLE_NAME is the third restriction column, so  
    // specify "authors" as the third restriction parameter:  
    hr = ColumnSchemaRowset.Open(ss, NULL, NULL, "authors");  
    hr = ColumnSchemaRowset.MoveFirst();  
    while (hr == S_OK)  
    {  
       hr = ColumnSchemaRowset.MoveNext();  
    }  
    ```  
  
3.  Chcete-li načíst informace, například přístup k členovi příslušná data objektu sady řádků schématu `ColumnSchemaRowset.m_szColumnName`. To odpovídá COLUMN_NAME. Každý člen dat odpovídá sloupce OLE DB, najdete v sekci [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).  
  
 Pro odkaz na sadu řádků schématu definiční třídy typů součástí šablony technologie OLE DB (viz [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).  
  
 Další informace o sad řádků schématu OLE DB, včetně sloupců omezení, najdete v části [sad řádků schématu příloha B:](http://go.microsoft.com/fwlink/?linkid=64681) v OLE DB referenční informace pro programátory.  
  
 Složitější příklady použití třídy sady řádků schématu najdete v tématu [ukázky CatDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046) a [DBViewer](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ukázky.  
  
 Informace o Podpora zprostředkovatele pro sady řádků schématu najdete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)