---
title: CDynamicStringAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: a0590bc015c5487315b8cbd38f0baf91eb3082cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211861"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor – třída

Umožňuje přístup ke zdroji dat, když nemáte žádné znalosti o schématu databáze (podkladové struktuře databáze).

## <a name="syntax"></a>Syntaxe

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Požadavky

**Záhlaví**: atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetString](#getstring)|Načte zadaná data sloupce jako řetězec.|
|[SetString](#setstring)|Nastaví zadaná data sloupce jako řetězec.|

## <a name="remarks"></a>Poznámky

I když [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) požaduje data v nativním formátu hlášené poskytovatelem, `CDynamicStringAccessor` vyžaduje, aby zprostředkovatel načetl všechna data, ke kterým se přistupovalo z úložiště dat, jako řetězcová data. To je užitečné hlavně při jednoduchých úlohách, které nevyžadují výpočet hodnot v úložišti dat, jako je například zobrazení nebo tisk obsahu úložiště dat.

Nativní typ dat sloupce v úložišti dat nezáleží na tom, Pokud zprostředkovatel podporuje převod dat, poskytne data ve formátu řetězce. Pokud zprostředkovatel nepodporuje převod z nativního datového typu na řetězec (což není běžné), bude žádající volání vracet hodnotu úspěchu DB_S_ERRORSOCCURED a stav odpovídajícího sloupce bude označovat problém s převodem DBSTATUS_E_CANTCONVERTVALUE.

K získání informací o sloupci použijte `CDynamicStringAccessor` metody. Tyto informace o sloupci slouží k vytvoření přístupového objektu dynamicky v době běhu.

Informace o sloupci jsou uloženy ve vyrovnávací paměti vytvořené a spravované touto třídou. Získejte data z vyrovnávací paměti pomocí [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)nebo ji uložte do vyrovnávací paměti pomocí [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

Diskuzi a příklady použití tříd dynamického přistupujícího objektu naleznete v tématu [použití dynamických přístupových objektů](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a>CDynamicStringAccessor:: GetString

Načte zadaná data sloupce jako řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pColumnName*<br/>
pro Ukazatel na řetězec znaků, který obsahuje název sloupce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na hodnotu řetězce načtený ze zadaného sloupce. Hodnota je typu `BaseType`, což bude **char** nebo **WCHAR** v závislosti na tom, zda je _UNICODE definována nebo nikoli. Vrátí hodnotu NULL, pokud zadaný sloupec nebyl nalezen.

### <a name="remarks"></a>Poznámky

Druhý formulář pro přepsání převezme název sloupce jako řetězec ANSI. Třetí formulář pro přepsání převezme název sloupce jako řetězec Unicode.

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a>CDynamicStringAccessor:: SetString

Nastaví zadaná data sloupce jako řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
pro Číslo sloupce Počet sloupců začíná 1. Speciální hodnota 0 odkazuje na sloupec Bookmark, pokud existuje.

*pColumnName*<br/>
pro Ukazatel na řetězec znaků, který obsahuje název sloupce.

*údajů*<br/>
pro Ukazatel na řetězcová data, která mají být zapsána do zadaného sloupce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na hodnotu řetězce, na který chcete nastavit zadaný sloupec. Hodnota je typu `BaseType`, což bude **char** nebo **WCHAR** v závislosti na tom, zda je _UNICODE definována nebo nikoli.

### <a name="remarks"></a>Poznámky

Druhý formulář pro přepsání převezme název sloupce jako řetězec ANSI a třetí formulář přepsání převezme název sloupce jako řetězec Unicode.

Pokud je _SECURE_ATL definována tak, aby měla nenulovou hodnotu, vygeneruje se chyba kontrolního výrazu modulu runtime, pokud je vstupní *datový* řetězec delší než maximální povolená délka odkazovaného datového sloupce. V opačném případě se vstupní řetězec zkrátí, pokud je delší než maximální povolená délka.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA – třída](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW – třída](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor – třída](../../data/oledb/cxmlaccessor-class.md)
