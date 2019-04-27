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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346350"
---
# <a name="cfieldexchange-class"></a>CFieldExchange – třída

Podporuje výměna pole záznamu (RFX) a Hromadná pole záznamu exchange (Bulk RFX) rutiny používané v rámci tříd databáze.

## <a name="syntax"></a>Syntaxe

```
class CFieldExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|Vrátí nenulovou hodnotu, pokud se aktuální operace je vhodné pro typ pole se aktualizuje.|
|[CFieldExchange::SetFieldType](#setfieldtype)|Určuje typ sady záznamů datový člen – sloupec nebo parametr-reprezentována veškerá následující volání funkce RFX až do příštího volání metody `SetFieldType`.|

## <a name="remarks"></a>Poznámky

`CFieldExchange` nemá základní třídu.

Tuto třídu použít, pokud vytváříte vlastní typy dat nebo když jsou implementaci hromadného načítání řádků; rutiny výměny dat v opačném případě nebudete používat přímo do této třídy. RFX a Bulk RFX vyměňuje data mezi odpovídající pole aktuální záznam ve zdroji dat a pole datové členy objektu sady záznamů.

> [!NOTE]
>  Pokud pracujete s třídami objektů DAO (Data Access), a ne třídy připojení ODBC (Open Database), použijte třídu [cdaofieldexchange –](../../mfc/reference/cdaofieldexchange-class.md) místo. Další informace najdete v článku [přehled: databáze programování](../../data/data-access-programming-mfc-atl.md).

A `CFieldExchange` objekt, který poskytuje kontextové informace potřebné pro výměna polí záznamu nebo hromadná výměna polí záznamu se umístit. `CFieldExchange` objekty podporují několik operací, včetně vázané parametry a pole datové členy a nastavení různé příznaky pro pole a aktuální záznam. RFX a Bulk RFX operace se provádějí na datové členy třídy sady záznamů typů definovaných **výčtu** **typ pole** v `CFieldExchange`. Je to možné **typ pole** hodnoty jsou:

- `CFieldExchange::outputColumn` pro datové členy.

- `CFieldExchange::inputParam` nebo `CFieldExchange::param` pro vstupní parametry datových členů.

- `CFieldExchange::outputParam` pro výstupní parametry datových členů.

- `CFieldExchange::inoutParam` pro parametr vstupní a výstupní datové členy.

Většina členů třídy členské funkce a data jsou k dispozici pro psaní vlastních rutin RFX. Budete používat `SetFieldType` často. Další informace najdete v článcích [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Podrobnosti o globálních funkcí RFX a Bulk RFX najdete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md) v části v makrech MFC a Globals tento odkaz.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CFieldExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType

Pokud píšete funkce RFX, zavolejte `IsFieldType` na začátku funkce k určení, zda aktuální operace může běžet na konkrétní pole nebo parametr datový typ členu ( `CFieldExchange::outputColumn`, `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, nebo `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parametry

*pnField*<br/>
Pořadové číslo datový člen pole nebo parametr se vrátí v tomto parametru. Toto číslo odpovídá pořadí datový člen [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) funkce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aktuální operace může běžet na aktuální pole nebo parametr typu.

### <a name="remarks"></a>Poznámky

Postupujte podle modelu existujících funkcí RFX.

##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType

Je třeba volání `SetFieldType` ve třídě sady záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) přepsat.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nFieldType*<br/>
Hodnota `enum FieldType`, které jsou deklarovány v `CFieldExchange`, což může být jeden z následujících akcí:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Poznámky

Pro datové členy, je nutné volat `SetFieldType` s parametrem `CFieldExchange::outputColumn`a po něm volání funkcí RFX nebo Bulk RFX. Pokud jste neimplementovali hromadné načítání řádků a potom to umístí ClassWizard `SetFieldType` volání můžete v části mapování pole `DoFieldExchange`.

Pokud jste parametrizovat vaší třídy sady záznamů, musíte zavolat `SetFieldType` znovu, mimo žádným oddílem. mapování pole, za nímž následuje volání funkce RFX pro parametr datových členů. Každý typ parametru datový člen musí mít svůj vlastní `SetFieldType` volání. V následující tabulce, která odlišuje různé hodnoty, kterou můžete předat `SetFieldType` k reprezentaci parametru datové členy třídy:

|Hodnota parametru SetFieldType|Typ parametru datový člen|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Vstupní parametr. Hodnota, která je předána do sady záznamů dotaz nebo úložné procedury.|
|`CFieldExchange::param` | Stejné jako `CFieldExchange::inputParam`.|
|`CFieldExchange::outputParam`|Výstupní parametr. Návratový typ sady záznamů uloženou proceduru.|
|`CFieldExchange::inoutParam`|Vstupní/výstupní parametr. Hodnota, která je do a ze sady záznamů uloženou proceduru.|

Obecně platí, všechny skupiny o volání funkcí RFX přidružené pole datové členy a parametry datových členů musí předcházet párový příkaz volání `SetFieldType`. *NFieldType* parametr jednotlivých `SetFieldType` volání jsou uvedeny typy datových členů, které následují volání funkce RFX reprezentována `SetFieldType` volání.

Další informace o zpracování výstupní a vstupní a výstupní parametry, najdete v článku `CRecordset` členskou funkci [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Další informace o funkcích RFX a Bulk RFX, naleznete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md). Související informace o hromadném načítání řádků naleznete v článku [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Příklad

Tento příklad ukazuje několik volání funkcí RFX s doplňujícími volání `SetFieldType`. Všimněte si, že `SetFieldType` zavolaném prostřednictvím `pFX` ukazatel `CFieldExchange` objektu.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
