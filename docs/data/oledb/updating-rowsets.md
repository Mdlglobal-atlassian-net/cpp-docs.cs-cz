---
title: Aktualizace sad řádků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ca0ef94ba6c60bd43e24672fe7db669a3930fd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="updating-rowsets"></a>Aktualizace sad řádků
Operace velmi základní databáze je aktualizovat nebo zapisovat data do úložiště dat. V OLE DB, je jednoduchý mechanismus aktualizace: aplikace příjemce nastaví hodnoty členů vázaných dat a pak zapíše tyto hodnoty do sady řádků; Příjemce potom požadavků, že aktualizovat zprostředkovatele úložiště dat.  
  
 Příjemci knihovny můžete provádět následující typy aktualizací dat řádků: nastavení hodnot sloupce v řádku, vložíte řádek nebo odstranění řádku. K provedení těchto operací třídu šablony technologie OLE DB [CRowset](../../data/oledb/crowset-class.md) implementuje [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) rozhraní a přepíše následující metody rozhraní:  
  
-   [SetData –](../../data/oledb/crowset-setdata.md) změny sloupec hodnoty v řádku sadu řádků, je ekvivalentní příkazu SQL UPDATE.  
  
-   [Vložit](../../data/oledb/crowset-insert.md) vloží řádek do sady řádků; je ekvivalentní k příkazu INSERT jazyka SQL.  
  
-   [Odstranit](../../data/oledb/crowset-delete.md) odstraní řádky ze sady řádků; ta je ekvivalentní příkaz SQL odstranit.  
  
## <a name="supporting-update-operations"></a>Podpora operací aktualizace  
 Při vytváření příjemce pomocí průvodce příjemcem knihovny ATL technologie OLE DB, může podporovat operace aktualizace výběrem jednoho nebo více ze tří zaškrtávacích políček **změnu**, **vložit**, a **odstranit**. Pokud vyberete ty, průvodce kód správně upravuje pro podporu typ změny, které zvolíte. Ale pokud použijete průvodce, je nutné nastavit následující vlastnosti sady řádků na `VARIANT_TRUE` pro podporu aktualizace:  
  
-   **DBPROPVAL_UP_CHANGE** vám umožní změnit hodnoty data v řádku.  
  
-   **DBPROPVAL_UP_INSERT** umožňuje vložit řádek.  
  
-   **DBPROPVAL_UP_DELETE** umožňuje odstranit řádek.  
  
 Nastavte vlastnosti takto:  
  
```  
CDBPropSet ps(DBPROPSET_ROWSET);  

ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
 Změna, insert nebo delete operace může selhat, pokud jeden nebo více sloupců se nedá zapisovat. Upravte mapu kurzor a opravu.  
  
## <a name="setting-data-in-rows"></a>Nastavení dat v řádcích  
 [CRowset::SetData](../../data/oledb/crowset-setdata.md) nastaví hodnoty dat v jeden nebo více sloupců na aktuálním řádku. Následující kód nastaví hodnoty datových členů, které jsou vázané na sloupce "Název" a "Jednotky v Stock" tabulky produktů a potom zavolá `SetData` k zápisu do 100. řádku sady řádků tyto hodnoty:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_UnitsInStock = 10000;  
  
// Set the data  
HRESULT hr = product.SetData();  
```  
  
## <a name="inserting-rows-into-rowsets"></a>Vložení řádků do sady řádků  
 [CRowset::Insert](../../data/oledb/crowset-insert.md) vytvoří a inicializuje nový řádek pomocí dat z přistupujícího objektu. **Vložit** vytvoří zcela nový řádek po řádku aktuální; je třeba zadat, jestli se má zvýšit na aktuálním řádku na další řádek nebo ponechat beze změny. To provedete nastavením *bGetRow* parametr:  
  
```  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
-   **false** (výchozí hodnota) určuje, že na aktuálním řádku zvýší na další řádek (v takovém případě odkazuje vloženého řádku).  
  
-   **Hodnota TRUE,** Určuje, že aktuální řádek zůstane tam, kde je.  
  
 Následující kód nastaví hodnoty datových členů, které jsou vázané na sloupce tabulky produktů a potom zavolá **vložit** vložit nový řádek s těmito hodnotami po 100. řádku sady řádků. Doporučuje se, že nastavíte všechny hodnoty ve sloupcích předejdete nedefinované dat na novém řádku:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Set the column values for a row of the Product table, then insert the row  
product.m_ProductID = 101;  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_SupplierID = 27857;  
product.m_CategoryID = 372;  
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit,  
           _T( "Pack of 10" ) );  

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
  
 Podrobnější příklad najdete v tématu [CRowset::Insert](../../data/oledb/crowset-insert.md).  
  
 Další informace o nastavení stavu a délky datových členů najdete v tématu [Datoví členové stavu pole v přístupových objektech generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
## <a name="deleting-rows-from-rowsets"></a>Odstranění řádků ze sady řádků  
 [CRowset::Delete](../../data/oledb/crowset-delete.md) odstraní na aktuálním řádku ze sady řádků. Následující kód volání **odstranit** odebrat 100. řádku sady řádků:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Delete the row  
HRESULT hr = product.Delete();  
```  
  
## <a name="immediate-and-deferred-updates"></a>Okamžité a odložené aktualizace  
 Pokud neurčíte jinak, volá, aby se `SetData`, **vložit**, a **odstranit** metody aktualizovat úložiště dat okamžitě. Můžete však odložení aktualizací, aby příjemci ukládá všechny změny v místní mezipaměti a převede je na úložiště dat při volání jedné z následujících metod aktualizace:  
  
-   [CRowset::Update](../../data/oledb/crowset-update.md) přenáší všechny neuložené změny provedené na aktuální řádek od posledního načtení nebo **aktualizace** volání na něm.  
  
-   [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) přenáší všechny neuložené změny provedené na všechny řádky od posledního načtení nebo **aktualizace** volání na něm.  
  
 Poznámka: Tato aktualizace, jak používat metody aktualizace, má zvláštní význam provádění změn u příkazu a nelze zaměňovat s příkazem SQL UPDATE (`SetData` je ekvivalentní příkaz jazyka SQL UPDATE).  
  
 Odložené aktualizace jsou užitečné, například v situacích, jako je například řadu bankovních transakcí; Pokud jeden transakce zrušena, můžete vrátit zpět změny, vzhledem k tomu, že neodesíláte řadu změny až po poslední potvrzené. Zprostředkovatel také můžete svázat změny do jednoho síťového volání, které je efektivnější.  
  
 Chcete-li podporovat odložené aktualizace, musíte nastavit **DBPROP_IRowsetChange** vlastnost kromě pomocí vlastností popsaných v "Podpora operací aktualizace":  
  
```  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
 Při volání **aktualizace** nebo `UpdateAll`, metody přenosu změn z místní mezipaměti do úložiště dat a potom vymažou místní mezipaměti. Aktualizace přenese změny pouze pro aktuální řádek, je důležité, které vaše aplikace udržovat na řádek, který má aktualizace a kdy se mají aktualizovat. Následující příklad ukazuje, jak aktualizovat dvě po sobě jdoucích řádků:  
  
```  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Wick" ) );  

product.m_UnitsInStock = 10000;  

HRESULT hr = product.SetData();  // No changes made to row 100 yet  
product.Update();                 // Update row 100 now  
  
// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table  
product.MoveNext();  

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName  
           _T( "Wax" ) );  

product.m_UnitsInStock = 500;  

HRESULT hr = product.SetData();  // No changes made to row 101 yet  
product.Update();                 // Update row 101 now  
```  
  
 Aby se zajistilo, že budou čekající změny přeneseny, by měly volat **aktualizace** než budete pokračovat na další řádek. Ale pokud je to zdlouhavé nebo neefektivní, například pokud aplikace potřebuje k aktualizaci stovky řádků, můžete použít `UpdateAll` chcete aktualizovat všechny řádky najednou.  
  
 Například pokud první **aktualizace** volání byly výše uvedeném kódu, řádek 100 zůstane beze změny, zatímco řádek 101 by byl změněn. Po tomto okamžiku by vaše aplikace mít buď volat `UpdateAll` nebo přesunutí zpátky na 100 řádků a volání **aktualizace** pro aktualizaci řádku.  
  
 Nakonec je možné vrátit zpět, je jeden z hlavních důvodů odložení změny. Volání metody [CRowset::Undo](../../data/oledb/crowset-undo.md) vrátí zpět stav mezipaměti místní změnit stav úložiště dat než nebyly provedeny žádné změny čekající na zpracování. Je důležité si uvědomit, že **vrátit zpět** není vrátit zpět stav místní mezipaměti o jeden krok (stav před poslední změnou); místo toho vymaže místní mezipaměti na příslušném řádku. Navíc **vrátit zpět** má vliv pouze na aktuálním řádku.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami příjemců OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)   
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)