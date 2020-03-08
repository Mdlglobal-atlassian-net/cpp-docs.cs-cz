---
title: Funkce výměny polí v záznamu
ms.date: 09/17/2019
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
ms.openlocfilehash: 491b00fe65634acf7c8805dd471fa6e3cc62acf0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78871649"
---
# <a name="record-field-exchange-functions"></a>Funkce výměny polí v záznamu

Toto téma obsahuje seznam funkcí výměny pole záznamu (RFX, Bulk RFX a DFX), které slouží k automatizaci přenosu dat mezi objektem sady záznamů a jeho zdrojem dat a k provádění dalších operací s daty.

Pokud používáte třídy založené na rozhraní ODBC a jste implementovali hromadné načítání řádků, je nutné ručně přepsat `DoBulkFieldExchange` členské funkce `CRecordset` voláním funkce Bulk RFX pro každý datový člen odpovídající sloupci zdroje dat.

Pokud jste neimplementovali hromadné načítání řádků do tříd založených na rozhraní ODBC nebo pokud používáte třídy založené na rozhraní DAO (zastaralé), pak ClassWizard `DoFieldExchange` přepíše členskou funkci `CRecordset` nebo `CDaoRecordset` voláním funkce RFX (pro třídy rozhraní ODBC) nebo funkcí DFX (pro třídy DAO) pro každý datový člen pole v sadě záznamů.

Výměna pole záznamu funkce přenáší data pokaždé, když rozhraní volá `DoFieldExchange` nebo `DoBulkFieldExchange`. Každá funkce přenáší konkrétní datový typ.

Další informace o tom, jak se tyto funkce používají, najdete v článcích [Výměna pole záznamu: Jak funguje RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pro sloupce dat, která lze svázat dynamicky, můžete také volat funkce RFX nebo DFX sami, jak je vysvětleno v článcích [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Navíc můžete napsat vlastní rutiny RFX nebo DFX, jak je vysvětleno v technické poznámce [43](../../mfc/tn043-rfx-routines.md) (pro rozhraní ODBC) a technickou poznámku [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pro DAO).

Příklad RFX a hromadné funkce RFX, jak se zobrazí ve funkcích `DoFieldExchange` a `DoBulkFieldExchange`, naleznete v tématu [RFX_Text](#rfx_text) a [RFX_Text_Bulk] #rfx_text_bulk). Funkce DFX jsou velmi podobné funkcím RFX.

### <a name="rfx-functions-odbc"></a>RFX – funkce (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Převede pole bajtů typu [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Přenáší logická data.|
|[RFX_Byte](#rfx_byte)|Převede jeden bajt dat.|
|[RFX_Date](#rfx_date)|Převede data času a data pomocí [CTime –](../../atl-mfc-shared/reference/ctime-class.md) nebo TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Převádí data typu Double-Precision.|
|[RFX_Int](#rfx_int)|Převádí celočíselná data.|
|[RFX_Long](#rfx_long)|Převede dlouhá celočíselná data.|
|[RFX_LongBinary](#rfx_longbinary)|Přenáší data binárního rozsáhlého objektu (BLOB) s objektem třídy [CLongBinary –](clongbinary-class.md) .|
|[RFX_Single](#rfx_single)|Převede data typu float.|
|[RFX_Text](#rfx_text)|Přenáší řetězcová data.|

### <a name="bulk-rfx-functions-odbc"></a>Funkce hromadného RFX (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Převede pole dat bajtů.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Převede pole logických dat.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Převede pole s jedním počtem bajtů.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Převede pole dat typu TIMESTAMP_STRUCT.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Převádí pole dat s dvojitou přesností a plovoucí desetinnou čárkou.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Převede pole celočíselných dat.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Převede pole dlouhých celočíselných dat.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Převede pole dat s plovoucí desetinnou čárkou.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Převede pole dat typu typem LPStr.|

### <a name="dfx-functions-dao"></a>DFX – funkce (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Převede pole bajtů typu [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Přenáší logická data.|
|[DFX_Byte](#dfx_byte)|Převede jeden bajt dat.|
|[DFX_Currency](#dfx_currency)|Převádí data měny typu [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Převede data času a data typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Převádí data typu Double-Precision.|
|[DFX_Long](#dfx_long)|Převede dlouhá celočíselná data.|
|[DFX_LongBinary](#dfx_longbinary)|Přenáší data binárního rozsáhlého objektu (BLOB) s objektem třídy `CLongBinary`. Pro rozhraní DAO doporučujeme místo toho použít [DFX_Binary](#dfx_binary) .|
|[DFX_Short](#dfx_short)|Převádí krátká celočíselná data.|
|[DFX_Single](#dfx_single)|Převede data typu float.|
|[DFX_Text](#dfx_text)|Přenáší řetězcová data.|

=============================================

## <a name="rfx_binary"></a>RFX_Binary

Převede pole bajtů mezi datovými členy pole `CRecordset` objektu a sloupci záznamu ve zdroji dat typu ODBC SQL_BINARY, SQL_VARBINARY nebo SQL_LONGVARBINARY.

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
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat se hodnota typu [CByteArray](cbytearray-class.md)převezme ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nMaxLength*<br/>
Maximální povolená délka předávaného řetězce nebo pole Výchozí hodnota *nMaxLength* je 255. Platné hodnoty jsou 1 pro INT_MAX. Rozhraní přiděluje toto množství místa pro data. Pro dosažení nejlepšího výkonu předejte dostatečně velký objem dat, aby se vešel na největší datovou položku, kterou očekáváte.

### <a name="remarks"></a>Poznámky

Data ve zdroji dat těchto typů jsou mapována na a z typu `CByteArray` v sadě záznamů.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_bool"></a>RFX_Bool

Přenáší logická data mezi datovými členy pole `CRecordset` objektu a sloupci záznamu ve zdroji dat typu ODBC SQL_BIT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat, hodnota typu BOOL je přijímán ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_byte"></a>RFX_Byte

Přenáší jednotlivé bajty mezi datovými členy pole `CRecordset` objektu a sloupci záznamu ve zdroji dat typu ODBC SQL_TINYINT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu BYTE přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_date"></a>RFX_Date

Přenáší data `CTime` nebo TIMESTAMP_STRUCT mezi datovými členy pole `CRecordset` objektu a sloupci záznamu ve zdroji dat typu ODBC SQL_DATE, SQL_TIME nebo SQL_TIMESTAMP.

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
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu; hodnota, která má být převedena. Různé verze funkce mají různé datové typy pro hodnotu:

První verze funkce přebírá odkaz na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) . Pro přenos ze sady záznamů na zdroj dat se tato hodnota převezme ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

Druhá verze funkce přebírá odkaz na strukturu `TIMESTAMP_STRUCT`. Tuto strukturu musíte nastavit sami před voláním. Pro tuto verzi nejsou k dispozici podporu pro výměnu dialogových dat (DDX) ani podpora průvodce kódem. Třetí verze funkce funguje podobně jako u první verze s tím rozdílem, že přebírá odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) .

### <a name="remarks"></a>Poznámky

`CTime` verze funkce ukládá režijní náklady na určité přechodné zpracování a má poněkud omezený rozsah. Pokud některý z těchto faktorů najde příliš omezený počet, použijte druhou verzi funkce. Všimněte si ale nedostatku průvodce kódem a podporu DDX a požadavek, abyste strukturu nastavili sami.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_double"></a>RFX_Double

Přenáší data **Double float** mezi datovými členy pole `CRecordset` objektu a sloupci záznamu ve zdroji dat typu ODBC SQL_DOUBLE.

### <a name="syntax"></a>Syntaxe

```
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **Double**převedená ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_int"></a>RFX_Int

Přenáší celočíselná data mezi poli datových členů objektu `CRecordset` a sloupce záznamu ve zdroji dat typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **int**přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_long"></a>RFX_Long

Převádí dlouhá celočíselná data mezi poli datových členů objektu `CRecordset` a sloupce záznamu ve zdroji dat typu ODBC SQL_INTEGER.

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
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **Long**přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_longbinary"></a>RFX_LongBinary

Přenáší data binárního rozsáhlého objektu (BLOB) pomocí třídy [CLongBinary –](clongbinary-class.md) mezi datovými členy pole objektu `CRecordset` a sloupci záznamu ve zdroji dat typu ODBC SQL_LONGVARBINARY nebo SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntaxe

```
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu `CLongBinary`převedená ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_single"></a>RFX_Single

Převádí data s plovoucí desetinnou čárkou mezi datovými členy pole `CRecordset` objektu a sloupci záznamu ve zdroji dat typu ODBC SQL_REAL.

### <a name="syntax"></a>Syntaxe

```
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **float**převedená ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_text"></a>RFX_Text

Přenáší `CString` data mezi datovými členy pole `CRecordset` objektu a sloupce záznamu ve zdroji dat typu ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL nebo SQL_NUMERIC.

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
Ukazatel na objekt třídy `CFieldExchange`. Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu `CString`převedená ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nMaxLength*<br/>
Maximální povolená délka předávaného řetězce nebo pole Výchozí hodnota *nMaxLength* je 255. Platné hodnoty jsou 1 pro INT_MAX). Rozhraní přiděluje toto množství místa pro data. Pro dosažení nejlepšího výkonu předejte dostatečně velký objem dat, aby se vešel na největší datovou položku, kterou očekáváte.

*nColumnType*<br/>
Používá se hlavně pro parametry. Celé číslo označující datový typ parametru. Typ je datový typ ODBC formuláře **SQL_XXX**.

*nScale*<br/>
Určuje měřítko pro hodnoty typu ODBC SQL_DECIMAL nebo SQL_NUMERIC. *nScale* je užitečné pouze při nastavování hodnot parametrů. Další informace najdete v tématu "přesnost, škálování, délka a velikost zobrazení" v příloze D *referenčních informací programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Data ve zdroji dat všech těchto typů jsou mapována na a z `CString` v sadě záznamů.

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání `RFX_Text`. Všimněte si také dvou volání `CFieldExchange::SetFieldType`. Pro parametry musíte napsat volání `SetFieldType` a jeho volání RFX. Volání výstupního sloupce a jeho přidružená volání RFX jsou obvykle zapisována průvodcem kódem.

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

**Záhlaví:** AFXDB. h

## <a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

Přenáší více řádků bajtových dat ze sloupce zdroje dat ODBC do odpovídajícího pole v objektu odvozeném od `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgByteVals*<br/>
Ukazatel na pole bajtů hodnot. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgByteVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

*nMaxLength*<br/>
Maximální povolená délka hodnot uložených v poli, na kterou odkazuje *prgByteVals*. Aby se zajistilo, že data nebudou zkrácená, předejte dostatečně velkou velikost, která bude vyhovovat největší datové položce, kterou očekáváte.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat může mít typ rozhraní ODBC SQL_BINARY, SQL_VARBINARY nebo SQL_LONGVARBINARY. Sada záznamů musí definovat datový člen pole typu pointer na BYTE.

Pokud inicializujete *prgByteVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

Přenáší více řádků logických dat ze sloupce zdroje dat ODBC do odpovídajícího pole v objektu odvozeném od `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgBoolVals*<br/>
Ukazatel na pole LOGICKÝch hodnot. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgBoolVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít SQL_BIT typ ODBC. Sada záznamů musí definovat datový člen pole typu pointer na BOOL.

Pokud inicializujete *prgBoolVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

Převede více řádků jednoho bajtu ze sloupce zdroje dat ODBC na odpovídající pole v objektu odvozeném od `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgByteVals*<br/>
Ukazatel na pole bajtů hodnot. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgByteVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít SQL_TINYINT typ ODBC. Sada záznamů musí definovat datový člen pole typu pointer na BYTE.

Pokud inicializujete *prgByteVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_date_bulk"></a>RFX_Date_Bulk

Přenáší více řádků TIMESTAMP_STRUCT dat ze sloupce zdroje dat ODBC do odpovídajícího pole v objektu odvozeném z `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgTSVals*<br/>
Ukazatel na pole hodnot TIMESTAMP_STRUCT. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů. Další informace o TIMESTAMP_STRUCT datový typ naleznete v tématu "datové typy jazyka C" v příloze D *referenčních informací programátora sady ODBC SDK*.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgTSVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat může mít typ rozhraní ODBC SQL_DATE, SQL_TIME nebo SQL_TIMESTAMP. Sada záznamů musí definovat datový člen pole typu pointer na TIMESTAMP_STRUCT.

Pokud inicializujete *prgTSVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_double_bulk"></a>RFX_Double_Bulk

Převádí více řádků dat s dvojitou přesností a plovoucí desetinnou čárkou ze sloupce datového zdroje ODBC k odpovídajícímu poli v objektu odvozeném od `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgDblVals*<br/>
Ukazatel na pole **dvojitých** hodnot. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgDblVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít SQL_DOUBLE typ ODBC. Sada záznamů musí definovat datový člen pole typu ukazatel na hodnotu **Double**.

Pokud inicializujete *prgDblVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_int_bulk"></a>RFX_Int_Bulk

Přenáší celočíselná data mezi poli datových členů objektu `CRecordset` a sloupce záznamu ve zdroji dat typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace o operacích, které může objekt `CFieldExchange` určit, najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **int**přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_long_bulk"></a>RFX_Long_Bulk

Převede více řádků dlouhých celočíselných dat ze sloupce datového zdroje ODBC na odpovídající pole v objektu odvozeném z `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgLongVals*<br/>
Ukazatel na pole dlouhých celých čísel. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgLongVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít SQL_INTEGER typ ODBC. Sada záznamů musí definovat pole datového člena typu ukazatel na hodnotu **Long**.

Pokud inicializujete *prgLongVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_single_bulk"></a>RFX_Single_Bulk

Přenáší více řádků dat s plovoucí desetinnou čárkou ze sloupce datového zdroje ODBC do odpovídajícího pole v objektu odvozeném od `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgFltVals*<br/>
Ukazatel na pole hodnot **typu float** . V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgFltVals*. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít SQL_REAL typ ODBC. Sada záznamů musí definovat datový člen pole typu pointer na typ **float**.

Pokud inicializujete *prgFltVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

## <a name="rfx_text_bulk"></a>RFX_Text_Bulk

Přenáší více řádků znakových dat ze sloupce zdroje dat ODBC do odpovídajícího pole v objektu odvozeném od `CRecordset`.

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
Ukazatel na objekt [CFieldExchange](cfieldexchange-class.md) . Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce. Další informace najdete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Název datového sloupce.

*prgStrVals*<br/>
Ukazatel na pole hodnot typem LPStr. V tomto poli budou uložena data, která mají být přenesena ze zdroje dat do sady záznamů. Všimněte si, že v aktuální verzi rozhraní ODBC nemůžou být tyto hodnoty Unicode.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude uchovávat délku v bajtech každé hodnoty v poli, na které odkazuje *prgStrVals*. Tato délka vylučuje ukončovací znak null. Všimněte si, že hodnota SQL_NULL_DATA bude uložena, pokud odpovídající datová položka obsahuje hodnotu null. Další podrobnosti najdete v tématu funkce rozhraní ODBC API `SQLBindCol` v *Referenční příručce programátora sady ODBC SDK*.

*nMaxLength*<br/>
Maximální povolená délka hodnot uložených v poli, na které ukazuje *prgStrVals*, včetně ukončovacího znaku null. Aby se zajistilo, že data nebudou zkrácená, předejte dostatečně velkou velikost, která bude vyhovovat největší datové položce, kterou očekáváte.

### <a name="remarks"></a>Poznámky

Sloupec zdroj dat může mít typ ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL nebo SQL_NUMERIC. Sada záznamů musí definovat datový člen pole typu typem LPStr.

Pokud inicializujete *prgStrVals* a *prgLengths* na hodnotu null, pak se pole, na která se odkazuje, přidělují automaticky s velikostmi, které se rovnají velikosti sady řádků.

> [!NOTE]
>  Hromadná výměna pole záznamu převádí data pouze ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, je nutné použít funkci rozhraní ODBC API `SQLSetPos`.

Další informace naleznete v článcích [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměny pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Příklad

V přepsání `DoBulkFieldExchange` musíte ručně napsat volání. Tento příklad ukazuje volání `RFX_Text_Bulk`a také volání `RFX_Long_Bulk`pro přenos dat. Těmto voláním předchází volání [CFieldExchange:: SetFieldType](CFieldExchange::SetFieldType.md). Všimněte si, že u parametrů je nutné volat funkce RFX místo hromadných funkcí RFX.

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

**Záhlaví:** AFXDB. h

## <a name="dfx_binary"></a>DFX_Binary

Převede pole bajtů mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupce záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat se hodnota typu [CByteArray](cbytearray-class.md)převezme ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nPreAllocSize*<br/>
Rozhraní předem přidělí tuto velikost paměti. Pokud jsou vaše data větší, rozhraní vám podle potřeby přidělí více místa. Pro lepší výkon nastavte tuto velikost na dostatečně velkou, aby se zabránilo přerozdělení. Výchozí velikost je definována v AFXDAO. Soubor H jako AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_DISABLE_FIELD_CACHE, nepoužívá dvojité ukládání do vyrovnávací paměti a je nutné volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami. Další možná hodnota, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti a není nutné provádět další práci k označení nevyřízených polí nebo hodnoty null. Z důvodu výkonu a paměti Vyhněte této hodnotě, pokud vaše binární data nejsou relativně malá.

> [!NOTE]
>  Můžete určit, zda mají být data ve výchozím nastavení dvojitě ukládána do vyrovnávací paměti pro všechna pole nastavením [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typy DAO_BYTES v rozhraní DAO a v sadě záznamů typu [CByteArray](cbytearray-class.md) .

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_bool"></a>DFX_Bool

Přenáší logická data mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat, hodnota typu BOOL je přijímán ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_BOOL v rozhraní DAO a typ BOOL v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_byte"></a>DFX_Byte

Přenáší jednotlivé bajty mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupce záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu BYTE přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_BYTES v rozhraní DAO a typem BYTE v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_currency"></a>DFX_Currency

Přenáší data měny mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů do zdroje dat je tato hodnota provedena ze zadaného datového členu typu [COleCurrency](colecurrency-class.md). Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typy DAO_CURRENCY v rozhraní DAO a v sadě záznamů typu [COleCurrency](colecurrency-class.md) .

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_datetime"></a>DFX_DateTime

Převádí data a data mezi datovými členy pole v objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Funkce přebírá odkaz na objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) . Pro přenos ze sady záznamů na zdroj dat se tato hodnota převezme ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typy DAO_DATE v rozhraní DAO a v sadě záznamů typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) .

> [!NOTE]
>  `COleDateTime` nahrazuje [CTime –](../../atl-mfc-shared/reference/ctime-class.md) a TIMESTAMP_STRUCT pro tento účel v třídách DAO. `CTime` a TIMESTAMP_STRUCT se pořád používají pro třídy přístupu k datům založené na rozhraní ODBC.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_double"></a>DFX_Double

Převádí data **typu Double float** mezi datovými členy pole v objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **Double**převedená ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_R8 v rozhraní DAO a v sadě záznamů typu **Double float** .

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_long"></a>DFX_Long

Převádí dlouhá celočíselná data mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **Long**přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_I4 v rozhraní DAO a v sadě záznamů typu **Long** .

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_longbinary"></a>DFX_LongBinary

**Důležité** informace Doporučujeme místo této funkce použít [DFX_Binary](#dfx_binary) .

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat se hodnota typu [CLongBinary –](clongbinary-class.md)převezme ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwPreAllocSize*<br/>
Rozhraní předem přidělí tuto velikost paměti. Pokud jsou vaše data větší, rozhraní vám podle potřeby přidělí více místa. Pro lepší výkon nastavte tuto velikost na dostatečně velkou, aby se zabránilo přerozdělení.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Ve výchozím nastavení AFX_DISABLE_FIELD_CACHE nepoužívá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_ENABLE_FIELD_CACHE. Používá dvojité ukládání do vyrovnávací paměti a není nutné provádět další práci k označení nevyřízených polí nebo hodnoty null. Z důvodu výkonu a paměti Vyhněte této hodnotě, pokud vaše binární data nejsou relativně malá.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

`DFX_LongBinary` je k dispozici pro kompatibilitu s třídami knihovny MFC rozhraní ODBC. Funkce `DFX_LongBinary` přenáší data binárního rozsáhlého objektu (BLOB) pomocí `CLongBinary` třídy mezi datovými členy pole v objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat. Data jsou mapována mezi typy DAO_BYTES v rozhraní DAO a v sadě záznamů typu [CLongBinary –](clongbinary-class.md) .

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_short"></a>DFX_Short

Převádí krátká celočíselná data mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **short**převedená od zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_I2 v rozhraní DAO a v sadě záznamů typu **short** .

> [!NOTE]
>  `DFX_Short` je ekvivalentem [RFX_Int](#rfx_int) pro třídy založené na rozhraní ODBC.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_single"></a>DFX_Single

Převádí data s plovoucí desetinnou čárkou mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu **float**převedená ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Je nutné volat `SetFieldDirty` a `SetFieldNull` sami.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typy DAO_R4 v rozhraní DAO a v sadě záznamů typu **float** .

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="dfx_text"></a>DFX_Text

Přenáší `CString` data mezi poli datových členů objektu [CDaoRecordset](cdaorecordset-class.md) a sloupce záznamu ve zdroji dat.

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
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace pro definování kontextu pro každé volání funkce.

*szName*<br/>
Název datového sloupce.

*value*<br/>
Hodnota uložená v označeném datovém členu – hodnota, která má být převedena. Pro přenos ze sady záznamů na zdroj dat je hodnota typu [CString](../../atl-mfc-shared/reference/cstringt-class.md)přijímána ze zadaného datového členu. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nPreAllocSize*<br/>
Rozhraní předem přidělí tuto velikost paměti. Pokud jsou vaše data větší, rozhraní vám podle potřeby přidělí více místa. Pro lepší výkon nastavte tuto velikost na dostatečně velkou, aby se zabránilo přerozdělení.

*dwBindOptions*<br/>
Možnost, která umožňuje využít výhod mechanismu dvojitého ukládání do vyrovnávací paměti knihovny MFC pro detekci polí sady záznamů, které se změnily. Výchozí AFX_DAO_ENABLE_FIELD_CACHE používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC neprovede kontrolu tohoto pole. Musíte volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami sebe.

> [!NOTE]
>  Nastavením možnosti [CDaoRecordset:: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete řídit, jestli jsou data ve výchozím nastavení dvojitě bufferovaná.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_CHAR v rozhraní DAO (nebo, pokud je definován _UNICODE symbol, DAO_WCHAR) a do sady záznamů zadejte [CString](../../atl-mfc-shared/reference/cstringt-class.md) .  n

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání `DFX_Text`. Všimněte si také dvou volání [CDaoFieldExchange:: SetFieldType](cdaofieldexchange-class.md#setfieldtype). Je nutné napsat první volání `SetFieldType` a jeho volání **DFX** . Druhé volání a přidružené volání **DFX** jsou obvykle zapisovány průvodcem kódem, který třídu vygeneroval.

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

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CRecordset::D oFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::D oBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::D oFieldExchange](cdaorecordset-class.md#dofieldexchange)
