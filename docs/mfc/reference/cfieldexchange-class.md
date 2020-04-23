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
ms.openlocfilehash: de9db2713a25b232bbd7f936958d1c10e96c511a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753164"
---
# <a name="cfieldexchange-class"></a>CFieldExchange – třída

Podporuje rutiny výměny pole záznamu (RFX) a hromadné hodového záznamu (Hromadné RFX) používané třídami databáze.

## <a name="syntax"></a>Syntaxe

```
class CFieldExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CfieldExchange::IsfieldType](#isfieldtype)|Vrátí nenulovou hodnotu, pokud je aktuální operace vhodná pro typ aktualizovaného pole.|
|[Cfieldexchange::setfieldtype](#setfieldtype)|Určuje typ datového člena sady záznamů – sloupec nebo parametr – reprezentované `SetFieldType`všemi následujícími voláními funkcí RFX až do dalšího volání aplikace .|

## <a name="remarks"></a>Poznámky

`CFieldExchange`nemá základní třídu.

Tuto třídu použijte, pokud píšete rutiny výměny dat pro vlastní datové typy nebo při implementaci hromadného načítání řádků; v opačném případě nebudete přímo používat tuto třídu. RFX a Bulk RFX vyměňují data mezi datovými členy pole objektu sady záznamů a odpovídajícími poli aktuálního záznamu ve zdroji dat.

> [!NOTE]
> Pokud pracujete s objekty přístupu k datům (DAO) třídy spíše než otevřené připojení k databázi (ODBC) třídy, použijte třídu [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) místo. Další informace naleznete v článku [Přehled:Programování databáze](../../data/data-access-programming-mfc-atl.md).

Objekt `CFieldExchange` poskytuje kontextové informace potřebné pro výměnu pole záznamu nebo hromadné výměny pole záznamu. `CFieldExchange`objekty podporují řadu operací, včetně parametrů vazby a datových členů polí a nastavení různých příznaků v polích aktuálního záznamu. RFX a Bulk RFX operace jsou prováděny na datových členech třídy `CFieldExchange`recordset typů definovaných **ve výčtu** **FieldType** in . Možné hodnoty **Typu pole** jsou:

- `CFieldExchange::outputColumn`pro datové členy pole.

- `CFieldExchange::inputParam`nebo `CFieldExchange::param` pro členy vstupních parametrů.

- `CFieldExchange::outputParam`pro datové členy výstupních parametrů.

- `CFieldExchange::inoutParam`pro datové členy vstupních a výstupních parametrů.

Většina členských funkcí třídy a datových členů jsou k dispozici pro psaní vlastní rutiny RFX. Budete používat `SetFieldType` často. Další informace naleznete v článcích [Výměna polí záznamů (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [Sada záznamů (ODBC).](../../data/odbc/recordset-odbc.md) Informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) Podrobnosti o globálních funkcích RFX a Bulk RFX naleznete v části [Záznam funkce výměny polí](../../mfc/reference/record-field-exchange-functions.md) v části MFC MFC MFC MFC makra a globální.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CFieldExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CfieldExchange::IsfieldType

Pokud píšete vlastní funkci RFX, `IsFieldType` volání na začátku funkce k určení, zda aktuální operace lze provést `CFieldExchange::outputColumn` `CFieldExchange::inputParam`na `CFieldExchange::param` `CFieldExchange::outputParam`konkrétní pole nebo typ datového člena parametru (, , , , nebo `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parametry

*pnField*<br/>
V tomto parametru je vráceno pořadové číslo datového člena pole nebo parametru. Toto číslo odpovídá pořadí datového člena ve funkci [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [CRecordset::DoBulkFieldExchange.](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze aktuální operaci provést u aktuálního pole nebo typu parametru.

### <a name="remarks"></a>Poznámky

Postupujte podle modelu existujících funkcí RFX.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>Cfieldexchange::setfieldtype

Potřebujete volání `SetFieldType` v přepsání třídy [doFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) vaší třídy záznamů.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nTyp pole*<br/>
Hodnota `enum FieldType`, deklarovaná v `CFieldExchange`písmenu a), která může být jednou z následujících hodnot:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Poznámky

Pro datové členy pole `SetFieldType` je nutné `CFieldExchange::outputColumn`volat s parametrem , následovaný voláním funkcí RFX nebo Bulk RFX. Pokud jste neimplementovali hromadné načítání řádků, `SetFieldType` pak ClassWizard umístí toto `DoFieldExchange`volání za vás v části mapy pole .

Pokud parametrizujete třídu sady záznamů, `SetFieldType` musíte volat znovu, mimo libovolnou část mapy pole, následovanou voláním RFX pro všechny členy dat parametrů. Každý typ datového člena parametru musí mít své vlastní `SetFieldType` volání. Následující tabulka rozlišuje různé `SetFieldType` hodnoty, které můžete předat, aby reprezentovaly členy dat parametrů vaší třídy:

|Hodnota parametru SetFieldType|Typ datového člena parametru|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Vstupní parametr. Hodnota, která je předána do dotazu sady záznamů nebo uložené procedury.|
|`CFieldExchange::param` | stejné `CFieldExchange::inputParam`jako .|
|`CFieldExchange::outputParam`|Výstupní parametr. Vrácená hodnota uložené procedury sady záznamů.|
|`CFieldExchange::inoutParam`|Vstupní/výstupní parametr. Hodnota, která je předána a vrácena z uložené procedury sady záznamů.|

Obecně platí, že každé skupině volání funkce RFX přidružené k datovým členům `SetFieldType`pole nebo datovým členům parametrů musí předcházet volání . Parametr *nFieldType* každého `SetFieldType` volání identifikuje typ datových členů reprezentované volánífunkce RFX, které následují po `SetFieldType` volání.

Další informace o zpracování výstupních a vstupních `CRecordset` a výstupních parametrů naleznete v členské funkci [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Další informace o funkcích RFX a Bulk RFX naleznete v tématu [Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md). Související informace o hromadném načítání řádků naleznete v článku [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání rfx funkce `SetFieldType`s doprovodné volání . Všimněte `SetFieldType` si, `pFX` že je `CFieldExchange` volána prostřednictvím ukazatele na objekt.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
