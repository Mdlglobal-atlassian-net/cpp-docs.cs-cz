---
title: Aktualizace sad řádků
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
ms.openlocfilehash: e0ee5cf97170cd9293abcb9039771f8fe23962aa
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525305"
---
# <a name="updating-rowsets"></a>Aktualizace sad řádků

Operace databáze basic je aktualizovat, nebo zápis dat do úložiště dat. V OLE DB, je jednoduchý mechanismus aktualizace: aplikace příjemce nastaví hodnoty vázaných dat členů a pak zapíše hodnoty do sady řádků; Příjemce potom, aktualizujte poskytovatele úložiště dat požadavky.

Uživatelé dokončit následující typy aktualizací na sadu řádků dat: nastavení hodnot sloupce v řádku, řádku vkládání a odstraňování řádku. K dokončení těchto operací třídu šablony technologie OLE DB [CRowset](../../data/oledb/crowset-class.md) implementuje [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) rozhraní a přepíše metody následující rozhraní:

- [Operaci SetData](../../data/oledb/crowset-setdata.md) hodnoty pro sloupce změny za sebou sady řádků; to odpovídá příkazu SQL UPDATE.

- [Vložit](../../data/oledb/crowset-insert.md) vloží řádek do sady řádků; to odpovídá příkazu INSERT jazyka SQL.

- [Odstranit](../../data/oledb/crowset-delete.md) odstraní řádky ze sady řádků; to odpovídá příkazu SQL DELETE.

## <a name="supporting-update-operations"></a>Podpora operací aktualizace

> [!NOTE]
> Průvodce spotřebitele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším. Funkce můžete přesto přidat ručně. Další informace najdete v tématu [vytvoření příjemce bez použití průvodce](creating-a-consumer-without-using-a-wizard.md).

Při vytváření příjemce s **průvodce příjemcem ATL OLE DB**, může podporovat operace aktualizace tak, že vyberete jeden nebo více ze tří zaškrtávacích políček **změnu**, **vložit**, a **odstranit**. Pokud vyberete tyto možnosti, Průvodce upravuje kód odpovídajícím způsobem pro podporu typ změny, které zvolíte. Nicméně pokud nepoužíváte průvodce, je nutné nastavit následující vlastnosti sady řádků `VARIANT_TRUE` podporovat aktualizace:

- `DBPROPVAL_UP_CHANGE` Umožňuje změnit hodnoty data v řádku.

- `DBPROPVAL_UP_INSERT` Umožňuje vložit řádek.

- `DBPROPVAL_UP_DELETE` Umožňuje odstranit řádek.

Nastavte vlastnosti následujícím způsobem:

```cpp
CDBPropSet ps(DBPROPSET_ROWSET);

ps.AddProperty(DBPROP_IRowsetChange, true);
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
```

Změna, insert nebo delete operace nemusí podařit, pokud jeden nebo více sloupců není zapisovatelný. Upravte mapu kurzor k vyřešení tohoto problému.

## <a name="setting-data-in-rows"></a>Nastavení Data v řádcích

[CRowset::SetData](../../data/oledb/crowset-setdata.md) nastaví hodnoty dat do jednoho nebo více sloupců na aktuálním řádku. Následující kód nastaví hodnoty datových členů, které jsou svázány se sloupci `Name` a `Units in Stock` tabulky `Products` a pak zavolá `SetData` zapsat hodnoty do 100th řádku v sadě řádků:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_UnitsInStock = 10000;

// Set the data
HRESULT hr = product.SetData();
```

## <a name="inserting-rows-into-rowsets"></a>Vkládání řádků do sady řádků

[CRowset::Insert](../../data/oledb/crowset-insert.md) vytvoří a inicializuje nový řádek pomocí dat z přistupujícího objektu. `Insert` vytvoří zcela nový řádek po řádku aktuální; je třeba zadat, jestli se má zvýšit aktuální řádek do dalšího řádku nebo ponechat jej beze změny. To provedete tak, že nastavíte *bGetRow* parametr:

```cpp
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)
```

- **false** (výchozí hodnota) určuje, že aktuální řádek zvýší na další řádek (v takovém případě odkazuje na vloženého řádku).

- **Hodnota TRUE** Určuje, že aktuální řádek zůstat tam, kde je.

Následující kód nastaví hodnoty datových členů, které jsou vázané na sloupce v tabulce `Products` a pak zavolá `Insert` vložte nový řádek s těmito hodnotami po 100th řádku v sadě řádků. Doporučuje se, že nastavíte všechny hodnoty sloupců nepoužíváte Nedefinovaná data na novém řádku:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Set the column values for a row of the Product table, then insert the row
product.m_ProductID = 101;
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) );

product.m_SupplierID = 27857;
product.m_CategoryID = 372;
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) );

product.m_UnitPrice = 20;
product.m_UnitsInStock = 10000;
product.m_UnitsOnOrder = 5201;
product.m_ReorderLevel = 5000;
product.m_Discontinued = false;

// You must also initialize the status and length fields before setting/inserting data
// Set the column status values
m_dwProductIDStatus = DBSTATUS_S_OK;
m_dwProductNameStatus = DBSTATUS_S_OK;
m_dwSupplierIDStatus = DBSTATUS_S_OK;
m_dwCategoryIDStatus = DBSTATUS_S_OK;
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;
m_dwUnitPriceStatus = DBSTATUS_S_OK;
m_dwUnitsInStockStatus = DBSTATUS_S_OK;
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;
m_dwReorderLevelStatus = DBSTATUS_S_OK;
m_dwDiscontinuedStatus = DBSTATUS_S_OK;

// Set the column length value for column data members that are not fixed-length types.
// The value should be the length of the string that you are setting.
m_dwProductNameLength = 6;             // "Candle" has 6 characters
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters

// Insert the data
HRESULT hr = product.Insert();
```

Podrobnější příklad naleznete v tématu [CRowset::Insert](../../data/oledb/crowset-insert.md).

Další informace o nastavení datové členy stavu a délky, naleznete v tématu [Datoví členové stavu pole v přístupových objektech generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

## <a name="deleting-rows-from-rowsets"></a>Odstranění řádků ze sady řádků

[CRowset::Delete](../../data/oledb/crowset-delete.md) odstraní aktuální řádek ze sady řádků. Následující kód volá `Delete` odebrat 100th řádku v sadě řádků:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Delete the row
HRESULT hr = product.Delete();
```

## <a name="immediate-and-deferred-updates"></a>Odložené a okamžité aktualizace

Pokud neurčíte jinak, volání `SetData`, `Insert`, a `Delete` metody aktualizujte úložiště dat okamžitě. Lze však odložit aktualizace tak, aby příjemce ukládá všechny změny v místní mezipaměti a převede je do úložiště dat při volání jedné z následujících metod aktualizace:

- [CRowset::Update](../../data/oledb/crowset-update.md) převede všechny neuložené změny provedené na aktuálním řádku od posledního načtení nebo `Update` zavolat.

- [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) všechny čekající změny provedené od posledního načtení všech řádků přenese nebo `Update` zavolat.

Aktualizace, jak používat metody aktualizace má zvláštní význam provedení změn na příkaz a není by se zaměňovat s SQL **aktualizovat** příkazu (`SetData` odpovídá SQL **aktualizovat** příkaz) .

Odložená aktualizace jsou užitečné, například v situacích, například řadu bankovních transakcí; Pokud dojde ke zrušení jedna transakce, může této změny vrátit zpátky, protože Neodesílat řady změn až po poslední z nich záleží. Navíc můžete zprostředkovatele sady změn do jedné sítě volání, což je efektivnější.

Pro podporu odložené aktualizace, je nutné nastavit `DBPROP_IRowsetChange` vlastnost spolu s vlastností popsaných v **podporuje operace aktualizace**:

```cpp
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);
```

Při volání `Update` nebo `UpdateAll`, metody přenést změny z místní mezipaměti do úložiště dat a pak vymazat místní mezipaměť. Aktualizace se přenáší změny pouze pro aktuální řádek, a proto je důležité, že vaše aplikace uchovává informace o řádek, který má aktualizace a kdy ji aktualizovat. Následující příklad ukazuje, jak aktualizovat dvě po sobě následující řádky:

```cpp
// Instantiate a rowset based on the user record class
CTable<CAccessor<CProductAccessor>> product;
CSession session;

// Open the rowset and move to the 100th row
product.Open(session, "Product", &ps, 1);  // ps is the property set
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row

// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) );

product.m_UnitsInStock = 10000;

HRESULT hr = product.SetData();  // No changes made to row 100 yet
product.Update();                 // Update row 100 now

// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table
product.MoveNext();

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) );

product.m_UnitsInStock = 500;

HRESULT hr = product.SetData();  // No changes made to row 101 yet
product.Update();                 // Update row 101 now
```

Aby bylo zajištěno, že čekající změny přenesou, měli byste zavolat `Update` před přechodem na další řádek. Ale pokud je to únavné nebo neefektivní, například když vaše aplikace potřebuje aktualizovat stovky řádků, můžete použít `UpdateAll` k aktualizaci všech řádků najednou.

Například pokud první `Update` volání chyběly výše uvedený kód, řádek 100 zůstává beze změny, když by byla změněna řádek 101. Po tomto okamžiku by buď mít vaše aplikace volat `UpdateAll` nebo přejděte zpět do řádku 100 a volání `Update` pro tento řádek aktualizovat.

Nakonec jeden z hlavních důvodů odložit změny je možné vrátit zpět, je. Volání [CRowset::Undo](../../data/oledb/crowset-undo.md) vrátí zpět stav změna v místní mezipaměti na stav úložiště dat než čekající změny byly provedeny. Je důležité si uvědomit, že `Undo` nelze vrátit zpět stav místní mezipaměti o jeden krok (stavu před pouze nejnovější změny); místo toho vymaže místní mezipaměť pro tento řádek. Navíc `Undo` má vliv jenom na aktuálním řádku.

## <a name="see-also"></a>Viz také:

[Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset – třída](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))<br/>
