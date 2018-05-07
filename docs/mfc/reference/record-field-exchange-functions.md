---
title: Funkce výměny polí záznamů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 564d797a30e4b2d8518c73c5f7589aae205b6907
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-functions"></a>Funkce výměny polí v záznamu
Toto téma obsahuje seznam výměna pole záznamu (RFX, hromadné RFX a DFX) použít k automatizaci přenos dat mezi objekt sady záznamů a zdrojem dat a provádění dalších operací data funkce.  
  
 Pokud používáte třídy založené na rozhraní ODBC a jste implementovali hromadné načítání řádků, je nutné ručně přepsat `DoBulkFieldExchange` členské funkce `CRecordset` voláním funkce RFX hromadné pro každého člena dat odpovídající sloupec datového zdroje.  
  
 Pokud ještě implementována hromadné načítání řádků v třídy založené na rozhraní ODBC, nebo pokud používáte třídy založené na rozhraní DAO, pak se přepíše ClassWizard `DoFieldExchange` členské funkce `CRecordset` nebo `CDaoRecordset` voláním funkce RFX (pro ODBC – třídy ) nebo DFX – funkce (pro třídy DAO) pro každé pole datového člena ve vaší sadě záznamů.  
  
 Funkce výměny polí záznamu přenos dat při každém volání rozhraní `DoFieldExchange` nebo `DoBulkFieldExchange`. Jednotlivé funkce přenáší určitého datového typu.  
  
 Další informace o tom, jak se tyto funkce používají, najdete v článcích [výměna polí záznamu: jak RFX funguje (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pro sloupce dat, která dynamicky vázat, můžete také volat funkce RFX nebo DFX sami, jak je popsáno v článcích [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Kromě toho můžete napsat vlastní vlastní RFX nebo DFX rutiny, jak je popsáno v technická Poznámka [43](../../mfc/tn043-rfx-routines.md) (pro rozhraní ODBC) a technická Poznámka [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pro rozhraní DAO).  
  
 Příklad RFX a Bulk RFX funguje, jak se zobrazují v `DoFieldExchange` a `DoBulkFieldExchange` funkce, najdete v části [RFX_Text](#rfx_text) a rfx_text_bulk – # [rfx_text_bulk –]). DFX – funkce jsou velmi podobné funkce RFX.  
  
### <a name="rfx-functions-odbc"></a>RFX – funkce (ODBC)  
  
|||  
|-|-|  
|[RFX_Binary –](#rfx_binary)|Přenosy pole bajtů typu [CByteArray](cbytearray-class.md).|  
|[Rfx_bool –](#rfx_bool)|Přenáší data logické hodnoty.|  
|[Rfx_byte –](#rfx_byte)|Přenosy dat byl jediný bajt.|  
|[RFX_Date –](#rfx_date)|Převede čas a datum dat pomocí [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo **TIMESTAMP_STRUCT z**.|  
|[Rfx_double –](#rfx_double)|Přenáší data Dvojitá přesnost float.|  
|[Rfx_int –](#rfx_int)|Přenosy dat celé číslo.|  
|[Rfx_long –](#rfx_long)|Přenosy dlouhé celé číslo data.|  
|[Rfx_longbinary –](#rfx_longbinary)|Přenosy dat binární rozsáhlý objekt (binární rozsáhlý OBJEKT) s objekt [CLongBinary](clongbinary-class.md) třídy.|  
|[Rfx_single –](#rfx_single)|Převody plovoucí data.|  
|[RFX_Text –](#rfx_text)|Přenosy řetězcová data.|  
  
### <a name="bulk-rfx-functions-odbc"></a>Hromadné funkce RFX (ODBC)  
  
|||  
|-|-|  
|[Rfx_binary_bulk –](#rfx_binary_bulk)|Přenosy dat bajtové pole.|  
|[Rfx_bool_bulk –](#rfx_bool_bulk)|Přenáší pole data logické hodnoty.|  
|[Rfx_byte_bulk –](#rfx_byte_bulk)|Převede pole jednoho bajtů.|  
|[Rfx_date_bulk –](#rfx_date_bulk)|Přenosy dat typu pole **TIMESTAMP_STRUCT z**.|  
|[Rfx_double_bulk –](#rfx_double_bulk)|Převede pole dat s dvojitou přesností, s plovoucí desetinnou čárkou.|  
|[Rfx_int_bulk –](#rfx_int_bulk)|Převede pole dat celé číslo.|  
|[Rfx_long_bulk –](#rfx_long_bulk)|Převede pole dat dlouhých celých čísel.|  
|[Rfx_single_bulk –](#rfx_single_bulk)|Převede pole dat s plovoucí desetinnou čárkou.|  
|[Rfx_text_bulk –](#rfx_text_bulk)|Přenosy dat typu pole **LPSTR**.|  
  
### <a name="dfx-functions-dao"></a>DFX – funkce (DAO)  
  
|||
|-|-|  
|[Dfx_binary –](#dfx_binary)|Přenosy pole bajtů typu [CByteArray](cbytearray-class.md).|  
|[Dfx_bool –](#dfx_bool)|Přenáší data logické hodnoty.|  
|[Dfx_byte –](#dfx_byte)|Přenosy dat byl jediný bajt.|  
|[Dfx_currency –](#dfx_currency)|Přenosy dat měny, typu [COleCurrency](colecurrency-class.md).|  
|[Dfx_datetime –](#dfx_datetime)|Přenosy dat a času, typu [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|  
|[Dfx_double –](#dfx_double)|Přenáší data Dvojitá přesnost float.|  
|[Dfx_long –](#dfx_long)|Přenosy dlouhé celé číslo data.|  
|[Dfx_longbinary –](#dfx_longbinary)|Přenosy dat binární rozsáhlý objekt (binární rozsáhlý OBJEKT) s objekt `CLongBinary` třídy. Pro rozhraní DAO, je doporučeno používat [dfx_binary –](#dfx_binary) místo.|  
|[Dfx_short –](#dfx_short)|Přenosy krátkodobých dat celé číslo.|  
|[Dfx_single –](#dfx_single)|Převody plovoucí data.|  
|[Dfx_text –](#dfx_text)|Přenosy řetězcová data.|  

 =============================================

## <a name="rfx_binary"></a>  RFX_Binary –
Přenosy mezi pole datových členů z pole bajtů `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_BINARY**, **SQL_VARBINARY**, nebo **SQL_ LONGVARBINARY**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Binary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CByteArray& value,  
   int nMaxLength = 255);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu [CByteArray](cbytearray-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `nMaxLength`  
 Maximální povolená délka řetězce nebo pole přenosu. Výchozí hodnota `nMaxLength` je 255. Platné hodnoty jsou 1 `INT_MAX`. Rozhraní framework přiděluje toto množství místa pro data. Pro nejlepší výkon předáte hodnotu dostatečně velké na to, aby dokázala pojmout největší položku dat, které očekáváte.  
  
### <a name="remarks"></a>Poznámky  
 Data ve zdroji dat z těchto typů je mapována do a z typu `CByteArray` v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_bool"></a>  Rfx_bool –
Boolean – datový přenos mezi pole datových členů z `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_BIT**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Bool(  
   CFieldExchange* pFX,  
   const char* szName,  
   BOOL& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **BOOL**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_byte"></a>  Rfx_byte –
Přenosy jednotné bajtů mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_TINYINT**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Byte(  
   CFieldExchange* pFX,  
   const char* szName,  
   BYTE& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **BAJTŮ**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_date"></a>  RFX_Date –
Přenosy `CTime` nebo **TIMESTAMP_STRUCT z** dat mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_DATE**, **SQL_TIME**, nebo **SQL_TIMESTAMP**.  
  
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
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen; hodnota, které se mají přenést. Různé verze funkce trvat různé datové typy pro hodnotu:  
  
 Odkaz na přebírá první verze součásti funkce [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu. Pro přenos z sady záznamů ke zdroji dat je tato hodnota převzat ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 Druhá verze funkce trvá odkaz na **TIMESTAMP_STRUCT z** struktura. Musíte vytvořit tuto strukturu sami před voláním. Podpora ani výměna dialogových dat (DDX) ani kód průvodce podpora je k dispozici pro tuto verzi. Třetí verzi funkce funguje podobně na první verzi s tím rozdílem, že trvá odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CTime` Verze funkce ukládá režii některé zprostředkující zpracování a má mírně omezené rozsah. Pokud zjistíte, buď tyto faktory příliš omezení, použijte druhá verze funkce. Ale nedostatečná kód průvodce a podpora DDX a požadavky, které jste nastavili strukturu sami.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_double"></a>  Rfx_double –
Přenosy **dvojité float** dat mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_DOUBLE**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Double(  
   CFieldExchange* pFX,  
   const char* szName,  
   double& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **dvojité**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_int"></a>  Rfx_int –
Přenosy dat celé číslo mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_SMALLINT**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu `int`, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_long"></a>  Rfx_long –
Přenosy dat dlouhé celé číslo mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_INTEGER**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Long(  
   CFieldExchange* pFX,  
   const char* szName,  
   LONG&   
value );  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **dlouho**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
## <a name="rfx_longbinary"></a>  Rfx_longbinary –
Přenosy dat binární rozsáhlý objekt (binární rozsáhlý OBJEKT) pomocí třídy [CLongBinary](clongbinary-class.md) mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_LONGVARBINARY**nebo **SQL_LONGVARCHAR**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_LongBinary(  
   CFieldExchange* pFX,  
   const char* szName,  
   CLongBinary& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu `CLongBinary`, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_single"></a>  Rfx_single –
Přenosy dat s plovoucí desetinnou čárkou mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_REAL**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Single(  
   CFieldExchange* pFX,  
   const char* szName,  
   float& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **float**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  

## <a name="rfx_text"></a>  RFX_Text –
Přenosy `CString` dat mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_ VARCHAR**, **SQL_DECIMAL**, nebo **SQL_NUMERIC**.  
  
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
 `pFX`  
 Ukazatel na objekt třídy `CFieldExchange`. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu `CString`, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `nMaxLength`  
 Maximální povolená délka řetězce nebo pole přenosu. Výchozí hodnota `nMaxLength` je 255. Platné hodnoty jsou 1 `INT_MAX`). Rozhraní framework přiděluje toto množství místa pro data. Pro nejlepší výkon předáte hodnotu dostatečně velké na to, aby dokázala pojmout největší položku dat, které očekáváte.  
  
 *nColumnType*  
 Používá se především pro parametry. Celé číslo, která určuje datový typ parametru. Typ je typ dat rozhraní ODBC formuláře **SQL_XXX**.  
  
 `nScale`  
 Určuje měřítko pro hodnoty typu ODBC **SQL_DECIMAL** nebo **SQL_NUMERIC**. `nScale` je užitečné pouze při nastavování hodnot parametrů. Další informace naleznete v tématu "Přesnost, měřítko, délku a zobrazovaná velikost" v dodatku D *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Data ve zdroji dat všech těchto typů je mapována do a z `CString` v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje několik volání `RFX_Text`. Všimněte si také dva volání `CFieldExchange::SetFieldType`. Pro parametry musíte napsat volání `SetFieldType` a jeho RFX volání. Výstupní sloupce volání a jeho přidružené volání RFX se obvykle zapisují Průvodcem kódu.  
  
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
Přenosy více řádků bajtů dat ze sloupce zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozené objektu.  
  
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
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgByteVals`  
 Ukazatel na pole **BAJTŮ** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgByteVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
 `nMaxLength`  
 Maximální povolená délka hodnoty uložené v poli, na kterou odkazuje `prgByteVals`. Aby se zajistilo, že data nebudou zkráceny, předáte hodnotu dostatečně velké na to, aby dokázala pojmout největší položku dat, které očekáváte.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojový sloupec dat může mít typ ODBC **SQL_BINARY**, **SQL_VARBINARY**, nebo **SQL_LONGVARBINARY**. Sady záznamů musí definovat členem pole datového typu ukazatel na **BAJTŮ**.  
  
 Pokud inicializaci `prgByteVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Aby bylo možné sady záznamů lze aktualizovat, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_bool_bulk"></a>  Rfx_bool_bulk –
Přenosy více řádků Boolean dat ze sloupce zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozené objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Bool_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL** prgBoolVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgBoolVals`  
 Ukazatel na pole **BOOL** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgBoolVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Sloupci zdroje dat musí mít typ ODBC **SQL_BIT**. Sady záznamů musí definovat členem pole datového typu ukazatel na **BOOL**.  
  
 Pokud inicializaci `prgBoolVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_byte_bulk"></a>  Rfx_byte_bulk –
Přenese jeden bajtů více řádků ze sloupce zdroje dat ODBC odpovídající pole v `CRecordset`-odvozené objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Byte_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE** prgByteVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgByteVals`  
 Ukazatel na pole **BAJTŮ** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgByteVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Sloupci zdroje dat musí mít typ ODBC **SQL_TINYINT**. Sady záznamů musí definovat členem pole datového typu ukazatel na **BAJTŮ**.  
  
 Pokud inicializaci `prgByteVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
## <a name="rfx_date_bulk"></a>  Rfx_date_bulk –
Přenosy z více řádků **TIMESTAMP_STRUCT z** data ze sloupce zdroje dat ODBC do odpovídající pole v `CRecordset`-odvozené objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Date_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   TIMESTAMP_STRUCT** prgTSVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgTSVals`  
 Ukazatel na pole **TIMESTAMP_STRUCT z** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů. Další informace o **TIMESTAMP_STRUCT z** datový typ, naleznete v tématu "C datové typy" v dodatku D *referenční příručka programátora SDK ODBC*.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgTSVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojový sloupec dat může mít typ ODBC **SQL_DATE**, **SQL_TIME**, nebo **SQL_TIMESTAMP**. Sady záznamů musí definovat členem pole datového typu ukazatel na **TIMESTAMP_STRUCT z**.  
  
 Pokud inicializaci `prgTSVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_double_bulk"></a>  Rfx_double_bulk –
Přenosy více řádků s dvojitou přesností a s plovoucí desetinnou čárkou dat ze sloupce zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozené objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Double_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   double** prgDblVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgDblVals`  
 Ukazatel na pole **dvojité** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgDblVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Sloupci zdroje dat musí mít typ ODBC **SQL_DOUBLE**. Sady záznamů musí definovat členem pole datového typu ukazatel na **dvojité**.  
  
 Pokud inicializaci `prgDblVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_int_bulk"></a>  Rfx_int_bulk –
Přenosy dat celé číslo mezi členy pole data `CRecordset` objekt a sloupce ve zdroji dat rozhraní ODBC typu záznamu **SQL_SMALLINT**.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Int(  
   CFieldExchange* pFX,  
   const char* szName,  
   int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CFieldExchange](cfieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace o operacích `CFieldExchange` objekt můžete určit, najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu `int`, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
### <a name="example"></a>Příklad  
 V tématu [RFX_Text](#rfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_long_bulk"></a>  Rfx_long_bulk –
Přenosy více řádků dlouhých celočíselných dat ze sloupce zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozené objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Long_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   long** prgLongVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgLongVals`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgLongVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Sloupci zdroje dat musí mít typ ODBC **SQL_INTEGER**. Sady záznamů musí definovat členem pole datového typu ukazatel na **dlouho**.  
  
 Pokud inicializaci `prgLongVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  

## <a name="rfx_single_bulk"></a>  Rfx_single_bulk –
Přenosy více řádků s plovoucí desetinnou čárkou dat ze sloupce zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozené objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void RFX_Single_Bulk(  
   CFieldExchange* pFX,  
   LPCTSTR szName,  
   float** prgFltVals,  
   long** prgLengths);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgFltVals`  
 Ukazatel na pole **float** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgFltVals`. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
### <a name="remarks"></a>Poznámky  
 Sloupci zdroje dat musí mít typ ODBC **SQL_REAL**. Sady záznamů musí definovat členem pole datového typu ukazatel na **float**.  
  
 Pokud inicializaci `prgFltVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 V tématu [rfx_text_bulk –](#rfx_text_bulk).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  

## <a name="rfx_text_bulk"></a>  Rfx_text_bulk –
Přenosy více řádků dat znaků ze sloupce zdroje dat ODBC na odpovídající pole v `CRecordset`-odvozené objektu.  
  
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
 `pFX`  
 Ukazatel [CFieldExchange](cfieldexchange-class.md) objektu. Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce. Další informace najdete v článku [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 `szName`  
 Název sloupce dat.  
  
 `prgStrVals`  
 Ukazatel na pole **LPSTR** hodnoty. Toto pole se uloží data přenášet ze zdroje dat na sadu záznamů. Všimněte si, že se v aktuální verzi rozhraní ODBC, nelze tyto hodnoty kódování Unicode.  
  
 `prgLengths`  
 Ukazatel na pole dlouho celých čísel. Toto pole se uloží délka v bajtech každou hodnotu v poli, na kterou odkazuje `prgStrVals`. Tato délka vyloučí null ukončovací znak. Všimněte si, že hodnota **SQL_NULL_DATA** bude uložen, pokud odpovídající položka dat obsahuje hodnotu Null. Další podrobnosti najdete v tématu funkce rozhraní API ODBC **SQLBindCol** v *referenční příručka programátora SDK ODBC*.  
  
 `nMaxLength`  
 Maximální povolená délka hodnoty uložené v poli, na kterou odkazuje `prgStrVals`, včetně znaku ukončení hodnotu null. Aby se zajistilo, že data nebudou zkráceny, předáte hodnotu dostatečně velké na to, aby dokázala pojmout největší položku dat, které očekáváte.  
  
### <a name="remarks"></a>Poznámky  
 Zdrojový sloupec dat může mít typ ODBC **SQL_LONGVARCHAR**, **SQL_CHAR**, **SQL_VARCHAR**, **SQL_DECIMAL**, nebo **SQL_NUMERIC**. Sady záznamů musí definovat pole datového člena typu **LPSTR**.  
  
 Pokud inicializaci `prgStrVals` a `prgLengths` k **NULL**, pak tato pole ukazovaly na přidělí automaticky, s velikostí, které se rovná velikosti řádků.  
  
> [!NOTE]
>  Hromadná výměna pole záznamu pouze přenáší data ze zdroje dat do objektu sady záznamů. Chcete-li sady záznamů v aktualizovatelné, musíte použít funkce rozhraní API ODBC **SQLSetPos**.  
  
 Další informace najdete v článcích [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) a [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
### <a name="example"></a>Příklad  
 Musíte ručně napsat volání vaší `DoBulkFieldExchange` přepsat. Tento příklad ukazuje volání `RFX_Text_Bulk`, a také volání `RFX_Long_Bulk`, pro přenos dat. Tyto volání předchází volání [CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md). Všimněte si, že se pro parametry, musí volat funkce RFX místo funkcí RFX hromadně.  
  
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

## <a name="dfx_binary"></a>  Dfx_binary –
Přenosy mezi pole datových členů z pole bajtů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
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
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu [CByteArray](cbytearray-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `nPreAllocSize`  
 Rozhraní framework preallocates toto množství paměti. Pokud vaše data jsou větší, rozhraní se přidělit více místa podle potřeby. Pro lepší výkon nastavená na hodnotu dostatečně velké na to, aby se zabránilo přerozdělení této velikosti. Výchozí velikost je definována v AFXDAO. H souboru jako **AFX_DAO_BINARY_DEFAULT_SIZE**.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_DISABLE_FIELD_CACHE`, nepoužívá, není použití dvojité ukládání do vyrovnávací paměti, a musí volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami. Další možná hodnota `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti a vy nemusíte práci, označit pole nesprávné nebo hodnota Null. Z důvodu paměti výkonu a nepoužívejte tuto hodnotu Pokud binárních dat je poměrně malý.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti pro všechna pole ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_BYTES** v rozhraní DAO a typ [CByteArray](cbytearray-class.md) v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  

## <a name="dfx_bool"></a>  Dfx_bool –
Boolean – datový přenos mezi pole datových členů z [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Bool(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BOOL& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **BOOL**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_BOOL** v rozhraní DAO a typ **BOOL** v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_byte"></a>  Dfx_byte –
Přenosy jednotné bajtů mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Byte(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   BYTE& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **BAJTŮ**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_BYTES** v rozhraní DAO a typ **BAJTŮ** v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_currency"></a>  Dfx_currency –
Přenosy dat měny mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Currency(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleCurrency& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů ke zdroji dat, tato hodnota je převzat ze zadaných dat člen typu [COleCurrency](colecurrency-class.md). Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_CURRENCY** v rozhraní DAO a typ [COleCurrency](colecurrency-class.md) v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_datetime"></a>  Dfx_datetime –
Přenosy dat a času mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_DateTime(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   COleDateTime& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Funkce přijímá odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu. Pro přenos z sady záznamů ke zdroji dat je tato hodnota převzat ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_DATE** v rozhraní DAO a typ [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) v sadě záznamů.  
  
> [!NOTE]
>  `COleDateTime` nahradí [CTime](../../atl-mfc-shared/reference/ctime-class.md) a **TIMESTAMP_STRUCT z** pro tento účel v třídy DAO. `CTime` a **TIMESTAMP_STRUCT z** jsou nadále používat pro přístup na základě ODBC datových tříd.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_double"></a>  Dfx_double –
Přenosy **dvojité float** dat mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Double(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   double& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **dvojité**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_R8** v rozhraní DAO a typ **dvojité float** v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_long"></a>  Dfx_long –
Přenosy dat dlouhé celé číslo mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Long(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   long& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **dlouho**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_I4** v rozhraní DAO a typ **dlouho** v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  

## <a name="dfx_longbinary"></a>  Dfx_longbinary –
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
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu [CLongBinary](clongbinary-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 *dwPreAllocSize*  
 Rozhraní framework preallocates toto množství paměti. Pokud vaše data jsou větší, rozhraní se přidělit více místa podle potřeby. Pro lepší výkon nastavená na hodnotu dostatečně velké na to, aby se zabránilo přerozdělení této velikosti.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, **AFX_DISABLE_FIELD_CACHE**, nepoužívá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_ENABLE_FIELD_CACHE`. Používá dvojité ukládání do vyrovnávací paměti a vy nemusíte práci, označit pole nesprávné nebo hodnota Null. Z důvodu paměti výkonu a nepoužívejte tuto hodnotu Pokud binárních dat je poměrně malý.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 `DFX_LongBinary` slouží k zajištění kompatibility s třídy knihovny MFC rozhraní ODBC. `DFX_LongBinary` Funkce přenáší binární-data rozsáhlého objektu (binární rozsáhlý OBJEKT) pomocí třídy `CLongBinary` mezi pole datových členů z [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji. Data je mapována mezi typy **DAO_BYTES** v rozhraní DAO a typ [CLongBinary](clongbinary-class.md) v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_short"></a>  Dfx_short –
Přenosy krátkodobých dat celé číslo mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Short(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   short& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **krátké**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_I2** v rozhraní DAO a typ **krátké** v sadě záznamů.  
  
> [!NOTE]
>  `DFX_Short` je ekvivalentní [rfx_int –](#rfx_int) pro třídy založené na rozhraní ODBC.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  

## <a name="dfx_single"></a>  Dfx_single –
Přenosy dat s plovoucí desetinnou čárkou mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
### <a name="syntax"></a>Syntaxe  
  
```
void AFXAPI DFX_Single(  
   CDaoFieldExchange* pFX,  
   LPCTSTR szName,  
   float& value,  
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);  
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu **float**, jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat `SetFieldDirty` a `SetFieldNull` sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_R4** v rozhraní DAO a typ **float** v sadě záznamů.  
  
### <a name="example"></a>Příklad  
 V tématu [dfx_text –](#dfx_text).  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

## <a name="dfx_text"></a>  Dfx_text –
Přenosy `CString` dat mezi pole datových členů [CDaoRecordset](cdaorecordset-class.md) objekt a sloupce záznamu na datovém zdroji.  
  
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
 `pFX`  
 Ukazatel na objekt třídy [CDaoFieldExchange](cdaofieldexchange-class.md). Tento objekt obsahuje informace, které definovat kontext pro každé volání funkce.  
  
 `szName`  
 Název sloupce dat.  
  
 *value*  
 Hodnota uložená v uvedených datový člen – hodnota, která má být převedena. Pro přenos z sady záznamů do zdroje dat, je hodnota typu [CString](../../atl-mfc-shared/reference/cstringt-class.md), jsou převzaty ze zadaného datového člena. Pro přenos ze zdroje dat do sady záznamů hodnota je uložena ve členovi zadaná data.  
  
 `nPreAllocSize`  
 Rozhraní framework preallocates toto množství paměti. Pokud vaše data jsou větší, rozhraní se přidělit více místa podle potřeby. Pro lepší výkon nastavená na hodnotu dostatečně velké na to, aby se zabránilo přerozdělení této velikosti.  
  
 `dwBindOptions`  
 Možnost, která umožňuje využít výhod dvojité vyrovnávací paměti mechanismus pro MFC pro zjišťování polí záznamů, které se změnily. Výchozí, `AFX_DAO_ENABLE_FIELD_CACHE`, používá dvojité ukládání do vyrovnávací paměti. Je možné hodnota `AFX_DAO_DISABLE_FIELD_CACHE`. Pokud zadáte tuto hodnotu, MFC nemá žádná kontrola v tomto poli. Je třeba volat [SetFieldDirty](cdaorecordset-class.md#setfielddirty) a [SetFieldNull](cdaorecordset-class.md#setfieldnull) sami.  
  
> [!NOTE]
>  Můžete řídit, jestli data jsou dvojité vyrovnávací paměti ve výchozím nastavení nastavením [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).  
  
### <a name="remarks"></a>Poznámky  
 Data je mapována mezi typy **DAO_CHAR** v rozhraní DAO (nebo, pokud symbol **_UNICODE** je definován **DAO_WCHAR**) a typ [CString](../../atl-mfc-shared/reference/cstringt-class.md) v Sada záznamů.  n
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje několik volání `DFX_Text`. Všimněte si také dva volání [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Musíte napsat první volání `SetFieldType` a jeho **DFX** volání. Druhé volání a jeho přidružený **DFX** volání zapisují normálně průvodcem kód, který vygenerované třídy.  
  
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
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)   
 [CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)   
 [CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)

