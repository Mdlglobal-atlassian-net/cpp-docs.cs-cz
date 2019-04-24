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
ms.openlocfilehash: 6ba56143beb3411734899839a46ab42992dfa4d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230992"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor – třída

Umožňuje přístup ke zdroji dat, když nemají žádné informace o schématu databáze (základní strukturu vaší databáze).

## <a name="syntax"></a>Syntaxe

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Požadavky

**Hlavička**: také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetString](#getstring)|Načte zadaný sloupec data jako řetězec.|
|[SetString –](#setstring)|Nastaví zadaný sloupec data jako řetězec.|

## <a name="remarks"></a>Poznámky

Zatímco [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) vyžádá data v nativním formátu hlášené poskytovatelem, `CDynamicStringAccessor` požadavků, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce dat. To je užitečné zejména pro jednoduché úlohy, které nevyžadují výpočet hodnot v úložišti dat, jako je například zobrazení nebo tisk obsah datového úložiště.

Nativní typ sloupce dat v úložišti dat, nezáleží; jako poskytovatel může podporovat převod dat, poskytne data ve formátu řetězce. Pokud zprostředkovatel nepodporuje převod z nativního datového typu na řetězec (což není běžné), žádost o volání vrátí hodnotu úspěch DB_S_ERRORSOCCURED a stavu pro odpovídající sloupce budou indikovat problém převod s DBSTATUS_E_CANTCONVERTVALUE.

Použití `CDynamicStringAccessor` metody získat informace o sloupci. Informace o tomto sloupci použijete k vytvoření přistupující objekt dynamicky za běhu.

Informace o sloupci je uložená do vyrovnávací paměti, vytvářet a spravovat touto třídou. Získání dat z vyrovnávací paměti pomocí [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), nebo je uložit do vyrovnávací paměti pomocí [SetString –](../../data/oledb/cdynamicstringaccessor-setstring.md).

Příklady použití tříd dynamického přístupového objektu a diskusi najdete v tématu [použití dynamických přístupových objektů](../../data/oledb/using-dynamic-accessors.md).

## <a name="getstring"></a> CDynamicStringAccessor::GetString

Načte zadaný sloupec data jako řetězec.

### <a name="syntax"></a>Syntaxe

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na hodnotu řetězce načítání ze zadaného sloupce. Hodnota je typu `BaseType`, která bude **CHAR** nebo **WCHAR** v závislosti na tom, zda je definován _UNICODE nebo ne. Vrátí hodnotu NULL, pokud zadaný sloupec nebyl nalezen.

### <a name="remarks"></a>Poznámky

Druhá přepsat formuláře přebírá název sloupce jako řetězec ANSI. Třetí přepsat formuláře přebírá název sloupce jako řetězce Unicode.

## <a name="setstring"></a> CDynamicStringAccessor::SetString

Nastaví zadaný sloupec data jako řetězec.

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
[in] Číslo sloupce. Sloupec čísel začínající číslem 1. Zvláštní hodnota 0 odkazuje na sloupec záložky, pokud existuje.

*pColumnName*<br/>
[in] Ukazatel na řetězec znaků, který obsahuje název sloupce.

*data*<br/>
[in] Ukazatel na řetězec data k zápisu do zadaného sloupce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na hodnotu řetězce, na kterou chcete nastavit zadaný sloupec. Hodnota je typu `BaseType`, která bude **CHAR** nebo **WCHAR** v závislosti na tom, zda je definován _UNICODE nebo ne.

### <a name="remarks"></a>Poznámky

Druhá přepsat formuláře přebírá název sloupce jako řetězec ANSI a třetí přepsat formuláře přebírá název sloupce jako řetězce Unicode.

Pokud je definován _SECURE_ATL s nenulovou hodnotu, bude generována neplatnost kontrolního výrazu modulu runtime, pokud vstupní *data* řetězec je delší než maximální povolená délka sloupce odkazované data. Vstupní řetězec, jinak bude zkrácen, pokud je delší než maximální povolenou délku.

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA – třída](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW – třída](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor – třída](../../data/oledb/cxmlaccessor-class.md)