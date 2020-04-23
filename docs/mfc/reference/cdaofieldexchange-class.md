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
ms.openlocfilehash: 86f12f78338d1c60e3dd13614ccedc2868f28d81
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754717"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange – třída

Podporuje rutiny výměny dat záznamu DAO (DFX) používané třídou databáze DAO.

DAO je podporováno prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé.

## <a name="syntax"></a>Syntaxe

```
class CDaoFieldExchange
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Vrátí nenulovou hodnotu, pokud je aktuální operace vhodná pro typ aktualizovaného pole.|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Určuje typ datového člena sady záznamů – sloupec nebo parametr – reprezentovaný `SetFieldType`všemi následnými voláními funkcí DFX až do dalšího volání .|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|Operace DFX prováděné aktuální volání `DoFieldExchange` členské funkce sady záznamů.|
|[CDaoFieldExchange::m_prs](#m_prs)|Ukazatel na sadu záznamů, na kterém jsou prováděny operace DFX.|

## <a name="remarks"></a>Poznámky

`CDaoFieldExchange`nemá základní třídu.

Tuto třídu použijte, pokud píšete rutiny výměny dat pro vlastní datové typy; v opačném případě nebudete přímo používat tuto třídu. DFX vyměňuje data mezi datovými členy pole objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) a odpovídajícími poli aktuálního záznamu ve zdroji dat. DFX spravuje výměnu v obou směrech, ze zdroje dat a do zdroje dat. Informace o psaní vlastních rutin DFX naleznete [v technické poznámce 53.](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)

> [!NOTE]
> Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Stále můžete přistupovat ke zdrojům dat ODBC pomocí tříd DAO. Obecně platí, že třídy Knihovny MFC založené na DAO jsou schopnější než třídy Knihovny MFC založené na rozhraní ODBC. Třídy založené na DAO mohou přistupovat k datům, včetně ovladačů ODBC, prostřednictvím vlastního databázového stroje. Podporují také operace jazyka ddl (Data Definition Language), jako je například přidávání tabulek prostřednictvím tříd namísto nutnosti volat DAO sami.

> [!NOTE]
> Výměna pole záznamu DAO (DFX) je velmi podobná výměně pole záznamu (RFX) `CDatabase` `CRecordset`v databázových třídách knihovny MFC založených na rozhraní ODBC ( , ). Pokud rozumíte RFX, zjistíte, že je snadné používat DFX.

Objekt `CDaoFieldExchange` poskytuje kontextové informace potřebné pro výměnu pole záznamu DAO. `CDaoFieldExchange`objekty podporují řadu operací, včetně parametrů vazby a datových členů polí a nastavení různých příznaků v polích aktuálního záznamu. DFX operace jsou prováděny na datových členech třídy recordset `CDaoFieldExchange`typů definovaných **ve výčtu** **FieldType** in . Možné hodnoty **Typu pole** jsou:

- `CDaoFieldExchange::outputColumn`pro datové členy pole.

- `CDaoFieldExchange::param`pro datové členy parametrů.

Členská funkce [IsValidOperation](#isvalidoperation) je k dispozici pro psaní vlastních rutin DFX. [SetFieldType](#setfieldtype) budete často používat ve funkcích [CDaoRecordset::DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) Podrobnosti o globálních funkcích DFX naleznete v [tématu Record Field Exchange Functions](../../mfc/reference/record-field-exchange-functions.md). Informace o psaní vlastních rutin DFX pro vlastní datové typy naleznete [v technické poznámce 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDaoFieldExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

Pokud píšete vlastní funkci DFX, volání `IsValidOperation` na začátku funkce k určení, zda aktuální operace lze `CDaoFieldExchange::outputColumn` provést `CDaoFieldExchange::param`na konkrétní typ datového člena pole (a nebo a ).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je aktuální operace vhodná pro typ aktualizovaného pole.

### <a name="remarks"></a>Poznámky

Některé operace prováděné mechanismem DFX platí pouze pro jeden z možných typů polí. Postupujte podle modelu existujících funkcí DFX.

Další informace o psaní vlastních rutin DFX naleznete [v technické poznámce 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDaoFieldExchange::m_nOperation

Identifikuje operaci, která má být provedena s objektem [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) přidruženým k objektu výměny polí.

### <a name="remarks"></a>Poznámky

Objekt `CDaoFieldExchange` poskytuje kontext pro řadu různých operací DFX v sadě záznamů.

> [!NOTE]
> Hodnota PSEUDONULL popsaná pod operacemi MarkForAddNew a SetFieldNull je hodnota používaná k označení polí Null. Mechanismus výměny pole záznamu DAO (DFX) používá tuto hodnotu k určení, která pole byla explicitně označena jako null. PseudoNULL není vyžadováno pro pole [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) a [COleCurrency.](../../mfc/reference/colecurrency-class.md)

Možné hodnoty `m_nOperation` jsou:

|Operace|Popis|
|---------------|-----------------|
|`AddToParameterList`|Vytvoří **klauzuli PARAMETERS** příkazu SQL.|
|`AddToSelectList`|Vytvoří **klauzuli SELECT** příkazu SQL.|
|`BindField`|Sváže pole v databázi s umístěním paměti v aplikaci.|
|`BindParam`|Nastaví hodnoty parametrů pro dotaz sady záznamů.|
|`Fixup`|Nastaví stav Null pro pole.|
|`AllocCache`|Přidělí mezipaměť používanou ke kontrole "nečistých" polí v sadě záznamů.|
|`StoreField`|Uloží aktuální záznam do mezipaměti.|
|`LoadField`|Obnoví proměnné datových členů uložených v mezipaměti v sadě záznamů.|
|`FreeCache`|Uvolní mezipaměť použitou ke kontrole "špinavých" polí v sadě záznamů.|
|`SetFieldNull`|Nastaví stav pole na Hodnotu Null a hodnotu na PSEUDONULL.|
|`MarkForAddNew`|Označuje pole "dirty", pokud není PSEUDONULL.|
|`MarkForEdit`|Označí pole "dirty", pokud neodpovídají mezipaměti.|
|`SetDirtyField`|Nastaví hodnoty polí označené jako "dirty".|
|`DumpField`|Vypíše obsah pole (pouze ladění).|
|`MaxDFXOperation`|Používá se pro kontrolu vstupu.|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDaoFieldExchange::m_prs

Obsahuje ukazatel na objekt [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) `CDaoFieldExchange` přidružený k objektu.

### <a name="remarks"></a>Poznámky

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

Zavolejte `SetFieldType` `CDaoRecordset` `DoFieldExchange` na třídu.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nTyp pole*<br/>
Hodnota **výčtu FieldType**, `CDaoFieldExchange`deklarovaná v , která může být buď z následujících:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Poznámky

Za normálních okolností ClassWizard zapíše toto volání za vás. Pokud píšete vlastní funkci a používáte `DoFieldExchange` průvodce k zápisu funkce, přidejte volání do své vlastní funkce mimo mapu pole. Pokud průvodce nepoužijete, nebude k dispozici mapa polí. Volání předchází volání funkcí DFX, jeden pro každého člena dat pole vaší `CDaoFieldExchange::outputColumn`třídy a identifikuje typ pole jako .

Pokud parametrizujete třídu sady záznamů, měli byste přidat volání DFX pro všechny členy dat parametrů (mimo mapu pole) a před těmito voláními předvolat . `SetFieldType` Předajte hodnotu `CDaoFieldExchange::param`. (Místo toho můžete použít [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) a nastavit jeho hodnoty parametrů.)

Obecně platí, že každé skupině volání funkce DFX přidružené k datovým členům `SetFieldType`pole nebo datovým členům parametrů musí předcházet volání . Parametr *nFieldType* každého `SetFieldType` volání identifikuje typ datových členů reprezentovaných voláním funkce DFX, která následují po `SetFieldType` volání.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
