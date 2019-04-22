---
title: Získávání metadat pomocí sad řádků schématu
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 12c3de79626411b76a402a7f5407f40a7b054318
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026000"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Získávání metadat pomocí sad řádků schématu

Někdy potřebujete získat informace o poskytovateli, sady řádků, tabulky, sloupce nebo jiné informace o databázi bez nutnosti otevřít v sadě řádků. Data o struktuře databáze s názvem metadat a je možné načíst podle několika způsoby. Jedním ze způsobů je použít sad řádků schématu.

Šablony technologie OLE DB poskytují sadu tříd pro načtení informací o schématu; Tyto třídy vytvoří předdefinované sady řádků schématu a jsou uvedeny v [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Pokud používáte OLAP a některé z vašich sady řádků nejsou podporovány třídy sady řádků schématu (například můžete mít proměnný počet sloupců), měli byste zvážit použití `CManualAccessor` nebo `CDynamicAccessor`. Můžete procházet sloupci a používat příkazy case zpracovat všechny možné datové typy pro každý sloupec.

## <a name="catalogschema-model"></a>Model katalogu nebo schématu

ANSI SQL definuje model katalogu nebo schématu pro úložiště dat; Tento model používá technologie OLE DB. V tomto modelu katalogy (databáze) mají schémata a schémata mají tabulek.

- **Katalog** katalog je jiný název databáze. Jde o kolekci souvisejících schémat. K zobrazení seznamu katalogy (databáze), které patří do daného zdroje dat, použijte [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Protože velký počet databází mít pouze jeden katalog, metadata se někdy označuje jako informace o schématu.

- **Schéma** schéma je kolekce databázové objekty, které jsou ve vlastnictví nebo vytvořili konkrétní uživatel. K zobrazení seznamu schémat vlastníkem daného uživatele, použijte [CSchemata](../../data/oledb/cschemata-cschematainfo.md).

   V systému Microsoft SQL Server a rozhraní ODBC 2.x podmínky, schéma je vlastníkem (třeba dbo je typické schemaname). Také ukládá metadata sadu tabulek systému SQL Server: jedna tabulka obsahuje seznam všech tabulek a jiná tabulka obsahuje seznam všech sloupců. Neexistuje žádný ekvivalent k schématu v databázi Microsoft Access.

- **Tabulka** tabulky jsou kolekce sloupců uspořádané do konkrétní objednávky. K zobrazení seznamu tabulek definovaných v daném katalogu (databáze) a informace o těchto tabulkách použijte [CTables](../../data/oledb/ctables-ctableinfo.md)).

## <a name="restrictions"></a>Omezení

Když odešlete dotaz na informace o schématu, můžete použít omezení k určení typu informací, které vás zajímá. Omezení jako kvalifikátoru v dotazu nebo filtru si můžete představit. Například v dotazu:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` je omezení. Toto je jednoduchý příklad s pouze jedno omezení; třídy sady řádků schématu podporovat několik omezení.

[Definice typu třídy sady řádků schématu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) zapouzdření všechny sady řádků schématu technologie OLE DB tak, aby sada řádků schématu stejně jako ostatní sady řádků se zpřístupní po vytvoření instance a jeho otevřením. Například třída definice typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) je definován jako:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md) poskytuje podporu omezení třídy. Po vytvoření instance sady řádků schématu volat [CRestrictions::Open](../../data/oledb/crestrictions-open.md). Tato metoda vrátí sadu výsledků dotazu na základě omezení, které zadáte.

Chcete-li zadat omezení, přečtěte si [příloha B: Sady řádků schématu](/previous-versions/windows/desktop/ms712921(v=vs.85)) a vyhledání řádků, které používáte. Například `CColumns` odpovídá [sady řádků sloupců](/previous-versions/windows/desktop/ms723052(v=vs.85)); Toto téma obsahuje seznam sloupců omezení v sadě řádků %{Rowset/ sloupce: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME. Je třeba dodržet toto pořadí v zadání vašeho omezení.

Ano, pokud chcete omezit tím, že název tabulky, TABLE_NAME je například třetí sloupec omezení a poté zavolejte `Open`, zadáte název požadované tabulky jako třetí parametr omezení, jak je znázorněno v následujícím příkladu.

### <a name="to-use-schema-rowsets"></a>Použití sad řádků schématu

1. Zahrnutím souboru hlaviček `Atldbsch.h` (budete potřebovat `Atldbcli.h` pro podporu příjemce).

1. Vytvoření instance objektu sady řádků schématu v paměti spotřebitele nebo dokumentu soubor hlaviček. Pokud chcete informace o tabulce, deklarujte `CTables` objektu; Pokud chcete informace o sloupci, deklarujte `CColumns` objektu. Tento příklad ukazuje, jak načíst sloupce v tabulce Autoři:

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. Chcete-li načíst informace, například přístup k příslušnému datovému členu objektu sady řádků schématu `ColumnSchemaRowset.m_szColumnName`. COLUMN_NAME odpovídá tomuto datovému členu. Každý datový člen odpovídá sloupec technologie OLE DB najdete v tématu [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).

Pro odkaz na sadu řádků schématu definiční třídy typů součástí šablony technologie OLE DB (viz [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Další informace o sad řádků schématu technologie OLE DB, včetně sloupců omezení, najdete v části [příloha B: Sady řádků schématu](/previous-versions/windows/desktop/ms712921(v=vs.85)) v **referenční informace pro OLE DB programátory**.

Složitější příklady toho, jak pomocí třídy sady řádků schématu, najdete v článku [CatDB](https://github.com/Microsoft/VCSamples) a [DBViewer](https://github.com/Microsoft/VCSamples) ukázky.

Informace týkající se podpory zprostředkovatele sady řádků schématu najdete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)