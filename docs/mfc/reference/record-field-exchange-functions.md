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
ms.openlocfilehash: bfd3ba64a33547b8a27e0f3bc896f39c94486464
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372980"
---
# <a name="record-field-exchange-functions"></a>Funkce výměny polí v záznamu

Toto téma obsahuje seznam funkcí Exchange pole záznamu (RFX, Hromadné RFX a DFX) slouží k automatizaci přenosu dat mezi objektem sady záznamů a jeho zdroj dat a provádět další operace s daty.

Pokud používáte třídy založené na rozhraní ODBC a implementovali jste hromadné `DoBulkFieldExchange` načítání řádků, musíte ručně přepsat členskou `CRecordset` funkci voláním funkcí Hromadné RFX pro každý datový člen odpovídající sloupci zdroje dat.

Pokud jste neimplementovali hromadné načítání řádků ve třídách založených na rozhraní ODBC nebo pokud používáte třídy založené `DoFieldExchange` na `CRecordset` DAO (zastaralé), pak ClassWizard přepíše členskou funkci nebo `CDaoRecordset` voláním funkcí RFX (pro třídy ODBC) nebo funkcí DFX (pro třídy DAO) pro každý datový člen pole ve vaší sadě záznamů.

Funkce výměny pole záznamu přenášejí `DoFieldExchange` data `DoBulkFieldExchange`při každém volání rozhraní nebo . Každá funkce přenáší určitý datový typ.

Další informace o tom, jak se tyto funkce používají, naleznete v článcích [Výměna polí záznamu: Jak funguje RFX (ODBC).](../../data/odbc/record-field-exchange-how-rfx-works.md) Další informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Pro sloupce dat, které svážete dynamicky, můžete také volat funkce RFX nebo DFX sami, jak je vysvětleno v článcích [Recordset: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Kromě toho můžete napsat vlastní rutiny RFX nebo DFX, jak je vysvětleno v technické poznámce [43](../../mfc/tn043-rfx-routines.md) (pro ROZHRANÍ ODBC) a technické poznámce [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pro DAO).

Příklad funkcí RFX a Bulk RFX tak, `DoFieldExchange` `DoBulkFieldExchange` jak jsou uvedeny ve funkcích a, naleznete v [tématu RFX_Text](#rfx_text) a [RFX_Text_Bulk]#rfx_text_bulk). Funkce DFX jsou velmi podobné funkcím RFX.

### <a name="rfx-functions-odbc"></a>Funkce RFX (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Přenáší pole bajtů typu [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Přenáší logická data.|
|[RFX_Byte](#rfx_byte)|Přenáší jeden bajt dat.|
|[RFX_Date](#rfx_date)|Přenáší data času a data pomocí [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Přenáší floatová data s dvojitou přesností.|
|[RFX_Int](#rfx_int)|Přenáší celá data.|
|[RFX_Long](#rfx_long)|Přenáší dlouhá data celé číslo.|
|[RFX_LongBinary](#rfx_longbinary)|Přenáší binární data velkých objektů (BLOB) s objektem třídy [CLongBinary.](clongbinary-class.md)|
|[RFX_Single](#rfx_single)|Přenáší plovoucí data.|
|[RFX_Text](#rfx_text)|Přenáší data řetězce.|

### <a name="bulk-rfx-functions-odbc"></a>Funkce hromadného RFX (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Přenáší pole bajtových dat.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Přenáší pole logických dat.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Přenáší pole jednoho bajtu.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Přenáší pole dat typu TIMESTAMP_STRUCT.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Přenáší pole s dvojitou přesností dat s plovoucí desetinnou desetinnou tázkem.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Přenáší pole celá data.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Přenáší pole dlouhých celých dat.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Přenáší pole dat s plovoucí desetinnou desetinnou tázkem.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Přenáší pole dat typu LPSTR.|

### <a name="dfx-functions-dao"></a>Funkce DFX (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Přenáší pole bajtů typu [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Přenáší logická data.|
|[DFX_Byte](#dfx_byte)|Přenáší jeden bajt dat.|
|[DFX_Currency](#dfx_currency)|Přenáší data měny typu [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Přenáší data času a data typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Přenáší floatová data s dvojitou přesností.|
|[DFX_Long](#dfx_long)|Přenáší dlouhá data celé číslo.|
|[DFX_LongBinary](#dfx_longbinary)|Přenáší binární data velkých objektů (BLOB) `CLongBinary` s objektem třídy. Pro DAO se doporučuje použít [DFX_Binary](#dfx_binary) místo.|
|[DFX_Short](#dfx_short)|Přenáší krátká data celé číslo.|
|[DFX_Single](#dfx_single)|Přenáší plovoucí data.|
|[DFX_Text](#dfx_text)|Přenáší data řetězce.|

=============================================

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

Přenáší pole bajtů mezi datovými členy `CRecordset` pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_BINARY, SQL_VARBINARY nebo SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu [CByteArray](cbytearray-class.md)převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nMaxLength*<br/>
Maximální povolená délka přeneseného řetězce nebo pole. Výchozí hodnota *nMaxLength* je 255. Zákonné hodnoty jsou 1 až INT_MAX. Rozhraní framework přiděluje toto množství místa pro data. Chcete-li dosáhnout nejlepšího výkonu, předejte dostatečně velkou hodnotu, aby se přizpůsobila největší datové položce, kterou očekáváte.

### <a name="remarks"></a>Poznámky

Data ve zdroji dat těchto typů jsou mapována na a z typu `CByteArray` v sadě záznamů.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

Přenáší logická data mezi datovými `CRecordset` členy pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_BIT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu BOOL převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

Přenáší jednotlivé bajty mezi datovými `CRecordset` členy pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_TINYINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu BYTE převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

Přenáší `CTime` nebo TIMESTAMP_STRUCT data mezi datovými členy pole objektu `CRecordset` a sloupci záznamu na zdroji dat typu ODBC SQL_DATE, SQL_TIME nebo SQL_TIMESTAMP.

### <a name="syntax"></a>Syntaxe

```cpp
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

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu; hodnotu, která má být převedena. Různé verze funkce mají různé datové typy pro hodnotu:

První verze funkce přebírá odkaz na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt. Pro přenos ze sady záznamů do zdroje dat je tato hodnota převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

Druhá verze funkce přebírá odkaz na `TIMESTAMP_STRUCT` strukturu. Tuto strukturu musíte nastavit sami před voláním. Pro tuto verzi není k dispozici podpora výměny dat v dialogu (DDX) ani podpora průvodce kódem. Třetí verze funkce funguje podobně jako první verze s tím rozdílem, že přebírá odkaz na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu.

### <a name="remarks"></a>Poznámky

Verze `CTime` funkce ukládá režii některé zprostředkující zpracování a má poněkud omezený rozsah. Pokud zjistíte, že některý z těchto faktorů je příliš omezující, použijte druhou verzi funkce. Ale všimněte si jeho nedostatek kódu průvodce a podporu DDX a požadavek, že jste nastavili strukturu sami.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

Přenáší **dvojitá plovoucí** data mezi `CRecordset` datovými členy pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_DOUBLE.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **double**, převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

Přenáší celá data mezi datovými členy `CRecordset` pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **int**, převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

Přenáší dlouhá celá data mezi datovými `CRecordset` členy pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_INTEGER.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **long**převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

Přenáší binární data velkých objektů (BLOB) pomocí třídy [CLongBinary](clongbinary-class.md) mezi datovými členy pole objektu `CRecordset` a sloupci záznamu na zdroji dat typu ODBC SQL_LONGVARBINARY nebo SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat `CLongBinary`je hodnota typu , převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

Přenáší data s plovoucí desetinnou `CRecordset` desetinnou tácem mezi datovými členy pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_REAL.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **float**převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

Přenáší `CString` data mezi datovými `CRecordset` členy pole objektu a sloupci záznamu na zdroj dat typu ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL nebo SQL_NUMERIC.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy `CFieldExchange`. Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat `CString`je hodnota typu , převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nMaxLength*<br/>
Maximální povolená délka přeneseného řetězce nebo pole. Výchozí hodnota *nMaxLength* je 255. Právní hodnoty jsou 1 až INT_MAX). Rozhraní framework přiděluje toto množství místa pro data. Chcete-li dosáhnout nejlepšího výkonu, předejte dostatečně velkou hodnotu, aby se přizpůsobila největší datové položce, kterou očekáváte.

*nColumnType*<br/>
Používá se hlavně pro parametry. Celé číslo označující datový typ parametru. Tento typ je datový typ ODBC formuláře **SQL_XXX**.

*nMěřítko*<br/>
Určuje měřítko pro hodnoty typu ODBC SQL_DECIMAL nebo SQL_NUMERIC. *nScale* je užitečné pouze při nastavování hodnot parametrů. Další informace naleznete v tématu Přesnost, měřítko, délka a velikost zobrazení v dodatku D *referenčního programu programu ODBC SDK*.

### <a name="remarks"></a>Poznámky

Data ve zdroji dat všech těchto typů jsou `CString` mapována do a z v sadě záznamů.

### <a name="example"></a>Příklad

Tento příklad ukazuje `RFX_Text`několik volání . Všimněte si také `CFieldExchange::SetFieldType`dvou volání . Pro parametry je nutné `SetFieldType` napsat volání a jeho RFX volání. Volání výstupního sloupce a přidružená volání RFX jsou obvykle zapsána průvodcem kódem.

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

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

Přenáší více řádků bajtových dat ze sloupce zdroje dat ODBC `CRecordset`do odpovídajícího pole v odvozeném objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgByteVals*<br/>
Ukazatel na pole hodnot BYTE. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgByteVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

*nMaxLength*<br/>
Maximální povolená délka hodnot uložených v poli, na které se vztahuje *hodnota prgByteVals*. Chcete-li zajistit, že data nebudou zkrácena, předejte hodnotu dostatečně velkou, aby se přizpůsobila největší datové položce, kterou očekáváte.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat může mít typ ODBC SQL_BINARY, SQL_VARBINARY nebo SQL_LONGVARBINARY. Sada záznamů musí definovat datový člen pole typu ukazatel na BYTE.

Pokud inicializujete *prgByteVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Aby bylo možné sadu záznamů aktualizovat, musíte použít funkci `SQLSetPos`ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

Přenese více řádků logických dat ze sloupce zdroje dat ODBC do odpovídajícího pole v odvozeném `CRecordset`objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgBoolVals*<br/>
Ukazatel na pole bool hodnot. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgBoolVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít typ odbc SQL_BIT. Sada záznamů musí definovat datový člen pole typu ukazatele na BOOL.

Pokud inicializujete *prgBoolVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

Přenese více řádků jednotlivých bajtů ze sloupce zdroje dat `CRecordset`ODBC do odpovídajícího pole v odvozeném objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgByteVals*<br/>
Ukazatel na pole hodnot BYTE. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgByteVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít typ odbc SQL_TINYINT. Sada záznamů musí definovat datový člen pole typu ukazatel na BYTE.

Pokud inicializujete *prgByteVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

Přenáší více řádků TIMESTAMP_STRUCT dat ze sloupce zdroje dat ODBC `CRecordset`do odpovídajícího pole v odvozeném objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgTSVals*<br/>
Ukazatel na pole TIMESTAMP_STRUCT hodnot. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů. Další informace o datovém typu TIMESTAMP_STRUCT naleznete v tématu "Datové typy C" v dodatku D *referenčního programu programu ODBC SDK*.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgTSVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat může mít typ rozhraní ODBC SQL_DATE, SQL_TIME nebo SQL_TIMESTAMP. Sada záznamů musí definovat datový člen pole ukazatele typu, aby TIMESTAMP_STRUCT.

Pokud inicializujete *prgTSVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

Přenáší více řádků dat s dvojitou přesností s plovoucí desetinnou desetinnou `CRecordset`tácem ze sloupce zdroje dat ODBC do odpovídajícího pole odvozeného objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgDblVals*<br/>
Ukazatel na pole **dvojité** hodnoty. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgDblVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít typ odbc SQL_DOUBLE. Sada záznamů musí definovat datový člen pole ukazatele typu, který má **být zdvojený**.

Pokud inicializujete *prgDblVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

Přenáší celá data mezi datovými členy `CRecordset` pole objektu a sloupci záznamu na zdroji dat typu ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace o operacích, které `CFieldExchange` může objekt specifikovat, naleznete v článku Výměna pole [záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **int**, převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

### <a name="example"></a>Příklad

Viz [RFX_Text](#rfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

Přenese více řádků dlouhých celočíselných dat ze sloupce zdroje dat `CRecordset`ODBC do odpovídajícího pole v odvozeném objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgLongVals*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgLongVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít typ odbc SQL_INTEGER. Sada záznamů musí definovat datový člen pole typu na **long**.

Pokud inicializujete *prgLongVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

Přenáší více řádků dat s plovoucí desetinnou desetinnou desetinnou `CRecordset`hodnotou ze sloupce zdroje dat ODBC do odpovídajícího pole v odvozeném objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgFltVals*<br/>
Ukazatel na pole **plovoucí** hodnoty. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgFltVals*. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat musí mít typ odbc SQL_REAL. Sada záznamů musí definovat datový člen pole ukazatele typu k **floatu**.

Pokud inicializujete *prgFltVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Viz [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

Přenese více řádků znakových dat ze sloupce zdroje dat `CRecordset`ODBC do odpovídajícího pole v odvozeném objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt [CFieldExchange.](cfieldexchange-class.md) Tento objekt obsahuje informace k definování kontextu pro každé volání funkce. Další informace naleznete v článku [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szJméno*<br/>
Název datového sloupce.

*prgStrVals*<br/>
Ukazatel na pole lpstr hodnot. Toto pole uloží data, která mají být přenesena ze zdroje dat do sady záznamů. Všimněte si, že s aktuální verzí rozhraní ODBC tyto hodnoty nemohou být Unicode.

*prgLengths*<br/>
Ukazatel na pole dlouhých celých čísel. Toto pole bude ukládat délku v bajtů každé hodnoty v poli, na které se vztahuje *prgStrVals*. Tato délka vylučuje znak ukončení null. Všimněte si, že hodnota SQL_NULL_DATA budou uloženy, pokud odpovídající datová položka obsahuje hodnotu Null. Další podrobnosti naleznete v funkci `SQLBindCol` ROZHRANÍ API ROZHRANÍ ODBC v *referenční příručce programátora sady ODBC SDK*.

*nMaxLength*<br/>
Maximální povolená délka hodnot uložených v poli, na které se vztahuje *prgStrVals*, včetně znaku null termination. Chcete-li zajistit, že data nebudou zkrácena, předejte hodnotu dostatečně velkou, aby se přizpůsobila největší datové položce, kterou očekáváte.

### <a name="remarks"></a>Poznámky

Sloupec zdroje dat může mít typ ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL nebo SQL_NUMERIC. Sada záznamů musí definovat datový člen pole typu LPSTR.

Pokud inicializujete *prgStrVals* a *prgLengths* na HODNOTU NULL, budou pole, na která odkazují, přidělena automaticky, s velikostí roven velikosti sady řádků.

> [!NOTE]
> Hromadné pole záznamu výměna pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li, aby byla sada záznamů aktualizovatelná, `SQLSetPos`musíte použít funkci ROZHRANÍ API ROZHRANÍ ODBC .

Další informace naleznete v článcích [Sada záznamů: Načítání záznamů hromadně (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [Výměna pole záznamu (RFX).](../../data/odbc/record-field-exchange-rfx.md)

### <a name="example"></a>Příklad

Je nutné ručně psát `DoBulkFieldExchange` volání v přepsání. Tento příklad ukazuje `RFX_Text_Bulk`volání , stejně `RFX_Long_Bulk`jako volání do , pro přenos dat. Těmto voláním předchází volání [CFieldExchange::SetFieldType](cfieldexchange-class.md#setfieldtype). Všimněte si, že pro parametry je nutné volat funkce RFX namísto funkce Hromadné RFX.

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

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

Přenáší pole bajtů mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu [CByteArray](cbytearray-class.md)převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nPreAllocVelikost*<br/>
Rozhraní framework předem přiděluje toto množství paměti. Pokud vaše data jsou větší, rozhraní bude přiděleno více místa podle potřeby. Pro lepší výkon nastavte tuto velikost na hodnotu dostatečně velkou, aby se zabránilo přerozdělení. Výchozí velikost je definována v AFXDAO. H jako AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_DISABLE_FIELD_CACHE, nepoužívá dvojité ukládání do vyrovnávací paměti a je nutné volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami. Další možná hodnota, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti a není třeba provést další práci k označení polí dirty nebo Null. Z důvodů výkonu a paměti se této hodnotě vyhněte, pokud binární data nejsou relativně malá.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení pro všechna pole uložena do vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_BYTES v DAO a typem [CByteArray](cbytearray-class.md) v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

Přenáší logická data mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu BOOL převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_BOOL v DAO a typem BOOL v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

Přenáší jednotlivé bajty mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu BYTE převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_BYTES v DAO a typem BYTE v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

Přenáší data měny mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je tato hodnota převzata ze zadaného datového člena typu [COleCurrency](colecurrency-class.md). Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_CURRENCY v DAO a [typem COleCurrency](colecurrency-class.md) v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

Přenáší data času a data mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Funkce přebírá odkaz na [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu. Pro přenos ze sady záznamů do zdroje dat je tato hodnota převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_DATE v DAO a typem [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) v sadě záznamů.

> [!NOTE]
> `COleDateTime`nahrazuje [CTime](../../atl-mfc-shared/reference/ctime-class.md) a TIMESTAMP_STRUCT pro tento účel ve třídách DAO. `CTime`a TIMESTAMP_STRUCT se stále používají pro třídy přístupu k datům založené na rozhraní ODBC.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

Přenáší **dvojitá plovoucí** data mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **double**, převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_R8 v DAO a zadejte **dvojité float** v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

Přenáší dlouhá data celéčíslo mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **long**převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_I4 v DAO a **typem long** v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**Důležité informace** Doporučujeme používat [DFX_Binary](#dfx_binary) místo této funkce.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu [CLongBinary](clongbinary-class.md)převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwPreAllocVelikost*<br/>
Rozhraní framework předem přiděluje toto množství paměti. Pokud vaše data jsou větší, rozhraní bude přiděleno více místa podle potřeby. Pro lepší výkon nastavte tuto velikost na hodnotu dostatečně velkou, aby se zabránilo přerozdělení.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DISABLE_FIELD_CACHE, nepoužívá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_ENABLE_FIELD_CACHE. Používá dvojité ukládání do vyrovnávací paměti a není třeba provést další práci označit pole dirty nebo Null. Z důvodů výkonu a paměti se této hodnotě vyhněte, pokud binární data nejsou relativně malá.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

`DFX_LongBinary`je k dispozici pro kompatibilitu s třídami MFC ODBC. Funkce `DFX_LongBinary` přenáší binární data s velkým objektem `CLongBinary` (BLOB) pomocí třídy mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat. Data jsou mapována mezi typem DAO_BYTES v DAO a typem [CLongBinary](clongbinary-class.md) v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

Přenáší krátká data celého čísla mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **short**převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_I2 v DAO a **textem krátký** v sadě záznamů.

> [!NOTE]
> `DFX_Short`je ekvivalentní [RFX_Int](#rfx_int) pro třídy založené na ROZHRANÍ ODBC.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

Přenáší data s plovoucí desetinnou desetinnou tácem mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu **float**převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíš `SetFieldDirty` zavolat i `SetFieldNull` sebe.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_R4 v DAO a **typem float** v sadě záznamů.

### <a name="example"></a>Příklad

Viz [DFX_Text](#dfx_text).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

Přenáší `CString` data mezi datovými členy pole objektu [CDaoRecordset](cdaorecordset-class.md) a sloupci záznamu ve zdroji dat.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace k definování kontextu pro každé volání funkce.

*szJméno*<br/>
Název datového sloupce.

*Hodnotu*<br/>
Hodnota uložená v uvedeném datovém členu – hodnota, která má být přenesena. Pro přenos ze sady záznamů do zdroje dat je hodnota typu [CString](../../atl-mfc-shared/reference/cstringt-class.md)převzata ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů je hodnota uložena v zadaném datovém členu.

*nPreAllocVelikost*<br/>
Rozhraní framework předem přiděluje toto množství paměti. Pokud vaše data jsou větší, rozhraní bude přiděleno více místa podle potřeby. Pro lepší výkon nastavte tuto velikost na hodnotu dostatečně velkou, aby se zabránilo přerozdělení.

*dwBindOptions*<br/>
Možnost, která umožňuje využít mechanismus dvojité vyrovnávací paměti knihovny MFC pro zjišťování polí sady záznamů, která se změnila. Výchozí, AFX_DAO_ENABLE_FIELD_CACHE, používá dvojité ukládání do vyrovnávací paměti. Další možnou hodnotou je AFX_DAO_DISABLE_FIELD_CACHE. Pokud zadáte tuto hodnotu, knihovna MFC nekontroluje toto pole. Musíte volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami.

> [!NOTE]
> Nastavením [sady CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields)můžete určit, zda budou data ve výchozím nastavení dvojitá ve vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Data jsou mapována mezi typem DAO_CHAR v DAO (nebo, pokud je definován symbol _UNICODE, DAO_WCHAR) a typem [CString](../../atl-mfc-shared/reference/cstringt-class.md) v sadě záznamů.  n

### <a name="example"></a>Příklad

Tento příklad ukazuje `DFX_Text`několik volání . Všimněte si také dvě volání [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Musíte napsat první volání `SetFieldType` a jeho **volání DFX.** Druhé volání a jeho přidružené **Volání DFX** jsou obvykle zapsány průvodcem kódu, který vygeneroval třídu.

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

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[Sada záznamů CDao::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
