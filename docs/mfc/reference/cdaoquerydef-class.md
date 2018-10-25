---
title: Cdaoquerydef – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a10e1f6adb1fc9274a2a59215564fb60984ea661
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074485"
---
# <a name="cdaoquerydef-class"></a>Cdaoquerydef – třída

Představuje definici dotazu, nebo "querydef", obvykle jeden uložený v databázi.

## <a name="syntax"></a>Syntaxe

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Vytvoří `CDaoQueryDef` objektu. Další volání `Open` nebo `Create`, v závislosti na požadavcích.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::Append](#append)|Querydef připojí k vaší databáze querydefs – kolekce jako uložený dotaz.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud dotaz můžete aktualizovat databázi.|
|[CDaoQueryDef::Close](#close)|Zavře querydef objekt. Zničte objekt jazyka C++, až skončí s ním.|
|[CDaoQueryDef::Create](#create)|Vytvoří základní objekt querydef DAO. Použít jako dočasné dotazu nebo volání querydef `Append` a zachraňte je v databázi.|
|[CDaoQueryDef::Execute](#execute)|Spustí dotaz definovaný v objektu querydef.|
|[CDaoQueryDef::GetConnect](#getconnect)|Vrátí řetězec připojení přidružené k querydef. Připojovací řetězec Určuje zdroj dat. (Pro SQL předávací dotazy pouze; v opačném případě prázdný řetězec.)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Vrátí datum vytvoření uloženého dotazu.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum, kdy byl naposledy aktualizován uloženého dotazu.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Vrátí počet polí, které jsou definované querydef.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Vrátí informace o zadané pole definované v dotazu.|
|[CDaoQueryDef::GetName](#getname)|Vrátí název querydef.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Vrátí hodnotu časového limitu, používá rozhraní ODBC (pro dotaz rozhraní ODBC) při provádění querydef. Určuje, jak dlouho umožňující na dokončení akce dotazu.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Vrátí počet parametrů definovaných pro dotaz.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Vrátí informace o zadaný parametr dotazu.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Vrátí hodnotu zadaného parametru dotazu.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů ovlivněný podle dotazu akce.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Vrátí nenulovou hodnotu, pokud je dotaz definovaný sadou querydef vrátí záznamy.|
|[CDaoQueryDef::GetSQL](#getsql)|Vrátí řetězec SQL, který určuje dotaz definovaný sadou querydef.|
|[CDaoQueryDef::GetType](#gettype)|Vrátí typ dotazu: odstranění, aktualizace, připojení, vytvoření tabulky a tak dále.|
|[CDaoQueryDef::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud querydef je otevřený a mohou být provedeny.|
|[CDaoQueryDef::Open](#open)|Otevře se existující querydef uložené v databáze querydefs – kolekce.|
|[CDaoQueryDef::SetConnect](#setconnect)|Nastaví připojovací řetězec pro předávací dotaz SQL na zdroji dat rozhraní ODBC.|
|[CDaoQueryDef::SetName](#setname)|Nastaví název uloženého dotazu, nahraďte název se používá při vytváření querydef.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Nastaví hodnotu časového limitu, používá rozhraní ODBC (pro dotaz rozhraní ODBC) při provádění querydef.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Nastaví hodnotu zadaného parametru dotazu.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Určuje, zda querydef vrátí záznamy. Tento atribut nastavíte na hodnotu TRUE je platná pouze pro předávací dotazy SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Nastaví řetězec SQL, který určuje dotaz definovaný sadou querydef.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Ukazatel na rozhraní OLE pro podkladové querydef objekt DAO.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Ukazatel `CDaoDatabase` objektu, ke kterému je přidružena querydef. Querydef může být uloženo v databázi, nebo ne.|

## <a name="remarks"></a>Poznámky

Querydef je datový objekt, který obsahuje příkaz jazyka SQL, který popisuje dotazu a její vlastnosti, jako je například "Datum vytvoření" a "ODBC časový limit." Můžete také vytvořit dočasný querydef objekty bez uložení, ale je praktické a mnohem efektivnější – uložení běžně znovu použít dotazů v databázi. A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu udržuje kolekci s názvem querydefs – kolekce, která obsahuje její uložené querydefs –.

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Je možné i nadále přístup ke zdrojům dat ODBC s tříd DAO. Obecně třídy knihovny MFC rozhraní DAO podle podporují více než třídy knihovny MFC založená na rozhraní ODBC; třídy založené na rozhraní DAO můžou přistupovat k datům, včetně prostřednictvím ovladače rozhraní ODBC, prostřednictvím vlastní databázového stroje. Třídy založené na rozhraní DAO také podporu jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy rozhraní, aniž byste museli DAO volat přímo.

## <a name="usage"></a>Použití

Querydef objekty použijte buď pro práci s existujícím uloženého dotazu, nebo vytvořit nový uložit nebo dočasné dotazu:

1. Ve všech případech, nejprve se vytvoří `CDaoQueryDef` objektu, poskytuje ukazatel na [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu, ke které patří dotazu.

1. Proveďte následující kroky, podle toho, co chcete:

   - Pokud chcete použít stávající uložený dotaz, volání objektu querydef [otevřít](#open) členskou funkci, zadáním názvu uloženého dotazu.

   - Chcete-li vytvořit nové uloženého dotazu, volání objektu querydef [vytvořit](#create) členskou funkci, zadáním názvu dotazu. Poté zavolejte [připojit](#append) Uložte dotaz pomocí připojení k vaší databáze querydefs – kolekce. `Create` Vloží querydef v otevřeném stavu, takže po volání `Create` není volána `Open`.

   - Chcete-li vytvořit dočasný querydef, zavolejte `Create`. Zadat prázdný řetězec pro název dotazu. Nevolejte `Append`.

Po dokončení používání objektu querydef volat jeho [Zavřít](#close) členské funkci; poté zničit objekt querydef.

> [!TIP]
>  Nejjednodušší způsob, jak vytvořit uložené dotazy, je vytvořit a uložit je do databáze pomocí aplikace Microsoft Access. Pak můžete otevřít a použít je ve vašem kódu knihovny MFC.

## <a name="purposes"></a>Účely

Objekt querydef můžete použít pro žádné z těchto důvodů:

- Chcete-li vytvořit `CDaoRecordset` objektu

- Volání objektu `Execute` členská funkce přímo spustit dotaz akce nebo předávací dotaz SQL

Můžete použít objekt querydef pro jakýkoli typ dotazu, včetně vyberte akce, křížové tabulky, odstranění, aktualizace, připojení, vytvoření tabulky, definice dat, předávací SQL, sjednocení a hromadně dotazy. Typ dotazu je určen podle obsahu, který zadáte příkaz jazyka SQL. Informace o typy dotazů, najdete v článku `Execute` a [GetType](#gettype) členské funkce. Sady záznamů se obvykle používají pro vrácení řádek dotazuje, obvykle těm, kteří používají **vyberte... Z** klíčová slova. `Execute` se nejčastěji používá pro hromadné operace. Další informace najdete v tématu [Execute](#execute) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs – a sad záznamů

Použití objektu querydef vytvořit `CDaoRecordset` objektu, obvykle vytvořte nebo otevřete querydef, jak je popsáno výše. Potom sestavíte objekt sady záznamů, předání ukazatele na váš objekt querydef při volání [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Querydef, které můžete předat musí být v otevřeném stavu. Další informace najdete v tématu třídy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Nelze použít querydef vytvořit sadu záznamů (nejčastěji používá querydef), pokud to není v otevřeném stavu. Převést querydef do otevřeného stavu voláním buď `Open` nebo `Create`.

## <a name="external-databases"></a>Externí databáze

QueryDef objekty jsou preferovaným způsobem, jak používat nativní dialekt SQL externí databázového stroje. Můžete například vytvořit dotaz jazyka Transact SQL (jak je použita na systému Microsoft SQL Server) a uložte ho do objektu querydef. Když budete muset použít dotaz SQL není založená na databázovém stroji Microsoft Jet, musíte zadat připojovací řetězec, který odkazuje na externí zdroj dat. Dotazy s platným připojovacím řetězci obejít databázový stroj a předat dotaz přímo externím databázový server pro zpracování.

> [!TIP]
>  Preferovaný způsob, jak pracovat s tabulkami ODBC se pro připojení k Microsoft Jet (. Databáze MDB).

Související informace naleznete v tématech "Objekt QueryDef", "Querydefs – kolekce" a "CdbDatabase objekt" v sadě SDK rozhraní DAO.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="append"></a>  CDaoQueryDef::Append

Voláním této členské funkce po zavolání [vytvořit](#create) k vytvoření nového objektu querydef.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

`Append` uloží do databáze querydef přidáním objektu do databáze querydefs – kolekce. Bez připojení ho můžete použít querydef jako dočasný objekt, ale pokud chcete zachovat, musíte zavolat `Append`.

Pokud se pokusíte připojit querydef dočasný objekt, MFC, dojde k výjimce typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate

Voláním této členské funkce k určení, zda lze upravit querydef, jako je například změna jeho názvu nebo řetězec SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povoleno jej dále upravit querydef; jinak 0.

### <a name="remarks"></a>Poznámky

Querydef můžete upravit, pokud:

- Není založena na databázi, která je otevřená jen pro čtení.

- Nemáte oprávnění aktualizace pro databázi.

   To závisí na tom, jestli jste implementovali funkce zabezpečení. MFC neposkytuje podporu pro zabezpečení. je nutné implementovat ho sami volání rozhraní DAO přímo nebo pomocí aplikace Microsoft Access. Naleznete v tématu "Oprávnění vlastnost" v nápovědě k DAO.

##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef

Vytvoří `CDaoQueryDef` objektu.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Ukazatel na otevřený [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.

### <a name="remarks"></a>Poznámky

Objekt může představovat existující querydef uložené v querydefs – kolekce databáze, nový dotaz mají být uloženy v kolekci nebo dočasné dotazu, aby se neukládaly. Dalším krokem, závisí na typu querydef:

- Pokud objekt představuje existující querydef, volání objektu [otevřít](#open) členská funkce je inicializace.

- Pokud objekt představuje nové querydef se má uložit, volání objektu [vytvořit](#create) členskou funkci. To přidá objekt databáze querydefs – kolekce. Poté zavolejte `CDaoQueryDef` členské funkce pro nastavení atributů objektu. Nakonec proveďte volání [připojit](#append).

- Pokud objekt představuje dočasné querydef (nesmí být uloženo v databázi), zavolejte `Create`, předá prázdný řetězec pro název dotazu. Po volání `Create`, inicializovat querydef přímo nastavením jeho atributy. Nevolejte `Append`.

Pokud chcete nastavit atributy querydef, můžete použít [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)a [SetReturnsRecords](#setreturnsrecords) členské funkce.

Po dokončení s objektem querydef volat jeho [Zavřít](#close) členskou funkci. Pokud máte ukazatel querydef, použijte **odstranit** operátor zničit objekt jazyka C++.

##  <a name="close"></a>  CDaoQueryDef::Close

Po dokončení používání objektu querydef Zavolejte tuto členskou funkci.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Zavírá querydef uvolní základní objekt rozhraní DAO, ale nezničí uloženého objektu querydef rozhraní DAO nebo jazyka C++ `CDaoQueryDef` objektu. Toto není stejný jako [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), což querydef odstraní z databáze querydefs – kolekce v rozhraní DAO (Pokud není dočasné querydef).

##  <a name="create"></a>  CDaoQueryDef::Create

Voláním této členské funkce k vytvoření nové uložený dotaz nebo dočasné nový dotaz.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Jedinečný název dotazu uloženo v databázi. Podrobnosti o řetězce naleznete v tématu "CreateQueryDef metodu" v nápovědě k DAO. Pokud přijměte výchozí hodnotu, prázdný řetězec, je vytvořen dočasný querydef. Takový dotaz není uložen v querydefs – kolekce.

*Ipszsql*<br/>
Řetězec SQL, který definuje dotaz. Pokud přijmete výchozí hodnotu NULL, musíte později volat [SetSQL](#setsql) nastavit řetězec. Dokud to neuděláte dotaz není definováno. Ale můžete nedefinované dotaz otevřít sadu záznamů; Podrobnosti najdete v části poznámky. Příkaz jazyka SQL musí být definovány před querydef můžete připojit k querydefs – kolekce.

### <a name="remarks"></a>Poznámky

Pokud předáte název v *lpszName*, pak můžete volat [připojit](#append) uložit querydef databáze querydefs – kolekce. Objekt, jinak je dočasný querydef a se neuloží. V obou případech je querydef v otevřeném stavu, a můžete použít buď ji vytvořit [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu nebo volání querydef [Execute](#execute) členskou funkci.

Pokud nezadáte příkazu SQL v *Ipszsql*, nelze spustit dotaz s `Execute` ale můžete ho použít k vytvoření sady záznamů. V takovém případě knihovna MFC používá výchozí příkaz SQL sady záznamů.

##  <a name="execute"></a>  CDaoQueryDef::Execute

Voláním této členské funkce Spustit dotaz definovaný v objektu querydef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*nOptions*<br/>
Celé číslo, které určují vlastnosti dotazu. Související informace naleznete v tématu "Spustit metodu" v nápovědě k DAO. Můžete použít operátor bitového operátoru OR ( **&#124;**) ke sloučení následující konstanty pro tento argument:

- `dbDenyWrite` Odepřete jiným uživatelům oprávnění k zápisu.

- `dbInconsistent` Nekonzistentní aktualizace.

- `dbConsistent` Konzistentní aktualizace.

- `dbSQLPassThrough` Předávací SQL. Způsobí, že příkaz jazyka SQL, které se mají předat databáze ODBC pro zpracování.

- `dbFailOnError` Výchozí hodnota. Vrátit zpět aktualizace, pokud dojde k chybě a sestavy chybu uživateli.

- `dbSeeChanges` Generovat chyb za běhu, pokud jiný uživatel se mění data, která jsou úpravy.

> [!NOTE]
>  Vysvětlení podmínek "nekonzistentní" a "konzistentní", naleznete v tématu "Spustit metodu" v nápovědě k DAO.

### <a name="remarks"></a>Poznámky

QueryDef objekty používané pro spuštění tímto způsobem může představovat pouze jeden z následujících typů dotazu:

- Akce dotazy

- Předávací dotazy SQL

`Execute` nefunguje pro dotazy, které vrací záznamy, jako je například dotazů select. `Execute` Obvykle se používá pro hromadné operace dotazů, jako například **aktualizace**, **vložit**, nebo **SELECT INTO**, nebo pro operace s daty definition language (DDL).

> [!TIP]
>  Preferovaný způsob, jak práci se zdroji dat rozhraní ODBC se pro připojení k Microsoft Jet tabulky (. Databáze MDB). Další informace naleznete v tématu "Přístup k externí databáze s objektem DAO" v nápovědě rozhraní DAO.

Volání [GetRecordsAffected](#getrecordsaffected) členské funkce objektu querydef k určení počtu záznamy ovlivněny nejnovější `Execute` volání. Například `GetRecordsAffected` vrátí informace o počtu záznamů odstraněny, aktualizaci nebo vložení při provádění dotazu akce. Počet, vrátí se neprojeví, změny v souvisejících tabulkách, když cascade aktualizuje nebo odstraní jsou aktivní.

Zadáte-li obě `dbInconsistent` a `dbConsistent` nebo pokud ani jedno, výsledek je standardně `dbInconsistent`.

`Execute` nevrací sadu záznamů. Pomocí `Execute` na dotaz, který vybírá záznamy způsobí, že knihovna MFC má vyvolat výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect

Voláním této členské funkce k získání připojovacího řetězce související se zdrojem dat querydef.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahuje připojovací řetězec pro querydef.

### <a name="remarks"></a>Poznámky

Tato funkce slouží pouze s zdroje dat ODBC a ovladači určité ISAM. Není použit stroji Microsoft Jet (. Databáze MDB); v takovém případě `GetConnect` vrátí prázdný řetězec. Další informace najdete v tématu [SetConnect](#setconnect).

> [!TIP]
>  Preferovaný způsob, jak pracovat s tabulkami ODBC se připojte je k. Databáze MDB. Další informace naleznete v tématu "Přístup k externí databáze s objektem DAO" v nápovědě rozhraní DAO.

Informace o připojovacích řetězcích naleznete v tématu "Připojit vlastnost" v nápovědě k DAO.

##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated

Voláním této členské funkce, chcete-li získat datum vytvoření objektu querydef.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje datum a čas querydef byl vytvořen.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated

Tato členská funkce, chcete-li získat objekt querydef datum poslední aktualizace volání – Pokud některý z jeho vlastnosti byly změněny, například jeho název, jeho řetězec SQL nebo její připojovací řetězec.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje datum a čas poslední aktualizace querydef.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount

Voláním této členské funkce se načíst počet polí v dotazu.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí definovaných v dotazu.

### <a name="remarks"></a>Poznámky

`GetFieldCount` je užitečné pro všechna pole v querydef ve smyčce. Pro tento účel použít `GetFieldCount` ve spojení s [GetFieldInfo](#getfieldinfo).

##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo

Voláním této členské funkce získat různé druhy informací o pole definované v querydef.

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule požadované pole v kolekci querydef pole pro vyhledávání podle indexu.

*FieldInfo*<br/>
Odkaz na `CDaoFieldInfo` objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o pole, které chcete načíst. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrátit:

- AFX_DAO_PRIMARY_INFO (výchozí) název, typ, velikosti, atributy

- Informace o primárním AFX_DAO_SECONDARY_INFO plus: ordinální číslo pozice, vyžaduje, Povolit nulovou délku, zdrojové pole, cizí název, zdrojová tabulka, pořadí řazení

- AFX_DAO_ALL_INFO primární a sekundární informace plus: výchozí hodnota ověření textu ověřovacího pravidla

*lpszName*<br/>
Řetězec obsahující název požadované pole pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Popis informací, v *fieldinfo*, najdete v článku [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají popisné informace v části *dwInfoOptions* výše. Pokud jste požádali o jednu úroveň informací, získáte všech předchozích úrovní také informace.

##  <a name="getname"></a>  CDaoQueryDef::GetName

Voláním této členské funkce načíst název dotazu reprezentována querydef.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Název dotazu.

### <a name="remarks"></a>Poznámky

Názvy QueryDef jsou jedinečné názvy definované uživatelem. Další informace o názvech querydef naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout

Voláním této členské funkce pro aktuální časový limit načtení předtím, než vyprší časový limit dotazu na zdroji dat rozhraní ODBC.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Počet sekund před dotaz vyprší časový limit.

### <a name="remarks"></a>Poznámky

Informace o tomto časový limit naleznete v tématu "Odezvy vlastnost" v nápovědě k DAO.

> [!TIP]
>  Preferovaný způsob, jak pracovat s tabulkami ODBC se pro připojení k Microsoft Jet (. Databáze MDB). Další informace naleznete v tématu "Přístup k externí databáze s objektem DAO" v nápovědě rozhraní DAO.

##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount

Voláním této členské funkce se načíst počet parametrů v uloženého dotazu.

```
short GetParameterCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet parametrů definovaných v dotazu.

### <a name="remarks"></a>Poznámky

`GetParameterCount` je užitečné pro všechny parametry v querydef ve smyčce. Pro tento účel použít `GetParameterCount` ve spojení s [getparameterinfo –](#getparameterinfo).

Související informace naleznete v tématech "Parametr objektu", "Kolekce parametrů" a "parametry deklarace (SQL)" v nápovědě k DAO.

##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo

Voláním této členské funkce získat informace o parametru definované v querydef.

```
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule požadovaný parametr v kolekci parametrů querydef, pro vyhledávání podle indexu.

*paraminfo*<br/>
Odkaz na [cdaoparameterinfo –](../../mfc/reference/cdaoparameterinfo-structure.md) objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o parametru pro načtení. K dispozici možnost zde uvedené spolu s co ho způsobuje, že funkce vrátí:

- Název AFX_DAO_PRIMARY_INFO (výchozí), zadejte

*lpszName*<br/>
Řetězec obsahující název požadovaného parametru pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Popis informací, v *paraminfo*, najdete v článku [cdaoparameterinfo –](../../mfc/reference/cdaoparameterinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají popisné informace v části *dwInfoOptions* výše.

Související informace naleznete v tématu "parametry deklarace (SQL)" v nápovědě k DAO.

##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue

Voláním této členské funkce načte aktuální hodnota uložená v kolekci parametrů querydef zadaný parametr.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název parametru, jehož hodnotu chcete pro vyhledávání podle názvu.

*nIndex*<br/>
Z nuly vycházející index parametru v kolekci parametrů querydef, pro vyhledávání podle indexu. Můžete získat tuto hodnotu s voláními [GetParameterCount](#getparametercount) a [getparameterinfo –](#getparameterinfo).

### <a name="return-value"></a>Návratová hodnota

Objekt třídy [COleVariant](../../mfc/reference/colevariant-class.md) , který obsahuje hodnoty parametru.

### <a name="remarks"></a>Poznámky

Tento parametr můžete přistupovat pomocí názvu nebo podle jeho pořadové číslo pozice v kolekci.

Související informace naleznete v tématu "parametry deklarace (SQL)" v nápovědě k DAO.

##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected

Voláním této členské funkce k určení, kolik záznamů vliv na poslední volání [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů ovlivněný.

### <a name="remarks"></a>Poznámky

Počet, vrátí se neprojeví, změny v souvisejících tabulkách, když cascade aktualizuje nebo odstraní jsou aktivní.

Související informace naleznete v tématu "RecordsAffected vlastnost" v nápovědě k DAO.

##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords

Voláním této členské funkce určete, zda querydef je založena na dotazu, které vrací záznamy.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud querydef je založena na dotazu, které vrací záznamy; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá pouze pro předávací dotazy SQL. Další informace o dotazech SQL najdete v tématu [Execute](#execute) členskou funkci. Další informace o práci s předávací dotazy SQL, najdete v článku [SetReturnsRecords](#setreturnsrecords) členskou funkci.

Související informace naleznete v tématu "Vrací záznamy vlastnost" v nápovědě k DAO.

##  <a name="getsql"></a>  CDaoQueryDef::GetSQL

Voláním této členské funkce načíst příkaz jazyka SQL, který definuje dotaz, na kterých je založena querydef.

```
CString GetSQL();
```

### <a name="return-value"></a>Návratová hodnota

Příkaz SQL, který definuje dotaz, na kterých je založena querydef.

### <a name="remarks"></a>Poznámky

Pak budou pravděpodobně analýzu řetězce pro klíčová slova, názvy tabulek a tak dále.

Související informace naleznete v tématech "Vlastnosti SQL", "Porovnání z Microsoft Jet databáze modul SQL a ANSI SQL" a "Dotazování databázi s SQL v kódu" v nápovědě rozhraní DAO.

##  <a name="gettype"></a>  CDaoQueryDef::GetType

Voláním této členské funkce, chcete-li zjistit typ dotazu querydef.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Zadejte dotaz definovaný sadou querydef. Hodnoty naleznete v části poznámky.

### <a name="remarks"></a>Poznámky

Typ dotazu je nastavena podle co zadáte řetězec SQL querydef při vytváření querydef nebo volat existující querydef [SetSQL](#setsql) členskou funkci. Typ dotazu vrácená touto funkcí může být jeden z následujících hodnot:

- `dbQSelect` Vyberte

- `dbQAction` Akce

- `dbQCrosstab` Křížové tabulky

- `dbQDelete` Odstranit

- `dbQUpdate` Aktualizace

- `dbQAppend` Připojení

- `dbQMakeTable` Vytvoření tabulky

- `dbQDDL` Definice dat

- `dbQSQLPassThrough` Předávací

- `dbQSetOperation` sjednocení

- `dbQSPTBulk` Použít s `dbQSQLPassThrough` zadat dotaz, který nevrací záznamy.

> [!NOTE]
>  K vytvoření předávací dotaz SQL, nemají nastavený `dbSQLPassThrough` konstantní. To je nastavena automaticky v databázovém stroji Microsoft Jet při vytváření objektu querydef a nastavíme připojovací řetězec.

Informace o řetězcích SQL najdete v tématu [GetSQL](#getsql). Informace o typech dotazů najdete v tématu [Execute](#execute).

##  <a name="isopen"></a>  CDaoQueryDef::IsOpen

Voláním této členské funkce k určení, zda `CDaoQueryDef` objektu je momentálně otevřený.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CDaoQueryDef` objekt je aktuálně otevřené; jinak 0.

### <a name="remarks"></a>Poznámky

Querydef musí být v otevřeném stavu, než ho použijete pro volání [Execute](#execute) nebo k vytvoření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu. Převést querydef do volání rozhraní otevřeného stavu buď [vytvořit](#create) (pro nové querydef) nebo [otevřete](#open) (pro existující querydef).

##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase

Obsahuje ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt přidružený k objektu querydef.

### <a name="remarks"></a>Poznámky

Pokud potřebujete přístup k databázi přímo použít tento ukazatel – například k získání ukazatele na další querydef nebo sadu záznamů. objekty v databáze kolekce.

##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef

Obsahuje ukazatel na rozhraní OLE pro podkladové querydef objekt DAO.

### <a name="remarks"></a>Poznámky

This – ukazatel se poskytuje pro úplnost a konzistence s jinými třídami. Ale protože knihovny MFC zapouzdřuje spíše plně querydefs – rozhraní DAO, budete pravděpodobně potřebovat. Pokud použijete, tak učinit s rozvahou – zejména, neměňte hodnotu ukazatele Pokud si nejste jisti, co právě děláte.

##  <a name="open"></a>  CDaoQueryDef::Open

Voláním této členské funkce a otevřete querydef předtím uložily do databáze querydefs – kolekce.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězec, který obsahuje název uloženého querydef otevřete. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Jakmile se otevře querydef, můžete volat jeho [Execute](#execute) členská funkce nebo použití querydef vytvořit [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu.

##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect

Voláním této členské funkce pro nastavení objektu querydef připojovací řetězec.

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Řetězec, který obsahuje připojovací řetězec pro přidružený [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.

### <a name="remarks"></a>Poznámky

Připojovací řetězec se používá k předávání dalších informací do rozhraní ODBC a ovladači určité ISAM podle potřeby. Není použit pro Microsoft Jet (. Databáze MDB).

> [!TIP]
>  Preferovaný způsob, jak pracovat s tabulkami ODBC se připojte je k. Databáze MDB.

Před provedením querydef, který představuje předávací dotaz SQL ke zdroji dat rozhraní ODBC, nastavíme připojovací řetězec s `SetConnect` a volat [SetReturnsRecords](#setreturnsrecords) k určení, zda dotaz vrací záznamy.

Další informace o struktuře a příklady součástí připojovací řetězec připojovacím řetězci naleznete v tématu "Připojit vlastnost" v nápovědě k DAO.

##  <a name="setname"></a>  CDaoQueryDef::SetName

Pokud chcete změnit název querydef, který není dočasné Zavolejte tuto členskou funkci.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězec, který obsahuje nový název pro nontemporary dotaz v přidruženém [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.

### <a name="remarks"></a>Poznámky

Názvy QueryDef jsou jedinečné, uživatelem definované názvy. Můžete volat `SetName` před querydef se objekt připojí querydefs – kolekce.

##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout

Voláním této členské funkce pro nastavení časového limitu, předtím, než vyprší časový limit dotazu na zdroji dat rozhraní ODBC.

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parametry

*nODBCTimeout*<br/>
Počet sekund před dotaz vyprší časový limit.

### <a name="remarks"></a>Poznámky

Tato členská funkce umožňuje přepsat výchozí počet sekund před následné operace s připojeného zdroje dat "časový limit." Operace může časový limit z důvodu problémů s přístupem k síti, doba zpracování nadměrné dotazu a tak dále. Volání `SetODBCTimeout` před spuštěním dotazu s této querydef, pokud chcete změnit hodnotu vypršení časového limitu dotazu. (Protože ODBC opětovně používá připojení, hodnota časového limitu je stejný pro všechny klienty ve stejné připojení.)

Výchozí hodnota pro vypršení časového limitu dotazu je 60 sekund.

##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue

Voláním této členské funkce k nastavení hodnoty parametru v querydef v době běhu.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název parametru, jehož hodnota, kterou chcete nastavit.

*varValue*<br/>
Hodnota pro nastavení; viz poznámky.

*nIndex*<br/>
Pořadové číslo pozice parametru v kolekci parametrů querydef. Můžete získat tuto hodnotu s voláními [GetParameterCount](#getparametercount) a [getparameterinfo –](#getparameterinfo).

### <a name="remarks"></a>Poznámky

Parametr musí již byly vytvořeny jako součást řetězce querydef SQL. Tento parametr můžete přistupovat pomocí názvu nebo podle jeho pořadové číslo pozice v kolekci.

Zadejte hodnotu pro nastavení jako `COleVariant` objektu. Informace o nastavení požadovanou hodnotu a typ v vaše `COleVariant` objektu, naleznete v tématu třídy [COleVariant](../../mfc/reference/colevariant-class.md).

##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords

Voláním této členské funkce jako součást procesu nastavení předávací dotaz SQL k externí databázi.

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parametry

*bReturnsRecords*<br/>
Předat hodnotu TRUE, pokud dotaz na externí databázi vrátí záznamy; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

V takovém případě musíte vytvořit querydef a nastavte její vlastnosti pomocí jiné `CDaoQueryDef` členské funkce. Popis externí databáze najdete v tématu [SetConnect](#setconnect).

##  <a name="setsql"></a>  CDaoQueryDef::SetSQL

Voláním této členské funkce pro nastavení příkazu SQL, který se spustí querydef.

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Ipszsql*<br/>
Řetězec obsahující úplný příkaz SQL, vhodný pro spuštění. Syntaxe tohoto řetězce závisí na správce databáze, který cílí váš dotaz. Informace o syntaxi používá v databázovém stroji Microsoft Jet naleznete v tématu "Vytváření SQL příkazy v kódu" v nápovědě rozhraní DAO.

### <a name="remarks"></a>Poznámky

Typické použití `SetSQL` je nastavení querydef objekt pro použití v předávací dotaz SQL. (Syntaxe předávací dotazy SQL v cílovém systému DBMS, najdete v dokumentaci k systému DBMS.)

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
