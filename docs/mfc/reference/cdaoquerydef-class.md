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
ms.openlocfilehash: ed298c40daa9485683d0b989e47b97fdce9f6562
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754708"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef – třída

Představuje definici dotazu nebo "querydef", obvykle jeden uložený v databázi.

## <a name="syntax"></a>Syntaxe

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Vytvoří `CDaoQueryDef` objekt. Další `Open` hovor `Create`nebo , v závislosti na vašich potřebách.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::Připojit](#append)|Připojí querydef do databáze QueryDefs kolekce jako uložený dotaz.|
|[CDaoQueryDef::CanUpdate](#canupdate)|Vrátí nenulovou, pokud dotaz může databázi aktualizovat.|
|[CDaoQueryDef::Zavřít](#close)|Zavře querydef objekt. Po dokončení objektu C++ zničte objekt jazyka C++.|
|[CDaoQueryDef::Vytvořit](#create)|Vytvoří základní objekt DAO querydef. Použijte querydef jako dočasný dotaz `Append` nebo volání uložit do databáze.|
|[CDaoQueryDef::Spustit](#execute)|Spustí dotaz definovaný objektem querydef.|
|[CDaoQueryDef::GetConnect](#getconnect)|Vrátí připojovací řetězec přidružený k querydef. Připojovací řetězec identifikuje zdroj dat. (Pouze pro předávací dotazy SQL, jinak prázdný řetězec.)|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Vrátí datum vytvoření uloženého dotazu.|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum poslední aktualizace uloženého dotazu.|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Vrátí počet polí definovaných querydef.|
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Vrátí informace o zadaném poli definovaném v dotazu.|
|[CDaoQueryDef::GetName](#getname)|Vrátí název querydef.|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Vrátí hodnotu časového limitu použitou rozhraním ODBC (pro dotaz ODBC) při spuštění querydef. To určuje, jak dlouho povolit akci dotazu k dokončení.|
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Vrátí počet parametrů definovaných pro dotaz.|
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Vrátí dotazu informace o zadaném parametru.|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Vrátí hodnotu zadaného parametru do dotazu.|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů ovlivněných akčním dotazem.|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Vrátí nenulovou, pokud dotaz definovaný querydef vrátí záznamy.|
|[CDaoQueryDef::GetSQL](#getsql)|Vrátí řetězec SQL, který určuje dotaz definovaný querydef.|
|[CDaoQueryDef::GetType](#gettype)|Vrátí typ dotazu: odstranit, aktualizovat, připojit, vytvořit tabulku a tak dále.|
|[CDaoQueryDef::Jeotevřeno](#isopen)|Vrátí nenulovou, pokud je querydef otevřená a může být spuštěna.|
|[CDaoQueryDef::Otevřít](#open)|Otevře existující querydef uložené v databázi QueryDefs kolekce.|
|[CDaoQueryDef::SetConnect](#setconnect)|Nastaví připojovací řetězec pro předávací dotaz SQL ve zdroji dat ODBC.|
|[CDaoQueryDef::SetName](#setname)|Nastaví název uloženého dotazu a nahradí název, který se použije při vytvoření querydef.|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Nastaví hodnotu časového limitu použitou rozhraním ODBC (pro dotaz ODBC) při spuštění querydef.|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Nastaví hodnotu zadaného parametru na dotaz.|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Určuje, zda querydef vrátí záznamy. Nastavení tohoto atributu na hodnotu TRUE je platné pouze pro předávací dotazy SQL.|
|[CDaoQueryDef::SetSQL](#setsql)|Nastaví řetězec SQL, který určuje dotaz definovaný querydef.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Ukazatel na rozhraní OLE pro základní objekt DAO querydef.|
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Ukazatel na `CDaoDatabase` objekt, ke kterému je přidružen querydef. Querydef může být uložen v databázi nebo ne.|

## <a name="remarks"></a>Poznámky

Querydef je objekt pro přístup k datům, který obsahuje příkaz SQL, který popisuje dotaz a jeho vlastnosti, například "Datum vytvoření" a "Časový limit ODBC". Můžete také vytvořit dočasné querydef objekty bez jejich uložení, ale je vhodné – a mnohem efektivnější – uložit běžně opakované dotazy v databázi. Objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) udržuje kolekci nazvanou QueryDefs, která obsahuje uložené querydefs.

> [!NOTE]
> Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Stále můžete přistupovat ke zdrojům dat ODBC pomocí tříd DAO. Obecně platí, že třídy Knihovny MFC založené na DAO jsou schopnější než třídy Knihovny MFC založené na rozhraní ODBC; třídy založené na DAO mohou přistupovat k datům, a to i prostřednictvím ovladačů ODBC, prostřednictvím vlastního databázového stroje. Třídy založené na DAO také podporují operace jazyka definice dat (DDL), jako je například přidávání tabulek prostřednictvím tříd, aniž by bylo třeba volat DAO přímo.

## <a name="usage"></a>Využití

Pomocí objektů querydef můžete pracovat s existujícím uloženým dotazem nebo vytvořit nový uložený dotaz nebo dočasný dotaz:

1. Ve všech případech nejprve vytvořte `CDaoQueryDef` objekt, který poskytuje ukazatel na objekt [CDaoDatabase,](../../mfc/reference/cdaodatabase-class.md) do kterého dotaz patří.

1. Pak udělejte následující, v závislosti na tom, co chcete:

   - Chcete-li použít existující uložený dotaz, zavolejte člennou funkci [Open](#open) objektu querydef a zadejte název uloženého dotazu.

   - Chcete-li vytvořit nový uložený dotaz, zavolejte členovou funkci [Create](#create) objektu querydef a zadejte název dotazu. Potom volání [Append](#append) uložit dotaz připojením do databáze QueryDefs kolekce. `Create`vloží querydef do otevřeného stavu, `Create` takže po `Open`volání nevoláte .

   - Chcete-li vytvořit dočasné `Create`querydef, volání . Předaj prázdný řetězec pro název dotazu. Nevolejte `Append`.

Po dokončení pomocí querydef objektu, volání jeho [Zavřít](#close) členská funkce; pak zničit querydef objektu.

> [!TIP]
> Nejjednodušší způsob, jak vytvořit uložené dotazy, je vytvořit je a uložit je do databáze pomocí aplikace Microsoft Access. Pak je můžete otevřít a použít v kódu knihovny MFC.

## <a name="purposes"></a>Účely

Objekt querydef můžete použít pro některý z následujících účelů:

- Vytvoření objektu `CDaoRecordset`

- Volání `Execute` členské funkce objektu k přímému spuštění akčního dotazu nebo předávacího dotazu SQL

Můžete použít querydef objekt pro jakýkoli typ dotazu, včetně výběru, akce, křížové tabulky, odstranit, aktualizovat, připojit, make-table, definice dat, SQL předávací, sjednocení a hromadné dotazy. Typ dotazu je určen obsahem příkazu SQL, který zadáte. Informace o typech dotazů naleznete v `Execute` členských funkcích a [GetType.](#gettype) Sady záznamů se běžně používají pro dotazy vracející řádky, obvykle ty, které používají **SELECT ... FROM** klíčová slova. `Execute`se nejčastěji používá pro hromadné operace. Další informace naleznete v [tématech Execute](#execute) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

## <a name="querydefs-and-recordsets"></a>Querydefs a sady záznamů

Chcete-li použít querydef `CDaoRecordset` objekt k vytvoření objektu, obvykle vytvořit nebo otevřít querydef, jak je popsáno výše. Potom vytvořte objekt sady záznamů a při volání [sady CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#open)předáte ukazatel objektu querydef::Open . Querydef, které předáte, musí být v otevřeném stavu. Další informace naleznete v tématu třída [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Nelze použít querydef k vytvoření sady záznamů (nejběžnější použití pro querydef), pokud je v otevřeném stavu. Uveďte querydef do otevřeného `Open` stavu `Create`voláním buď nebo .

## <a name="external-databases"></a>Externí databáze

Querydef objekty jsou upřednostňovaný způsob, jak používat nativní dialekt SQL externí databázový stroj. Můžete například vytvořit dotaz Transact SQL (jak se používá na serveru Microsoft SQL Server) a uložit jej do objektu querydef. Pokud potřebujete použít dotaz SQL, který není založen na databázovém stroji Microsoft Jet, musíte zadat připojovací řetězec, který odkazuje na externí zdroj dat. Dotazy s platnými připojovacími řetězci obejdou databázový stroj a předají dotaz přímo externímu databázovému serveru ke zpracování.

> [!TIP]
> Upřednostňovaným způsobem práce s tabulkami ODBC je jejich připojení k systému Microsoft Jet (. MDB).

Související informace naleznete v tématech "QueryDef Object", "QueryDefs Collection" a "CdbDatabase Object" v sadě DAO SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef::Připojit

Volání této členské funkce po volání [Create](#create) vytvořit nový querydef objektu.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

`Append`uloží querydef v databázi připojením objektu do kolekce QueryDefs databáze. Můžete použít querydef jako dočasný objekt bez připojení, ale pokud chcete, aby `Append`přetrvávat, musíte volat .

Pokud se pokusíte připojit dočasný querydef objektu, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef::CanUpdate

Volání této členské funkce k určení, zda můžete upravit querydef – například změna jeho název nebo řetězec SQL.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je povoleno upravit querydef; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete upravit querydef pokud:

- Není založena na databázi, která je otevřena jen pro čtení.

- Máte oprávnění k aktualizaci databáze.

   To závisí na tom, zda jste implementovali funkce zabezpečení. Knihovna MFC neposkytuje podporu pro zabezpečení. musíte implementovat sami voláním DAO přímo nebo pomocí aplikace Microsoft Access. Podívejte se na téma "Vlastnost oprávnění" v nápovědě DAO.

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

Vytvoří `CDaoQueryDef` objekt.

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabáze*<br/>
Ukazatel na otevřený objekt [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Poznámky

Objekt může představovat existující querydef uložené v databázi QueryDefs kolekce, nový dotaz, který má být uložen v kolekci nebo dočasný dotaz, které nemají být uloženy. Další krok závisí na typu querydef:

- Pokud objekt představuje existující querydef, volání objektu [Open](#open) členská funkce inicializovat.

- Pokud objekt představuje nový querydef, který má být uložen, volání objektu [Vytvořit](#create) člennou funkci. Tím přidáte objekt do kolekce QueryDefs databáze. Potom `CDaoQueryDef` volání členských funkcí nastavit atributy objektu. Nakonec volejte [Append](#append).

- Pokud objekt představuje dočasné querydef (nesmí být uloženy `Create`v databázi), volání , předání prázdný řetězec pro název dotazu. Po `Create`volání , inicializovat querydef přímým nastavením jeho atributy. Nevolejte `Append`.

Chcete-li nastavit atributy querydef, můžete použít [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)a [SetReturnsRecords](#setreturnsrecords) členské funkce.

Po dokončení s querydef objektu, volání jeho [Zavřít](#close) členská funkce. Pokud máte ukazatel na querydef, použijte **operátor delete** zničit objekt C++.

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef::Zavřít

Volání této členské funkce po dokončení pomocí querydef objektu.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Zavření querydef uvolní základní DAO objekt, ale nezničí uložený objekt DAO querydef nebo c++ `CDaoQueryDef` objekt. To není stejné jako [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), který odstraní querydef z databáze QueryDefs kolekce v DAO (pokud ne dočasné querydef).

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef::Vytvořit

Volánítéto členské funkce k vytvoření nového uloženého dotazu nebo nového dočasného dotazu.

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Jedinečný název dotazu uloženého v databázi. Podrobnosti o řetězci naleznete v tématu "Metoda CreateQueryDef" v nápovědě dao. Pokud přijmete výchozí hodnotu, prázdný řetězec, vytvoří se dočasný querydef. Takový dotaz není uložen v kolekci QueryDefs.

*Lpszsql*<br/>
Řetězec SQL, který definuje dotaz. Pokud přijmete výchozí hodnotu NULL, musíte později zavolat [SetSQL](#setsql) nastavit řetězec. Do té doby dotaz není definován. Nedefinovaný dotaz však můžete použít k otevření sady záznamů. podrobnosti naleznete v části Poznámky. Příkaz SQL musí být definován před připojením querydef do kolekce QueryDefs.

### <a name="remarks"></a>Poznámky

Pokud předáte název v *lpszName*, pak můžete volat [Append](#append) uložit querydef v databázi QueryDefs kolekce. V opačném případě je objekt dočasné querydef a není uložen. V obou případech querydef je v otevřeném stavu a můžete jej buď použít k vytvoření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) nebo volání querydef [je Execute](#execute) členské funkce.

Pokud nezadáte příkaz SQL v *lpszSQL*, nelze `Execute` spustit dotaz s, ale můžete jej použít k vytvoření sady záznamů. V takovém případě knihovna MFC používá výchozí příkaz SQL sady záznamů.

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef::Spustit

Volání této členské funkce ke spuštění dotazu definovaného querydef objektu.

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*nMožnosti*<br/>
Celé číslo, které určuje charakteristiky dotazu. Související informace naleznete v tématu "Metoda spuštění" v nápovědě dao. Pomocí operátoru Bitwise-OR ( **&#124;**) můžete kombinovat následující konstanty pro tento argument:

- `dbDenyWrite`Odepřít oprávnění k zápisu ostatním uživatelům.

- `dbInconsistent`Nekonzistentní aktualizace.

- `dbConsistent`Konzistentní aktualizace.

- `dbSQLPassThrough`Průchod SQL. Způsobí, že příkaz SQL, který má být předán do databáze ODBC pro zpracování.

- `dbFailOnError`Výchozí hodnota. Vrátit zpět aktualizace, pokud dojde k chybě a hlásit chybu uživateli.

- `dbSeeChanges`Vygenerujte chybu za běhu, pokud jiný uživatel mění data, která upravujete.

> [!NOTE]
> Vysvětlení pojmů "nekonzistentní" a "konzistentní", naleznete v tématu "Metoda spuštění" v nápovědě DAO.

### <a name="remarks"></a>Poznámky

Querydef objekty používané pro spuštění tímto způsobem může představovat pouze jeden z následujících typů dotazů:

- Akční dotazy

- Předávací dotazy SQL

`Execute`nefunguje pro dotazy, které vracejí záznamy, jako jsou například výběrové dotazy. `Execute`Se běžně používá pro hromadné operace dotazy, jako je **například UPDATE**, **INSERT**, nebo **SELECT INTO**, nebo pro operace definice dat (DDL).

> [!TIP]
> Upřednostňovaným způsobem práce se zdroji dat ODBC je připojení tabulek k systému Microsoft Jet (. MDB). Další informace naleznete v tématu "Přístup k externím databázím s DAO" v nápovědě DAO.

Volání [GetRecordsAffected](#getrecordsaffected) členské funkce querydef objektu k určení počtu záznamů `Execute` ovlivněných poslední volání. Vrátí například `GetRecordsAffected` informace o počtu záznamů odstraněných, aktualizovaných nebo vložených při provádění akčního dotazu. Vrácený počet nebude odrážet změny v souvisejících tabulkách při kaskádové aktualizace nebo odstranění jsou v platnosti.

Pokud zahrnete obojí `dbInconsistent` a `dbConsistent` nebo nezahrnete `dbInconsistent`ani jedno, bude výsledkem výchozí hodnota .

`Execute`nevrátí sadu záznamů. Použití `Execute` na dotaz, který vybere záznamy způsobí, že knihovna MFC vyvolat výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef::GetConnect

Volání této členské funkce získat připojovací řetězec spojené se zdrojem dat querydef.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující připojovací řetězec pro querydef.

### <a name="remarks"></a>Poznámky

Tato funkce se používá pouze se zdroji dat ODBC a určitými ovladači ISAM. Nepoužívá se s Microsoft Jet (. MDB) databáze; v tomto `GetConnect` případě vrátí prázdný řetězec. Další informace naleznete v tématu [SetConnect](#setconnect).

> [!TIP]
> Upřednostňovaným způsobem práce s tabulkami ODBC je jejich připojení k tabulce . Databáze MDB. Další informace naleznete v tématu "Přístup k externím databázím s DAO" v nápovědě DAO.

Informace o připojovacích řetězcích naleznete v tématu "Connect Property" v nápovědě dao.

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

Volání této členské funkce získat datum querydef objekt byl vytvořen.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas querydef byl vytvořen.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu DateCreated, LastUpdated Properties v nápovědě dao.

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

Volání této členské funkce získat datum querydef objekt byl naposledy aktualizován – při některé z jeho vlastností byly změněny, například jeho název, jeho řetězec SQL nebo jeho připojovací řetězec.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas querydef byl naposledy aktualizován.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu DateCreated, LastUpdated Properties v nápovědě dao.

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

Volání této členské funkce načíst počet polí v dotazu.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí definovaných v dotazu.

### <a name="remarks"></a>Poznámky

`GetFieldCount`je užitečné pro opakování všech polí v querydef. Pro tento účel `GetFieldCount` použijte ve spojení s [GetFieldInfo](#getfieldinfo).

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo

Volání této členské funkce získat různé druhy informací o pole definované v querydef.

```cpp
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
Nula na základě indexu požadované pole v querydef pole kolekce, pro vyhledávání podle indexu.

*Fieldinfo*<br/>
Odkaz na `CDaoFieldInfo` objekt, který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o poli mají být načteny. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit:

- AFX_DAO_PRIMARY_INFO (Výchozí) Název, Typ, Velikost, Atributy

- AFX_DAO_SECONDARY_INFO primární informace plus: Ordinální pozice, Povinné, Povolit nulovou délku, Zdrojové pole, Cizí jméno, Zdrojová tabulka, Pořadí řazení

- AFX_DAO_ALL_INFO primární a sekundární informace plus: Výchozí hodnota, ověřovací text, ověřovací pravidlo

*název lpsz*<br/>
Řetězec obsahující název požadovaného pole pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Popis informací vrácených v *fieldinfo*naleznete v tématu [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) struktura. Tato struktura má členy, které odpovídají popisné informace pod *dwInfoOptions* výše. Pokud požadujete jednu úroveň informací, získáte také všechny předchozí úrovně informací.

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef::GetName

Volání této členské funkce načíst název dotazu reprezentované querydef.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Název dotazu.

### <a name="remarks"></a>Poznámky

Querydef názvy jsou jedinečné uživatelem definované názvy. Další informace o názvech querydef naleznete v tématu "Name Property" v nápovědě dao.

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

Volání této členské funkce načíst aktuální časový limit před dotazem na zdroj dat ODBC časový limit.

```
short GetODBCTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Počet sekund před vypršením dotazu.

### <a name="remarks"></a>Poznámky

Informace o tomto časovém limitu naleznete v tématu "VLASTNOST ODBCTimeout" v nápovědě dao.

> [!TIP]
> Upřednostňovaným způsobem práce s tabulkami ODBC je jejich připojení k systému Microsoft Jet (. MDB). Další informace naleznete v tématu "Přístup k externím databázím s DAO" v nápovědě DAO.

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDaoQueryDef::GetParameterCount

Volání této členské funkce načíst počet parametrů v uloženém dotazu.

```
short GetParameterCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet parametrů definovaných v dotazu.

### <a name="remarks"></a>Poznámky

`GetParameterCount`je užitečné pro opakování přes všechny parametry v querydef. Pro tento účel `GetParameterCount` použijte ve spojení s [GetParameterInfo](#getparameterinfo).

Související informace naleznete v tématech "Objekt parametrů", "Kolekce parametrů" a "Deklarace parametrů (SQL)" v nápovědě DAO.

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo

Volání této členské funkce získat informace o parametr definovaný v querydef.

```cpp
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
Nula na základě indexu požadovaný parametr v querydef parametry kolekce, pro vyhledávání podle indexu.

*paraminfo*<br/>
Odkaz na objekt [CDaoParameterInfo,](../../mfc/reference/cdaoparameterinfo-structure.md) který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o parametru načíst. Zde je uvedena dostupná možnost spolu s tím, co způsobí, že se funkce vrátí:

- AFX_DAO_PRIMARY_INFO (Výchozí) Název, zadejte

*název lpsz*<br/>
Řetězec obsahující název požadovaného parametru pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Popis informací vrácených v *paraminfo*naleznete [cDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) struktury. Tato struktura má členy, které odpovídají popisné informace pod *dwInfoOptions* výše.

Související informace naleznete v tématu "DEKLARACE PARAMETRŮ (SQL)" v nápovědě DAO.

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

Volání této členské funkce načíst aktuální hodnotu zadaný parametr uložený v querydef parametry kolekce.

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název parametru, jehož hodnotu chcete, pro vyhledávání podle názvu.

*nIndex*<br/>
Nula index parametru v querydef parametry kolekce, pro vyhledávání podle indexu. Tuto hodnotu můžete získat pomocí volání [GetParameterCount](#getparametercount) a [GetParameterInfo](#getparameterinfo).

### <a name="return-value"></a>Návratová hodnota

Objekt třídy [COleVariant,](../../mfc/reference/colevariant-class.md) který obsahuje hodnotu parametru.

### <a name="remarks"></a>Poznámky

K parametru můžete přistupovat buď podle názvu, nebo podle jeho pořadí v kolekci.

Související informace naleznete v tématu "DEKLARACE PARAMETRŮ (SQL)" v nápovědě DAO.

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

Volání této členské funkce k určení, kolik záznamů byly ovlivněny poslední volání [Execute](#execute).

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Návratová hodnota

Počet ovlivněných záznamů.

### <a name="remarks"></a>Poznámky

Vrácený počet nebude odrážet změny v souvisejících tabulkách při kaskádové aktualizace nebo odstranění jsou v platnosti.

Související informace naleznete v tématu "RecordsAffected Property" v nápovědě DAO.

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

Volání této členské funkce k určení, zda querydef je založena na dotaz, který vrací záznamy.

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je querydef založen na dotazu, který vrací záznamy; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce se používá pouze pro předávací dotazy SQL. Další informace o dotazech SQL naleznete v členské funkci [Spustit.](#execute) Další informace o práci s předávacími dotazy SQL naleznete v členské funkci [SetReturnsRecords.](#setreturnsrecords)

Související informace naleznete v tématu "ReturnsRecords Property" v nápovědě dao.

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef::GetSQL

Volání této členské funkce načíst příkaz SQL, který definuje dotaz, na kterém querydef je založena.

```
CString GetSQL();
```

### <a name="return-value"></a>Návratová hodnota

Příkaz SQL, který definuje dotaz, na kterém je založena querydef.

### <a name="remarks"></a>Poznámky

Potom budete pravděpodobně analyzovat řetězec pro klíčová slova, názvy tabulek a tak dále.

Související informace naleznete v tématech "Vlastnosti SQL", "Porovnání Microsoft Jet Database Engine SQL a ANSI SQL" a "Dotazování databáze s SQL v kódu" v Nápovědě DAO.

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef::GetType

Volání této členské funkce k určení typu dotazu querydef.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Typ dotazu definované querydef. Hodnoty naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Typ dotazu je nastaven podle toho, co zadáte v řetězci SQL querydef při vytváření querydef nebo volání existující querydef [je SetSQL](#setsql) členská funkce. Typ dotazu vrácený touto funkcí může být jednou z následujících hodnot:

- `dbQSelect`Vyberte

- `dbQAction`Akce

- `dbQCrosstab`Křížového

- `dbQDelete`Odstranit

- `dbQUpdate`Aktualizace

- `dbQAppend`Připojit

- `dbQMakeTable`Make-table

- `dbQDDL`Definice dat

- `dbQSQLPassThrough`Předávací

- `dbQSetOperation`Unie

- `dbQSPTBulk`Používá `dbQSQLPassThrough` se k určení dotazu, který nevrací záznamy.

> [!NOTE]
> Chcete-li vytvořit předávací dotaz `dbSQLPassThrough` SQL, nenastavovat konstantu. To je nastavena automaticky databázový stroj Microsoft Jet při vytváření querydef objektu a nastavení připojovacího řetězce.

Informace o strunách SQL naleznete v tématu [GetSQL](#getsql). Informace o typech dotazů naleznete v [tématu Execute](#execute).

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef::Jeotevřeno

Volání této členské funkce `CDaoQueryDef` k určení, zda je objekt aktuálně otevřen.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CDaoQueryDef` pokud je objekt aktuálně otevřen; jinak 0.

### <a name="remarks"></a>Poznámky

Querydef musí být v otevřeném stavu před použitím k volání [Execute](#execute) nebo k vytvoření objektu [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Chcete-li umístit querydef do otevřeného stavu volání buď [Create](#create) (pro nový querydef) nebo [Open](#open) (pro existující querydef).

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase

Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) přidružený k objektu querydef.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte, pokud potřebujete získat přímý přístup k databázi , například k získání ukazatelů na jiné querydef nebo recordset objekty v kolekcích databáze.

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef

Obsahuje ukazatel na rozhraní OLE pro základní objekt DAO querydef.

### <a name="remarks"></a>Poznámky

Tento ukazatel je k dispozici pro úplnost a konzistenci s ostatními třídami. Však protože knihovna MFC poměrně plně zapouzdřuje DAO querydefs, je nepravděpodobné, že ji budete potřebovat. Pokud jej používáte, uvažte to opatrně – zejména neměňte hodnotu ukazatele, pokud nevíte, co děláte.

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef::Otevřít

Volání této členské funkce otevřete querydef dříve uložené v databázi QueryDefs kolekce.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Řetězec, který obsahuje název uložené querydef otevřít. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Jakmile querydef je otevřena, můžete volat jeho [execute](#execute) členské funkce nebo pomocí querydef vytvořit objekt [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef::SetConnect

Volání této členské funkce nastavit připojovací řetězec objektu querydef.

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszPřipojit*<br/>
Řetězec, který obsahuje připojovací řetězec pro přidružený objekt [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Poznámky

Připojovací řetězec se používá k předání dalších informací rozhraní ODBC a určitým ovladačům ISAM podle potřeby. Nepoužívá se pro Microsoft Jet (. MDB).

> [!TIP]
> Upřednostňovaným způsobem práce s tabulkami ODBC je jejich připojení k tabulce . Databáze MDB.

Před spuštěním querydef, který představuje předávací dotaz SQL do zdroje `SetConnect` dat ODBC, nastavte připojovací řetězec s a volání [SetReturnsRecords](#setreturnsrecords) určit, zda dotaz vrátí záznamy.

Další informace o struktuře připojovacího řetězce a příkladech součástí připojovacího řetězce naleznete v tématu "Connect Property" v nápovědě dao.

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef::SetName

Volání této členské funkce, pokud chcete změnit název querydef, který není dočasný.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Řetězec, který obsahuje nový název pro nedočasný dotaz v přidruženém [objektu CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Poznámky

Querydef názvy jsou jedinečné, uživatelem definované názvy. Můžete volat `SetName` před querydef objekt je připojen k kolekci QueryDefs.

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

Voláním této členské funkce nastavte časový limit před dotazem na časový limit zdroje dat ROZHRANÍ ODBC.

```cpp
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>Parametry

*nODBCTimeout*<br/>
Počet sekund před vypršením dotazu.

### <a name="remarks"></a>Poznámky

Tato členská funkce umožňuje přepsat výchozí počet sekund před následnými operacemi na připojeném zdroji dat "out out". Operace může časový limit z důvodu problémů s přístupem k síti, nadměrné doby zpracování dotazů a tak dále. Volání `SetODBCTimeout` před spuštěním dotazu s tímto querydef, pokud chcete změnit hodnotu časového limitu dotazu. (Jako ROZHRANÍ ODBC opakovaně používá připojení, hodnota časového limitu je stejná pro všechny klienty ve stejném připojení.)

Výchozí hodnota pro časové limity dotazu je 60 sekund.

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

Volání této členské funkce nastavit hodnotu parametru v querydef v době běhu.

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název parametru, jehož hodnotu chcete nastavit.

*varValue*<br/>
Hodnota, která má být nastavena; viz Poznámky.

*nIndex*<br/>
Pořadí pozice parametru v querydef parametry kolekce. Tuto hodnotu můžete získat pomocí volání [GetParameterCount](#getparametercount) a [GetParameterInfo](#getparameterinfo).

### <a name="remarks"></a>Poznámky

Parametr musí již byly stanoveny jako součást querydef je sql řetězec. K parametru můžete přistupovat buď podle názvu, nebo podle jeho pořadí v kolekci.

Zadejte hodnotu, `COleVariant` kterou chcete nastavit jako objekt. Informace o nastavení požadované hodnoty a `COleVariant` zadejte do objektu naleznete v tématu [colevariant](../../mfc/reference/colevariant-class.md)třídy .

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

Volání této členské funkce jako součást procesu nastavení předávacího dotazu SQL do externí databáze.

```cpp
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>Parametry

*bReturnsRecords*<br/>
Předat hodnotu TRUE, pokud dotaz v externí databázi vrátí záznamy; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

V takovém případě je nutné vytvořit querydef a `CDaoQueryDef` nastavit jeho vlastnosti pomocí jiných členských funkcí. Popis externích databází naleznete v tématu [SetConnect](#setconnect).

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDaoQueryDef::SetSQL

Volání této členské funkce nastavit příkaz SQL, který querydef provede.

```cpp
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>Parametry

*Lpszsql*<br/>
Řetězec obsahující úplný příkaz SQL, vhodný pro spuštění. Syntaxe tohoto řetězce závisí na DBMS, na které váš dotaz cílí. Diskuse o syntaxi použité v databázovém stroji Microsoft Jet naleznete v tématu Vytváření příkazů SQL v kódu v nápovědě dao.

### <a name="remarks"></a>Poznámky

Typické použití `SetSQL` je nastavení querydef objekt pro použití v dotazu SQL předávací dotaz. (Syntaxe předávacích dotazů SQL v cílovém systému DBMS naleznete v dokumentaci k systému DBMS.)

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
