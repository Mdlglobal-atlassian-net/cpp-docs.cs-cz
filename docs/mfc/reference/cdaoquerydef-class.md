---
title: CDaoQueryDef – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 08fb2909a4fd2e5bda3dfc63d19224a515c7c699
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883886"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef – třída

Představuje definici dotazu nebo "querydef", obvykle uloženou v databázi.

## <a name="syntax"></a>Syntaxe

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Vytvoří objekt `CDaoQueryDef`. Další volání `Open` nebo `Create`podle vašich potřeb.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef:: Append](#append)|Připojí objekt querydef do kolekce QueryDefs databáze jako uložený dotaz.|
|[CDaoQueryDef:: CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud dotaz může aktualizovat databázi.|
|[CDaoQueryDef:: Close](#close)|Zavře objekt querydef. Zničení C++ objektu po jeho dokončení.|
|[CDaoQueryDef:: Create](#create)|Vytvoří podkladový objekt DAO querydef. Použijte jako dočasný dotaz querydef nebo zavolejte `Append` a uložte ho do databáze.|
|[CDaoQueryDef:: Execute](#execute)|Provede dotaz definovaný objektem querydef.|
|[CDaoQueryDef:: GetConnect](#getconnect)|Vrátí připojovací řetězec přidružený k poli querydef. Připojovací řetězec identifikuje zdroj dat. (Pouze předávací dotazy SQL; v opačném případě prázdný řetězec)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Vrátí datum vytvoření uloženého dotazu.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum poslední aktualizace uloženého dotazu.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Vrátí počet polí definovaných v poli querydef.|
|[CDaoQueryDef:: GetFieldInfo](#getfieldinfo)|Vrátí informace o zadaném poli definovaném v dotazu.|
|[CDaoQueryDef:: GetName](#getname)|Vrátí název querydef.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Vrátí hodnotu časového limitu použitou rozhraním ODBC (pro dotaz ODBC) při spuštění objektu querydef. Určuje, jak dlouho má být povoleno provedení akce dotazu.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Vrátí počet parametrů definovaných pro dotaz.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Vrátí informace o zadaném parametru dotazu.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Vrátí hodnotu zadaného parametru dotazu.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů ovlivněných dotazem akce.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Vrátí nenulovou hodnotu, pokud dotaz definovaný pomocí querydef vrátí záznamy.|
|[CDaoQueryDef::GetSQL](#getsql)|Vrátí řetězec SQL, který určuje dotaz definovaný pomocí querydef.|
|[CDaoQueryDef:: GetType](#gettype)|Vrátí typ dotazu: odstranit, aktualizovat, připojit, vytvořit tabulku a tak dále.|
|[CDaoQueryDef:: Open](#isopen)|Vrátí nenulovou hodnotu, pokud je otevřen querydef a lze jej spustit.|
|[CDaoQueryDef:: Open](#open)|Otevře existující objekt querydef uložený v kolekci QueryDefs databáze.|
|[CDaoQueryDef::SetConnect](#setconnect)|Nastaví připojovací řetězec pro předávací dotaz SQL na zdroj dat ODBC.|
|[CDaoQueryDef::SetName](#setname)|Nastaví název uloženého dotazu a nahradí název, který se používá, když byl vytvořen querydef.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Nastaví hodnotu časového limitu použitou rozhraním ODBC (pro dotaz ODBC) při spuštění objektu querydef.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Nastaví hodnotu zadaného parametru dotazu.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Určuje, zda se v poli querydef vrátí záznamy. Nastavení tohoto atributu na hodnotu TRUE je platné pouze pro předávací dotazy SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Nastaví řetězec SQL, který určuje dotaz definovaný pomocí querydef.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef:: m_pDAOQueryDef](#m_pdaoquerydef)|Ukazatel na rozhraní OLE pro podkladový objekt DAO querydef.|
|[CDaoQueryDef:: m_pDatabase](#m_pdatabase)|Ukazatel na objekt `CDaoDatabase`, ke kterému je přidružen querydef. Tento querydef může být uložen v databázi, nebo ne.|

## <a name="remarks"></a>Poznámky

Querydef je objekt pro přístup k datům, který obsahuje příkaz SQL, který popisuje dotaz, a jeho vlastnosti, například "datum vytvoření" a "časový limit ODBC". Můžete také vytvořit dočasné objekty QueryDef bez jejich uložení, ale je to pohodlné a mnohem efektivnější – pro uložení běžně používaných dotazů v databázi. Objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) udržuje kolekci s názvem kolekce QueryDefs, která obsahuje své uložené QueryDefs.

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd knihovny MFC založených na rozhraní ODBC (Open Database Connectivity). Všechny názvy databázových tříd DAO mají předponu "CDao". Ke zdrojům dat rozhraní ODBC můžete přistupovat i s třídami DAO. Obecně jsou třídy knihovny MFC založené na rozhraní DAO větší, než třídy knihovny MFC založené na rozhraní ODBC; třídy založené na rozhraní DAO mají přístup k datům, včetně přes ovladače rozhraní ODBC, prostřednictvím vlastního databázového stroje. Třídy založené na rozhraní DAO také podporují operace DDL (Data Definition Language), jako je například přidávání tabulek přes třídy, aniž by bylo nutné volat rozhraní DAO přímo.

## <a name="usage"></a>Využití

Použijte objekty QueryDef buď pro práci s existujícím uloženým dotazem, nebo pro vytvoření nového uloženého dotazu nebo dočasného dotazu:

1. Ve všech případech nejprve Sestavte objekt `CDaoQueryDef` a poskytněte ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) , ke kterému dotaz patří.

1. Pak proveďte následující postup v závislosti na tom, co chcete:

   - Chcete-li použít existující uložený dotaz, zavolejte členskou funkci [Open](#open) member objektu querydef a zadejte název uloženého dotazu.

   - Chcete-li vytvořit nový uložený dotaz, zavolejte funkci [Create](#create) member objektu querydef a zadejte název dotazu. Pak voláním [Append](#append) Uložte dotaz tak, že ho připojíte do kolekce QueryDefs databáze. `Create` vloží objekt querydef do otevřeného stavu, takže po volání `Create` nebudete volat `Open`.

   - Chcete-li vytvořit dočasný objekt querydef, zavolejte `Create`. Pro název dotazu předejte prázdný řetězec. Nevolejte `Append`.

Po dokončení použití objektu querydef volejte jeho členskou funkci [Close](#close) ; Poté odstraňte objekt querydef.

> [!TIP]
>  Nejjednodušší způsob, jak vytvořit uložené dotazy, je vytvořit je a uložit je do databáze pomocí Microsoft Accessu. Pak je můžete otevřít a použít ve svém kódu knihovny MFC.

## <a name="purposes"></a>Cíle

Objekt querydef můžete použít pro některý z následujících důvodů:

- Vytvoření objektu `CDaoRecordset`

- Chcete-li volat členskou funkci objektu `Execute` k přímému provedení dotazu akce nebo předávacího dotazu SQL

Objekt querydef můžete použít pro jakýkoliv typ dotazu, včetně příkazu SELECT, Action, křížová, DELETE, Update, Append, the-Table, definition, data, Pass-through, Union a Bulk dotazů SQL. Typ dotazu je určen obsahem příkazu jazyka SQL, který zadáte. Informace o typech dotazů naleznete v tématu členské funkce `Execute` a [GetType](#gettype) . Sady záznamů se běžně používají pro dotazy vracející řádky, obvykle s použitím **SELECT... Z** klíčových slov. `Execute` se nejčastěji používá pro hromadné operace. Další informace najdete v tématu věnovaném [provádění](#execute) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>QueryDefs a sady záznamů

Chcete-li použít objekt querydef k vytvoření objektu `CDaoRecordset`, obvykle je třeba vytvořit nebo otevřít objekt querydef, jak je popsáno výše. Poté vytvořte objekt sady záznamů a předejte ukazatel na objekt querydef při volání [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). Objekt querydef, který předáte, musí být v otevřeném stavu. Další informace najdete v tématu Třída [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

K vytvoření sady záznamů (nejběžnější použití pro querydef) nemůžete použít querydef, pokud není v otevřeném stavu. Vložte querydef do otevřeného stavu voláním `Open` nebo `Create`.

## <a name="external-databases"></a>Externí databáze

Objekty QueryDef jsou preferovaným způsobem, jak použít nativní dialekt SQL externího databázového stroje. Můžete například vytvořit dotaz Transact SQL (jak se používá na Microsoft SQL Server) a uložit ho do objektu querydef. Pokud potřebujete použít dotaz SQL, který není založen na databázovém stroji Microsoft Jet, je nutné zadat připojovací řetězec, který odkazuje na externí zdroj dat. Dotazy s platnými připojovacími řetězci vycházejí z databázového stroje a předají dotaz přímo na externí databázový server ke zpracování.

> [!TIP]
>  Upřednostňovaným způsobem, jak pracovat s tabulkami ODBC, je připojit je k Microsoft Jet (. MDB) databáze.

Související informace naleznete v tématech "objekt QueryDef", "QueryDefs Collection" a "CdbDatabase Object" v sadě SDK pro rozhraní DAO.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="append"></a>CDaoQueryDef:: Append

Po volání metody [Create](#create) pro vytvoření nového objektu querydef volejte tuto členskou funkci.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

`Append` uloží objekt querydef do databáze připojením objektu k kolekci QueryDefs databáze. Můžete použít querydef jako dočasný objekt bez připojení, ale pokud chcete zachovat, je nutné volat `Append`.

Pokusíte-li se připojit k dočasnému objektu QueryDef, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="canupdate"></a>CDaoQueryDef:: CanUpdate

Zavolejte tuto členskou funkci, abyste zjistili, jestli můžete upravit querydef, třeba změnit jeho název nebo řetězec SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je povoleno upravit querydef; v opačném případě 0.

### <a name="remarks"></a>Poznámky

V případě potřeby můžete upravit querydef.

- Není založen na databázi, která je otevřena jen pro čtení.

- Máte oprávnění k aktualizaci databáze.

   To závisí na tom, jestli jste implementovali funkce zabezpečení. Knihovna MFC neposkytuje podporu pro zabezpečení; musíte ji implementovat sami voláním DAO přímo nebo pomocí Microsoft Accessu. Viz téma "vlastnost oprávnění" v nápovědě pro rozhraní DAO.

##  <a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Vytvoří objekt `CDaoQueryDef`.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Ukazatel na otevřený objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Poznámky

Objekt může představovat existující querydef uložený v kolekci QueryDefs databáze, nový dotaz, který se má uložit v kolekci, nebo dočasný dotaz, který se má uložit. Váš další krok závisí na typu querydef:

- Pokud objekt představuje existující querydef, zavolejte na [otevřené](#open) členské funkce objektu a inicializujte ho.

- Pokud objekt představuje nový objekt querydef pro uložení, zavolejte členskou funkci [Create](#create) objektu. Tím se objekt přidá do kolekce QueryDefs databáze. Potom zavolejte `CDaoQueryDef` členské funkce pro nastavení atributů objektu. Nakonec zavolejte [připojit](#append).

- Pokud objekt představuje dočasný objekt QueryDef (nesmí být uložen v databázi), zavolejte `Create`a předejte prázdný řetězec pro název dotazu. Po volání `Create`inicializujte parametr querydef přímo nastavením jeho atributů. Nevolejte `Append`.

Chcete-li nastavit atributy querydef, můžete použít členské funkce [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)a [SetReturnsRecords](#setreturnsrecords) .

Po dokončení objektu querydef volejte jeho členskou funkci [Close](#close) . Pokud máte ukazatel na querydef, použijte k zničení C++ objektu operátor **Delete** .

##  <a name="close"></a>CDaoQueryDef:: Close

Tuto členskou funkci zavolejte po dokončení použití objektu querydef.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Zavřením objektu querydef vydáváte základní objekt DAO, ale nezničíte uložený objekt DAO C++ querydef nebo objekt `CDaoQueryDef`. Nejedná se o stejnou hodnotu jako [CDaoDatabase::D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), která odstraní objekt querydef z kolekce QueryDefs databáze v rozhraní DAO (Pokud není dočasným objektem querydef).

##  <a name="create"></a>CDaoQueryDef:: Create

Zavolejte tuto členskou funkci pro vytvoření nového uloženého dotazu nebo nového dočasného dotazu.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Jedinečný název dotazu, který byl uložen v databázi. Podrobnosti o řetězci naleznete v tématu "CreateQueryDef metoda" v nápovědě rozhraní DAO. Pokud přijmete výchozí hodnotu, vytvoří se dočasný řetězec querydef. Takový dotaz není uložen v kolekci QueryDefs.

*Ipszsql*<br/>
Řetězec SQL definující dotaz Pokud přijmete výchozí hodnotu NULL, musíte později volat [SetSQL](#setsql) a nastavit řetězec. Do té doby nebude dotaz definován. K otevření sady záznamů ale můžete použít nedefinovaný dotaz. Podrobnosti najdete v části poznámky. Příkaz jazyka SQL musí být definován předtím, než bude možné připojit soubor querydef do kolekce QueryDefs.

### <a name="remarks"></a>Poznámky

Pokud předáte název v *lpszName*, můžete zavolat příkaz [Append](#append) k uložení querydef v kolekci QueryDefs databáze. V opačném případě je objekt dočasným objektem querydef a není uložen. V obou případech je objekt querydef v otevřeném stavu a lze jej použít k vytvoření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) nebo k volání členské funkce [Execute](#execute) objektu querydef.

Pokud nezadáte příkaz SQL v *lpszSQL*, nelze spustit dotaz s `Execute`, ale lze jej použít k vytvoření sady záznamů. V takovém případě knihovna MFC používá výchozí příkaz SQL sady záznamů.

##  <a name="execute"></a>CDaoQueryDef:: Execute

Zavolejte tuto členskou funkci pro spuštění dotazu definovaného objektem querydef.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*nOptions*<br/>
Celé číslo, které určuje charakteristiky dotazu. Související informace naleznete v tématu "spustit metodu" v nápovědě rozhraní DAO. K kombinování následujících konstant pro tento argument můžete **&#124;** použít bitový operátor OR ():

- `dbDenyWrite` odepřít oprávnění k zápisu jiným uživatelům.

- `dbInconsistent` nekonzistentní aktualizace.

- `dbConsistent` konzistentní aktualizace.

- `dbSQLPassThrough` průchod SQL. Způsobí, že příkaz SQL bude předán databázi ODBC ke zpracování.

- `dbFailOnError` výchozí hodnota. Vrátit zpět aktualizace, pokud dojde k chybě, a nahlásit chybu uživateli

- `dbSeeChanges` vygenerovat běhovou chybu, pokud jiný uživatel mění data, která upravujete.

> [!NOTE]
>  Vysvětlení podmínek "nekonzistentní" a "konzistentní" naleznete v nápovědě k rozhraní DAO v tématu "Execute Method".

### <a name="remarks"></a>Poznámky

Objekty QueryDef použité pro provedení tímto způsobem mohou představovat pouze jeden z následujících typů dotazů:

- Akční dotazy

- Předávací dotazy SQL

`Execute` nefunguje u dotazů, které vracejí záznamy, jako jsou například dotazy SELECT. `Execute` se běžně používá pro dotazy hromadné operace, jako je například **aktualizace**, **vložení**nebo **Výběr do**nebo pro operace jazyka DDL (Data Definition Language).

> [!TIP]
>  Upřednostňovaným způsobem, jak pracovat se zdroji dat ODBC, je připojení tabulek ke službě Microsoft Jet (. MDB) databáze. Další informace najdete v nápovědě k rozhraní DAO v tématu "přístup k externím databázím s rozhraním DAO".

Zavolejte členskou funkci [GetRecordsAffected](#getrecordsaffected) objektu QueryDef, abyste určili počet záznamů ovlivněných nejnovějším voláním `Execute`. `GetRecordsAffected` například vrátí informace o počtu odstraněných, aktualizovaných nebo vložených záznamů při provádění dotazu akce. Vrácený počet nebude odrážet změny v souvisejících tabulkách, pokud jsou v platnosti kaskádové aktualizace nebo odstraňování.

Pokud zahrnete `dbInconsistent` i `dbConsistent` nebo pokud nezadáte hodnotu, bude výsledkem výchozí hodnota `dbInconsistent`.

`Execute` nevrací sadu záznamů. Použití `Execute` u dotazu, který vybere záznamy, způsobí, že knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

##  <a name="getconnect"></a>CDaoQueryDef:: GetConnect

Zavolejte tuto členskou funkci pro získání připojovacího řetězce spojeného se zdrojem dat querydef.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující připojovací řetězec pro querydef.

### <a name="remarks"></a>Poznámky

Tato funkce se používá jenom u zdrojů dat ODBC a některých ovladačů ISAM. Nepoužívá se s Microsoft Jet (. MDB) databází; v tomto případě `GetConnect` vrátí prázdný řetězec. Další informace najdete v tématu [SetConnect](#setconnect).

> [!TIP]
>  Upřednostňovaným způsobem, jak pracovat s tabulkami ODBC, je připojit je k. Databáze MDB. Další informace najdete v nápovědě k rozhraní DAO v tématu "přístup k externím databázím s rozhraním DAO".

Informace o připojovacích řetězcích najdete v nápovědě k rozhraní DAO v tématu "vlastnosti připojení".

##  <a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

Voláním této členské funkce získáte datum vytvoření objektu querydef.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

Objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obsahující datum a čas vytvoření objektu querydef.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "DateCreated, hodnota LastUpdated Properties" v nápovědě pro rozhraní DAO.

##  <a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Voláním této členské funkce získáte datum poslední aktualizace objektu querydef – Pokud se změnila kterákoli z jeho vlastností, jako je název, řetězec SQL nebo jeho připojovací řetězec.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

Objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obsahující datum a čas poslední aktualizace objektu querydef.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "DateCreated, hodnota LastUpdated Properties" v nápovědě pro rozhraní DAO.

##  <a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Zavolejte tuto členskou funkci pro načtení počtu polí v dotazu.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí definovaných v dotazu.

### <a name="remarks"></a>Poznámky

`GetFieldCount` je užitečné pro procházení všemi poli v querydef. Pro tento účel použijte `GetFieldCount` ve spojení s parametrem [GetFieldInfo](#getfieldinfo).

##  <a name="getfieldinfo"></a>CDaoQueryDef:: GetFieldInfo

Voláním této členské funkce získáte různé druhy informací o poli definovaném v querydef.

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
Index založený na nule požadovaného pole v kolekci polí querydef pro vyhledávání podle indexu.

*FieldInfo*<br/>
Odkaz na objekt `CDaoFieldInfo`, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, které informace o poli se mají načíst. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí:

- AFX_DAO_PRIMARY_INFO (výchozí) název, typ, velikost, atributy

- AFX_DAO_SECONDARY_INFO primární informace plus: ordinální pozice, požadováno, povolení nulové délky, zdrojové pole, cizí název, zdrojová tabulka, pořadí řazení

- AFX_DAO_ALL_INFO primární a sekundární informace plus: výchozí hodnota, text ověření, ověřovací pravidlo

*lpszName*<br/>
Řetězec obsahující název požadovaného pole pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Popis informací vrácených v rozhraní *FieldInfo*naleznete v tématu struktura [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají popisným informacím v *dwInfoOptions* výše. Pokud si vyžádáte jednu úroveň informací, dostanete také předchozí úrovně informací.

##  <a name="getname"></a>CDaoQueryDef:: GetName

Voláním této členské funkce načtete název dotazu reprezentovaný querydef.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Název dotazu.

### <a name="remarks"></a>Poznámky

Názvy QueryDef jsou jedinečné uživatelsky definované názvy. Další informace o názvech querydef naleznete v tématu "vlastnost Name" v nápovědě pro rozhraní DAO.

##  <a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Zavolejte tuto členskou funkci, aby se načetl aktuální časový limit předtím, než vyprší časový limit dotazu na zdroj dat rozhraní ODBC.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Počet sekund, po jejichž uplynutí vyprší časový limit dotazu.

### <a name="remarks"></a>Poznámky

Informace o tomto časovém limitu najdete v tématu "vlastnost ODBCTimeout" v nápovědě k rozhraní DAO.

> [!TIP]
>  Upřednostňovaným způsobem, jak pracovat s tabulkami ODBC, je připojit je k Microsoft Jet (. MDB) databáze. Další informace najdete v nápovědě k rozhraní DAO v tématu "přístup k externím databázím s rozhraním DAO".

##  <a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Zavolejte tuto členskou funkci pro načtení počtu parametrů v uloženém dotazu.

```
short GetParameterCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet parametrů definovaných v dotazu.

### <a name="remarks"></a>Poznámky

`GetParameterCount` je užitečné pro procházení všech parametrů v querydef. Pro tento účel použijte `GetParameterCount` ve spojení s [GetParameterInfo](#getparameterinfo).

Související informace naleznete v tématech "objekt parametru", "kolekce parametrů" a "deklarace PARAMETERS" (SQL) v nápovědě k rozhraní DAO.

##  <a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo

Voláním této členské funkce získáte informace o parametru definovaném v querydef.

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
Index založený na nule požadovaného parametru v kolekci parametrů querydef pro vyhledávání podle indexu.

*paraminfo*<br/>
Odkaz na objekt [CDaoParameterInfo –](../../mfc/reference/cdaoparameterinfo-structure.md) , který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují informace o parametru, který se má načíst. Dostupná možnost je uvedena zde spolu s tím, co způsobí, že funkce vrátí:

- AFX_DAO_PRIMARY_INFO (výchozí) název zadejte

*lpszName*<br/>
Řetězec obsahující název požadovaného parametru pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Popis informací vrácených v *ParamInfo*najdete v tématu struktura [CDaoParameterInfo –](../../mfc/reference/cdaoparameterinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají popisným informacím v *dwInfoOptions* výše.

Související informace naleznete v tématu deklarace PARAMETERS (SQL) v nápovědě k rozhraní DAO.

##  <a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Zavolejte tuto členskou funkci, aby se načetla aktuální hodnota zadaného parametru, který je uložený v kolekci parametrů querydef.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název parametru, jehož hodnotu chcete vyhledat podle názvu.

*nIndex*<br/>
Index založený na nule parametru v kolekci parametrů querydef pro vyhledávání podle indexu. Tuto hodnotu můžete získat pomocí volání [GetParameterCount](#getparametercount) a [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Návratová hodnota

Objekt třídy [COleVariant](../../mfc/reference/colevariant-class.md) , který obsahuje hodnotu parametru.

### <a name="remarks"></a>Poznámky

K parametru můžete přistupovat buď podle názvu, nebo podle jeho ordinální pozice v kolekci.

Související informace naleznete v tématu deklarace PARAMETERS (SQL) v nápovědě k rozhraní DAO.

##  <a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Voláním této členské funkce určíte, kolik záznamů bylo ovlivněno posledním voláním metody [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Návratová hodnota

Počet ovlivněných záznamů.

### <a name="remarks"></a>Poznámky

Vrácený počet nebude odrážet změny v souvisejících tabulkách, pokud jsou v platnosti kaskádové aktualizace nebo odstraňování.

Související informace najdete v tématu "vlastnost RecordsAffected" v nápovědě k rozhraní DAO.

##  <a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Voláním této členské funkce určíte, zda je objekt querydef založen na dotazu, který vrací záznamy.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt querydef založen na dotazu, který vrací záznamy; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá jenom pro předávací dotazy SQL. Další informace o dotazech SQL naleznete v tématu členská funkce [Execute](#execute) . Další informace o práci s předávacími dotazy SQL naleznete v tématu členská funkce [SetReturnsRecords](#setreturnsrecords) .

Související informace najdete v tématu "Vlastnost ReturnsRecords" v nápovědě k rozhraní DAO.

##  <a name="getsql"></a>CDaoQueryDef::GetSQL

Zavolejte tuto členskou funkci pro načtení příkazu jazyka SQL definujícího dotaz, na kterém je založen querydef.

```
CString GetSQL();
```

### <a name="return-value"></a>Návratová hodnota

Příkaz jazyka SQL definující dotaz, na kterém je založen querydef.

### <a name="remarks"></a>Poznámky

Pak budete pravděpodobně analyzovat řetězec pro klíčová slova, názvy tabulek a tak dále.

Související informace naleznete v tématech "vlastnost SQL", "porovnání Microsoft Jet Database Engine SQL a ANSI SQL" a "dotazování databáze pomocí SQL v kódu" v nápovědě k rozhraním DAO.

##  <a name="gettype"></a>CDaoQueryDef:: GetType

Voláním této členské funkce určíte typ dotazu querydef.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Typ dotazu definovaného pomocí querydef. Hodnoty naleznete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Typ dotazu je nastaven podle toho, co zadáte v řetězci SQL querydef při vytváření objektu querydef nebo volání existující členské funkce [SetSQL](#setsql) objektu querydef. Typ dotazu vrácený touto funkcí může být jedna z následujících hodnot:

- `dbQSelect` vybrat

- Akce `dbQAction`

- `dbQCrosstab` křížově

- Odstranit `dbQDelete`

- Aktualizace `dbQUpdate`

- `dbQAppend` připojit

- Vytvoření tabulky `dbQMakeTable`

- `dbQDDL` – definice dat

- `dbQSQLPassThrough` průchozí

- `dbQSetOperation` sjednocení

- `dbQSPTBulk` používá se `dbQSQLPassThrough` k určení dotazu, který nevrací záznamy.

> [!NOTE]
>  Chcete-li vytvořit předávací dotaz SQL, nenastavujte `dbSQLPassThrough` konstanty. To je automaticky nastaveno databázovým strojem Microsoft Jet při vytváření objektu querydef a nastavení připojovacího řetězce.

Informace o řetězcích SQL naleznete v tématu [GetSQL](#getsql). Informace o typech dotazů naleznete v tématu [Execute](#execute).

##  <a name="isopen"></a>CDaoQueryDef:: Open

Voláním této členské funkce určíte, zda je objekt `CDaoQueryDef` aktuálně otevřen.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt `CDaoQueryDef` aktuálně otevřený; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Objekt querydef musí být v otevřeném stavu, než ho použijete k volání metody [Execute](#execute) nebo k vytvoření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . Chcete-li vložit querydef do otevřeného stavu, zavolejte buď [Create](#create) (pro nový querydef), nebo [otevřete](#open) (pro existující querydef).

##  <a name="m_pdatabase"></a>CDaoQueryDef:: m_pDatabase

Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) přidružený k objektu querydef.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte v případě, že potřebujete získat přístup k databázi přímo – například pro získání ukazatelů na jiné objekty QueryDef nebo Recordset v kolekcích databází.

##  <a name="m_pdaoquerydef"></a>CDaoQueryDef:: m_pDAOQueryDef

Obsahuje ukazatel na rozhraní OLE pro podkladový objekt DAO querydef.

### <a name="remarks"></a>Poznámky

Tento ukazatel je k dispozici pro úplnost a konzistenci s jinými třídami. Protože však knihovna MFC místo toho plně zapouzdřuje rozhraní DAO QueryDefs, je pravděpodobné, že ji nebudete potřebovat. Pokud je použijete, buďte opatrní – zejména neměňte hodnotu ukazatele, Pokud nevíte, co děláte.

##  <a name="open"></a>CDaoQueryDef:: Open

Voláním této členské funkce otevřete objekt querydef, dříve uložený v kolekci QueryDefs databáze.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězec obsahující název uloženého querydef, který se má otevřít Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Jakmile je objekt querydef otevřený, můžete zavolat jeho členskou funkci [Execute](#execute) nebo použít objekt querydef k vytvoření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

##  <a name="setconnect"></a>CDaoQueryDef::SetConnect

Chcete-li nastavit připojovací řetězec objektu QueryDef, zavolejte tuto členskou funkci.

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Řetězec, který obsahuje připojovací řetězec pro přidružený objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Poznámky

Připojovací řetězec se používá k předávání dalších informací do ODBC a určitých ovladačů ISAM podle potřeby. Nepoužívá se pro Microsoft Jet (. MDB) databáze.

> [!TIP]
>  Upřednostňovaným způsobem, jak pracovat s tabulkami ODBC, je připojit je k. Databáze MDB.

Před spuštěním objektu QueryDef, který představuje předávací dotaz SQL ke zdroji dat ODBC, nastavte připojovací řetězec pomocí `SetConnect` a zavolejte [SetReturnsRecords](#setreturnsrecords) a určete, zda dotaz vrátí záznamy.

Další informace o struktuře připojovacího řetězce a příklady součástí připojovacího řetězce najdete v nápovědě k rozhraní DAO v tématu "připojení vlastnosti".

##  <a name="setname"></a>CDaoQueryDef::SetName

Pokud chcete změnit název querydef, který není dočasný, zavolejte tuto členskou funkci.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězec, který obsahuje nový název nedočasného dotazu v přidruženém objektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Poznámky

Názvy QueryDef jsou jedinečné, uživatelsky definované názvy. Můžete volat `SetName` před tím, než se objekt querydef připojí k kolekci QueryDefs.

##  <a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Zavolejte tuto členskou funkci pro nastavení časového limitu před vypršením dotazu na zdroj dat ODBC.

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parametry

*nODBCTimeout*<br/>
Počet sekund, po jejichž uplynutí vyprší časový limit dotazu.

### <a name="remarks"></a>Poznámky

Tato členská funkce vám umožní přepsat výchozí počet sekund před následnými operacemi na připojeném zdroji dat "časový limit". Kvůli problémům s přístupem k síti, nadměrnému zpracování dotazů a tak dále může dojít k vypršení časového limitu operace. Pokud chcete změnit hodnotu časového limitu dotazu, zavolejte `SetODBCTimeout` před provedením dotazu s tímto objektem querydef. (Protože rozhraní ODBC znovu používá připojení, je hodnota časového limitu stejná pro všechny klienty ve stejném připojení.)

Výchozí hodnota pro vypršení časového limitu dotazu je 60 sekund.

##  <a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

Zavolejte tuto členskou funkci pro nastavení hodnoty parametru v poli querydef za běhu.

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
Název parametru, jehož hodnota má být nastavena.

*varValue*<br/>
Hodnota, která se má nastavit; viz poznámky.

*nIndex*<br/>
Pořadové místo parametru v kolekci parametrů querydef. Tuto hodnotu můžete získat pomocí volání [GetParameterCount](#getparametercount) a [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Poznámky

Parametr již měl být vytvořen jako součást řetězce kódu querydef. K parametru můžete přistupovat buď podle názvu, nebo podle jeho ordinální pozice v kolekci.

Zadejte hodnotu, která se má nastavit jako objekt `COleVariant`. Informace o nastavení požadované hodnoty a typu v objektu `COleVariant` naleznete v tématu Třída [COleVariant](../../mfc/reference/colevariant-class.md).

##  <a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Tuto členskou funkci volejte jako součást procesu nastavení předávacího dotazu SQL do externí databáze.

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parametry

*bReturnsRecords*<br/>
Předat hodnotu TRUE, pokud dotaz na externí databázi vrátí záznamy; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

V takovém případě je nutné vytvořit objekt querydef a nastavit jeho vlastnosti pomocí jiných `CDaoQueryDef` členských funkcí. Popis externích databází najdete v tématu [SetConnect](#setconnect).

##  <a name="setsql"></a>CDaoQueryDef::SetSQL

Voláním této členské funkce nastavte příkaz SQL, který se v souboru querydef spustí.

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Ipszsql*<br/>
Řetězec obsahující úplný příkaz SQL, který je vhodný pro provedení. Syntaxe tohoto řetězce závisí na systému DBMS, na který se dotaz zaměřuje. Diskuzi o syntaxi použitou v databázovém stroji Microsoft Jet naleznete v tématu "vytváření příkazů SQL v kódu" v nápovědě pro rozhraní DAO.

### <a name="remarks"></a>Poznámky

Typickým použitím `SetSQL` je nastavení objektu querydef pro použití v předávacím dotazu SQL. (Informace o syntaxi předávacích dotazů SQL na cílovém systému DBMS najdete v dokumentaci k vašemu systému DBMS.)

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
