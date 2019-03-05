---
title: Funkce výměny polí v záznamu
ms.date: 11/04/2016
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
ms.openlocfilehash: 865c67b88c37e32ef33fa410ef178b81b7a6ecac
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297070"
---
# <a name="record-field-exchange-functions"></a>Funkce výměny polí v záznamu

Toto téma obsahuje seznam výměna pole záznamu (RFX Bulk RFX a DFX) funkce používané k automatizaci přenos dat mezi objektem sady záznamů a zdrojem dat a k provádění jiných operací s daty.

Pokud používáte třídy založené na rozhraní ODBC a implementovali hromadné načítání řádků, je nutné ručně přepsat `DoBulkFieldExchange` členskou funkci `CRecordset` voláním funkce Bulk RFX pro každý datový člen odpovídající zdrojový sloupec data.

Pokud jste neimplementovali hromadné načítání řádků třídy založené na rozhraní ODBC, nebo pokud používáte třídy založené na rozhraní DAO, pak se přepíše ClassWizard `DoFieldExchange` členskou funkci `CRecordset` nebo `CDaoRecordset` pomocí volání funkcí RFX (pro ODBC – třídy ) nebo DFX – funkce (pro třídy DAO) pro každé pole datového člena ve vaší sadě záznamů.

Funkce výměny polí záznamu přenosu dat pokaždé, když volá framework `DoFieldExchange` nebo `DoBulkFieldExchange`. Každá funkce převede určitý datový typ.

Další informace o tom, jak jsou tyto funkce používají, najdete v článcích [výměna polí záznamu: Jak funkce RFX pracuje (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

U sloupců dat, která dynamicky navázat, můžete také volat funkce RFX nebo DFX sami, jak je popsáno v článcích [sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Kromě toho můžete napsat vlastní vlastní RFX nebo DFX rutiny, jak je vysvětleno v technická Poznámka [43](../../mfc/tn043-rfx-routines.md) (pro rozhraní ODBC) a technická Poznámka [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pro rozhraní DAO).

Příklad RFX a Bulk RFX pracuje, jak se objeví v `DoFieldExchange` a `DoBulkFieldExchange` funkce, najdete v článku [RFX_Text](#rfx_text) a rfx_text_bulk – # [rfx_text_bulk –]). DFX – funkce jsou velmi podobné funkce RFX.

### <a name="rfx-functions-odbc"></a>Funkce RFX (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Převede pole bajtů typu [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Přenese logickou data.|
|[RFX_Byte](#rfx_byte)|Přenese jeden bajt data.|
|[RFX_Date](#rfx_date)|Převede čas a datum data s využitím [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo TIMESTAMP_STRUCT z.|
|[RFX_Double](#rfx_double)|Převede datový typ float dvojitou přesností.|
|[RFX_Int](#rfx_int)|Přenáší data o celé číslo.|
|[RFX_Long](#rfx_long)|Přenosy dlouhé data o celé číslo.|
|[RFX_LongBinary](#rfx_longbinary)|Data binárního rozsáhlého objektu (BLOB) se objekt přenese [CLongBinary](clongbinary-class.md) třídy.|
|[RFX_Single](#rfx_single)|Převody plovoucí data.|
|[RFX_Text](#rfx_text)|Data řetězce přenosy.|

### <a name="bulk-rfx-functions-odbc"></a>Hromadné funkce RFX (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Převede pole bajtů data.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Převede pole logická data.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Převede pole jednoho bajtů.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Přenosy dat TIMESTAMP_STRUCT z typu pole.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Převede pole dat dvojitou přesností a plovoucí desetinnou čárkou.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Převede pole data o celé číslo.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Převede pole dat dlouhé celé číslo.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Převede pole dat, s plovoucí desetinnou čárkou.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Převede pole datového typu LPSTR.|

### <a name="dfx-functions-dao"></a>DFX – funkce (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Převede pole bajtů typu [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Přenese logickou data.|
|[DFX_Byte](#dfx_byte)|Přenese jeden bajt data.|
|[DFX_Currency](#dfx_currency)|Přenosy dat měny, typu [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Převede data a času typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Převede datový typ float dvojitou přesností.|
|[DFX_Long](#dfx_long)|Přenosy dlouhé data o celé číslo.|
|[DFX_LongBinary](#dfx_longbinary)|Data binárního rozsáhlého objektu (BLOB) se objekt přenese `CLongBinary` třídy. Pro rozhraní DAO, se doporučuje použít [dfx_binary –](#dfx_binary) místo.|
|[DFX_Short](#dfx_short)|Přenosy krátká celočíselná data.|
|[DFX_Single](#dfx_single)|Převody plovoucí data.|
|[DFX_Text](#dfx_text)|Data řetězce přenosy.|

=============================================

## <a name="rfx_binary"></a>  RFX_Binary

Převede pole bajtů mezi pole datové členy `CRecordset` objektu a sloupců záznamu ve zdroji dat rozhraní ODBC zadejte SQL_BINARY, SQL_VARBINARY nebo SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntaxe

```
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu [CByteArray](cbytearray-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*nMaxLength*<br/>
Maximální povolená délka řetězce nebo pole přenosu. Výchozí hodnota *nMaxLength* je 255. Platné hodnoty jsou 1 INT_MAX. Rozhraní framework přiděluje toto množství místa pro data. Pro zajištění nejlepšího výkonu předejte hodnotu dostatečně velký, aby největší datové položky, které očekáváte.

### <a name="remarks"></a>Poznámky

Data ve zdroji dat z těchto typů je mapována do a z typů `CByteArray` v sadě záznamů.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_bool"></a>  RFX_Bool

Boolean – datový přenos mezi pole datové členy `CRecordset` SQL_BIT typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat je hodnota typu BOOL, provést ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_byte"></a>  RFX_Byte

Přenosy jednotné bajtů mezi pole datové členy `CRecordset` SQL_TINYINT typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat je hodnota typu BYTE, provést ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_date"></a>  RFX_Date

Přenosy `CTime` nebo TIMESTAMP_STRUCT z dat mezi pole datové členy `CRecordset` objektu a sloupců záznamu ve zdroji dat rozhraní ODBC zadejte SQL_DATE, SQL_TIME nebo SQL_TIMESTAMP.

### <a name="syntax"></a>Syntaxe

```
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen; Hodnota k převedení. Různé verze funkce přijímají různé datové typy pro hodnotu:

První verzi funkce používá odkaz na objekt [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu. Pro přenos ze sady záznamů ke zdroji dat je tato hodnota získána z zadaný datový člen. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

Druhou verzi funkce používá odkaz na objekt `TIMESTAMP_STRUCT` struktury. Musíte nastavit tuto strukturu sami před voláním. Podpora ani výměna dat dialogových oken (DDX) ani kód průvodce je k dispozici pro tuto verzi. Třetí verzi funkce funguje podobně jako na první verzi s tím rozdílem, že používá odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu.

### <a name="remarks"></a>Poznámky

`CTime` Verze funkce ukládá režii nějaké zprostředkující zpracování a má mírně omezené rozsah. Pokud některý z těchto faktorů příliš omezování zjistíte, použijte druhý verze funkce. Ale jeho nedostatek Průvodce kódu a podpora DDX a požadavky, které jste nastavili strukturu sami.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_double"></a>  RFX_Double

Přenosy **double float** data mezi pole datové členy `CRecordset` SQL_DOUBLE typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **double**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_int"></a>  RFX_Int

Přenosy dat celé číslo mezi pole datové členy `CRecordset` SQL_SMALLINT typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **int**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_long"></a>  RFX_Long

Přenosy dat dlouhé celé číslo mezi pole datové členy `CRecordset` SQL_INTEGER typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **dlouhé**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_longbinary"></a>  RFX_LongBinary

Přenosy dat binárních rozsáhlých objektů (BLOB) pomocí třídy [CLongBinary](clongbinary-class.md) mezi pole datové členy `CRecordset` objektu a sloupců záznamu ve zdroji dat rozhraní ODBC zadejte SQL_LONGVARBINARY nebo SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntaxe

```
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu `CLongBinary`, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_single"></a>  Rfx_single –

Přenosy dat s plovoucí desetinnou čárkou mezi pole datové členy `CRecordset` SQL_REAL typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **float**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_text"></a>  RFX_Text

Přenosy `CString` data mezi pole datové členy `CRecordset` objektu a sloupců záznamu ve zdroji dat rozhraní ODBC zadejte SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL nebo SQL_NUMERIC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy `CFieldExchange`. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu `CString`, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*nMaxLength*<br/>
Maximální povolená délka řetězce nebo pole přenosu. Výchozí hodnota *nMaxLength* je 255. Platné hodnoty jsou od 1 do INT_MAX). Rozhraní framework přiděluje toto množství místa pro data. Pro zajištění nejlepšího výkonu předejte hodnotu dostatečně velký, aby největší datové položky, které očekáváte.

*nColumnType*<br/>
Používá se hlavně pro parametry. Celé číslo udávající datový typ parametru. Typ je typ dat rozhraní ODBC formuláře **SQL_XXX**.

*nScale*<br/>
Určuje měřítko pro hodnoty typu ODBC SQL_DECIMAL nebo SQL_NUMERIC. *nScale* je užitečná pouze při nastavování hodnot parametrů. Další informace naleznete v tématu "Přesnost, měřítko, délku a velikost zobrazení" v dodatku D *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Data ve zdroji dat všech těchto typů je mapována do a z `CString` v sadě záznamů.

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání `RFX_Text`. Všimněte si také dvě volání na `CFieldExchange::SetFieldType`. Pro parametry, je nutné napsat volání `SetFieldType` a jeho RFX volání. Volání výstupní sloupce a jeho přidružené volání funkce RFX jsou obvykle zapsána Průvodcem kódu.

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_binary_bulk"></a>  Rfx_binary_bulk –

Přenese více řádků bajtů dat ze sloupce ze zdroje dat rozhraní ODBC pro odpovídající pole v `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgByteVals*<br/>
Ukazatel na pole BAJTŮ hodnot. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgByteVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

*nMaxLength*<br/>
Maximální povolená délka hodnoty uložené v poli, na které odkazuje *prgByteVals*. Aby bylo zajištěno, že data nebudou zkráceny, předejte hodnotu dostatečně velký, aby největší datové položky, které očekáváte.

### <a name="remarks"></a>Poznámky

Zdrojový sloupec data může mít typem ODBC SQL_BINARY, SQL_VARBINARY nebo SQL_LONGVARBINARY. Sada záznamů musí definovat datový člen pole typu ukazatele na BAJTY.

Pokud je inicializovat *prgByteVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Pokud chcete mít aktualizovatelné sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_bool_bulk"></a>  RFX_Bool_Bulk

Přenese více řádků logická data ze sloupce ze zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgBoolVals*<br/>
Ukazatel na pole hodnot typu BOOL. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgBoolVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Sloupci zdroje dat musí mít typ ODBC SQL_BIT. Sada záznamů musí definovat datový člen pole typu ukazatele na typ BOOL.

Pokud je inicializovat *prgBoolVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_byte_bulk"></a>  RFX_Byte_Bulk

Přenese na odpovídající pole v více řádků jednoho bajtů ze sloupce ze zdroje dat rozhraní ODBC `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgByteVals*<br/>
Ukazatel na pole BAJTŮ hodnot. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgByteVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Sloupci zdroje dat musí mít typ ODBC SQL_TINYINT. Sada záznamů musí definovat datový člen pole typu ukazatele na BAJTY.

Pokud je inicializovat *prgByteVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_date_bulk"></a>  RFX_Date_Bulk

Přenosy dat TIMESTAMP_STRUCT z více řádků ze sloupce ze zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgTSVals*<br/>
Ukazatel na pole TIMESTAMP_STRUCT z hodnot. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů. Další informace o typu TIMESTAMP_STRUCT z dat, naleznete v tématu "Datové typy jazyka C" v dodatku D *SDK Programátorská Reference ODBC*.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgTSVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Zdrojový sloupec data může mít typem ODBC SQL_DATE, SQL_TIME nebo SQL_TIMESTAMP. Sada záznamů musí definovat datový člen pole typu ukazatele na TIMESTAMP_STRUCT z.

Pokud je inicializovat *prgTSVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_double_bulk"></a>  RFX_Double_Bulk

Přenese více řádků dvojitou přesností a plovoucí desetinnou čárkou dat ze sloupce ze zdroje dat ODBC pro odpovídající pole v `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgDblVals*<br/>
Ukazatel na pole **double** hodnoty. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgDblVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Sloupci zdroje dat musí mít typ ODBC SQL_DOUBLE. Sada záznamů musí definovat datový člen pole typu ukazatele do **double**.

Pokud je inicializovat *prgDblVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_int_bulk"></a>  RFX_Int_Bulk

Přenosy dat celé číslo mezi pole datové členy `CRecordset` SQL_SMALLINT typ objektu a sloupců záznamu ve zdroji dat rozhraní ODBC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objektu můžete určit, najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **int**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

### <a name="example"></a>Příklad

See [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_long_bulk"></a>  RFX_Long_Bulk

Přenese na odpovídající pole v více řádků dlouhých celočíselných dat ze sloupce ze zdroje dat rozhraní ODBC `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgLongVals*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgLongVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Sloupci zdroje dat musí mít typ ODBC SQL_INTEGER. Sada záznamů musí definovat datový člen pole typu ukazatele do **dlouhé**.

Pokud je inicializovat *prgLongVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_single_bulk"></a>  RFX_Single_Bulk

Přenese více řádků s plovoucí desetinnou čárkou dat ze sloupce ze zdroje dat rozhraní ODBC pro odpovídající pole v `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgFltVals*<br/>
Ukazatel na pole **float** hodnoty. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgFltVals*. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

### <a name="remarks"></a>Poznámky

Sloupci zdroje dat musí mít typ ODBC SQL_REAL. Sada záznamů musí definovat datový člen pole typu ukazatele do **float**.

Pokud je inicializovat *prgFltVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

See [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_text_bulk"></a>  RFX_Text_Bulk

Přenese více řádků znaková data ze sloupce ze zdroje dat rozhraní ODBC pro odpovídající pole v `CRecordset`-odvozenému objektu.

### <a name="syntax"></a>Syntaxe

```
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definují kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název sloupce data.

*prgStrVals*<br/>
Ukazatel na pole hodnot LPSTR. Toto pole se uloží data přenos ze zdroje dat na sadu záznamů. Všimněte si, že aktuální verze rozhraní ODBC, tyto hodnoty nemůže být v kódování Unicode.

*prgLengths*<br/>
Ukazatel na pole dlouhé celých čísel. Toto pole se uloží délku v bajtech každé hodnoty v poli, na které odkazuje *prgStrVals*. Délka vyloučí null ukončovací znak. Všimněte si, že hodnota SQL_NULL_DATA, se uloží, pokud odpovídající položku dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce ODBC API `SQLBindCol` v *SDK Programátorská Reference ODBC*.

*nMaxLength*<br/>
Maximální povolená délka hodnoty uložené v poli, na které odkazuje *prgStrVals*, včetně null ukončovací znak. Aby bylo zajištěno, že data nebudou zkráceny, předejte hodnotu dostatečně velký, aby největší datové položky, které očekáváte.

### <a name="remarks"></a>Poznámky

Zdrojový sloupec data může mít typem ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL nebo SQL_NUMERIC. Datový člen pole typu LPSTR musí definovat sadu záznamů.

Pokud je inicializovat *prgStrVals* a *prgLengths* na hodnotu NULL, pak tato pole, které ukazují na přidělí automaticky, s velikostí odpovídající velikosti řádků.

> [!NOTE]
>  Hromadná výměna polí záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li aktualizovat sady záznamů, musíte použít funkci rozhraní API ODBC `SQLSetPos`.

Další informace najdete v článcích [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [zaznamenat Exchange poli (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Volání musíte napsat ručně v vaše `DoBulkFieldExchange` přepsat. Tento příklad ukazuje volání `RFX_Text_Bulk`, a také volání `RFX_Long_Bulk`, přenášet data. Tato volání před voláním [CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md). Všimněte si, že se pro parametry, je potřeba volat funkce RFX místo Bulk RFX funkce.

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="dfx_binary"></a>  DFX_Binary

Převede pole bajtů mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu [CByteArray](cbytearray-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*nPreAllocSize*<br/>
Rozhraní framework preallocates toto množství paměti. Pokud vaše data jsou větší, rozhraní framework bude přiděleno více místa podle potřeby. Pro zajištění lepšího výkonu nastavena na hodnotu dostatečně velký, aby se zabránilo přerozdělení této velikosti. Výchozí velikost je definován v AFXDAO. H soubor jako AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_DISABLE_FIELD_CACHE, nepoužívá dvojité ukládání do vyrovnávací paměti a je nutné volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami. Další možné hodnotu, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti a není potřeba provádět další práci pro označení pole nesprávné nebo hodnota Null. Z důvodů paměti a výkonu vyhněte tuto hodnotu, pokud binárních dat je poměrně malý.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměť pro všechna pole tak, že nastavíte výchozí [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_BYTES v rozhraní DAO a typem [CByteArray](cbytearray-class.md) v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_bool"></a>  DFX_Bool

Boolean – datový přenos mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat je hodnota typu BOOL, provést ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi typem DAO_BOOL v rozhraní DAO a typu BOOL v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_byte"></a>  DFX_Byte

Přenosy jednotné bajtů mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat je hodnota typu BYTE, provést ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi typem DAO_BYTES v rozhraní DAO a typ BAJTU v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_currency"></a>  DFX_Currency

Přenosy dat měny mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je tato hodnota získána z zadaný datový člen typu [COleCurrency](colecurrency-class.md). Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_CURRENCY v rozhraní DAO a typem [COleCurrency](colecurrency-class.md) v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_datetime"></a>  DFX_DateTime

Přenosy dat data a času mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Funkce používá odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu. Pro přenos ze sady záznamů ke zdroji dat je tato hodnota získána z zadaný datový člen. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_DATE v rozhraní DAO a typem [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) v sadě záznamů.

> [!NOTE]
>  `COleDateTime` nahradí [CTime](../../atl-mfc-shared/reference/ctime-class.md) a TIMESTAMP_STRUCT z pro tento účel tříd DAO. `CTime` a TIMESTAMP_STRUCT z jsou i nadále používán tříd pro přístup k data založená na rozhraní ODBC.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_double"></a>  DFX_Double

Přenosy **double float** data mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **double**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_R8 v rozhraní DAO a typem **double float** v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_long"></a>  DFX_Long

Přenosy dat dlouhé celé číslo mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **dlouhé**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_I4 v rozhraní DAO a typem **dlouhé** v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_longbinary"></a>  DFX_LongBinary

**Důležité** se doporučuje použít [dfx_binary –](#dfx_binary) místo této funkce.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu [CLongBinary](clongbinary-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwPreAllocSize*<br/>
Rozhraní framework preallocates toto množství paměti. Pokud vaše data jsou větší, rozhraní framework bude přiděleno více místa podle potřeby. Pro zajištění lepšího výkonu nastavena na hodnotu dostatečně velký, aby se zabránilo přerozdělení této velikosti.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DISABLE_FIELD_CACHE, nepoužívá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_ENABLE_FIELD_CACHE. Používá dvojité ukládání do vyrovnávací paměti a není potřeba další práci pro označení pole nesprávné nebo hodnota Null. Z důvodů paměti a výkonu vyhněte tuto hodnotu, pokud binárních dat je poměrně malý.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

`DFX_LongBinary` je k dispozici pro kompatibilitu s tříd knihovny MFC rozhraní ODBC. `DFX_LongBinary` Funkce převede binární-data rozsáhlého objektu (BLOB) horizontálních oddílů pomocí třídy `CLongBinary` mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat. Data je mapována mezi DAO_BYTES v rozhraní DAO a typem [CLongBinary](clongbinary-class.md) v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_short"></a>  DFX_Short

Přenosy krátká celočíselná data mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **krátký**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_I2 v rozhraní DAO a typem **krátký** v sadě záznamů.

> [!NOTE]
>  `DFX_Short` je ekvivalentní [rfx_int –](#rfx_int) pro třídy založené na rozhraní ODBC.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_single"></a>  DFX_Single

Přenosy dat s plovoucí desetinnou čárkou mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu **float**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi DAO_R4 v rozhraní DAO a typem **float** v sadě záznamů.

### <a name="example"></a>Příklad

See [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_text"></a>  DFX_Text

Přenosy `CString` data mezi pole datové členy [CDaoRecordset](cdaorecordset-class.md) objektu a sloupců záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [cdaofieldexchange –](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definují kontext pro každé volání funkce.

*szName*<br/>
Název sloupce data.

*value*<br/>
Hodnota uložená v označeném datový člen – hodnota, která má být převedena. Pro přenos ze sady záznamů ke zdroji dat, je hodnota typu [CString](../../atl-mfc-shared/reference/cstringt-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadané datový člen.

*nPreAllocSize*<br/>
Rozhraní framework preallocates toto množství paměti. Pokud vaše data jsou větší, rozhraní framework bude přiděleno více místa podle potřeby. Pro zajištění lepšího výkonu nastavena na hodnotu dostatečně velký, aby se zabránilo přerozdělení této velikosti.

*dwBindOptions*<br/>
Možnost, která vám umožní využít MFC dvojité vyrovnávací paměti mechanismus pro zjišťování polím sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. S možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud chcete zadat tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je nutné volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami.

> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení tak, že nastavíte [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data je mapována mezi typem DAO_CHAR v rozhraní DAO (nebo, pokud je definován symbol _UNICODE, DAO_WCHAR) a typ [CString](../../atl-mfc-shared/reference/cstringt-class.md) v sadě záznamů.  n

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání `DFX_Text`. Všimněte si také dvě volání na [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Je nutné napsat první volání `SetFieldType` a jeho **DFX** volání. Druhé volání a jeho přidruženého **DFX** volání jsou obvykle zapsána průvodcem kód, který vygeneruje třídu.

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
