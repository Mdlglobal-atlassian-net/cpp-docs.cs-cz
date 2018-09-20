---
title: Cdaofieldexchange – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed7f8eabc8df2d4aefb6b1350404b03d90736a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432398"
---
# <a name="cdaofieldexchange-class"></a>Cdaofieldexchange – třída

Podporuje rutiny (DFX) systému exchange pole záznamu DAO používané databázové třídy DAO.

## <a name="syntax"></a>Syntaxe

```
class CDaoFieldExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Vrátí nenulovou hodnotu, pokud se aktuální operace je vhodné pro typ pole se aktualizuje.|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Určuje typ sady záznamů datový člen – sloupec nebo parametr-reprezentována všechny následné volání funkcí DFX až do příštího volání metody `SetFieldType`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|Právě prováděnou aktuálním voláním na sadu záznamů operaci DFX `DoFieldExchange` členskou funkci.|
|[CDaoFieldExchange::m_prs](#m_prs)|Ukazatel na sadu záznamů, na které DFX jsou právě probíhá operace.|

## <a name="remarks"></a>Poznámky

`CDaoFieldExchange` nemá základní třídu.

Tuto třídu použít, pokud píšete rutiny výměny dat pro vlastní datové typy; v opačném případě nebudete používat přímo do této třídy. DFX vyměňuje data mezi pole datové členy vašeho [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) odpovídající pole aktuální záznam ve zdroji dat a objektů. DFX spravuje exchange v obou směrech ze zdroje dat a ke zdroji dat. Zobrazit [technická Poznámka: 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) informace o tvorbě vlastní rutiny DFX.

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Je možné i nadále přístup ke zdrojům dat ODBC s tříd DAO. Obecně třídy knihovny MFC rozhraní DAO podle podporují více než třídy knihovny MFC založená na rozhraní ODBC. Třídy založené na rozhraní DAO můžou přistupovat k datům, včetně prostřednictvím ovladače rozhraní ODBC, prostřednictvím vlastní databázového stroje. Podporují také jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy místo nutnosti volání rozhraní DAO sami.

> [!NOTE]
>  Výměna polí záznamu DAO (DFX) je velmi podobný výměna pole záznamu (RFX) v databázové třídy MFC založených na rozhraní ODBC ( `CDatabase`, `CRecordset`). Pokud rozumíte RFX, najdete je snadno použitelný DFX.

A `CDaoFieldExchange` objekt, který poskytuje kontextové informace potřebné pro rozhraní DAO zaznamenat výměna polí uskutečnit. `CDaoFieldExchange` objekty podporují několik operací, včetně vázané parametry a pole datové členy a nastavení různé příznaky pro pole a aktuální záznam. DFX operace se provádějí na datové členy třídy sady záznamů typů definovaných **výčtu** **typ pole** v `CDaoFieldExchange`. Je to možné **typ pole** hodnoty jsou:

- `CDaoFieldExchange::outputColumn` pro datové členy.

- `CDaoFieldExchange::param` pro parametry datových členů.

[IsValidOperation](#isvalidoperation) členská funkce je k dispozici pro psaní vlastních vlastní rutiny DFX. Budete používat [SetFieldType](#setfieldtype) často ve vaší [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkce. Podrobnosti o DFX globálních funkcí najdete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md). Informace o tvorbě vlastní rutiny DFX pro vlastní datové typy najdete v tématu [technická Poznámka: 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDaoFieldExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation

Při zápisu funkce DFX, volání `IsValidOperation` na začátku funkce k určení, zda aktuální operaci lze provést na datovém typu člena určitého pole ( `CDaoFieldExchange::outputColumn` nebo `CDaoFieldExchange::param`).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aktuální operace je vhodné pro typ pole se aktualizuje.

### <a name="remarks"></a>Poznámky

Některé z operací provedených metodou mechanismus DFX platí pouze pro jeden z typů možná pole. Postupujte podle modelu existující DFX – funkce.

Další informace o vytváření vlastní rutiny DFX, naleznete v tématu [technická Poznámka: 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

##  <a name="m_noperation"></a>  CDaoFieldExchange::m_nOperation

Identifikuje operace má být proveden [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt přidružený k objektu pole exchange.

### <a name="remarks"></a>Poznámky

`CDaoFieldExchange` Objekt poskytuje kontext pro celou řadou různých DFX operací v sadě záznamů.

> [!NOTE]
>  PSEUDONULL hodnota popsaná MarkForAddNew a SetFieldNull operacemi níže je hodnota používá k označení pole hodnotu Null. DAO mechanismem výměny pole záznamu (DFX) používá tuto hodnotu k určení pole, která jsou explicitně označené hodnotou Null. Není vyžadován pro PSEUDONULL [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) a [COleCurrency](../../mfc/reference/colecurrency-class.md) pole.

Možné hodnoty `m_nOperation` jsou:

|Operace|Popis|
|---------------|-----------------|
|`AddToParameterList`|Sestavení **parametry** klauzule příkaz jazyka SQL.|
|`AddToSelectList`|Sestavení **vyberte** klauzule příkaz jazyka SQL.|
|`BindField`|Vytvoří vazbu na pole v databázi do umístění v paměti v aplikaci.|
|`BindParam`|Nastaví hodnoty parametrů pro sady záznamů dotazu.|
|`Fixup`|Nastaví stav hodnotu Null pro pole.|
|`AllocCache`|Přidělí mezipaměti sloužící ke kontrole "nezapsané" polí v sadě záznamů.|
|`StoreField`|Aktuální záznam se uloží do mezipaměti.|
|`LoadField`|Obnoví data uložená v mezipaměti proměnné členů v sadě záznamů.|
|`FreeCache`|Uvolní mezipaměti sloužící ke kontrole "nezapsané" polí v sadě záznamů.|
|`SetFieldNull`|Nastaví stav pole na hodnotu Null a hodnota, která má PSEUDONULL.|
|`MarkForAddNew`|Pole značky "nesprávné" Pokud nejsou PSEUDONULL.|
|`MarkForEdit`|Označí pole "změny", pokud shodné nejsou mezipaměti.|
|`SetDirtyField`|Nastaví pole hodnoty, které jsou označeny jako "nečisté."|
|`DumpField`|Vypíše obsah pole (pouze debug).|
|`MaxDFXOperation`|Používá se pro kontrolu vstupu.|

##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs

Obsahuje ukazatel [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt přidružený k `CDaoFieldExchange` objektu.

### <a name="remarks"></a>Poznámky

##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType

Volání `SetFieldType` ve vašich `CDaoRecordset` třídy `DoFieldExchange` přepsat.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nFieldType*<br/>
Hodnota **výčtu typ pole**, které jsou deklarovány v `CDaoFieldExchange`, což může být buď z následujících akcí:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Poznámky

Za normálních okolností ClassWizard zapíše toto volání za vás. Pokud můžete napsat vlastní funkci a používáte Průvodce zapisovat vaše `DoFieldExchange` funkci, přidejte volání vlastní funkce mimo mapování polí. Pokud je velmi riskantní používat průvodce, nebudete se mapování polí. Volání předchází volání funkcí DFX, jeden pro každé pole datového člena vaší třídy a jsou uvedeny typy pole jako `CDaoFieldExchange::outputColumn`.

Pokud jste parametrizovat vaší třídy sady záznamů, by měl přidat DFX volání pro všechny parametry datových členů (mimo mapování polí) a předcházet těchto volání voláním `SetFieldType`. Předejte hodnotu `CDaoFieldExchange::param`. (Místo toho můžete použít [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md) a nastavení jeho hodnoty parametru.)

Obecně platí, všechny skupiny o volání funkcí DFX přidružené pole datové členy a parametry datových členů musí předcházet párový příkaz volání `SetFieldType`. *NFieldType* parametr jednotlivých `SetFieldType` volání jsou uvedeny typy datových členů reprezentována DFX volání funkcí, které následují `SetFieldType` volání.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
