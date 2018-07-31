---
title: Získávání metadat pomocí sad řádků schématu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9d86984dc67dd5cbea6fe52ff1c8b099e5b061f5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337187"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Získávání metadat pomocí sad řádků schématu
Někdy potřebujete získat informace o poskytovateli, sady řádků, tabulky, sloupce nebo jiné informace o databázi bez nutnosti otevřít v sadě řádků. Data o struktuře databáze s názvem metadat a je možné načíst podle několika způsoby. Jedním ze způsobů je použít sad řádků schématu.  
  
 Šablony technologie OLE DB poskytují sadu tříd pro načtení informací o schématu; Tyto třídy vytvoří předdefinované sady řádků schématu a jsou uvedeny v [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
> [!NOTE]
>  Pokud používáte OLAP a některé z vašich sady řádků nejsou podporovány třídy sady řádků schématu (například můžete mít proměnný počet sloupců), měli byste zvážit použití `CManualAccessor` nebo `CDynamicAccessor`. Můžete procházet sloupci a používat příkazy case zpracovat všechny možné datové typy pro každý sloupec.  
  
## <a name="catalogschema-model"></a>Model katalogu nebo schématu  
 ANSI SQL definuje model katalogu nebo schématu pro úložiště dat; Tento model používá technologie OLE DB. V tomto modelu katalogy (databáze) obsahují schémata a schémata obsahují tabulky.  
  
-   **Katalog** katalog je jiný název databáze. Jde o kolekci souvisejících schémat. K zobrazení seznamu katalogy (databáze), které patří do daného zdroje dat, použijte [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Protože velký počet databází mít pouze jeden katalog, metadata v některých případech lze volat informace o schématu.  
  
-   **Schéma** schéma je kolekce databázové objekty, které jsou ve vlastnictví nebo vytvořili konkrétní uživatel. K zobrazení seznamu schémat vlastníkem daného uživatele, použijte [CSchemata](../../data/oledb/cschemata-cschematainfo.md).  
  
     V systému Microsoft SQL Server a rozhraní ODBC 2.x podmínky, schéma je vlastníkem (třeba dbo je typické schemaname). Také ukládá metadata sadu tabulek systému SQL Server: jedna tabulka obsahuje seznam všech tabulek a jiná tabulka obsahuje seznam všech sloupců. Neexistuje žádný ekvivalent k schématu v databázi Microsoft Access.  
  
-   **Tabulka** tabulky jsou kolekce sloupců uspořádané do konkrétní objednávky. K zobrazení seznamu tabulek definovaných v daném katalogu (databáze) a informace o těchto tabulkách použijte [CTables](../../data/oledb/ctables-ctableinfo.md)).  
  
## <a name="restrictions"></a>Omezení  
 Když odešlete dotaz na informace o schématu, můžete použít omezení k určení typu informací, které vás zajímají. Omezení jako kvalifikátoru v dotazu nebo filtru si můžete představit. Například v dotazu:  
  
```sql  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` je omezení. To je velmi jednoduchý příklad s pouze jedno omezení; třídy sady řádků schématu podporovat několik omezení.  
  
 [Definice typu třídy sady řádků schématu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) zapouzdření všechny sady řádků schématu technologie OLE DB tak, aby sada řádků schématu stejně jako ostatní sady řádků se zpřístupní po vytvoření instance a jeho otevřením. Například třída definice typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) je definován jako:  
  
```cpp  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md) poskytuje podporu omezení třídy. Po vytvoření instance sady řádků schématu volat [CRestrictions::Open](../../data/oledb/crestrictions-open.md). Tato metoda vrátí sadu výsledků dotazu na základě omezení, které zadáte.  
  
 Chcete-li zadat omezení, přečtěte si [sad řádků schématu příloha B:](http://go.microsoft.com/fwlink/p/?linkid=64681) a vyhledání řádků, který používáte. Například `CColumns` odpovídá [sady řádků sloupců](http://go.microsoft.com/fwlink/p/?linkid=64682); Toto téma obsahuje seznam sloupců omezení v sadě řádků sloupců: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME. Je třeba dodržet toto pořadí v zadání vašeho omezení.  
  
 Tak, například pokud chcete omezit tím, že název tabulky, mějte na paměti, že je TABLE_NAME třetí sloupec omezení a poté zavolejte `Open`, zadáním požadovaného názvu tabulky jako třetí parametr omezení, jak je znázorněno v následujícím příkladu.  
  
#### <a name="to-use-schema-rowsets"></a>Použití sad řádků schématu  
  
1.  Je nutné zahrnout soubor hlaviček Atldbsch.h (samozřejmě budete potřebovat také Atldbcli.h pro podporu příjemce).  
  
2.  Vytvoření instance objektu sady řádků schématu v paměti spotřebitele nebo dokumentu soubor hlaviček. Pokud chcete informace o tabulce, deklarujte `CTables` objektu; Pokud chcete informace o sloupci, deklarujte `CColumns` objektu. Tento příklad ukazuje, jak načíst sloupce v tabulce Autoři:  
  
    ```cpp  
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
  
3.  Chcete-li načíst informace, například přístup k příslušnému datovému členu objektu sady řádků schématu `ColumnSchemaRowset.m_szColumnName`. To odpovídá COLUMN_NAME. Každý datový člen odpovídá sloupec technologie OLE DB najdete v tématu [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).  
  
 Pro odkaz na sadu řádků schématu definiční třídy typů součástí šablony technologie OLE DB (viz [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).  
  
 Další informace o sad řádků schématu technologie OLE DB, včetně sloupců omezení, najdete v části [sad řádků schématu příloha B:](http://go.microsoft.com/fwlink/p/?linkid=64681) v OLE DB programátora odkazu.  
  
 Složitější příklady toho, jak pomocí třídy sady řádků schématu, najdete v článku [CatDB](http://msdn.microsoft.com/003d516b-2bf6-444e-8be5-4ebaa0b66046) a [DBViewer](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) ukázky.  
  
 Informace týkající se podpory zprostředkovatele sady řádků schématu najdete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)