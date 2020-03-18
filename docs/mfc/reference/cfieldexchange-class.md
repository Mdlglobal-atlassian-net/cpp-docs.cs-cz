---
title: CFieldExchange – třída
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: e66b3ed16d4f21d46567c37bfaf7929d32f63b8e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420405"
---
# <a name="cfieldexchange-class"></a>CFieldExchange – třída

Podporuje rutiny výměny pole záznamu (RFX) a hromadná výměna pole záznamu (Bulk RFX) používané třídami databáze.

## <a name="syntax"></a>Syntaxe

```
class CFieldExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFieldExchange:: IsFieldType](#isfieldtype)|Vrátí nenulovou hodnotu, pokud je aktuální operace vhodná pro typ aktualizovaného pole.|
|[CFieldExchange:: SetFieldType](#setfieldtype)|Určuje typ datového členu sady záznamů – sloupec nebo parametr – reprezentovaný všemi následujícími voláními RFX funkcí do dalšího volání `SetFieldType`.|

## <a name="remarks"></a>Poznámky

`CFieldExchange` nemá základní třídu.

Tuto třídu použijte v případě, že píšete rutiny výměny dat pro vlastní datové typy nebo když implementujete hromadné načítání řádků; v opačném případě tuto třídu nebudete používat přímo. RFX a Hromadná RFX vyměňuje data mezi poli datových členů objektu Recordset a odpovídajícími poli aktuálního záznamu ve zdroji dat.

> [!NOTE]
>  Pokud pracujete s třídami objektů pro přístup k datům (DAO), nikoli s třídami rozhraní ODBC (Open Database Connectivity), místo toho použijte třídu [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) . Další informace najdete v článku [Přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).

Objekt `CFieldExchange` poskytuje kontextové informace potřebné k tomu, aby mohlo probíhat výměna pole záznamů nebo hromadné výměny pole záznamů. objekty `CFieldExchange` podporují řadu operací, včetně parametrů vazby a datových členů polí a nastavení různých příznaků pro pole aktuálního záznamu. Operace RFX a Bulk RFX jsou prováděny na datových členech třídy recordset typů definovaných **výčtovým** **FieldType** v `CFieldExchange`. Možné hodnoty **FieldType** jsou:

- `CFieldExchange::outputColumn` pro datové členy polí.

- pro datové členy vstupních parametrů `CFieldExchange::inputParam` nebo `CFieldExchange::param`.

- `CFieldExchange::outputParam` pro datové členy parametru Output

- `CFieldExchange::inoutParam` pro datové členy vstupní/výstupní parametry.

Většina členských funkcí a datových členů třídy je k dispozici pro psaní vlastních rutin RFX. Budete často používat `SetFieldType`. Další informace najdete v článcích [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Podrobnosti o globálních funkcích RFX a Bulk RFX naleznete v části [funkce výměny pole záznamu](../../mfc/reference/record-field-exchange-functions.md) v části makra MFC a Globals tohoto odkazu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CFieldExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

##  <a name="isfieldtype"></a>CFieldExchange:: IsFieldType

Pokud zapíšete vlastní funkci RFX, volejte `IsFieldType` na začátku vaší funkce, abyste zjistili, zda lze aktuální operaci provést na určitém typu datového členu pole nebo parametru (`CFieldExchange::outputColumn`, `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`nebo `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parametry

*pnField*<br/>
Pořadové číslo datového členu pole nebo parametru je vráceno v tomto parametru. Toto číslo odpovídá pořadí datového člena ve funkci [CRecordset::D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [CRecordset::D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud lze aktuální operaci provést pro aktuální pole nebo typ parametru.

### <a name="remarks"></a>Poznámky

Sledujte model existujících funkcí RFX.

##  <a name="setfieldtype"></a>CFieldExchange:: SetFieldType

Budete potřebovat volání `SetFieldType` v přepsání metody [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) vaší třídy sady záznamů.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nFieldType*<br/>
Hodnota `enum FieldType`deklarovaná v `CFieldExchange`, která může být jedna z následujících:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Poznámky

Pro pole datových členů je třeba volat `SetFieldType` s parametrem `CFieldExchange::outputColumn`a následovat volání funkcí RFX nebo hromadného RFX. Pokud jste neimplementovali hromadné načítání řádků, pak ClassWizard toto volání `SetFieldType` v části mapa pole v `DoFieldExchange`.

Pokud parametrizovatte třídu sady záznamů, je nutné volat `SetFieldType` znovu, mimo část mapování polí, následovaná voláními RFX pro všechny datové členy parametru. Každý typ datového členu parametru musí mít své vlastní volání `SetFieldType`. Následující tabulka rozlišuje různé hodnoty, které můžete předat `SetFieldType`, aby představovaly parametry datových členů vaší třídy:

|Hodnota parametru SetFieldType|Typ datového členu parametru|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Vstupní parametr Hodnota, která je předána dotazu nebo uložené proceduře sady záznamů.|
|`CFieldExchange::param` | Stejné jako `CFieldExchange::inputParam`.|
|`CFieldExchange::outputParam`|Výstupní parametr Návratová hodnota uložené procedury sady záznamů.|
|`CFieldExchange::inoutParam`|Vstupní/výstupní parametr Hodnota, která je předána a vrácena z uložené procedury sady záznamů.|

Obecně platí, že každá skupina volání RFX funkce přidružená k datovým členům pole nebo k datovým členům parametru musí předcházet volání `SetFieldType`. Parametr *nFieldType* každého volání `SetFieldType` identifikuje typ datových členů reprezentovaných voláními funkce RFX, které následují volání `SetFieldType`.

Další informace o zpracování výstupních a vstupně-výstupních parametrů naleznete v tématu `CRecordset` členská funkce [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Další informace o funkcích RFX a Bulk RFX najdete v tématu [funkce výměny pole záznamu](../../mfc/reference/record-field-exchange-functions.md)v tématu. Související informace o hromadném načítání řádků naleznete v článku [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání funkcí RFX s doprovodnou voláním `SetFieldType`. Všimněte si, že `SetFieldType` je volána prostřednictvím ukazatele `pFX` na objekt `CFieldExchange`.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
