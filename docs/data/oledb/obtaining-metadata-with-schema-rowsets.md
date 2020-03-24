---
title: Získávání metadat pomocí sad řádků schématu
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: e04b9a335c60cefdc28be2347ef1f0762c424d8e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210129"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Získávání metadat pomocí sad řádků schématu

Někdy potřebujete získat informace o poskytovateli, sadě řádků, tabulce, sloupcích nebo jiných informacích o databázi, aniž byste museli otevřít sadu řádků. Data o struktuře databáze se nazývají metadata a lze je načíst řadou různých metod. Jednou z metod je použití sad řádků schématu.

Šablony OLE DB poskytují sadu tříd pro načtení informací o schématu; Tyto třídy vytvoří předdefinované sady řádků schématu a jsou uvedeny v seznamu [třídy sady řádků schématu a třídy typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Pokud používáte OLAP a některé sady řádků nejsou podporovány třídami sady řádků schématu (například máte proměnlivý počet sloupců), měli byste zvážit použití `CManualAccessor` nebo `CDynamicAccessor`. Můžete procházet sloupci a použít příkazy Case pro zpracování možných datových typů pro každý sloupec.

## <a name="catalogschema-model"></a>Model katalogu/schématu

ANSI SQL definuje model katalogu/schématu pro úložiště dat; OLE DB používá tento model. V tomto modelu mají katalogy (databáze) schémata a schémata tabulky.

- **Katalog** Katalog je jiný název databáze. Jedná se o kolekci souvisejících schémat. Chcete-li zobrazit seznam katalogů (databází) patřících k danému zdroji dat, použijte [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Vzhledem k tomu, že mnoho databází má pouze jeden katalog, metadata se někdy označují jako informace o schématu.

- **Schéma** Schéma je kolekce databázových objektů, které jsou vlastněny nebo byly vytvořeny konkrétním uživatelem. Chcete-li zobrazit seznam schémat vlastněných daným uživatelem, použijte [CSchemata](../../data/oledb/cschemata-cschematainfo.md).

   V rámci podmínek Microsoft SQL Server a ODBC 2. x je schéma vlastníkem (například dbo je typický název schématu). SQL Server také ukládá metadata v sadě tabulek: jedna tabulka obsahuje seznam všech tabulek a další tabulka obsahuje seznam všech sloupců. V databázi aplikace Microsoft Access není ekvivalent schématu.

- **Tabulka** Tabulky jsou kolekce sloupců uspořádané do konkrétních objednávek. K vypsání tabulek definovaných v daném katalogu (databáze) a informací o těchto tabulkách použijte [CTable](../../data/oledb/ctables-ctableinfo.md).

## <a name="restrictions"></a>Omezení

Při dotazování na informace o schématu můžete pomocí omezení určit typ informací, které vás zajímají. Omezení můžete v dotazu představit jako filtr nebo kvalifikátor. Například v dotazu:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` je omezení. Toto je jednoduchý příklad s pouze jedním omezením; třídy sady řádků schématu podporují několik omezení.

[Třídy typedef sady řádků schématu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) zapouzdřují všechny sady řádků schématu OLE DB tak, abyste měli přístup k sadě řádků schématu stejně jako všechny jiné sady řádků, a to vytvořením instance a jejím otevřením. Například třída typedef třídy [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) je definována jako:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

Třída [CRestrictions –](../../data/oledb/crestrictions-class.md) poskytuje podporu omezení. Po vytvoření instance sady řádků schématu zavolejte [CRestrictions –:: Open](../../data/oledb/crestrictions-open.md). Tato metoda vrací sadu výsledků na základě omezení, která zadáte.

Chcete-li zadat omezení, přečtěte si [Dodatek B: sady řádků schématu](/previous-versions/windows/desktop/ms712921(v=vs.85)) a vyhledejte sadu řádků, kterou používáte. Například `CColumns` odpovídá [sadě řádků Columns](/previous-versions/windows/desktop/ms723052(v=vs.85)); Toto téma obsahuje sloupce omezení v sadě řádků COLUMNs: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME COLUMN_NAME. Musíte postupovat podle tohoto pořadí při určování vašich omezení.

Pokud například chcete omezit podle názvu tabulky, TABLE_NAME je třetí sloupec omezení a potom zavolejte `Open`a jako třetí parametr omezení zadejte požadovaný název tabulky, jak je znázorněno v následujícím příkladu.

### <a name="to-use-schema-rowsets"></a>Použití sad řádků schématu

1. Zahrňte do souboru hlaviček `Atldbsch.h` (budete potřebovat `Atldbcli.h` i pro podporu zákazníků).

1. Vytvořte instanci objektu sady řádků schématu v souboru hlaviček příjemce nebo dokumentu. Pokud chcete informace o tabulce, deklarujte objekt `CTables`; Pokud chcete informace o sloupci, deklarujte objekt `CColumns`. Tento příklad ukazuje, jak načíst sloupce v tabulce Autoři:

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

1. Chcete-li načíst informace, přístup k příslušnému datovému členu objektu sady řádků schématu, například `ColumnSchemaRowset.m_szColumnName`. Tento datový člen odpovídá COLUMN_NAME. Chcete-li zjistit, který OLE DB sloupec každý datový člen odpovídá, přečtěte si téma [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).

Pro referenci na sadu řádků schématu, třídy typedef poskytované v šablonách OLE DB (viz [třídy sady řádků schématu a třídy typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Další informace o OLE DB schémat sad řádků, včetně sloupců omezení, naleznete v [příloze B: sady řádků schématu](/previous-versions/windows/desktop/ms712921(v=vs.85)) v **Referenční příručce programátora OLE DB**.

Složitější příklady použití tříd sady řádků schématu naleznete v ukázkách [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) a [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

Informace o podpoře poskytovatele pro sady řádků schématu naleznete v tématu [podpůrné sady řádků schématu](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
