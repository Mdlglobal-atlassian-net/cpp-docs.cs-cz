---
title: CDaoFieldExchange – třída
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: 015fcdf0ece03bd52927196b6ff3cbe25f370e2b
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096121"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange – třída

Podporuje rutiny pro výměnu záznamů pole (DFX) DAO používané databázovými třídami DAO.

Rozhraní DAO je podporováno prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.


## <a name="syntax"></a>Syntaxe

```
class CDaoFieldExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Vrátí nenulovou hodnotu, pokud je aktuální operace vhodná pro typ aktualizovaného pole.|
|[CDaoFieldExchange:: SetFieldType](#setfieldtype)|Určuje typ datového členu sady záznamů – sloupec nebo parametr, který je reprezentován všemi následnými voláními funkcí DFX do dalšího volání `SetFieldType`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|Operace DFX prováděná aktuálním voláním `DoFieldExchange` členské funkce sady záznamů.|
|[CDaoFieldExchange::m_prs](#m_prs)|Ukazatel na sadu záznamů, na které jsou prováděny operace DFX.|

## <a name="remarks"></a>Poznámky

`CDaoFieldExchange`nemá základní třídu.

Tuto třídu použijte v případě, že píšete rutiny výměny dat pro vlastní datové typy; v opačném případě tuto třídu nebudete používat přímo. DFX vyměňuje data mezi poli datových členů vašeho objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) a odpovídajícími poli aktuálního záznamu ve zdroji dat. DFX spravuje Exchange v obou směrech, ze zdroje dat a zdroje dat. Informace o vytváření vlastních rutin DFX najdete v části [Technická poznámka 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) .

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd knihovny MFC založených na rozhraní ODBC (Open Database Connectivity). Všechny názvy databázových tříd DAO mají předponu "CDao". Ke zdrojům dat rozhraní ODBC můžete přistupovat i s třídami DAO. Obecně jsou třídy knihovny MFC založené na rozhraní DAO větší, než třídy knihovny MFC založené na rozhraní ODBC. Třídy založené na rozhraní DAO mají přístup k datům, včetně přes ovladače rozhraní ODBC, prostřednictvím vlastního databázového stroje. Podporují také operace DDL (Data Definition Language), jako například přidávání tabulek přes třídy místo nutnosti volat rozhraní DAO sami.

> [!NOTE]
>  Výměna pole záznamu DAO (DFX) se velmi podobá záznamu výměny pole (RFX) v třídách databáze MFC založených na rozhraní `CDatabase`ODBC `CRecordset`(,). Pokud rozumíte RFX, bude snadné použít DFX.

`CDaoFieldExchange` Objekt poskytuje kontextové informace potřebné k tomu, aby mohlo probíhat výměna pole záznamů DAO. `CDaoFieldExchange`objekty podporují několik operací, včetně parametrů vazby a datových členů polí a nastavení různých příznaků pro pole aktuálního záznamu. Operace DFX se provádějí na datových členech třídy sady záznamů definovaných pomocí **výčtu** **FieldType** v `CDaoFieldExchange`. Možné hodnoty **FieldType** jsou:

- `CDaoFieldExchange::outputColumn`pro pole datových členů.

- `CDaoFieldExchange::param`pro datové členy parametru.

Členská funkce [IsValidOperation](#isvalidoperation) je k dispozici pro psaní vlastní rutiny DFX. Často použijete [SetFieldType](#setfieldtype) v rámci své funkce [CDaoRecordset::D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) . Podrobnosti o globálních funkcích DFX najdete v tématu [funkce výměny pole záznamu](../../mfc/reference/record-field-exchange-functions.md). Informace o vytváření vlastních rutin DFX pro vlastní datové typy najdete v části [Technická poznámka 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDaoFieldExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

Pokud zapíšete vlastní funkci DFX, zavolejte `IsValidOperation` na začátek vaší funkce a určete, zda lze aktuální operaci provést na určitém typu datového člena pole (a `CDaoFieldExchange::outputColumn` nebo `CDaoFieldExchange::param`).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je aktuální operace vhodná pro typ aktualizovaného pole.

### <a name="remarks"></a>Poznámky

Některé operace provedené mechanismem DFX se vztahují pouze na jeden z možných typů polí. Použijte model existujících funkcí DFX.

Další informace o vytváření vlastních rutin DFX najdete v části [Technická poznámka 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

##  <a name="m_noperation"></a>CDaoFieldExchange::m_nOperation

Určuje operaci, která má být provedena u objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) přidruženého k objektu výměny pole.

### <a name="remarks"></a>Poznámky

`CDaoFieldExchange` Objekt poskytuje kontext pro řadu různých operací DFX na sadě záznamů.

> [!NOTE]
>  Hodnota PSEUDONULL popisovaná v rámci níže uvedených operací MarkForAddNew a SetFieldNull je hodnota, která slouží k označení polí na hodnotu null. Mechanismus výměny pole záznamu DAO (DFX) používá tuto hodnotu k určení, která pole jsou explicitně označena jako null. PSEUDONULL se nevyžaduje pro pole [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) a [COleCurrency](../../mfc/reference/colecurrency-class.md) .

Možné hodnoty `m_nOperation` jsou:

|Operace|Popis|
|---------------|-----------------|
|`AddToParameterList`|Vytvoří klauzuli **Parameters** příkazu SQL.|
|`AddToSelectList`|Vytvoří klauzuli **Select** příkazu SQL.|
|`BindField`|Vytvoří vazby pole v databázi k umístění paměti ve vaší aplikaci.|
|`BindParam`|Nastaví hodnoty parametrů pro dotaz sady záznamů.|
|`Fixup`|Nastaví u pole stav null.|
|`AllocCache`|Přidělí mezipaměť použitou ke kontrole nečistých polí v sadě záznamů.|
|`StoreField`|Uloží aktuální záznam do mezipaměti.|
|`LoadField`|Obnoví proměnné datových členů v mezipaměti v sadě záznamů.|
|`FreeCache`|Uvolní mezipaměť použitou ke kontrole nečistých polí v sadě záznamů.|
|`SetFieldNull`|Nastaví stav pole na hodnotu null a hodnotu na PSEUDONULL.|
|`MarkForAddNew`|Označí pole "dirty", pokud není PSEUDONULL.|
|`MarkForEdit`|Označí pole "dirty", pokud se neshodují s mezipamětí.|
|`SetDirtyField`|Nastaví hodnoty polí označené jako "špinavé".|
|`DumpField`|Vypíše obsah pole (pouze ladění).|
|`MaxDFXOperation`|Slouží ke kontrole vstupu.|

##  <a name="m_prs"></a>CDaoFieldExchange::m_prs

Obsahuje ukazatel na objekt [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) přidružený `CDaoFieldExchange` k objektu.

### <a name="remarks"></a>Poznámky

##  <a name="setfieldtype"></a>CDaoFieldExchange:: SetFieldType

Zavolejte `SetFieldType` na `DoFieldExchange` přepsání `CDaoRecordset` vaší třídy.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nFieldType*<br/>
Hodnota **výčtu FieldType**, která je deklarována v `CDaoFieldExchange`, což může být jedna z následujících:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Poznámky

Za normálních okolností ClassWizard zapisuje toto volání za vás. Pokud zapíšete vlastní funkci a pomocí Průvodce zapíšete `DoFieldExchange` funkci, přidejte volání do své vlastní funkce mimo mapu pole. Pokud Průvodce nepoužijete, nebudete mít mapování polí. Volání předchází volání funkcí DFX, jednu pro každé pole datového člena vaší třídy a identifikuje typ pole jako `CDaoFieldExchange::outputColumn`.

Pokud parametrizovatte třídu sady záznamů, měli byste přidat volání DFX pro všechny datové členy parametrů (mimo mapu pole) a předcházet těmto voláním volání `SetFieldType`. Předejte hodnotu `CDaoFieldExchange::param`. (Místo toho můžete použít [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) a nastavit jeho hodnoty parametrů.)

Obecně platí, že každá skupina volání funkcí DFX přidružená k polím datových členů nebo k datovým členům parametrů musí předcházet volání `SetFieldType`. Parametr *nFieldType* každého `SetFieldType` volání identifikuje typ datových členů reprezentovaných voláními funkce DFX, které následují po `SetFieldType` volání.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
