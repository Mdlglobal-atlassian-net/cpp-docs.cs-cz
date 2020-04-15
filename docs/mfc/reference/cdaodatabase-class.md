---
title: CDaoDatabase – třída
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
ms.openlocfilehash: debba137878da49921df83da7630003a7d62db2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369022"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase – třída

Představuje připojení k databázi aplikace Access pomocí objektů přístupu k datům (DAO). DAO je podporováno prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé.

## <a name="syntax"></a>Syntaxe

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Databáze CDao::Databáze CDao](#cdaodatabase)|Vytvoří `CDaoDatabase` objekt. Volání `Open` pro připojení objektu k databázi.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Databáze CDao::CanTransact](#cantransact)|Vrátí nenulovou, pokud databáze podporuje transakce.|
|[Databáze CDao::CanUpdate](#canupdate)|Vrátí nenulovou, pokud je `CDaoDatabase` objekt aktualizovatelný (není jen pro čtení).|
|[CDaoDatabáze::Zavřít](#close)|Zavře připojení k databázi.|
|[CDaoDatabáze::Vytvořit](#create)|Vytvoří základní databázový objekt DAO a `CDaoDatabase` inicializuje objekt.|
|[CDaoDatabase::Vytvořitvztah](#createrelation)|Definuje nový vztah mezi tabulkami v databázi.|
|[CDaoDatabáze::DeleteQueryDef](#deletequerydef)|Odstraní objekt querydef uložený v kolekci QueryDefs databáze.|
|[CDaoDatabáze::DeleteRelation](#deleterelation)|Odstraní existující vztah mezi tabulkami v databázi.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Odstraní definici tabulky v databázi. Tím odstraníte skutečnou tabulku a všechna její data.|
|[Databáze CDao::Spustit](#execute)|Spustí akční dotaz. Volání `Execute` dotazu, který vrací výsledky, vyvolá výjimku.|
|[Databáze CDao::GetConnect](#getconnect)|Vrátí připojovací řetězec `CDaoDatabase` použitý k připojení objektu k databázi. Používá se pro rozhraní ODBC.|
|[CDaoDatabáze::GetName](#getname)|Vrátí název aktuálně použitelné databáze.|
|[Databáze CDao::GetQueryDefCount](#getquerydefcount)|Vrátí počet dotazů definovaných pro databázi.|
|[CDaoDatabáze::GetQueryDefInfo](#getquerydefinfo)|Vrátí informace o zadaném dotazu definovaném v databázi.|
|[CDaoDatabáze::GetQueryTimeout](#getquerytimeout)|Vrátí počet sekund, po které budou časové limity operací dotazu databáze. Ovlivňuje všechny následné operace otevření, aktualizace a úpravy a další operace ve `Execute` zdrojích dat ODBC (pouze), například volání.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů ovlivněných poslední aktualizací, úpravou nebo přidáním `Execute`operace nebo voláním programu .|
|[CDaoDatabáze::GetRelationCount](#getrelationcount)|Vrátí počet vztahů definovaných mezi tabulkami v databázi.|
|[CDaoDatabáze::GetRelationInfo](#getrelationinfo)|Vrátí informace o zadaném vztahu definovaném mezi tabulkami v databázi.|
|[Databáze CDao::GetTableDefCount](#gettabledefcount)|Vrátí počet tabulek definovaných v databázi.|
|[CDaoDatabáze::GetTableDefInfo](#gettabledefinfo)|Vrátí informace o zadané tabulce v databázi.|
|[Databáze CDao::GetVersion](#getversion)|Vrátí verzi databázového stroje přidruženého k databázi.|
|[Databáze CDao::Jeotevřeno](#isopen)|Vrátí nenulovou, pokud je `CDaoDatabase` objekt aktuálně připojen k databázi.|
|[Databáze CDao::Otevřít](#open)|Naváže připojení k databázi.|
|[CDaoDatabáze::SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po kterých budou časové dotazy databáze (pouze ve zdrojích dat ROZHRANÍ ODBC) vypočte. Ovlivňuje všechny následné operace otevření, přidání nových, aktualizací a odstranění.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CDaoDatabáze::m_pDAODatabase](#m_pdaodatabase)|Ukazatel na základní databázový objekt DAO.|
|[CDaoDatabáze::m_pWorkspace](#m_pworkspace)|Ukazatel na objekt [CDaoWorkspace,](../../mfc/reference/cdaoworkspace-class.md) který obsahuje databázi a definuje její transakční prostor.|

## <a name="remarks"></a>Poznámky

Informace o podporovaných formátech databáze naleznete v členské funkci [GetName.](../../mfc/reference/cdaoworkspace-class.md#getname) Můžete mít jeden `CDaoDatabase` nebo více objektů aktivních současně v daném "pracovním prostoru", reprezentovaném objektem [CDaoWorkspace.](../../mfc/reference/cdaoworkspace-class.md) Pracovní prostor udržuje kolekci otevřených databázových objektů, které se nazývají kolekce Databases.

## <a name="usage"></a>Využití

Databázové objekty můžete vytvořit implicitně, když vytváříte objekty sady záznamů. Ale můžete také explicitně vytvořit databázové objekty. Chcete-li použít existující `CDaoDatabase`databázi explicitně s , proveďte některou z následujících akcí:

- Vytvořte `CDaoDatabase` objekt a předejte ukazatel otevřenému objektu [CDaoWorkspace.](../../mfc/reference/cdaoworkspace-class.md)

- Nebo vytvořte `CDaoDatabase` objekt bez zadání pracovního prostoru (knihovna MFC vytvoří dočasný objekt pracovního prostoru).

Chcete-li vytvořit nový Microsoft Jet (. MDB) databáze, `CDaoDatabase` konstrukce objektu a volání jeho [Vytvořit](#create) členovou funkci. *Nevolejte* `Open` po `Create`.

Chcete-li otevřít existující `CDaoDatabase` databázi, vytvořte objekt a zavolejte jeho člennou funkci [Open.](#open)

Všechny tyto techniky připojí databázový objekt DAO do kolekce databáze pracovního prostoru a otevře připojení k datům. Když potom vytvoříte objekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)nebo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) pro provoz v připojené databázi, předejte konstruktorům těchto objektů ukazatel `CDaoDatabase` objektu. Po dokončení pomocí připojení volejte [zavřít](#close) členská `CDaoDatabase` funkce a zničit objekt. `Close`zavře všechny sady záznamů, které jste dříve nezavřeli.

## <a name="transactions"></a>Transakce

Zpracování databázových transakcí je poskytováno na úrovni pracovního prostoru – viz základní `CDaoWorkspace`funkce [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)a [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) třídy .

## <a name="odbc-connections"></a>Připojení ODBC

Doporučený způsob práce se zdroji dat ODBC je připojit externí tabulky k microsoft jet (. MDB).

## <a name="collections"></a>Kolekce

Každá databáze udržuje své vlastní kolekce tabledef, querydef, recordset a relační objekty. Třída `CDaoDatabase` poskytuje členské funkce pro manipulaci s těmito objekty.

> [!NOTE]
> Objekty jsou uloženy v DAO, nikoli v databázovém objektu knihovny MFC. Knihovna MFC poskytuje třídy pro tabledef, querydef a recordset objekty, ale ne pro objekty vztahu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaodatabasecantransact"></a><a name="cantransact"></a>Databáze CDao::CanTransact

Volání této členské funkce k určení, zda databáze umožňuje transakce.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud databáze podporuje transakce; jinak 0.

### <a name="remarks"></a>Poznámky

Transakce jsou spravovány v pracovním prostoru databáze.

## <a name="cdaodatabasecanupdate"></a><a name="canupdate"></a>Databáze CDao::CanUpdate

Volání této členské funkce `CDaoDatabase` k určení, zda objekt umožňuje aktualizace.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CDaoDatabase` pokud objekt umožňuje aktualizace; jinak 0, označující buď, že jste předali `CDaoDatabase` TRUE v *bReadOnly* při otevření objektu nebo že samotná databáze je jen pro čtení. Viz [členská](#open) funkce Otevřít.

### <a name="remarks"></a>Poznámky

Informace o aktualizovatelnosti databáze naleznete v tématu "Aktualizovatelná vlastnost" v nápovědě dao.

## <a name="cdaodatabasecdaodatabase"></a><a name="cdaodatabase"></a>Databáze CDao::Databáze CDao

Vytvoří `CDaoDatabase` objekt.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parametry

*pPracovní prostor*<br/>
Ukazatel na `CDaoWorkspace` objekt, který bude obsahovat nový databázový objekt. Pokud přijmete výchozí hodnotu NULL, konstruktor `CDaoWorkspace` vytvoří dočasný objekt, který používá výchozí pracovní prostor DAO. Ukazatel na objekt pracovního prostoru můžete získat prostřednictvím datového člena [m_pWorkspace.](#m_pworkspace)

### <a name="remarks"></a>Poznámky

Po vytvoření objektu, pokud vytváříte nový Microsoft Jet (. MDB) databáze, volání objektu [Vytvořit](#create) člennou funkci. Pokud jste, místo toho otevření existující databáze, volání objektu [Open](#open) členské funkce.

Po dokončení s objektem, měli [Close](#close) byste zavolat jeho `CDaoDatabase` Zavřít člen funkce a potom zničit objekt.

Může být vhodné vložit objekt `CDaoDatabase` do třídy dokumentu.

> [!NOTE]
> Objekt `CDaoDatabase` je také vytvořen implicitně, pokud otevřete objekt [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez předání ukazatele na existující `CDaoDatabase` objekt. Tento databázový objekt je uzavřen při zavření objektu sady záznamů.

## <a name="cdaodatabaseclose"></a><a name="close"></a>CDaoDatabáze::Zavřít

Volání této členské funkce odpojit od databáze a zavřete všechny otevřené sady záznamů, tabledefs a querydefs přidružené k databázi.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Je vhodné zavřít tyto objekty sami před voláním této členské funkce. Zavřením `CDaoDatabase` objektu jej odeberete z kolekce Databases v přidruženém [pracovním prostoru](../../mfc/reference/cdaoworkspace-class.md). Protože `Close` nezničí `CDaoDatabase` objekt, můžete objekt znovu použít otevřením stejné databáze nebo jiné databáze.

> [!CAUTION]
> Před [Update](../../mfc/reference/cdaorecordset-class.md#update) zavření databáze zavolejte členská funkci `Close` Update (pokud existují čekající úpravy) a členní funkci na všech otevřených objektech sady záznamů. Pokud ukončíte funkci, která deklaruje `CDaoDatabase` [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) nebo objekty v zásobníku, databáze je uzavřena, všechny neuložené změny jsou ztraceny, všechny čekající transakce jsou vráceny zpět a všechny čekající úpravy dat jsou ztraceny.

> [!CAUTION]
> Pokud se pokusíte zavřít databázový objekt, zatímco jsou otevřeny všechny objekty sady záznamů, nebo pokud se pokusíte zavřít objekt pracovního prostoru, zatímco jsou otevřeny všechny databázové objekty patřící do určitého pracovního prostoru, budou tyto objekty sady záznamů uzavřeny a všechny čekající aktualizace nebo úpravy budou vráceny zpět. Pokud se pokusíte zavřít objekt pracovního prostoru, zatímco všechny databázové objekty, které k němu patří, jsou otevřené, operace zavře všechny databázové objekty, které patří k tomuto konkrétnímu objektu pracovního prostoru, což může mít za následek zavření neuzavřených objektů sady záznamů. Pokud nezavřete databázový objekt, knihovna MFC hlásí selhání kontrolního výrazu v sestaveních ladění.

Pokud je databázový objekt definován mimo rozsah funkce a ukončíte funkci bez zavření, databázový objekt zůstane otevřený, dokud není explicitně uzavřen nebo modul, ve kterém je definován, není vymezen.

## <a name="cdaodatabasecreate"></a><a name="create"></a>CDaoDatabáze::Vytvořit

Chcete-li vytvořit nový Microsoft Jet (. MDB) databáze, volání této členské `CDaoDatabase` funkce po vytvoření objektu.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Řetězec výraz, který je název souboru databáze, který vytváříte. Může to být úplná cesta a název\\souboru, například "C: \MYDB. MDB". Musíte zadat jméno. Pokud nezadáte příponu názvu souboru, . MDB je připojen. Pokud vaše síť podporuje jednotnou konvenci pojmenování (UNC),\\\\\\můžete\\také zadat\\síťovou\\cestu, například " \MYSERVER \MYSHARE \MYDIR \MYDB". Pouze Microsoft Jet (. MDB) databázové soubory lze vytvořit pomocí této členské funkce. (Dvojitá zpětná lomítka jsou\\vyžadována v řetězcových literálech, protože " " je řídicí znak Jazyka C++.)

*lpszLocale*<br/>
Řetězec výraz slouží k určení pořadí řazení pro vytvoření databáze. Výchozí hodnota je `dbLangGeneral`. Možné hodnoty:

- `dbLangGeneral`angličtina, němčina, francouzština, portugalština, italština a moderní španělština

- `dbLangArabic`Arabština

- `dbLangCyrillic`Ruština

- `dbLangCzech`Čeština

- `dbLangDutch`Holandština

- `dbLangGreek`Řečtina

- `dbLangHebrew`Hebrejština

- `dbLangHungarian`Maďarština

- `dbLangIcelandic`Islandština

- `dbLangNordic`Severské jazyky (pouze databázový stroj Microsoft Jet verze 1.0)

- `dbLangNorwdan`norština a dánština

- `dbLangPolish`Polština

- `dbLangSpanish`Tradiční španělština

- `dbLangSwedfin`švédština a finština

- `dbLangTurkish`Turečtina

*Dwoptions*<br/>
Celé číslo, které označuje jednu nebo více možností. Možné hodnoty:

- `dbEncrypt`Vytvořte šifrovanou databázi.

- `dbVersion10`Vytvořte databázi s databází Microsoft Jet verze 1.0.

- `dbVersion11`Vytvořte databázi s databází Microsoft Jet verze 1.1.

- `dbVersion20`Vytvořte databázi s databází Microsoft Jet verze 2.0.

- `dbVersion30`Vytvořte databázi s databází Microsoft Jet verze 3.0.

Pokud vynechete konstantu šifrování, vytvoří se nešifrovaná databáze. Můžete zadat pouze jednu konstantu verze. Pokud vyneche konstantu verze, je vytvořena databáze, která používá databázi Microsoft Jet verze 3.0.

> [!CAUTION]
> Pokud databáze není šifrována, je možné, i když implementujete zabezpečení uživatele/hesla, přímo číst binární soubor disku, který tvoří databázi.

### <a name="remarks"></a>Poznámky

`Create`vytvoří databázový soubor a základní databázový objekt DAO a inicializuje objekt Jazyka C++. Objekt je připojen ke kolekci databází přidruženého pracovního prostoru. Databázový objekt je v otevřeném stavu. nevolejte `Open*` po `Create`.

> [!NOTE]
> Pomocí `Create`aplikace můžete vytvořit pouze aplikaci Microsoft Jet (. MDB). Nelze vytvořit databáze ISAM nebo databáze ODBC.

## <a name="cdaodatabasecreaterelation"></a><a name="createrelation"></a>CDaoDatabase::Vytvořitvztah

Volání této členské funkce k vytvoření vztahu mezi jedním nebo více poli v primární tabulce v databázi a jedním nebo více poli v cizí tabulce (jiná tabulka v databázi).

```
void CreateRelation(
    LPCTSTR lpszName,
    LPCTSTR lpszTable,
    LPCTSTR lpszForeignTable,
    long lAttributes,
    LPCTSTR lpszField,
    LPCTSTR lpszForeignField);

void CreateRelation(CDaoRelationInfo& relinfo);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Jedinečný název objektu vztahu. Název musí začínat písmenem a může obsahovat maximálně 40 znaků. Může obsahovat čísla a znaky podtržítka, ale nemůže obsahovat interpunkci nebo mezery.

*lpszTable*<br/>
Název primární tabulky v relaci. Pokud tabulka neexistuje, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Název cizí tabulky v relaci. Pokud tabulka neexistuje, knihovna MFC vyvolá `CDaoException`výjimku typu .

*lAtributy*<br/>
Dlouhá hodnota, která obsahuje informace o typu relace. Tuto hodnotu můžete použít mimo jiné k vynucení referenční integrity. Pomocí operátoru bitové nebo ( **&#124;**) můžete zkombinovat některou z následujících hodnot (pokud má kombinace smysl):

- `dbRelationUnique`Vztah je jeden na jednoho.

- `dbRelationDontEnforce`Vztah není vynuceno (žádná referenční integrita).

- `dbRelationInherited`Vztah existuje v neaktuální databázi, která obsahuje dvě připojené tabulky.

- `dbRelationUpdateCascade`Aktualizace budou kaskády (více o kaskádách, viz Poznámky).

- `dbRelationDeleteCascade`Odstranění se přenesou do kaskády.

*lpszField*<br/>
Ukazatel na řetězec s nulovým ukončením obsahující název pole v primární tabulce (pojmenovaný *lpszTable).*

*lpszForeignField*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název pole v cizí tabulce (pojmenovaný *lpszForeignTable).*

*relinfo*<br/>
Odkaz na objekt [CDaoRelationInfo,](../../mfc/reference/cdaorelationinfo-structure.md) který obsahuje informace o vztahu, který chcete vytvořit.

### <a name="remarks"></a>Poznámky

Relace nemůže zahrnovat dotaz nebo připojenou tabulku z externí databáze.

První verzi funkce použijte, pokud vztah zahrnuje jedno pole v každé ze dvou tabulek. Druhou verzi použijte, pokud vztah zahrnuje více polí. Maximální počet polí v relaci je 14.

Tato akce vytvoří základní objekt vztahu DAO, ale toto je podrobnosti implementace knihovny MFC, `CDaoDatabase`protože zapouzdření objektů relačů knihovny MFC je obsaženo v rámci třídy . Knihovna MFC neposkytuje třídu pro vztahy.

Pokud nastavíte atributy objektu vztahu pro aktivaci kaskádových operací, databázový stroj automaticky aktualizuje nebo odstraní záznamy v jedné nebo více dalších tabulkách při provádění změn v souvisejících tabulkách primárního klíče.

Předpokládejme například, že vytvoříte kaskádovou relaci odstranění mezi tabulkou Zákazníci a tabulkou Objednávky. Když odstraníte záznamy z tabulky Zákazníci, odstraní se také záznamy v tabulce Objednávky související s tímto zákazníkem. Kromě toho pokud vytvoříte kaskádové odstranění relací mezi tabulkou Objednávky a jinými tabulkami, záznamy z těchto tabulek se automaticky odstraní při odstranění záznamů z tabulky Zákazníci.

Související informace naleznete v tématu "CreateRelation Method" v nápovědě DAO.

## <a name="cdaodatabasedeletequerydef"></a><a name="deletequerydef"></a>CDaoDatabáze::DeleteQueryDef

Volání této členské funkce odstranit zadaný querydef `CDaoDatabase` – uložený dotaz – z kolekce QueryDefs objektu.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název uloženého dotazu, který chcete odstranit.

### <a name="remarks"></a>Poznámky

Poté tento dotaz již není definován v databázi.

Informace o vytváření objektů querydef naleznete v tématu class [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Querydef objekt se stane `CDaoDatabase` přidružen k určitému objektu při vytváření objektu, `CDaoQueryDef` předání mačká ukazatel na databázový objekt.

## <a name="cdaodatabasedeleterelation"></a><a name="deleterelation"></a>CDaoDatabáze::DeleteRelation

Volání této členské funkce odstranit existující vztah z kolekce vztahy objektu databáze.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název vztahu k odstranění.

### <a name="remarks"></a>Poznámky

Poté vztah již neexistuje.

Související informace naleznete v tématu "Delete Method" v nápovědě dao.

## <a name="cdaodatabasedeletetabledef"></a><a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef

Volání této členské funkce odstranit zadanou tabulku a `CDaoDatabase` všechna její data z kolekce Objekt TableDefs.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název tabledef odstranit.

### <a name="remarks"></a>Poznámky

Poté tato tabulka již není definována v databázi.

> [!NOTE]
> Dávejte velký pozor, abyste neodstranili systémové tabulky.

Informace o vytváření objektů tabledef naleznete v tématu třída [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Objekt tabledef se při `CDaoDatabase` vytváření objektu `CDaoTableDef` přikonstruje k určitému objektu a předává mu ukazatel databázového objektu.

Související informace naleznete v tématu "Delete Method" v nápovědě dao.

## <a name="cdaodatabaseexecute"></a><a name="execute"></a>Databáze CDao::Spustit

Volání této členské funkce spustit akční dotaz nebo spustit příkaz SQL v databázi.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*Lpszsql*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující platný příkaz SQL, který má být proveden.

*nMožnosti*<br/>
Celé číslo, které určuje možnosti týkající se integrity dotazu. Pomocí bitového operátoru OR ( **&#124;**) můžete zkombinovat některou z následujících konstant (za předpokladu, že kombinace dává smysl – například byste se nekombinovali `dbInconsistent` s `dbConsistent`):

- `dbDenyWrite`Odepřít oprávnění k zápisu ostatním uživatelům.

- `dbInconsistent`(Výchozí) Nekonzistentní aktualizace.

- `dbConsistent`Konzistentní aktualizace.

- `dbSQLPassThrough`Průchod SQL. Způsobí, že příkaz SQL, který má být předán ke zdroji dat ODBC pro zpracování.

- `dbFailOnError`Pokud dojde k chybě, vraťte aktualizace zpět.

- `dbSeeChanges`Vygenerujte chybu za běhu, pokud jiný uživatel mění data, která upravujete.

> [!NOTE]
> Pokud `dbInconsistent` jsou `dbConsistent` zahrnuty oba a nebo pokud ani není zahrnuta, výsledek je výchozí. Vysvětlení těchto konstant naleznete v tématu "Metoda spuštění" v nápovědě DAO.

### <a name="remarks"></a>Poznámky

`Execute`funguje pouze pro akční dotazy nebo předávací dotazy SQL, které nevracejí výsledky. Nefunguje pro vybrané dotazy, které vracejí záznamy.

Definice a informace o akčních dotazech naleznete v tématech "Akční dotaz" a "Metoda spuštění" v nápovědě dao.

> [!TIP]
> Vzhledem k tomu, syntakticky `Execute` správný příkaz SQL a správná oprávnění, členská funkce neselže, i když ani jeden řádek lze upravit nebo odstranit. Proto vždy použijte `dbFailOnError` možnost při `Execute` použití členské funkce ke spuštění aktualizace nebo odstranění dotazu. Tato možnost způsobí, že knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md) a vrátí zpět všechny úspěšné změny, pokud jsou některé z ovlivněných záznamů uzamčeny a nelze je aktualizovat ani odstranit. Všimněte si, `GetRecordsAffected` že můžete vždy volat a zjistit, kolik záznamů bylo ovlivněno.

Volání [GetRecordsAffected](#getrecordsaffected) členské funkce databázového objektu k určení počtu `Execute` záznamů ovlivněných poslední volání. Vrátí například `GetRecordsAffected` informace o počtu záznamů odstraněných, aktualizovaných nebo vložených při provádění akčního dotazu. Vrácený počet nebude odrážet změny v souvisejících tabulkách při kaskádové aktualizace nebo odstranění jsou v platnosti.

`Execute`nevrátí sadu záznamů. Použití `Execute` na dotaz, který vybere záznamy způsobí, že `CDaoException`knihovna MFC vyvolat výjimku typu . (Neexistuje žádná `ExecuteSQL` členská funkce `CDatabase::ExecuteSQL`obdobná .)

## <a name="cdaodatabasegetconnect"></a><a name="getconnect"></a>Databáze CDao::GetConnect

Volání této členské funkce k načtení `CDaoDatabase` připojovacího řetězce použitého k připojení objektu k databázi ROZHRANÍ ODBC nebo ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

Připojovací řetězec, pokud [open](#open) byl úspěšně volán na zdroj dat ODBC; v opačném případě prázdný řetězec. Pro Microsoft Jet (. MDB), řetězec je vždy prázdný, pokud jej nenastavíte pro použití s `dbSQLPassThrough` možností použitou s funkcí [Execute](#execute) member nebo použitým při otevírání sady záznamů.

### <a name="remarks"></a>Poznámky

Řetězec obsahuje informace o zdroji otevřené databáze nebo databáze používané v předávací dotaz. Připojovací řetězec se skládá z specifikátoru typu databáze a nulových nebo více parametrů oddělených středníky.

> [!NOTE]
> Použití tříd MFC DAO pro připojení ke zdroji dat prostřednictvím rozhraní ODBC je méně efektivní než připojení prostřednictvím připojené tabulky.

> [!NOTE]
> Připojovací řetězec se používá k předání dalších informací rozhraní ODBC a určitým ovladačům ISAM podle potřeby. Nepoužívá se pro . Databáze MDB. Pro základní tabulky databáze Microsoft Jet je připojovací řetězec prázdný řetězec ("" s výjimkou případů, kdy jej použijete pro předávací dotaz SQL, jak je popsáno výše v části Vrácená hodnota výše.

Popis vytvoření připojovacího řetězce naleznete v členské funkci [Otevřít.](#open) Po nastavení připojovacího `Open` řetězce ve volání jej můžete později použít ke kontrole nastavení a určit typ, cestu, ID uživatele, heslo nebo zdroj dat ODBC databáze.

## <a name="cdaodatabasegetname"></a><a name="getname"></a>CDaoDatabáze::GetName

Volání této členské funkce načíst název aktuálně otevřené databáze, což je název existujícího databázového souboru nebo název registrovaného zdroje dat ODBC.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta a název souboru databáze, pokud je úspěšná; v opačném případě prázdný [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Pokud vaše síť podporuje jednotnou konvenci pojmenování (UNC),\\\\\\můžete také\\zadat\\síťovou\\cestu – například " \MYSERVER \MYSHARE \MYDIR \MYDB. MDB". (Dvojitá zpětná lomítka jsou\\vyžadována v řetězcových literálech, protože " " je řídicí znak Jazyka C++.)

Tento název můžete například chtít zobrazit v záhlaví. Pokud dojde k chybě při načítání názvu, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
> Pro lepší výkon při přístupu k externím databázím doporučujeme připojit externí databázové tabulky k databázi Microsoft Jet (. MDB) spíše než připojení přímo ke zdroji dat.

Typ databáze je označen souborem nebo adresářem, na který cesta odkazuje, a to následovně:

|Pathname odkazuje na..|Typ databáze|
|--------------------------|-------------------|
|. Soubor MDB|Databáze Microsoft Jet (Microsoft Access)|
|Adresář, který obsahuje . DBF soubor (soubory)|databáze dBASE|
|Adresář, který obsahuje . SOUBOR XLS|Databáze aplikace Microsoft Excel|
|Adresář, který obsahuje . PDX soubory|Databáze paradoxů|
|Adresář obsahující vhodně formátované soubory textové databáze|Databáze textového formátu|

Pro databáze ODBC, jako je SQL Server a Oracle, připojovací řetězec databáze identifikuje název zdroje dat (DSN), který je registrován rozhraním ODBC.

## <a name="cdaodatabasegetquerydefcount"></a><a name="getquerydefcount"></a>Databáze CDao::GetQueryDefCount

Volání této členské funkce načíst počet dotazů definovaných v databázi QueryDefs kolekce.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet dotazů definovaných v databázi.

### <a name="remarks"></a>Poznámky

`GetQueryDefCount`je užitečné, pokud potřebujete procházet všechny querydefs v QueryDefs kolekce. Informace o daném dotazu v kolekci získáte v tématu [GetQueryDefInfo](#getquerydefinfo).

## <a name="cdaodatabasegetquerydefinfo"></a><a name="getquerydefinfo"></a>CDaoDatabáze::GetQueryDefInfo

Volání této členské funkce získat různé druhy informací o dotaz definovaný chvatvá v databázi.

```
void GetQueryDefInfo(
    int nIndex,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetQueryDefInfo(
    LPCTSTR lpszName,
    CDaoQueryDefInfo& querydefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index předdefinovaného dotazu v databázi QueryDefs kolekce, pro vyhledávání podle indexu.

*querydefinfo*<br/>
Odkaz na objekt [CDaoQueryDefInfo,](../../mfc/reference/cdaoquerydefinfo-structure.md) který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o sadě záznamů mají být načteny. Dostupné možnosti jsou zde uvedeny spolu s tím, co způsobí, že funkce vrátit o sadu záznamů:

- AFX_DAO_PRIMARY_INFO (Výchozí) Název, zadejte

- AFX_DAO_SECONDARY_INFO primární informace plus: Datum vytvoření, Datum poslední aktualizace, Vrátí záznamy, Aktualizovatelné

- AFX_DAO_ALL_INFO primární a sekundární informace plus: SQL, Connect, ODBCTimeout

*název lpsz*<br/>
Řetězec obsahující název dotazu definovaného v databázi, pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jsou zadány dvě verze funkce, takže můžete vybrat dotaz buď podle indexu v databázi QueryDefs kolekce nebo podle názvu dotazu.

Popis informací vrácených v *querydefinfo*naleznete ve struktuře [CDaoQueryDefInfo.](../../mfc/reference/cdaoquerydefinfo-structure.md) Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Pokud požadujete jednu úroveň informací, získáte také všechny předchozí úrovně informací.

## <a name="cdaodatabasegetquerytimeout"></a><a name="getquerytimeout"></a>CDaoDatabáze::GetQueryTimeout

Volání této členské funkce načíst aktuální počet sekund povolit před následné operace v připojené databázi jsou časový mat.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Krátké celé číslo obsahující hodnotu časového času v sekundách.

### <a name="remarks"></a>Poznámky

Operace může časový limit z důvodu problémů s přístupem k síti, nadměrné doby zpracování dotazů a tak dále. Během platnosti nastavení ovlivní všechny operace otevření, přidání nových, aktualizací a odstranění `CDaoDatabase` všech sad záznamů přidružených k tomuto objektu. Aktuální nastavení časového limitu můžete změnit voláním [SetQueryTimeout](#setquerytimeout). Změna hodnoty časového limitu dotazu pro sadu záznamů po otevření nezmění hodnotu sady záznamů. Například následné operace [přesunutí](../../mfc/reference/cdaorecordset-class.md#move) nepoužívají novou hodnotu. Výchozí hodnota je zpočátku nastavena při inicializování databázového stroje.

Výchozí hodnota časového limitu dotazu je převzata z registru systému Windows. Pokud není k dispozici žádné nastavení registru, výchozí hodnota je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, nedojde k žádnému časovému limitu; a komunikace s databází může přestat reagovat. Toto chování může být užitečné během vývoje. Pokud volání selže, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Související informace naleznete v tématu "QueryTimeout Property" v nápovědě dao.

## <a name="cdaodatabasegetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Volání této členské funkce k určení počtu záznamů ovlivněných nejnovějšívolání funkce [člena execute.](#execute)

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Návratová hodnota

Dlouhé celé číslo obsahující počet ovlivněných záznamů.

### <a name="remarks"></a>Poznámky

Vrácená hodnota zahrnuje počet záznamů odstraněných, aktualizovaných nebo vložených akčním dotazem spuštěným pomocí `Execute`aplikace . Vrácený počet nebude odrážet změny v souvisejících tabulkách při kaskádové aktualizace nebo odstranění jsou v platnosti.

Související informace naleznete v tématu "RecordsAffected Property" v nápovědě dao.

## <a name="cdaodatabasegetrelationcount"></a><a name="getrelationcount"></a>CDaoDatabáze::GetRelationCount

Volání této členské funkce získat počet vztahů definovaných mezi tabulkami v databázi.

```
short GetRelationCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet vztahů definovaných mezi tabulkami v databázi.

### <a name="remarks"></a>Poznámky

`GetRelationCount`je užitečné, pokud potřebujete procházet všechny definované vztahy v kolekci vztahů databáze. Informace o daném vztahu v kolekci získáte v tématu [GetRelationInfo](#getrelationinfo).

Chcete-li ilustrovat koncept relace, zvažte tabulku Dodavatelé a tabulku Produkty, které mohou mít relaci 1:N. V tomto vztahu může jeden dodavatel dodat více než jeden produkt. Ostatní vztahy jsou 1:1 a n:N.

## <a name="cdaodatabasegetrelationinfo"></a><a name="getrelationinfo"></a>CDaoDatabáze::GetRelationInfo

Volání této členské funkce získat informace o zadaný vztah v kolekci vztahy databáze.

```
void GetRelationInfo(
    int nIndex,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetRelationInfo(
    LPCTSTR lpszName,
    CDaoRelationInfo& relinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index objektu vztahu v kolekci vztahů databáze pro vyhledávání podle indexu.

*relinfo*<br/>
Odkaz na objekt [CDaoRelationInfo,](../../mfc/reference/cdaorelationinfo-structure.md) který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o vztahu načíst. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit o vztahu:

- AFX_DAO_PRIMARY_INFO (Výchozí) Název, Tabulka, Cizí tabulka

- AFX_DAO_SECONDARY_INFO atributy, informace o poli

Informace o poli je objekt [CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) obsahující pole z primární tabulky, která je součástí vztahu.

*název lpsz*<br/>
Řetězec obsahující název objektu vztahu, pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Dvě verze této funkce poskytují přístup buď podle indexu nebo podle názvu. Popis informací vrácených v *relinfo*naleznete v [cdaorelationinfo](../../mfc/reference/cdaorelationinfo-structure.md) struktury. Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Pokud požadujete informace na jedné úrovni, získáte také informace na všech předchozích úrovních.

> [!NOTE]
> Pokud nastavíte atributy objektu vztahu pro`dbRelationUpdateCascades` `dbRelationDeleteCascades`aktivaci kaskádových operací ( nebo ), databázový stroj Microsoft Jet automaticky aktualizuje nebo odstraní záznamy v jedné nebo více dalších tabulkách při provádění změn v souvisejících tabulkách primárního klíče. Předpokládejme například, že vytvoříte kaskádovou relaci odstranění mezi tabulkou Zákazníci a tabulkou Objednávky. Když odstraníte záznamy z tabulky Zákazníci, odstraní se také záznamy v tabulce Objednávky související s tímto zákazníkem. Kromě toho pokud vytvoříte kaskádové odstranění relací mezi tabulkou Objednávky a jinými tabulkami, záznamy z těchto tabulek se automaticky odstraní při odstranění záznamů z tabulky Zákazníci.

## <a name="cdaodatabasegettabledefcount"></a><a name="gettabledefcount"></a>Databáze CDao::GetTableDefCount

Volání této členské funkce načíst počet tabulek definovaných v databázi.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet tabledefs definované v databázi.

### <a name="remarks"></a>Poznámky

`GetTableDefCount`je užitečné, pokud potřebujete procházet všechny tabledefs v databázi TableDefs kolekce. Informace o dané tabulce v kolekci získáte v tématu [GetTableDefInfo](#gettabledefinfo).

## <a name="cdaodatabasegettabledefinfo"></a><a name="gettabledefinfo"></a>CDaoDatabáze::GetTableDefInfo

Volání této členské funkce získat různé druhy informací o tabulce definované v databázi.

```
void GetTableDefInfo(
    int nIndex,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetTableDefInfo(
    LPCTSTR lpszName,
    CDaoTableDefInfo& tabledefinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index tabledef objektu v databázi TableDefs kolekce, pro vyhledávání podle indexu.

*tabulkadefinfo*<br/>
Odkaz na objekt [CDaoTableDefInfo,](../../mfc/reference/cdaotabledefinfo-structure.md) který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o tabulce mají být načteny. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit o vztahu:

- AFX_DAO_PRIMARY_INFO (Výchozí) Název, Aktualizovatelné, Atributy

- AFX_DAO_SECONDARY_INFO primární informace plus: Datum vytvoření, Datum poslední aktualizace, Název zdrojové tabulky, Připojení

- AFX_DAO_ALL_INFO primární a sekundární informace plus: Ověřovací pravidlo, ověřovací text, počet záznamů

*název lpsz*<br/>
Název objektu tabledef pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jsou dodávány dvě verze funkce, takže můžete vybrat tabulku buď podle indexu v databázi TableDefs kolekce nebo podle názvu tabulky.

Popis informací vrácených v *tabledefinfo*naleznete ve struktuře [CDaoTableDefInfo.](../../mfc/reference/cdaotabledefinfo-structure.md) Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Pokud požadujete informace na jedné úrovni, získáte také informace pro všechny předchozí úrovně.

> [!NOTE]
> Možnost AFX_DAO_ALL_INFO poskytuje informace, které mohou být pomalé získat. V tomto případě počítání záznamů v tabulce může být velmi časově náročné, pokud existuje mnoho záznamů.

## <a name="cdaodatabasegetversion"></a><a name="getversion"></a>Databáze CDao::GetVersion

Volání této členské funkce k určení verze souboru databáze Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který označuje verzi souboru databáze přidružené k objektu.

### <a name="remarks"></a>Poznámky

Vrácená hodnota představuje číslo verze ve tvaru "major.minor"; například "3.0". Číslo verze produktu (například 3.0) se skládá z čísla verze (3), tečky a čísla verze (0). Dosavadní verze jsou 1.0, 1.1, 2.0 a 3.0.

Související informace naleznete v tématu "Vlastnost verze" v nápovědě dao.

## <a name="cdaodatabaseisopen"></a><a name="isopen"></a>Databáze CDao::Jeotevřeno

Volání této členské funkce `CDaoDatabase` k určení, zda je objekt aktuálně otevřen v databázi.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CDaoDatabase` pokud je objekt aktuálně otevřen; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="cdaodatabasem_pdaodatabase"></a><a name="m_pdaodatabase"></a>CDaoDatabáze::m_pDAODatabase

Obsahuje ukazatel na rozhraní OLE pro databázový objekt `CDaoDatabase` DAO, který objekt obsahuje.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte, pokud potřebujete přímý přístup k rozhraní DAO.

Informace o přímém volání dao naleznete [v technické poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaodatabasem_pworkspace"></a><a name="m_pworkspace"></a>CDaoDatabáze::m_pWorkspace

Obsahuje ukazatel na objekt [CDaoWorkspace,](../../mfc/reference/cdaoworkspace-class.md) který obsahuje databázový objekt.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte, pokud potřebujete přímý přístup k pracovnímu prostoru, například k získání ukazatelů na jiné databázové objekty v kolekci databáze pracovního prostoru.

## <a name="cdaodatabaseopen"></a><a name="open"></a>Databáze CDao::Otevřít

Tuto členskou funkci je nutné volat k `CDaoDatabase` inicializaci nově vytvořeného objektu, který představuje existující databázi.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Řetězec výraz, který je název existující hod (Microsoft Jet (. MDB) databázového souboru. Pokud má název souboru příponu, je vyžadován. Pokud vaše síť podporuje jednotnou konvenci pojmenování (UNC),\\\\\\můžete\\také zadat\\síťovou\\cestu, například " \MYSERVER \MYSHARE \MYDIR \MYDB. MDB". (Dvojitá zpětná lomítka jsou\\vyžadována v řetězcových literálech, protože " " je řídicí znak Jazyka C++.)

Některé aspekty platí při použití *lpszName*. Pokud:

- Odkazuje na databázi, která je již otevřena pro výhradní přístup jiného uživatele, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Depeše tuto výjimku, aby uživatel věděl, že databáze není k dispozici.

- Je prázdný řetězec ("") a *lpszConnect* je "ODBC;", zobrazí se dialogové okno se seznamem všech registrovaných názvů zdrojů dat ODBC, aby uživatel mohl vybrat databázi. Měli byste se vyhnout přímému připojení ke zdrojům dat ODBC. místo toho použijte připojenou tabulku.

- V opačném případě neodkazuje na existující databázi nebo platný název zdroje `CDaoException`dat ROZHRANÍ ODBC, knihovna MFC vyvolá výjimku typu .

> [!NOTE]
> Podrobnosti o chybových kódech DAO naleznete v DAOERR. H soubor. Související informace naleznete v tématu "Zachytitelné chyby přístupu k datům" v nápovědě dao.

*bExkluzivní*<br/>
Logická hodnota, která je PRAVDA, pokud má být databáze otevřena pro výhradní (nesdílený) přístup a FALSE, pokud má být databáze otevřena pro sdílený přístup. Pokud tento argument vynesete, databáze se otevře pro sdílený přístup.

*bReadOnly*<br/>
Logická hodnota, která je PRAVDA, pokud má být databáze otevřena pro přístup jen pro čtení a NEPRAVDA, má-li být databáze otevřena pro přístup pro čtení a zápis. Pokud tento argument vynesete, databáze se otevře pro přístup pro čtení a zápis. Všechny závislé sady záznamů dědí tento atribut.

*lpszPřipojit*<br/>
Řetězec výraz používaný pro otevření databáze. Tento řetězec představuje argumenty připojení ODBC. Je nutné zadat výhradní argumenty a argumenty jen pro čtení zadat zdrojový řetězec. Pokud je databáze databáze Microsoft Jet (. MDB), tento řetězec je prázdný (""). Syntaxe výchozí hodnoty – **_T**("") – poskytuje přenositelnost pro unicode i ansi sestavení aplikace.

### <a name="remarks"></a>Poznámky

`Open`přidruží databázi k podkladovému objektu DAO. Databázový objekt nelze použít ke vytvoření objektů sady záznamů, tabledef nebo querydef, dokud nebude inicializován. `Open`připojí databázový objekt do kolekce databází přidruženého pracovního prostoru.

Použijte následující parametry:

- Pokud otevíráte Microsoft Jet (. MDB) databáze, použijte parametr *lpszName* a předavěte prázdný řetězec pro parametr *lpszConnect* nebo předavte řetězec hesla formuláře "; PWD=heslo", pokud je databáze chráněna heslem (. pouze databáze MDB).

- Pokud otevíráte zdroj dat ODBC, předajte platný připojovací řetězec ODBC v *lpszConnect* a prázdný řetězec v *lpszName*.

Související informace naleznete v tématu "OpenDatabase Method" v nápovědě DAO.

> [!NOTE]
> Pro lepší výkon při přístupu k externím databázím, včetně databází ISAM a zdrojů dat ODBC, se doporučuje připojit externí databázové tabulky k databázi motoru Microsoft Jet (. MDB) spíše než připojení přímo ke zdroji dat.

Je možné, že pokus o připojení časový limit, pokud například hostitel DBMS není k dispozici. Pokud se pokus `Open` o připojení nezdaří, vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Zbývající poznámky se vztahují pouze na databáze ROZHRANÍ ODBC:

Pokud je databáze databáze ODBC a parametry ve volání `Open` neobsahují dostatek informací k vytvoření připojení, ovladač ODBC otevře dialogové okno pro získání potřebných informací od uživatele. Při volání `Open`je připojovací řetězec *lpszConnect*uložen soukromě a je k dispozici voláním členské funkce [GetConnect.](#getconnect)

Pokud chcete, můžete před voláním `Open` otevřít vlastní dialogové okno, abyste získali informace od uživatele, například heslo, a pak tyto informace přidat do připojovacího řetězce, kterému předáte `Open`. Nebo můžete chtít uložit připojovací řetězec, který předáte (možná v registru systému `Open` Windows), abyste jej mohli znovu použít při příštím volání aplikace na `CDaoDatabase` objekt.

Připojovací řetězec můžete také použít pro více úrovní `CDaoDatabase` autorizace přihlášení (každá pro jiný objekt) nebo k předávání dalších informací specifických pro databázi.

## <a name="cdaodatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDaoDatabáze::SetQueryTimeout

Volání této členské funkce přepsat výchozí počet sekund povolit před následné operace na připojené databáze časový limit.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSekundy*<br/>
Počet sekund, které mají být povoleny před vypršením doby pokusu o dotaz.

### <a name="remarks"></a>Poznámky

Operace může časový limit z důvodu problémů s přístupem k síti, nadměrné doby zpracování dotazů a tak dále. Volání `SetQueryTimeout` před otevřením sady záznamů nebo před voláním členské funkce [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)nebo [Delete,](../../mfc/reference/cdaorecordset-class.md#delete) pokud chcete změnit hodnotu časového limitu dotazu. Toto nastavení ovlivní `AddNew`všechny `Update`následné `Delete` [open](../../mfc/reference/cdaorecordset-class.md#open), , a `CDaoDatabase` volání všech sad záznamů přidružených k tomuto objektu. Změna hodnoty časového limitu dotazu pro sadu záznamů po otevření nezmění hodnotu sady záznamů. Například následné operace [přesunutí](../../mfc/reference/cdaorecordset-class.md#move) nepoužívají novou hodnotu.

Výchozí hodnota pro časové limity dotazu je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, nedojde k žádnému časovému limitu; komunikace s databází může přestat reagovat. Toto chování může být užitečné během vývoje.

Související informace naleznete v tématu "QueryTimeout Property" v nápovědě dao.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
