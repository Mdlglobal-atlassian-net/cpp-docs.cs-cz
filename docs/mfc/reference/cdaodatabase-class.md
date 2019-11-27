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
ms.openlocfilehash: 4c594b1ddfc1464417506557bb8743c4979be677
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304282"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase – třída

Představuje připojení k databázi Accessu pomocí objektů DAO (Data Access Objects). Rozhraní DAO je podporováno prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

## <a name="syntax"></a>Syntaxe

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Vytvoří objekt `CDaoDatabase`. Zavolejte `Open` pro připojení objektu k databázi.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud databáze podporuje transakce.|
|[CDaoDatabase:: CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud je objekt `CDaoDatabase` možné aktualizovat (není jen pro čtení).|
|[CDaoDatabase:: Close](#close)|Zavře připojení k databázi.|
|[CDaoDatabase:: Create](#create)|Vytvoří základní databázový objekt DAO a inicializuje objekt `CDaoDatabase`.|
|[CDaoDatabase::CreateRelation](#createrelation)|Definuje novou relaci mezi tabulkami v databázi.|
|[CDaoDatabase::D eleteQueryDef](#deletequerydef)|Odstraní objekt querydef uložený v kolekci QueryDefs databáze.|
|[CDaoDatabase::D eleteRelation](#deleterelation)|Odstraní existující relaci mezi tabulkami v databázi.|
|[CDaoDatabase::D eleteTableDef](#deletetabledef)|Odstraní definici tabulky v databázi. Tím se odstraní skutečná tabulka a veškerá její data.|
|[CDaoDatabase:: Execute](#execute)|Provede dotaz akce. Volání `Execute` pro dotaz, který vrací výsledky, vyvolá výjimku.|
|[CDaoDatabase:: GetConnect](#getconnect)|Vrátí připojovací řetězec, který se používá pro připojení objektu `CDaoDatabase` k databázi. Používá se pro rozhraní ODBC.|
|[CDaoDatabase:: GetName](#getname)|Vrátí název databáze, která se právě používá.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Vrátí počet dotazů, které jsou definovány pro databázi.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Vrátí informace o zadaném dotazu definovaném v databázi.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Vrátí počet sekund, po jejichž uplynutí vyprší platnost operací databázového dotazu. Má vliv na všechny následné operace otevřít, přidat nové, aktualizovat a upravit a jiné operace na zdroje dat ODBC (pouze), jako jsou například volání `Execute`.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů ovlivněných operací Poslední aktualizace, úpravy nebo přidání nebo voláním `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Vrátí počet vztahů definovaných mezi tabulkami v databázi.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Vrátí informace o zadané relaci definované mezi tabulkami v databázi.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Vrátí počet tabulek definovaných v databázi.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Vrátí informace o zadané tabulce v databázi.|
|[CDaoDatabase:: GetVersion](#getversion)|Vrátí verzi databázového stroje přidruženého k databázi.|
|[CDaoDatabase:: Open](#isopen)|Vrátí nenulovou hodnotu, pokud je objekt `CDaoDatabase` aktuálně připojen k databázi.|
|[CDaoDatabase:: Open](#open)|Naváže připojení k databázi.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Nastaví dobu v sekundách, po jejímž uplynutí budou operace databázového dotazu (jenom u zdrojů dat ODBC) vyprší. Má vliv na všechny následné operace otevřít, přidat nové, aktualizovat a odstranit.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoDatabase:: m_pDAODatabase](#m_pdaodatabase)|Ukazatel na základní databázový objekt DAO.|
|[CDaoDatabase:: m_pWorkspace](#m_pworkspace)|Ukazatel na objekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , který obsahuje databázi a definuje jeho místo transakce.|

## <a name="remarks"></a>Poznámky

Informace o podporovaných formátech databáze naleznete v tématu funkce členu [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) . Jeden nebo více objektů `CDaoDatabase` můžete v daném okamžiku v daném pracovním prostoru, který je reprezentován objektem [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , aktivovat v daném čase. Pracovní prostor udržuje kolekci otevřených databázových objektů, které se nazývají kolekce databází.

## <a name="usage"></a>Využití

Objekty databáze lze vytvořit implicitně při vytváření objektů sady záznamů. Můžete ale také vytvořit databázové objekty explicitně. Chcete-li použít existující databázi explicitně s `CDaoDatabase`, proveďte jednu z následujících akcí:

- Sestavte objekt `CDaoDatabase` a předejte ukazatel na otevřený objekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) .

- Nebo vytvořte objekt `CDaoDatabase` bez zadání pracovního prostoru (MFC vytvoří objekt dočasného pracovního prostoru).

Chcete-li vytvořit novou aplikaci Microsoft Jet (. MDB) databáze, Sestavte objekt `CDaoDatabase` a zavolejte jeho členskou funkci [Create](#create) . Nevolejte *`Open`* po `Create`.

Chcete-li otevřít existující databázi, vytvořte objekt `CDaoDatabase` a zavolejte jeho [otevřenou](#open) členskou funkci.

Některé z těchto postupů připojí objekt databáze DAO do kolekce databází v pracovním prostoru a otevře připojení k datům. Při vytváření objektů [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)nebo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) pro provoz v připojené databázi předejte konstruktory pro tyto objekty ukazatel na objekt `CDaoDatabase`. Po dokončení používání připojení Zavolejte členskou funkci [Close](#close) a odstraňte objekt `CDaoDatabase`. `Close` zavře všechny sady záznamů, které jste předtím nezavřeli.

## <a name="transactions"></a>Transakce

Zpracování transakce databáze je dodáno na úrovni pracovního prostoru – viz členské funkce [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans)a [Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) třídy `CDaoWorkspace`.

## <a name="odbc-connections"></a>Připojení ODBC

Doporučený způsob práce se zdroji dat ODBC je připojení externích tabulek ke službě Microsoft Jet (. MDB) databáze.

## <a name="collections"></a>Kolekce

Každá databáze udržuje vlastní kolekce objektů tabledef, QueryDef, Recordset a relation. Třída `CDaoDatabase` poskytuje členské funkce pro manipulaci s těmito objekty.

> [!NOTE]
>  Objekty jsou uloženy v rozhraní DAO, nikoli v objektu databáze knihovny MFC. Knihovna MFC dodává třídy pro objekty TableDef, querydef a Recordset, ale ne pro objekty vztahů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="cantransact"></a>CDaoDatabase::CanTransact

Voláním této členské funkce určíte, zda databáze povoluje transakce.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud databáze podporuje transakce; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Transakce se spravují v pracovním prostoru databáze.

##  <a name="canupdate"></a>CDaoDatabase:: CanUpdate

Voláním této členské funkce určíte, zda objekt `CDaoDatabase` povoluje aktualizace.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt `CDaoDatabase` povoluje aktualizace. jinak 0, což znamená, že jste při otevření `CDaoDatabase`ho objektu předali hodnotu TRUE v *bReadOnly* nebo že je samotná databáze jen pro čtení. Podívejte se na [otevřenou](#open) členskou funkci.

### <a name="remarks"></a>Poznámky

Informace o možnosti aktualizace databáze najdete v tématu "Aktualizovatelná vlastnost" v nápovědě k rozhraní DAO.

##  <a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase

Vytvoří objekt `CDaoDatabase`.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parametry

*pWorkspace*<br/>
Ukazatel na objekt `CDaoWorkspace`, který bude obsahovat nový databázový objekt. Pokud přijmete výchozí hodnotu NULL, vytvoří konstruktor dočasný objekt `CDaoWorkspace`, který používá výchozí pracovní prostor DAO. Můžete získat ukazatel na objekt pracovního prostoru prostřednictvím datového členu [m_pWorkspace](#m_pworkspace) .

### <a name="remarks"></a>Poznámky

Pokud vytváříte nový Microsoft Jet, po sestavení objektu. MDB) databáze Zavolejte členskou funkci [Create](#create) objektu. Pokud jste místo toho, otevřete existující databázi, zavolejte funkci [otevřené](#open) členské funkce objektu.

Po dokončení s objektem byste měli zavolat jeho členskou funkci [Close](#close) a poté zničit objekt `CDaoDatabase`.

Je možné, že bude vhodné vložit objekt `CDaoDatabase` do třídy dokumentu.

> [!NOTE]
>  Objekt `CDaoDatabase` je také implicitně vytvořen, pokud otevřete objekt [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez předání ukazatele na existující objekt `CDaoDatabase`. Tento databázový objekt je uzavřen při zavření objektu Recordset.

##  <a name="close"></a>CDaoDatabase:: Close

Zavolejte tuto členskou funkci, aby se odpojila od databáze a zavřela všechny otevřené sady záznamů, TableDefs a QueryDefs přidružené k databázi.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Je vhodné tyto objekty před voláním této členské funkce Zavřít sami. Zavření objektu `CDaoDatabase` odebere z kolekce databáze v přidruženém [pracovním prostoru](../../mfc/reference/cdaoworkspace-class.md). Vzhledem k tomu, že `Close` nezničí objekt `CDaoDatabase`, můžete znovu použít objekt otevřením stejné databáze nebo jiné databáze.

> [!CAUTION]
>  Zavolejte členskou funkci [Update](../../mfc/reference/cdaorecordset-class.md#update) (pokud existují probíhající úpravy) a `Close` členskou funkci na všech otevřených objektech sady záznamů před zavřením databáze. Pokud ukončíte funkci, která deklaruje objekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) nebo `CDaoDatabase` v zásobníku, bude databáze zavřena, všechny neuložené změny budou ztraceny, všechny probíhající transakce budou vráceny zpět a všechny probíhající úpravy dat budou ztraceny.

> [!CAUTION]
>  Pokud se pokusíte zavřít databázový objekt, když jsou otevřené nějaké objekty sady záznamů, nebo pokud se pokusíte zavřít objekt pracovního prostoru, zatímco všechny databázové objekty patřící do daného konkrétního pracovního prostoru jsou otevřené, tyto objekty sady záznamů budou uzavřeny a všechny probíhající aktualizace nebo úpravy budou vráceno zpět. Pokud se pokusíte zavřít objekt pracovního prostoru, zatímco jsou otevřené všechny databázové objekty, které jsou v něm otevřeny, operace zavře všechny databázové objekty patřící do tohoto konkrétního objektu pracovního prostoru, což může vést k zavření neuzavřených objektů sady záznamů. Pokud nezavřete objekt databáze, knihovna MFC ohlásí selhání kontrolního výrazu v sestavení ladění.

Pokud je objekt databáze definován mimo rozsah funkce a ukončíte funkci bez jejího zavření, zůstane objekt databáze otevřený, dokud není explicitně zavřen, nebo modul, ve kterém je definován, není mimo rozsah.

##  <a name="create"></a>CDaoDatabase:: Create

Chcete-li vytvořit novou aplikaci Microsoft Jet (. MDB) databáze, zavolejte tuto členskou funkci po vytvoření objektu `CDaoDatabase`.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězcový výraz, který je název databázového souboru, který vytváříte. Může se jednat o úplnou cestu a název souboru, například "C:\\\MYDB. MDB ". Je nutné, abyste zadali jméno. Pokud nezadáte příponu názvu souboru,. MDB je připojeno. Pokud vaše síť podporuje konvence UNC (Uniform Naming Convention), můžete také zadat síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Pouze Microsoft Jet (. MDB) soubory databáze lze vytvořit pomocí této členské funkce. (Pro řetězcové literály jsou vyžadovány dvojité zpětné lomítko, protože "\\C++ " je řídicí znak.)

*lpszLocale*<br/>
Řetězcový výraz, který slouží k zadání pořadí řazení pro vytvoření databáze. Výchozí hodnota je `dbLangGeneral`. Možné hodnoty jsou:

- `dbLangGeneral` angličtinu, němčinu, francouzštině, portugalštině, italštině a moderní španělštině

- `dbLangArabic` Arabština

- `dbLangCyrillic` Ruština

- `dbLangCzech` Čeština

- `dbLangDutch` holandština

- `dbLangGreek` Řečtina

- `dbLangHebrew` Hebrejština

- `dbLangHungarian` Maďarština

- `dbLangIcelandic` Island

- `dbLangNordic` Severské jazyky (jenom Microsoft Jet Database Engine verze 1,0)

- `dbLangNorwdan` norština a Dánština

- `dbLangPolish` Polština

- `dbLangSpanish` tradiční španělština

- `dbLangSwedfin` švédština a finština

- `dbLangTurkish` turecké

*dwOptions*<br/>
Celé číslo, které označuje jednu nebo více možností. Možné hodnoty jsou:

- `dbEncrypt` vytvořit zašifrovanou databázi.

- `dbVersion10` vytvořit databázi pomocí databáze Microsoft Jet verze 1,0.

- `dbVersion11` vytvořit databázi pomocí databáze Microsoft Jet verze 1,1.

- `dbVersion20` vytvořit databázi pomocí databáze Microsoft Jet verze 2,0.

- `dbVersion30` vytvořit databázi pomocí databáze Microsoft Jet verze 3,0.

Pokud vynecháte šifrovací konstantu, vytvoří se nezašifrovaná databáze. Můžete zadat jenom jednu konstantu verze. Pokud vynecháte konstantu verze, vytvoří se databáze používající databázi Microsoft Jet verze 3,0.

> [!CAUTION]
>  Pokud není databáze šifrována, je možné, že i když implementujete zabezpečení uživatele nebo hesla, můžete přímo číst soubor binárního disku, který tvoří databázi.

### <a name="remarks"></a>Poznámky

`Create` vytvoří databázový soubor a základní databázový objekt DAO a inicializuje C++ objekt. Objekt je připojen do kolekce databází přidruženého pracovního prostoru. Databázový objekt je v otevřeném stavu. Nevolejte `Open*` po `Create`.

> [!NOTE]
>  Pomocí `Create`můžete vytvořit pouze Microsoft Jet (. MDB) databáze. Nemůžete vytvořit databáze ISAM nebo databáze ODBC.

##  <a name="createrelation"></a>CDaoDatabase::CreateRelation

Voláním této členské funkce navažte relaci mezi jedním nebo více poli v primární tabulce v databázi a jedním nebo více poli v cizí tabulce (Další tabulka v databázi).

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

*lpszName*<br/>
Jedinečný název objektu vztahu Název musí začínat písmenem a může obsahovat maximálně 40 znaků. Může obsahovat číslice a podtržítka, ale nemůže obsahovat interpunkční znaménka nebo mezery.

*lpszTable*<br/>
Název primární tabulky v relaci. Pokud tabulka neexistuje, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Název cizí tabulky v relaci. Pokud tabulka neexistuje, knihovna MFC vyvolá výjimku typu `CDaoException`.

*lAttributes*<br/>
Dlouhá hodnota, která obsahuje informace o typu vztahu. Tuto hodnotu můžete použít k prosazování referenční integrity mimo jiné. Můžete použít bitový operátor OR ( **&#124;** ) pro kombinování libovolné z následujících hodnot (Pokud je to kombinace smysl):

- Vztah `dbRelationUnique` je 1 – jeden.

- Relace `dbRelationDontEnforce` není vynutila (bez referenční integrity).

- Relace `dbRelationInherited` existuje v neaktuální databázi, která obsahuje dvě připojené tabulky.

- Aktualizace `dbRelationUpdateCascade` budou kaskádovitě (Další informace najdete v části poznámky).

- Odstranění `dbRelationDeleteCascade` se kaskádová.

*lpszField*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje název pole v primární tabulce (s názvem *lpszTable*).

*lpszForeignField*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje název pole v cizí tabulce (s názvem *lpszForeignTable*).

*relinfo*<br/>
Odkaz na objekt [CDaoRelationInfo –](../../mfc/reference/cdaorelationinfo-structure.md) , který obsahuje informace o relaci, kterou chcete vytvořit.

### <a name="remarks"></a>Poznámky

Vztah nemůže zahrnovat dotaz nebo připojenou tabulku z externí databáze.

První verzi funkce použijte, pokud relace zahrnuje jedno pole v každé z obou tabulek. Druhá verze se používá v případě, že relace zahrnuje více polí. Maximální počet polí v relaci je 14.

Tato akce vytvoří základní objekt vztahu DAO, ale jedná se o podrobnosti implementace knihovny MFC, protože zapouzdření objektů v objektu knihovny MFC je obsaženo v rámci třídy `CDaoDatabase`. Knihovna MFC neposkytuje třídu pro vztahy.

Pokud nastavíte atributy objektu relace pro aktivaci operací kaskády, databázový stroj automaticky aktualizuje nebo odstraní záznamy v jedné nebo více dalších tabulkách, pokud jsou provedeny změny v souvisejících tabulkách primárního klíče.

Předpokládejme například, že vytvoříte relaci kaskádového odstranění mezi tabulkou Zákazníci a tabulkou objednávky. Když odstraníte záznamy z tabulky Customers, odstraní se i záznamy v tabulce Orders týkající se tohoto zákazníka. Kromě toho platí, že pokud vytvoříte relace mezi tabulkami Objednávky a dalšími tabulkami, budou záznamy z těchto tabulek automaticky odstraněny při odstraňování záznamů z tabulky Customers.

Související informace naleznete v tématu "metoda CreateRelation" v nápovědě k rozhraní DAO.

##  <a name="deletequerydef"></a>CDaoDatabase::D eleteQueryDef

Tuto členskou funkci volejte pro odstranění zadaného dotazu querydef – z kolekce QueryDefs objektu `CDaoDatabase`.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název uloženého dotazu, který se má odstranit

### <a name="remarks"></a>Poznámky

Následně tento dotaz již není v databázi definován.

Informace o vytváření objektů querydef naleznete v tématu Třída [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Objekt querydef se při vytváření objektu `CDaoQueryDef` přiřadí k určitému objektu `CDaoDatabase` a předá ho ukazatelem na databázový objekt.

##  <a name="deleterelation"></a>CDaoDatabase::D eleteRelation

Chcete-li odstranit existující relaci z kolekce vztahů objektu databáze, zavolejte tuto členskou funkci.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název vztahu, který se má odstranit

### <a name="remarks"></a>Poznámky

Relace následně již neexistuje.

Související informace naleznete v tématu "odstranění metody" v nápovědě rozhraní DAO.

##  <a name="deletetabledef"></a>CDaoDatabase::D eleteTableDef

Zavolejte tuto členskou funkci, aby se odstranila zadaná tabulka a veškerá její data z kolekce TableDefs objektu `CDaoDatabase`.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název tabledef, který se má odstranit

### <a name="remarks"></a>Poznámky

Následně už tato tabulka není v databázi definovaná.

> [!NOTE]
>  Pokud chcete odstranit systémové tabulky, buďte velmi opatrní.

Informace o vytváření objektů tabledef naleznete v tématu Class [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Objekt tabledef se při vytváření objektu `CDaoTableDef` přiřadí k určitému objektu `CDaoDatabase` a předá ho ukazatelem na databázový objekt.

Související informace naleznete v tématu "odstranění metody" v nápovědě rozhraní DAO.

##  <a name="execute"></a>CDaoDatabase:: Execute

Zavolejte tuto členskou funkci pro spuštění dotazu akce nebo provedení příkazu jazyka SQL v databázi.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*Ipszsql*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující platný příkaz SQL, který má být proveden.

*nOptions*<br/>
Celé číslo, které určuje možnosti týkající se integrity dotazu. Bitový operátor OR ( **&#124;** ) můžete použít ke kombinování libovolné z následujících konstant (za předpokladu, že nebudete kombinovat `dbInconsistent` s `dbConsistent`):

- `dbDenyWrite` odepřít oprávnění k zápisu jiným uživatelům.

- `dbInconsistent` (výchozí) nekonzistentní aktualizace.

- `dbConsistent` konzistentní aktualizace.

- `dbSQLPassThrough` průchod SQL. Způsobí, že příkaz SQL bude předán zdroji dat ODBC ke zpracování.

- `dbFailOnError` vrátit aktualizace, pokud dojde k chybě.

- `dbSeeChanges` vygenerovat běhovou chybu, pokud jiný uživatel mění data, která upravujete.

> [!NOTE]
>  Pokud jsou zahrnuté `dbInconsistent` i `dbConsistent`, nebo pokud není zahrnutá ani jedna, je výsledkem výchozí hodnota. Vysvětlení těchto konstant naleznete v tématu "Execute Method" v nápovědě rozhraní DAO.

### <a name="remarks"></a>Poznámky

`Execute` funguje pouze pro akční dotazy nebo předávací dotazy SQL, které nevracejí výsledky. Pro vybrané dotazy nefunguje, které vracejí záznamy.

Definici a informace o dotazech na akce naleznete v tématech "akční dotaz" a "spustit metodu" v nápovědě rozhraní DAO.

> [!TIP]
>  Vzhledem k syntakticky správnému příkazu SQL a správným oprávněním se členská funkce `Execute` nezdařila, i když není možné upravovat nebo odstraňovat jeden řádek. Proto vždy použijte možnost `dbFailOnError` při použití členské funkce `Execute` ke spuštění dotazu Update nebo DELETE. Tato možnost způsobí, že knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md) a vrátí všechny úspěšné změny, pokud nějaký ovlivněný záznam je uzamčen a nelze jej aktualizovat ani odstranit. Všimněte si, že můžete vždy volat `GetRecordsAffected`, abyste viděli, kolik záznamů bylo ovlivněno.

Zavolejte členskou funkci [GetRecordsAffected](#getrecordsaffected) objektu Database, abyste určili počet záznamů ovlivněných nejnovějším voláním `Execute`. `GetRecordsAffected` například vrátí informace o počtu odstraněných, aktualizovaných nebo vložených záznamů při provádění dotazu akce. Vrácený počet nebude odrážet změny v souvisejících tabulkách, pokud jsou v platnosti kaskádové aktualizace nebo odstraňování.

`Execute` nevrací sadu záznamů. Použití `Execute` u dotazu, který vybere záznamy, způsobí, že knihovna MFC vyvolá výjimku typu `CDaoException`. (Neexistuje žádná `ExecuteSQL` členská funkce podobná `CDatabase::ExecuteSQL`.)

##  <a name="getconnect"></a>CDaoDatabase:: GetConnect

Zavolejte tuto členskou funkci pro načtení připojovacího řetězce použitého pro připojení objektu `CDaoDatabase` k databázi ODBC nebo ISAM.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

Připojovací řetězec, pokud bylo na zdroji dat ODBC úspěšně voláno [otevření](#open) ; v opačném případě prázdný řetězec. Pro Microsoft Jet (. MDB) databáze je řetězec vždy prázdný, pokud jej nenastavíte pro použití s možností `dbSQLPassThrough` použitou s členskou funkcí [Execute](#execute) nebo použitým v otevření sady záznamů.

### <a name="remarks"></a>Poznámky

Řetězec poskytuje informace o zdroji otevřené databáze nebo databázi použité v předávacím dotazu. Připojovací řetězec se skládá z specifikátoru typu databáze a nula nebo více parametrů oddělených středníky.

> [!NOTE]
>  Použití tříd knihovny MFC DAO pro připojení ke zdroji dat prostřednictvím rozhraní ODBC je méně efektivní než připojení přes připojenou tabulku.

> [!NOTE]
>  Připojovací řetězec se používá k předávání dalších informací do ODBC a určitých ovladačů ISAM podle potřeby. Nepoužívá se pro. Databáze MDB. Pro základní tabulky databáze Microsoft Jet je připojovací řetězec prázdný řetězec ("") s výjimkou případů, kdy jej použijete pro předávací dotaz SQL, jak je popsáno v části vrácená hodnota výše.

Popis způsobu vytvoření připojovacího řetězce naleznete v tématu [otevřená](#open) členská funkce. Jakmile je připojovací řetězec nastaven ve `Open` volání, můžete ho později použít ke kontrole nastavení pro určení typu, cesty, ID uživatele, hesla nebo zdroje dat ODBC databáze.

##  <a name="getname"></a>CDaoDatabase:: GetName

Voláním této členské funkce načtěte název aktuálně otevřené databáze, což je název existujícího databázového souboru nebo název registrovaného zdroje dat ODBC.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta a název souboru databáze, pokud je úspěšná; jinak prázdná [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Pokud vaše síť podporuje konvence Uniform Naming Convention (UNC), můžete také zadat síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ". (Pro řetězcové literály jsou vyžadovány dvojité zpětné lomítko, protože "\\C++ " je řídicí znak.)

Například můžete chtít zobrazit tento název v záhlaví. Pokud při načítání názvu dojde k chybě, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  Pro lepší výkon při použití externích databází doporučujeme připojit tabulky externích databází k databázi Microsoft Jet (. MDB) místo přímého připojení ke zdroji dat.

Typ databáze je označen souborem nebo adresářem, na který odkazuje cesta, následovně:

|Cesta odkazuje na...|Typ databáze|
|--------------------------|-------------------|
|. Soubor MDB|Databáze Microsoft Jet (Microsoft Access)|
|Adresář, který obsahuje. Soubory DBF|databáze dBASE|
|Adresář, který obsahuje. Soubor XLS|Databáze Microsoft Excelu|
|Adresář, který obsahuje. Soubory: PDX|Databáze Paradox|
|Adresář, který obsahuje vhodně naformátované soubory databáze textu|Databáze formátu textu|

Pro databáze ODBC, jako je například SQL Server a Oracle, Určuje připojovací řetězec databáze název zdroje dat (DSN), který je zaregistrován rozhraním ODBC.

##  <a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount

Voláním této členské funkce načtěte počet dotazů, které jsou definovány v kolekci QueryDefs databáze.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet dotazů, které jsou definovány v databázi.

### <a name="remarks"></a>Poznámky

`GetQueryDefCount` je užitečné, pokud potřebujete projít všemi QueryDefs v kolekci QueryDefs. Informace o daném dotazu v kolekci najdete v tématu [GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo

Voláním této členské funkce získáte různé druhy informací o dotazu definovaném v databázi.

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
Index předdefinovaného dotazu v kolekci QueryDefs databáze pro vyhledávání podle indexu.

*querydefinfo*<br/>
Odkaz na objekt [CDaoQueryDefInfo –](../../mfc/reference/cdaoquerydefinfo-structure.md) , který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o sadě záznamů se mají načíst. Dostupné možnosti jsou zde uvedeny spolu s tím, co způsobí, že funkce vrátí informace o sadě záznamů:

- AFX_DAO_PRIMARY_INFO (výchozí) název zadejte

- AFX_DAO_SECONDARY_INFO primární informace plus: datum vytvoření, datum poslední aktualizace, vrácení záznamů, aktualizovatelné

- AFX_DAO_ALL_INFO primární a sekundární informace plus: SQL, Connect, ODBCTimeout

*lpszName*<br/>
Řetězec obsahující název dotazu definovaný v databázi pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jsou k dispozici dvě verze funkce, takže můžete vybrat dotaz buď podle indexu v kolekci QueryDefs databáze, nebo podle názvu dotazu.

Popis informací vrácených v *querydefinfo*najdete v tématu struktura [CDaoQueryDefInfo –](../../mfc/reference/cdaoquerydefinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Pokud si vyžádáte jednu úroveň informací, dostanete také předchozí úrovně informací.

##  <a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout

Zavolejte tuto členskou funkci, aby se načetl aktuální počet sekund, který se povolí před vypršením časového limitu dalších operací na připojené databázi.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Krátké celé číslo obsahující hodnotu časového limitu v sekundách.

### <a name="remarks"></a>Poznámky

Kvůli problémům s přístupem k síti, nadměrnému zpracování dotazů a tak dále může dojít k vypršení časového limitu operace. I když nastavení platí, má vliv na všechny sady záznamů přidružené k tomuto `CDaoDatabase` objektu, což má vliv na všechny operace otevřít, přidat nové, aktualizovat a odstranit. Aktuální nastavení časového limitu můžete změnit voláním [SetQueryTimeout](#setquerytimeout). Změna hodnoty časového limitu dotazu pro sadu záznamů po otevření nemění hodnotu sady záznamů. Například následné operace [přesunu](../../mfc/reference/cdaorecordset-class.md#move) nepoužívají novou hodnotu. Výchozí hodnota je zpočátku nastavena při inicializaci databázového stroje.

Výchozí hodnota pro vypršení časového limitu dotazu je pořízena z registru systému Windows. Pokud není nastavené žádné nastavení registru, výchozí hodnota je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, nedojde k žádnému vypršení časového limitu. a komunikace s databází může přestat reagovat. Toto chování může být užitečné při vývoji. Pokud se volání nezdařilo, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Související informace najdete v tématu "vlastnost QueryTimeout" v nápovědě k rozhraní DAO.

##  <a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected

Zavolejte tuto členskou funkci pro určení počtu záznamů ovlivněných nejnovějším voláním členské funkce [Execute](#execute) .

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Návratová hodnota

Dlouhé celé číslo obsahující počet ovlivněných záznamů.

### <a name="remarks"></a>Poznámky

Vrácená hodnota zahrnuje počet záznamů, které byly odstraněny, aktualizovány nebo vloženy dotazem akce spuštěným pomocí `Execute`. Vrácený počet nebude odrážet změny v souvisejících tabulkách, pokud jsou v platnosti kaskádové aktualizace nebo odstraňování.

Související informace najdete v tématu "vlastnost RecordsAffected" v nápovědě k rozhraní DAO.

##  <a name="getrelationcount"></a>CDaoDatabase::GetRelationCount

Zavolejte tuto členskou funkci, aby se získal počet vztahů definovaných mezi tabulkami v databázi.

```
short GetRelationCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet vztahů definovaných mezi tabulkami v databázi.

### <a name="remarks"></a>Poznámky

`GetRelationCount` je užitečné v případě, že potřebujete projít všemi definovanými relacemi v kolekci vztahů databáze. Chcete-li získat informace o dané relaci v kolekci, přečtěte si téma [GetRelationInfo](#getrelationinfo).

Chcete-li ilustrovat koncept vztahu, vezměte v úvahu tabulku dodavatelé a tabulku Products, která může mít relaci 1: n. V této relaci může jeden dodavatel poskytovat více než jeden produkt. Další relace jsou 1:1 a m:n.

##  <a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo

Voláním této členské funkce získáte informace o zadané relaci v kolekci vztahů databáze.

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
Index objektu relace v kolekci vztahů databáze pro vyhledávání podle indexu.

*relinfo*<br/>
Odkaz na objekt [CDaoRelationInfo –](../../mfc/reference/cdaorelationinfo-structure.md) , který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují informace o relaci, která se má načíst. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že se funkce vrátí k relaci:

- AFX_DAO_PRIMARY_INFO (výchozí) název, tabulka, cizí tabulka

- AFX_DAO_SECONDARY_INFO atributy, informace o poli

Informace o poli je objekt [CDaoRelationFieldInfo –](../../mfc/reference/cdaorelationfieldinfo-structure.md) obsahující pole z primární tabulky zahrnuté ve vztahu.

*lpszName*<br/>
Řetězec obsahující název objektu relace pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Dvě verze této funkce poskytují přístup buď podle indexu, nebo podle názvu. Popis informací vrácených v *relinfo*najdete v tématu struktura [CDaoRelationInfo –](../../mfc/reference/cdaorelationinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Pokud si vyžádáte informace na jedné úrovni, získáte také informace na jakékoli předchozí úrovni.

> [!NOTE]
>  Pokud nastavíte atributy objektu relace pro aktivaci operací na kaskádě (`dbRelationUpdateCascades` nebo `dbRelationDeleteCascades`), databázový stroj Microsoft Jet automaticky aktualizuje nebo odstraní záznamy v jedné nebo více dalších tabulkách, pokud jsou provedeny změny v souvisejících tabulkách primárního klíče. Předpokládejme například, že vytvoříte relaci kaskádového odstranění mezi tabulkou Zákazníci a tabulkou objednávky. Když odstraníte záznamy z tabulky Customers, odstraní se i záznamy v tabulce Orders týkající se tohoto zákazníka. Kromě toho platí, že pokud vytvoříte relace mezi tabulkami Objednávky a dalšími tabulkami, budou záznamy z těchto tabulek automaticky odstraněny při odstraňování záznamů z tabulky Customers.

##  <a name="gettabledefcount"></a>CDaoDatabase::GetTableDefCount

Zavolejte tuto členskou funkci pro načtení počtu tabulek definovaných v databázi.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet TableDefs definovaných v databázi.

### <a name="remarks"></a>Poznámky

`GetTableDefCount` je užitečné, pokud potřebujete projít všemi TableDefs v kolekci TableDefs databáze. Informace o dané tabulce v kolekci najdete v tématu [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>CDaoDatabase::GetTableDefInfo

Tuto členskou funkci volejte pro získání různých druhů informací o tabulce definované v databázi.

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
Index objektu tabledef v kolekci TableDefs databáze pro vyhledávání podle indexu.

*tabledefinfo*<br/>
Odkaz na objekt [CDaoTableDefInfo –](../../mfc/reference/cdaotabledefinfo-structure.md) , který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o tabulce se mají načíst. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že se funkce vrátí k relaci:

- AFX_DAO_PRIMARY_INFO (výchozí) název, aktualizovatelné atributy

- AFX_DAO_SECONDARY_INFO primární informace plus: datum vytvoření, datum poslední aktualizace, název zdrojové tabulky, připojit

- AFX_DAO_ALL_INFO primární a sekundární informace plus: ověřovací pravidlo, text ověření, počet záznamů

*lpszName*<br/>
Název objektu tabledef pro vyhledávání podle názvu

### <a name="remarks"></a>Poznámky

Jsou zadány dvě verze funkce, takže můžete vybrat tabulku podle indexu v kolekci TableDefs databáze nebo podle názvu tabulky.

Popis informací vrácených v *tabledefinfo*najdete v tématu struktura [CDaoTableDefInfo –](../../mfc/reference/cdaotabledefinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Pokud si vyžádáte informace na jedné úrovni, získáte informace také pro všechny předchozí úrovně.

> [!NOTE]
>  Možnost AFX_DAO_ALL_INFO poskytuje informace, které mohou být pomalé pro získání. V takovém případě může být počítání záznamů v tabulce velmi časově náročné, pokud existuje mnoho záznamů.

##  <a name="getversion"></a>CDaoDatabase:: GetVersion

Voláním této členské funkce určíte verzi databázového souboru Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) , která označuje verzi databázového souboru přidruženého k objektu.

### <a name="remarks"></a>Poznámky

Vrácená hodnota představuje číslo verze ve formátu "hlavní_verze. podverze"; například "3,0". Číslo verze produktu (například 3,0) se skládá z čísla verze (3), tečky a čísla vydání (0). Verze do data jsou 1,0, 1,1, 2,0 a 3,0.

Související informace naleznete v tématu "vlastnost verze" v nápovědě rozhraní DAO.

##  <a name="isopen"></a>CDaoDatabase:: Open

Voláním této členské funkce určíte, zda je objekt `CDaoDatabase` v databázi aktuálně otevřen.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt `CDaoDatabase` aktuálně otevřený; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="m_pdaodatabase"></a>CDaoDatabase:: m_pDAODatabase

Obsahuje ukazatel na rozhraní OLE pro databázový objekt DAO základní objekt `CDaoDatabase`.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte v případě, že potřebujete získat přímý přístup k rozhraní DAO.

Informace o přímém volání rozhraní DAO naleznete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>CDaoDatabase:: m_pWorkspace

Obsahuje ukazatel na objekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , který obsahuje databázový objekt.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte v případě, že potřebujete získat přímý přístup k pracovnímu prostoru – například k získání ukazatelů na jiné databázové objekty v kolekci databází v pracovním prostoru.

##  <a name="open"></a>CDaoDatabase:: Open

Chcete-li inicializovat nově vytvořený `CDaoDatabase` objekt, který představuje existující databázi, je nutné zavolat tuto členskou funkci.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězcový výraz, který je název existující služby Microsoft Jet (. MDB) soubor databáze. Pokud název souboru má příponu, je vyžadován. Pokud vaše síť podporuje konvence UNC (Uniform Naming Convention), můžete také zadat síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB ". (Pro řetězcové literály jsou vyžadovány dvojité zpětné lomítko, protože "\\C++ " je řídicí znak.)

Při použití *lpszName*se vztahují k určitým hlediskům. Pokud:

- Odkazuje na databázi, která je již otevřena pro výhradní přístup jiným uživatelem, knihovna MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Zachytit tuto výjimku, aby uživatel věděli, že databáze není k dispozici.

- Je prázdný řetězec ("") a *lpszConnect* je "ODBC;", zobrazí se dialogové okno se seznamem všech registrovaných názvů zdrojů dat ODBC, aby uživatel mohl vybrat databázi. Měli byste se vyhnout přímému připojení ke zdrojům dat ODBC; místo toho použijte připojenou tabulku.

- V opačném případě neodkazuje na existující databázi ani na platný název zdroje dat ODBC, knihovna MFC vyvolá výjimku typu `CDaoException`.

> [!NOTE]
>  Podrobnosti o kódech chyb rozhraní DAO naleznete v tématu DAOERR. Soubor H. Související informace najdete v nápovědě k rozhraní DAO v tématu "chyby při přístupu k datům v tomto případě".

*bExclusive*<br/>
Logická hodnota, která má hodnotu TRUE, pokud má být databáze otevřena pro výhradní (nesdílený) přístup a hodnotu FALSE, pokud má být databáze otevřena pro sdílený přístup. Pokud tento argument vynecháte, otevře se databáze pro sdílený přístup.

*bReadOnly*<br/>
Logická hodnota, která má hodnotu TRUE, pokud má být databáze otevřena pro přístup jen pro čtení a FALSE, pokud má být databáze otevřena pro přístup pro čtení a zápis. Pokud tento argument vynecháte, otevře se databáze pro přístup pro čtení a zápis. Všechny závislé sady záznamů dědí tento atribut.

*lpszConnect*<br/>
Řetězcový výraz, který se používá pro otevření databáze. Tento řetězec představuje argumenty připojení rozhraní ODBC. K poskytnutí zdrojového řetězce je nutné, abyste zadali argumenty Exclusive a jen pro čtení. Pokud je databáze Microsoft Jet Database (. MDB), tento řetězec je prázdný (""). Syntaxe výchozí hodnoty – **_T**("") – poskytuje přenositelnost pro kódování Unicode a také ANSI sestavení vaší aplikace.

### <a name="remarks"></a>Poznámky

`Open` přidruží databázi k základnímu objektu DAO. Objekt databáze nelze použít k sestavování objektů Recordset, tabledef nebo querydef, dokud není inicializována. `Open` připojí objekt databáze k kolekci databází přidruženého pracovního prostoru.

Použijte parametry následujícím způsobem:

- Pokud otevíráte Microsoft Jet (. MDB) databáze, použijte parametr *lpszName* a předejte prázdný řetězec pro parametr *lpszConnect* nebo předejte řetězec hesla formuláře "; PWD = Password, pokud je databáze chráněná heslem (. Pouze databáze MDB).

- Pokud otevíráte zdroj dat ODBC, předejte platný připojovací řetězec ODBC v *lpszConnect* a prázdný řetězec v *lpszName*.

Související informace naleznete v tématu "Metoda OpenDatabase" v nápovědě k rozhraní DAO.

> [!NOTE]
>  Pro lepší výkon při přístupu k externím databázím, včetně databází ISAM a zdrojů dat ODBC, se doporučuje připojit tabulky externích databází k databázi Microsoft Jet Engine (. MDB) místo přímého připojení ke zdroji dat.

Je možné, že se pokus o připojení vyprší, pokud například není k dispozici hostitel DBMS. Pokud se pokus o připojení nezdaří, `Open` vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).

Zbývající poznámky platí pouze pro databáze ODBC:

Pokud se jedná o databázi rozhraní ODBC a parametry ve volání `Open` neobsahují dostatek informací pro vytvoření připojení, ovladač ODBC otevře dialogové okno, které získá informace potřebné od uživatele. Při volání `Open`je připojovací řetězec *lpszConnect*uložen soukromě a je k dispozici voláním členské funkce [GetConnect](#getconnect) .

Pokud chcete, můžete otevřít vlastní dialogové okno před voláním `Open` a získat informace od uživatele, jako je třeba heslo, a pak tyto informace přidat do připojovacího řetězce, který předáte do `Open`. Nebo můžete chtít uložit připojovací řetězec, který předáte (například v registru Windows), abyste ho mohli znovu použít při příštím volání `Open` na objekt `CDaoDatabase`.

Připojovací řetězec můžete použít také pro více úrovní autorizace přihlášení (každý pro jiný objekt `CDaoDatabase`) nebo pro předávání jiných informací specifických pro databázi.

##  <a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout

Tuto členskou funkci zavolejte, pokud chcete přepsat výchozí počet sekund, který bude povolen před tím, než dojde k vypršení časového limitu dalších operací s připojenou databází.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSeconds*<br/>
Počet sekund povolených před vypršením časového limitu dotazu.

### <a name="remarks"></a>Poznámky

Operace může vyprší časový limit kvůli problémům s přístupem k síti, nadměrnému času zpracování dotazů atd. Chcete-li změnit hodnotu časového limitu dotazu, zavolejte `SetQueryTimeout` před otevřením sady záznamů nebo před voláním funkce [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [Update](../../mfc/reference/cdaorecordset-class.md#update)nebo [Delete](../../mfc/reference/cdaorecordset-class.md#delete) sady záznamů. Toto nastavení má vliv na všechna následující [otevřená](../../mfc/reference/cdaorecordset-class.md#open)`AddNew`, `Update`a `Delete` volání všech sad záznamů přidružených k tomuto `CDaoDatabase` objektu. Změna hodnoty časového limitu dotazu pro sadu záznamů po otevření nemění hodnotu sady záznamů. Například následné operace [přesunu](../../mfc/reference/cdaorecordset-class.md#move) nepoužívají novou hodnotu.

Výchozí hodnota pro vypršení časového limitu dotazu je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, nedojde k žádnému vypršení časového limitu. komunikace s databází může přestat reagovat. Toto chování může být užitečné při vývoji.

Související informace najdete v tématu "vlastnost QueryTimeout" v nápovědě k rozhraní DAO.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
