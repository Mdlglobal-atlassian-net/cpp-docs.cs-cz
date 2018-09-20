---
title: CDaoDatabase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6cf84b2e5709a4ac31965501005b5260499a3213
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408801"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase – třída

Představuje připojení k databázi, pomocí které můžete pracovat s daty.

## <a name="syntax"></a>Syntaxe

```
class CDaoDatabase : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Vytvoří `CDaoDatabase` objektu. Volání `Open` objekt připojení k databázi.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoDatabase::CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud databáze podporuje transakce.|
|[CDaoDatabase::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud `CDaoDatabase` aktualizovatelný objekt (ne jen pro čtení).|
|[CDaoDatabase::Close](#close)|Zavře připojení k databázi.|
|[CDaoDatabase::Create](#create)|Vytvoří základní objekt databáze rozhraní DAO a inicializuje `CDaoDatabase` objektu.|
|[CDaoDatabase::CreateRelation](#createrelation)|Definuje nový vztah mezi tabulkami v databázi.|
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Odstraní objekt querydef uloží do databáze querydefs – kolekce.|
|[CDaoDatabase::DeleteRelation](#deleterelation)|Odstraní existující relace mezi tabulkami v databázi.|
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Odstraní definici tabulky v databázi. Tím se odstraní skutečné tabulky a všechna jeho data.|
|[CDaoDatabase::Execute](#execute)|Spustí dotaz akce. Volání `Execute` pro dotaz, který vrátí výsledky, dojde k výjimce.|
|[CDaoDatabase::GetConnect](#getconnect)|Vrátí připojovací řetězec použitý pro připojení `CDaoDatabase` objektu do databáze. Používá se pro ODBC.|
|[CDaoDatabase::GetName](#getname)|Vrátí název databáze aktuálně používá.|
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Vrátí počet dotazů, které jsou definovány pro databázi.|
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Vrátí informace o zadaný dotaz definovaný v databázi.|
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Vrátí počet sekund, po kterou databázi dotazovat operace vyprší časový limit. Ovlivňuje všechny následné otevřít, přidat nový, aktualizovat a upravovat operací a dalším operacím nad zdroje dat ODBC (pouze), jako `Execute` volání.|
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů, které jsou ovlivněny poslední aktualizace, upravit nebo přidat operaci nebo voláním `Execute`.|
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Vrátí počet vztahy definované mezi tabulkami v databázi.|
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Vrátí informace o zadaný vztah definované mezi tabulkami v databázi.|
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Vrátí počet tabulek definovaných v databázi.|
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Vrátí informace o zadané tabulky v databázi.|
|[CDaoDatabase::GetVersion](#getversion)|Vrátí verzi databázového stroje, který je přidružený k databázi.|
|[CDaoDatabase::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud `CDaoDatabase` objektu je aktuálně připojena k databázi.|
|[CDaoDatabase::Open](#open)|Naváže připojení k databázi.|
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po kterou databázi dotazovat operace (v ODBC pouze zdroje dat) vyprší časový limit. Ovlivňuje všechny následné otevřít, přidat nové, aktualizovat a operace odstranění.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Ukazatel na základní objekt rozhraní DAO databáze.|
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Ukazatel [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md) objekt, který obsahuje databázi a definuje svého oboru transakce.|

## <a name="remarks"></a>Poznámky

Informace o databázi formáty podporované, najdete v článku [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) členskou funkci. Můžete mít jednu nebo více `CDaoDatabase` objekty v každém okamžiku aktivní v daném "pracovní prostor," reprezentován [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md) objektu. Pracovním prostoru udržuje kolekci otevřít databázové objekty, názvem databáze kolekce.

> [!NOTE]
>  Třídy databází MFC DAO se liší od databázových tříd MFC založených na rozhraní ODBC. Všechny názvy tříd DAO databáze mají předponu "CDao". Třída `CDaoDatabase` poskytuje rozhraní podobný třídě ODBC [CDatabase](../../mfc/reference/cdatabase-class.md). Hlavní rozdíl je, že `CDatabase` DBMS přistupuje prostřednictvím připojení ODBC (Open Database) a ovladač ODBC pro tento systém DBMS. `CDaoDatabase` přistupuje k datům prostřednictvím objekt DAO (Data Access) založená na databázovém stroji Microsoft Jet. Obecně třídy knihovny MFC rozhraní DAO podle podporují více než třídy knihovny MFC založená na rozhraní ODBC; třídy založené na rozhraní DAO můžou přistupovat k datům, včetně prostřednictvím ovladače rozhraní ODBC, prostřednictvím vlastní databázového stroje. Třídy založené na rozhraní DAO také podporu jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy rozhraní, aniž byste museli DAO volat přímo.

## <a name="usage"></a>Použití

Při vytváření záznamů objektů lze implicitně, vytváření databázových objektů. Ale můžete také vytvořit databázové objekty explicitně. Chcete-li použít existující databázi explicitně s `CDaoDatabase`, proveďte jednu z následujících akcí:

- Vytvoření `CDaoDatabase` objekt předání ukazatele na otevřený [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md) objektu.

- Nebo vytvořit `CDaoDatabase` objektu bez zadání pracovního prostoru (MFC vytvoří objekt dočasný pracovní prostor).

Chcete-li vytvořit nový Microsoft Jet (. Databáze MDB), vytvořit `CDaoDatabase` objektu a volání jeho [vytvořit](#create) členskou funkci. Proveďte *není* volání `Open` po `Create`.

Otevřete existující databázi, vytvoření `CDaoDatabase` objektu a volání jeho [otevřete](#open) členskou funkci.

Některé z následujících postupů připojí databázový objekt DAO do kolekce databází pracovní prostor a otevře připojení k datům. Když potom vytvoříte [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md), nebo [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md) objekty pro provozování na připojeném databázovém předat konstruktory pro tyto objekty ukazatel na váš `CDaoDatabase` objektu. Volat po dokončení práce připojení [Zavřít](#close) členské funkce a zničit `CDaoDatabase` objektu. `Close` Zavře všechny sady záznamů, které nebyly uzavřeny dříve.

## <a name="transactions"></a>Transakce

Zpracování transakcí databáze je zadaný na úrovni pracovního prostoru – najdete v článku [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), a [vrácení zpět](../../mfc/reference/cdaoworkspace-class.md#rollback) členské funkce třídy `CDaoWorkspace` .

## <a name="odbc-connections"></a>Připojení ODBC

Připojení externí tabulky, které Microsoft Jet je doporučený postup pro práci se zdroji dat rozhraní ODBC (. Databáze MDB).

## <a name="collections"></a>Kolekce

Každé databázi udržuje vlastní kolekce tabledef, querydef, záznamů a objekty relace. Třída `CDaoDatabase` poskytuje členské funkce pro manipulaci s těmito objekty.

> [!NOTE]
>  Objekty jsou uloženy v rozhraní DAO, není v objektu databáze knihovny MFC. Knihovna MFC poskytuje třídy pro objekty tabledef querydef a sady záznamů, ale ne pro objekty relace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDaoDatabase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="cantransact"></a>  CDaoDatabase::CanTransact

Voláním této členské funkce k určení, zda databáze umožňuje transakce.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud databáze podporuje transakce; jinak 0.

### <a name="remarks"></a>Poznámky

Transakce se spravují v pracovním prostoru vaší databáze.

##  <a name="canupdate"></a>  CDaoDatabase::CanUpdate

Voláním této členské funkce k určení, zda `CDaoDatabase` objektu umožňuje instalaci aktualizací.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CDaoDatabase` objektu umožňuje instalaci aktualizací; jinak 0 označující buď, kterou jste předány nastavena hodnota TRUE v *bReadOnly* při otevření `CDaoDatabase` objektu nebo že samotná databáze je jen pro čtení. Zobrazit [otevřít](#open) členskou funkci.

### <a name="remarks"></a>Poznámky

Informace o možnosti aktualizace databáze naleznete v tématu "Aktualizovat vlastnost" v nápovědě k DAO.

##  <a name="cdaodatabase"></a>  CDaoDatabase::CDaoDatabase

Vytvoří `CDaoDatabase` objektu.

```
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```

### <a name="parameters"></a>Parametry

*pWorkspace*<br/>
Ukazatel `CDaoWorkspace` objekt, který bude obsahovat nový objekt databáze. Pokud přijmete výchozí hodnotu NULL, konstruktor vytvoří dočasnou `CDaoWorkspace` objekt, který používá rozhraní DAO výchozího pracovního prostoru. Můžete získat ukazatel objektu pracovního prostoru prostřednictvím [m_pWorkspace](#m_pworkspace) datový člen.

### <a name="remarks"></a>Poznámky

Po vytvoření objektu, pokud vytváříte nový Microsoft Jet (. MDB) databáze, volání objektu [vytvořit](#create) členskou funkci. Pokud jste místo toho otevřít existující databáze, volání objektu [otevřít](#open) členskou funkci.

Jakmile skončíte s objektem, byste měli volat jeho [Zavřít](#close) členské funkce a pak zničilo `CDaoDatabase` objektu.

Možná pro vás bude vhodné vložit `CDaoDatabase` objekt ve své třídě dokumentu.

> [!NOTE]
>  A `CDaoDatabase` objekt se vytvoří také implicitně případě otevíráte [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt bez předání ukazatele na existující `CDaoDatabase` objektu. Tento databázový objekt je zavřený při zavření objektu sady záznamů.

##  <a name="close"></a>  CDaoDatabase::Close

Voláním této členské funkce odpojit z databáze a zavřete všechny otevřené sady záznamů, tabledefs – a querydefs – souvisejících s databází.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Je vhodné zavřít tyto objekty, sami před voláním této členské funkce. Zavření `CDaoDatabase` objekt ji odebere z kolekce databází v přidruženém [pracovní prostor](../../mfc/reference/cdaoworkspace-class.md). Protože `Close` nezničí `CDaoDatabase` objektu, můžete znovu použít objekt tak, že otevřete stejnou databázi nebo jinou databázi.

> [!CAUTION]
>  Volání [aktualizace](../../mfc/reference/cdaorecordset-class.md#update) členská funkce (pokud existují čekající změny) a `Close` členskou funkci pro všechny objekty otevřít sadu záznamů před zavřením databázi. Při ukončení funkce, která deklaruje [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) nebo `CDaoDatabase` objekty v zásobníku, databáze je zavřená, všechny neuložené změny budou ztraceny, všechny čekající transakce jsou vrácena zpět a veškeré úpravy čekající na vaše data budou ztracena.

> [!CAUTION]
>  Když zkusíte zavřít objekt databáze všechny objekty sady záznamů, které jsou otevřené nebo když zkusíte zavřít objekt pracovního prostoru, když jsou otevřené žádné databázové objekty patřící do tohoto konkrétního pracovního prostoru, tyto objekty sady záznamů se zavře a bude žádné čekající aktualizace nebo úpravy vrátit zpět. Když zkusíte zavřít objekt pracovního prostoru, když jsou otevřené žádné databázové objekty, které patří k němu, tato operace ukončí všechny objekty databáze, které patří na tento objekt určitý pracovní prostor, což může vést k objekty neuzavřený sady záznamů se zavírá. Pokud databázový objekt neukončíte, MFC sestavy selhání kontrolního výrazu v sestaveních ladění.

Pokud objekt databáze je definována mimo obor funkce a ukončení funkce bez jeho uzavřením, objekt databáze zůstane otevřený, dokud explicitně nezavře nebo modul, ve kterém je definována sahá nad rámec.

##  <a name="create"></a>  CDaoDatabase::Create

Chcete-li vytvořit nový Microsoft Jet (. MDB) databáze, poté, co vytvoříte zavolat tuto členskou funkci `CDaoDatabase` objektu.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int dwOptions = 0);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězcový výraz, který je název souboru databáze, kterou vytváříte. Úplná cesta a název souboru, může být například "C:\\\MYDB. MDB". Je nutné zadat název. Pokud nezadáte příponu názvu souboru. Připojí se MDB. Pokud vaše síť podporuje jednotné pojmenování (UNC), můžete taky zadat síťovou cestu jako "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Jenom Microsoft Jet (. Databázové soubory MDB) lze vytvořit pomocí tato členská funkce. (Dvojitá zpětná lomítka jsou nutné v řetězcové literály, proto, že "\\" je znak escape jazyka C++.)

*lpszLocale*<br/>
Řetězcový výraz používá k určení pořadí řazení pro vytvoření databáze. Výchozí hodnota je `dbLangGeneral`. Možné hodnoty jsou:

- `dbLangGeneral` Angličtina, němčina, francouzština, portugalština, italské a moderní španělština

- `dbLangArabic` Arabština

- `dbLangCyrillic` Ruština

- `dbLangCzech` Čeština

- `dbLangDutch` Holandština

- `dbLangGreek` Řečtina

- `dbLangHebrew` Hebrejština

- `dbLangHungarian` Maďarština

- `dbLangIcelandic` Islandština

- `dbLangNordic` Severské jazyky (Microsoft Jet databáze modulu verze 1.0 jenom)

- `dbLangNorwdan` Norština a dánština

- `dbLangPolish` Polština

- `dbLangSpanish` Tradiční španělština

- `dbLangSwedfin` Švédština a finština

- `dbLangTurkish` Turečtina

*dwOptions*<br/>
Celé číslo, které určuje jeden nebo více možností. Možné hodnoty jsou:

- `dbEncrypt` Vytvoření databáze šifrovaná.

- `dbVersion10` Vytvoření databáze pomocí Microsoft Jet databáze verze 1.0.

- `dbVersion11` Vytvoření databáze pomocí Microsoft Jet databáze verze 1.1.

- `dbVersion20` Vytvoření databáze pomocí Microsoft Jet databáze verze 2.0.

- `dbVersion30` Vytvoření databáze pomocí Microsoft Jet databáze verze 3.0.

Vynecháte-li konstanta šifrování, se vytvoří databáze nešifrované. Můžete zadat pouze jednu verzi konstanta. Vynecháte-li konstanta verze, se vytvoří databáze s použitím Microsoft Jet databáze ve verzi 3.0.

> [!CAUTION]
>  Pokud databáze není zašifrovaný, je možné, i pokud se rozhodnete implementovat zabezpečení uživatele a hesla k přímému čtení disku binární soubor, který představuje databáze.

### <a name="remarks"></a>Poznámky

`Create` Vytvoří soubor databáze a podkladový databázový objekt DAO a inicializuje objekt jazyka C++. Objekt se připojí k přidružené pracovní prostor databáze kolekce. Objekt databáze je v otevřeném stavu; Nevolejte `Open*` po `Create`.

> [!NOTE]
>  S `Create`, můžete vytvořit pouze Microsoft Jet (. Databáze MDB). Nelze vytvořit databáze ISAM nebo ODBC databází.

##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation

Voláním této členské funkce k vytvoření vztahu mezi jedno nebo více polí v primární tabulce v databázi a jedno nebo více polí v tabulce cizího (jiné tabulky v databázi).

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
Jedinečný název objektu relace. Název musí začínat písmenem a může obsahovat nejvýše 40 znaků. Může obsahovat čísla a podtržítka znaků, ale nemůže obsahovat interpunkční znaménka nebo mezery.

*lpszTable*<br/>
Název tabulky primární vztah. Pokud tabulka neexistuje, MFC, vyvolá výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

*lpszForeignTable*<br/>
Název tabulky cizího ve vztahu. Pokud tabulka neexistuje, MFC, vyvolá výjimku typu `CDaoException`.

*lAttributes*<br/>
Dlouhou hodnotu, která obsahuje informace o typu vztahu. Tato hodnota slouží k vynucení referenční integrity, mimo jiné. Můžete použít operátor bitového operátoru OR ( **&#124;**) ke sloučení některý z následujících hodnot (jako kombinace smysl):

- `dbRelationUnique` Je relace 1: 1.

- `dbRelationDontEnforce` Relace není vynucena (žádná referenční integrita).

- `dbRelationInherited` Existuje relace v databázi fixní, která obsahuje dvě připojené tabulky.

- `dbRelationUpdateCascade` Aktualizace budou přeneseny (Další informace o cascades viz poznámky).

- `dbRelationDeleteCascade` Odstranění budou přeneseny.

*lpszField*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název pole v primární tabulce (s názvem podle *lpszTable*).

*lpszForeignField*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název pole v tabulce cizího (s názvem podle *lpszForeignTable*).

*relinfo*<br/>
Odkaz na [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objekt, který obsahuje informace o vztahu, kterou chcete vytvořit.

### <a name="remarks"></a>Poznámky

Vztah nemůže zahrnovat dotaz nebo připojené tabulky z externí databáze.

Používejte první verzi funkce vztah zahrnuje jedno pole v každém z obou tabulek. Používejte druhou verzi vztah zahrnuje více polí. Maximální počet polí v relaci je 14.

Tato akce vytvoří objekt vztahu základní rozhraní DAO, ale je to podrobnost implementace MFC, protože MFC zapouzdření objekty relace je obsažena v rámci třídy `CDaoDatabase`. MFC neposkytuje třídu pro vztahy.

Pokud nastavíte relace atributů objektu k aktivaci operací cascade, databázový stroj automaticky aktualizuje nebo odstraní záznamy v jedné nebo více tabulek při změně související tabulky primární klíče.

Předpokládejme například, že vytvoříte cascade delete vztah mezi tabulky Zákazníci a objednávky. Při odstraňování záznamů z tabulky Zákazníci budou odstraněny také záznamy v tabulce objednávky týkající se tohoto zákazníka. Kromě toho Pokud zavedete kaskádové odstranění vztahů mezi tabulky objednávky a dalšími tabulkami, záznamů z těchto tabulek se automaticky odstraní při odstranění záznamů z tabulky Zákazníci.

Související informace naleznete v tématu "CreateRelation metodu" v nápovědě k DAO.

##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef

Zavolat tuto členskou funkci odstranění zadaného querydef – uloženého dotazu, z `CDaoDatabase` objektu querydefs – kolekce.

```
void DeleteQueryDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název uloženého dotazu, chcete-li odstranit.

### <a name="remarks"></a>Poznámky

Potom tento dotaz už není definovaná v databázi.

Informace o vytváření objektů querydef najdete v tématu třídy [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md). Objekt querydef se sváže s konkrétní `CDaoDatabase` objektu při vytváření `CDaoQueryDef` objekt předáním ukazatel na objekt databáze.

##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation

Voláním této členské funkce z kolekce vztahů databázový objekt odstranit existující relace.

```
void DeleteRelation(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název relace odstranit.

### <a name="remarks"></a>Poznámky

Potom se vztah již existuje.

Související informace naleznete v tématu "Odstranit metodu" v nápovědě k DAO.

##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef

Voláním této členské funkce, odstranit, pokud má zadaná tabulka a všechna jeho data z `CDaoDatabase` objektu tabledefs – kolekce.

```
void DeleteTableDef(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název tabledef odstranit.

### <a name="remarks"></a>Poznámky

Potom tato tabulka je již definována v databázi.

> [!NOTE]
>  Buďte velmi opatrní neodstraňovat systémové tabulky.

Informace o vytváření objektů tabledef najdete v tématu třídy [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md). Objekt tabledef se sváže s konkrétní `CDaoDatabase` objektu při vytváření `CDaoTableDef` objekt předáním ukazatel na objekt databáze.

Související informace naleznete v tématu "Odstranit metodu" v nápovědě k DAO.

##  <a name="execute"></a>  CDaoDatabase::Execute

Voláním této členské funkce ke spuštění dotazu akce nebo provedení příkazu SQL na databázi.

```
void Execute(
    LPCTSTR lpszSQL,
    int nOptions = dbFailOnError);
```

### <a name="parameters"></a>Parametry

*Ipszsql*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující platný příkaz SQL pro spuštění.

*nOptions*<br/>
Celé číslo, které určuje možnosti týkající se integrity dotazu. Můžete použít operátor bitového operátoru OR ( **&#124;**) ke sloučení, některé z následujících konstant (Zadaná kombinace smysl – například nebude kombinovat `dbInconsistent` s `dbConsistent`):

- `dbDenyWrite` Odepřete jiným uživatelům oprávnění k zápisu.

- `dbInconsistent` (Výchozí) Nekonzistentní aktualizace.

- `dbConsistent` Konzistentní aktualizace.

- `dbSQLPassThrough` Předávací SQL. Způsobí, že se mají předat zdroji dat rozhraní ODBC pro zpracování příkaz jazyka SQL.

- `dbFailOnError` Vrácení zpět aktualizace, pokud dojde k chybě.

- `dbSeeChanges` Generovat chyb za běhu, pokud jiný uživatel se mění data, která jsou úpravy.

> [!NOTE]
>  Pokud mají oba `dbInconsistent` a `dbConsistent` budou zahrnuty nebo pokud ani jeden není součástí, výsledek je výchozí hodnota. Vysvětlení těchto konstanty naleznete v tématu "Spustit metodu" v nápovědě k DAO.

### <a name="remarks"></a>Poznámky

`Execute` platí jenom pro akce dotazy nebo předávací dotazy SQL, které nevracejí výsledky. Nefunguje pro vyberte dotazy, které vrací záznamy.

Definice a informace o dotazech akce najdete v tématech "Akce dotazu" a "Spustit metodu" v nápovědě k DAO.

> [!TIP]
>  Syntakticky správný příkaz SQL a příslušná oprávnění `Execute` členská funkce nebudou ještě není-li jeden řádek může být změněn nebo odstraněn. Proto vždy používat `dbFailOnError` možnost při použití `Execute` členské funkce spuštění aktualizace nebo odstranění dotazu. Tato možnost způsobí, že knihovna MFC má vyvolat výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md) a vrátí zpět všechny změny úspěšné, pokud žádný vliv na záznamy jsou zamknuté a nejde aktualizovat ani odstranit. Všimněte si, že vždy můžete volat `GetRecordsAffected` zobrazíte vliv na tom, kolik záznamů.

Volání [GetRecordsAffected](#getrecordsaffected) členské funkce objektu databáze k určení počtu záznamy ovlivněny nejnovější `Execute` volání. Například `GetRecordsAffected` vrátí informace o počtu záznamů odstraněny, aktualizaci nebo vložení při provádění dotazu akce. Počet, vrátí se neprojeví, změny v souvisejících tabulkách, když cascade aktualizuje nebo odstraní jsou aktivní.

`Execute` nevrací sadu záznamů. Pomocí `Execute` na dotaz, který vybírá záznamy způsobí, že knihovna MFC má vyvolat výjimku typu `CDaoException`. (Neexistuje žádný `ExecuteSQL` členská funkce, které jsou obdobou `CDatabase::ExecuteSQL`.)

##  <a name="getconnect"></a>  CDaoDatabase::GetConnect

Voláním této členské funkce se načíst připojovací řetězec použitý pro připojení `CDaoDatabase` objektu do rozhraní ODBC nebo ISAM databáze.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

Připojovací řetězec, pokud [otevřít](#open) byl volaný úspěšně na zdroje dat ODBC; v opačném případě prázdný řetězec. Pro databázový stroj Microsoft Jet (. Databáze MDB), řetězec je vždy prázdné, pokud ji nastavíte pro použití se službou `dbSQLPassThrough` možnost použít s [Execute](#execute) členská funkce nebo při otevření sady záznamů.

### <a name="remarks"></a>Poznámky

Řetězec obsahuje informace o zdroji otevřenou databázi nebo databáze používané předávací dotaz. Připojovací řetězec se skládá z specifikátor typu databáze a nula nebo více parametrů oddělené středníky.

> [!NOTE]
>  Používání tříd DAO knihovny MFC pro připojení ke zdroji dat prostřednictvím rozhraní ODBC je méně efektivní než připojení přes připojené tabulky.

> [!NOTE]
>  Připojovací řetězec se používá k předávání dalších informací do rozhraní ODBC a ovladači určité ISAM podle potřeby. Pro se nepoužívá. MDB databází. Pro základní tabulky databáze Microsoft Jet připojovací řetězec je prázdný řetězec ("") s výjimkou případů, kdy ji použijete k předávací dotaz SQL jak je popsáno v části vrátit hodnotu.

Zobrazit [otevřít](#open) členskou funkci pro popis, jak se vytváří připojovací řetězec. Po nastavení připojovacího řetězce `Open` volání, později slouží ke kontrole nastavení k určení typu, cesta, uživatelské ID, heslo nebo ODBC zdroj dat databáze.

##  <a name="getname"></a>  CDaoDatabase::GetName

Voláním této členské funkce načíst název databáze aktuálně otevřené, což je název existující soubor databáze a název registrované zdroje dat ODBC.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta a název souboru databáze v případě úspěchu; v opačném případě prázdný [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Pokud sítě podporuje jednotné pojmenování (UNC), můžete taky zadat síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojitá zpětná lomítka jsou nutné v řetězcové literály, proto, že "\\" je znak escape jazyka C++.)

Můžete například zobrazit tento název v záhlaví. Pokud dojde k chybě při načítání názvu, MFC, vyvolá výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

> [!NOTE]
>  Pro zajištění lepšího výkonu při přistupuje externí databáze, doporučujeme připojení k databázi Microsoft Jet externí databázových tabulek (. MDB) místo připojování přímo ke zdroji dat.

Typ databáze je indikován soubor nebo adresář, který odkazuje cestu, následujícím způsobem:

|Cesta odkazuje na...|Typ databáze|
|--------------------------|-------------------|
|. Soubor MDB|Databáze Microsoft Jet (Microsoft Access)|
|Adresář, který obsahuje. Soubor DBF není Podporován|dBASE databáze|
|Adresář, který obsahuje. Soubor XLS|Databáze aplikace Microsoft Excel|
|Adresář, který obsahuje. Soubory PDX|Databázový stroj|
|Adresář, který obsahuje soubory databáze správně formátovaný text|Databáze ve formátu textu|

Připojovací řetězec databáze pro ODBC databází, jako je například SQL Server a Oracle, identifikuje název zdroje dat (DSN), který je registrovaný pomocí rozhraní ODBC.

##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount

Voláním této členské funkce se načíst počet dotazů, které jsou definované v databáze querydefs – kolekce.

```
short GetQueryDefCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet dotazů, které jsou definované v databázi.

### <a name="remarks"></a>Poznámky

`GetQueryDefCount` je užitečné, pokud budete potřebovat k prosmyčkování všech querydefs – v querydefs – kolekce. Pokud chcete získat informace o daný dotaz v kolekci, najdete v článku [GetQueryDefInfo](#getquerydefinfo).

##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo

Voláním této členské funkce získat různé druhy informací o dotaz definovaný v databázi.

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
Index předdefinovaný dotaz do databáze querydefs – kolekce, pro vyhledávání podle indexu.

*querydefinfo*<br/>
Odkaz na [cdaoquerydefinfo –](../../mfc/reference/cdaoquerydefinfo-structure.md) objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o sadě záznamů pro načtení. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrací informace o sadě záznamů:

- Název AFX_DAO_PRIMARY_INFO (výchozí), zadejte

- Informace o primárním AFX_DAO_SECONDARY_INFO plus: datum vytvoření, datum poslední aktualizace, vrátí záznamy, možností aktualizace

- AFX_DAO_ALL_INFO primární a sekundární informace plus: SQL připojit a odezvy

*lpszName*<br/>
Řetězec obsahující název dotaz definovaný v databázi pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Takže dotaz můžete vybrat podle indexu v databáze querydefs – kolekce nebo podle názvu dotazu jsou k dispozici dvě verze funkce.

Popis informací, v *querydefinfo*, najdete v článku [cdaoquerydefinfo –](../../mfc/reference/cdaoquerydefinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud jste požádali o jednu úroveň informací, získáte všech předchozích úrovní také informace.

##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout

Voláním této členské funkce se načíst aktuální počet sekund před následné operace v připojené databázi jsou vypršel časový limit.

```
short GetQueryTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Krátké celé číslo obsahující hodnotu časového limitu v sekundách.

### <a name="remarks"></a>Poznámky

Operace může časový limit z důvodu problémů s přístupem k síti, doba zpracování nadměrné dotazu a tak dále. Dokud je nastavení, ovlivňuje všechny otevřené, přidávat nové, aktualizace a odstranění týkající se žádné sady záznamů přidružený k tomuto `CDaoDatabase` objektu. Můžete změnit nastavení časového limitu v aktuálním voláním [SetQueryTimeout](#setquerytimeout). Změna časový limit dotazu pro sadu záznamů po otevření nezmění hodnotu pro sady záznamů. Například následující [přesunout](../../mfc/reference/cdaorecordset-class.md#move) operace nepoužívejte novou hodnotu. Výchozí hodnota je zpočátku nastaven při inicializaci modulu databáze.

Výchozí hodnota pro vypršení časového limitu dotazu je převzatý z registru Windows. Pokud neexistuje žádné nastavení registru, výchozí hodnota je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, dojde k žádný časový limit; a komunikaci s databází může přestat reagovat. Toto chování může být užitečné během vývoje. Pokud volání selže, MFC, vyvolá výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

Související informace naleznete v tématu "QueryTimeout vlastnost" v nápovědě k DAO.

##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected

Voláním této členské funkce k určení počtu záznamy ovlivněny posledního volání [Execute](#execute) členskou funkci.

```
long GetRecordsAffected();
```

### <a name="return-value"></a>Návratová hodnota

Dlouhé celé číslo obsahující počet záznamů ovlivněný.

### <a name="remarks"></a>Poznámky

Vrácená hodnota obsahuje několik záznamů odstraněny, aktualizaci nebo vložení dotazem akci spuštění s `Execute`. Počet, vrátí se neprojeví, změny v souvisejících tabulkách, když cascade aktualizuje nebo odstraní jsou aktivní.

Související informace naleznete v tématu "RecordsAffected vlastnost" v nápovědě k DAO.

##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount

Voláním této členské funkce získat počet vztahy definované mezi tabulkami v databázi.

```
short GetRelationCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet vztahů, které jsou definované mezi tabulkami v databázi.

### <a name="remarks"></a>Poznámky

`GetRelationCount` je užitečné, pokud budete muset projít všechny vztahy definované v kolekci Relations vaší databáze. Pokud chcete získat informace o dané relace v kolekci, najdete v článku [GetRelationInfo](#getrelationinfo).

K objasnění konceptu vztah, vezměte v úvahu dodavatelé tabulku a tabulku produktů, který může mít vztah jeden mnoho. V tomto vztahu jednoho dodavatele, můžete zadat více než jeden produkt. Jiné vztahy jsou 1: 1 a many-to-many.

##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo

Voláním této členské funkce získat informace o zadané relace v kolekci Relations vaší databáze.

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
Index objektu relace v kolekci relací databáze, pro vyhledávání podle indexu.

*relinfo*<br/>
Odkaz na [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, které informace o vztahu k načtení. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrací informace o vztahu:

- Tabulka cizího název tabulky, AFX_DAO_PRIMARY_INFO (výchozí)

- Atributy AFX_DAO_SECONDARY_INFO, informace z pole

Informace o poli [cdaorelationfieldinfo –](../../mfc/reference/cdaorelationfieldinfo-structure.md) objekt, který obsahuje pole z účastnící se vztahu primární tabulce.

*lpszName*<br/>
Řetězec obsahující název objektu relace, pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Dvě verze této funkce poskytují přístup, index nebo název. Popis informací, v *relinfo*, najdete v článku [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud jste požádali o informace na jedné úrovni, získáte také informace ve všech předchozích úrovní.

> [!NOTE]
>  Pokud nastavíte relace atributů objektu k aktivaci operací cascade (`dbRelationUpdateCascades` nebo `dbRelationDeleteCascades`), databázový stroj Microsoft Jet automaticky aktualizuje nebo odstraní záznamy v jednom nebo více další tabulky, když jsou provedeny změny související s primární klíč tabulky. Předpokládejme například, že vytvoříte cascade delete vztah mezi tabulky Zákazníci a objednávky. Při odstraňování záznamů z tabulky Zákazníci budou odstraněny také záznamy v tabulce objednávky týkající se tohoto zákazníka. Kromě toho Pokud zavedete kaskádové odstranění vztahů mezi tabulky objednávky a dalšími tabulkami, záznamů z těchto tabulek se automaticky odstraní při odstranění záznamů z tabulky Zákazníci.

##  <a name="gettabledefcount"></a>  CDaoDatabase::GetTableDefCount

Voláním této členské funkce se načíst počet tabulek definovaných v databázi.

```
short GetTableDefCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet tabledefs – definovanými v databázi.

### <a name="remarks"></a>Poznámky

`GetTableDefCount` je užitečné, pokud budete potřebovat k prosmyčkování všech tabledefs – ve vaší databáze tabledefs – kolekce. Pokud chcete získat informace o dané tabulky v kolekci, najdete v článku [GetTableDefInfo](#gettabledefinfo).

##  <a name="gettabledefinfo"></a>  CDaoDatabase::GetTableDefInfo

Voláním této členské funkce získat různé druhy informací o tabulce definovanými v databázi.

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
Index objektu tabledef v tabledefs – kolekce databáze, pro vyhledávání podle indexu.

*tabledefinfo*<br/>
Odkaz na [cdaotabledefinfo –](../../mfc/reference/cdaotabledefinfo-structure.md) objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o tabulce k načtení. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrací informace o vztahu:

- Atributy název AFX_DAO_PRIMARY_INFO (výchozí), aktualizovat,

- Informace o primárním AFX_DAO_SECONDARY_INFO plus: datum vytvoření, datum poslední aktualizace název zdrojové tabulky, připojit

- AFX_DAO_ALL_INFO primární a sekundární informace plus: ověřovací pravidlo, Text pro ověření, počet záznamů

*lpszName*<br/>
Název objektu tabledef pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Dvě verze funkce jsou dodávány, takže můžete vybrat tabulku indexu v tabledefs – kolekce vaší databáze nebo název tabulky.

Popis informací, v *tabledefinfo*, najdete v článku [cdaotabledefinfo –](../../mfc/reference/cdaotabledefinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud jste požádali o informace na jedné úrovni, můžete získat informace o všech předchozích úrovní.

> [!NOTE]
>  Možnost AFX_DAO_ALL_INFO poskytuje informace, které může trvat dlouho. Chcete-li získat. Počítání záznamy v tabulce v takovém případě může být časově velmi náročné Pokud mnoho záznamů.

##  <a name="getversion"></a>  CDaoDatabase::GetVersion

Voláním této členské funkce se určit verzi databázový soubor Microsoft Jet.

```
CString GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který určuje verzi souboru databáze, která je přidružená k objektu.

### <a name="remarks"></a>Poznámky

Vrácená hodnota představuje číslo verze ve formátu "hlavní.vedlejší"; například "3.0". Číslo verze produktu (například 3.0) se skládá z číslo verze (3), tečku a číslo verze (0). Verze datum jsou 1.0, 1.1, 2.0 a 3.0.

Související informace naleznete v tématu "Verze vlastnost" v nápovědě k DAO.

##  <a name="isopen"></a>  CDaoDatabase::IsOpen

Voláním této členské funkce k určení, zda `CDaoDatabase` objektu je momentálně otevřený na databázi.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CDaoDatabase` objekt je aktuálně otevřené; jinak 0.

### <a name="remarks"></a>Poznámky

##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase

Obsahuje ukazatel na rozhraní OLE pro podkladové objekt DAO databáze `CDaoDatabase` objektu.

### <a name="remarks"></a>Poznámky

Pokud je potřeba získat přímo přístup k rozhraní DAO, použijte tento ukazatel.

Informace o volání rozhraní DAO přímo, naleznete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace

Obsahuje ukazatel [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md) objekt, který obsahuje databázový objekt.

### <a name="remarks"></a>Poznámky

Použít tento ukazatel, pokud je potřeba získat přímo přístup k pracovnímu prostoru – například k získání ukazatele na ostatních databázových objektů v pracovním prostoru databáze kolekce.

##  <a name="open"></a>  CDaoDatabase::Open

Lze zavolat tuto členskou funkci inicializace nově vytvořeného `CDaoDatabase` objekt, který představuje existující databázi.

```
virtual void Open(
    LPCTSTR lpszName,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T(""));
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Výraz řetězce, který je název existující Microsoft Jet (. Soubor databáze MDB). Pokud název souboru má příponu, je povinný. Pokud vaše síť podporuje jednotné pojmenování (UNC), můžete taky zadat síťovou cestu jako "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojitá zpětná lomítka jsou nutné v řetězcové literály, proto, že "\\" je znak escape jazyka C++.)

Při použití platí některé aspekty *lpszName*. Pokud ho:

- Odkazuje na databázi, která je již otevřena pro výhradní přístup jiným uživatelem, MFC vyvolává výjimky typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md). Tato výjimka umožňuje uživateli vědět, že databáze je k dispozici pro depeše.

- Je prázdný řetězec ("") a *lpszConnect* je "ODBC;", takže uživatel může vybrat databáze, zobrazí se dialogové okno, ve výpisu všech registrovaných názvy zdrojů dat ODBC. Měli byste se vyhnout přímé připojení ke zdrojům dat ODBC; Místo toho použijte připojené tabulky.

- V opačném případě neodkazuje na existující databáze nebo platný název zdroje dat ODBC, MFC vyvolává výjimky typu `CDaoException`.

> [!NOTE]
>  Podrobnosti o rozhraní DAO chybových kódech naleznete v tématu DAOERR. Soubor H. Související informace naleznete v tématu "Zachytitelné chyb přístupu k datům" v nápovědě k DAO.

*bExclusive*<br/>
Logická hodnota, která je TRUE, pokud se databáze nachází na Otevřít pro výhradní přístup (nesdílené) a hodnotu FALSE, pokud je databáze otevřít pro sdílený přístup. Pokud tento argument vynecháte, databázi otevřít pro sdílený přístup.

*bReadOnly*<br/>
Logická hodnota, která je TRUE, pokud se databáze nachází na Otevřít pro přístup jen pro čtení a hodnotu FALSE, pokud má být otevřen pro čtení a zápisu databáze. Pokud tento argument vynecháte, databázi je otevřen pro čtení a zápisu. Všechny závislé sady záznamů zdědí tento atribut.

*lpszConnect*<br/>
Řetězcový výraz použitý pro otevření databáze. Tento řetězec představuje rozhraní ODBC připojení argumenty. Je třeba zadat argumenty výhradní a jen pro čtení k poskytování zdrojový řetězec. Pokud se databáze nachází databáze aplikace Microsoft Jet (. MDB), je prázdný řetězec (""). Syntaxe pro výchozí hodnotu – **_T**(""), nabízí přenositelnost pro kódování Unicode, stejně jako ANSI sestavení vaší aplikace.

### <a name="remarks"></a>Poznámky

`Open` Přidruží databáze základní objekt rozhraní DAO. Databázový objekt nelze použít k vytvoření sady záznamů, tabledef nebo querydef objekty, dokud není inicializován. `Open` Přidá objekt databáze kolekce databází přidružených pracovních prostorů.

Použijte následující parametry:

- Pokud otevíráte Microsoft Jet (. Databáze MDB), použijte *lpszName* parametr a předáte prázdný řetězec *lpszConnect* parametr nebo pass heslo řetězec ve tvaru "; PWD = heslo "Pokud se databáze nachází v chráněném heslem (. MDB pouze pro databáze).

- Pokud otevíráte zdroji dat rozhraní ODBC, předejte platný připojovací řetězec ODBC v *lpszConnect* a prázdný řetězec v *lpszName*.

Související informace naleznete v tématu "OpenDatabase metodu" v nápovědě k DAO.

> [!NOTE]
>  Pro zajištění lepšího výkonu při přístupu k externí databází, včetně ISAM a zdroje dat ODBC, doporučujeme připojit externí databázových tabulek pro databázový stroj Microsoft Jet (. MDB) místo připojování přímo ke zdroji dat.

Je možné pro pokus o připojení k vypršení časového limitu, pokud je například DBMS hostitele není k dispozici. Pokud se nezdaří pokus o připojení, `Open` vyvolá výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

Zbývající poznámky platí pouze pro ODBC databází:

Pokud je databáze ODBC a parametry v databáze vaší `Open` volání neobsahují dostatek informací k vytvoření připojení, ovladač ODBC se otevře dialogové okno pro získání potřebných informací od uživatele. Při volání `Open`, připojovací řetězec *lpszConnect*, je uložen soukromou a je k dispozici prostřednictvím volání [GetConnect](#getconnect) členskou funkci.

Pokud chcete, můžete otevřít dialogové okno Vlastní před voláním `Open` k získání informací od uživatele, jako jsou hesla, zadejte tyto informace na připojovací řetězec můžete předat `Open`. Nebo můžete chtít uložit připojovací řetězec, předáte (ideálně v registru Windows), znovu ho můžete použít další čas volání aplikace `Open` na `CDaoDatabase` objektu.

Připojovací řetězec můžete použít také pro několik úrovní autorizace přihlášení (každou pro jiný `CDaoDatabase` objekt) nebo sdělit Další informace o konkrétních databází.

##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout

Voláním této členské funkce přepsat výchozí počet sekund před následné operace na připojeném databázovém časový limit.

```
void SetQueryTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*Počet_sekund*<br/>
Počet sekund před pokusu o dotaz vyprší časový limit.

### <a name="remarks"></a>Poznámky

Operace může časový limit z důvodu problémů s přístupem k síti, doba zpracování nadměrné dotazu a tak dále. Volání `SetQueryTimeout` před otevřením sady záznamů nebo před voláním sady záznamů [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [aktualizace](../../mfc/reference/cdaorecordset-class.md#update), nebo [odstranit](../../mfc/reference/cdaorecordset-class.md#delete) členské funkce, pokud chcete změnit dotaz Hodnota časového limitu. Toto nastavení ovlivňuje všechny následné [otevřít](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, `Update`, a `Delete` volání jakékoli sady záznamů přidružený k tomuto `CDaoDatabase` objektu. Změna časový limit dotazu pro sadu záznamů po otevření nezmění hodnotu pro sady záznamů. Například následující [přesunout](../../mfc/reference/cdaorecordset-class.md#move) operace nepoužívejte novou hodnotu.

Výchozí hodnota pro vypršení časového limitu dotazu je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, dojde k žádný časový limit; komunikace s databází může přestat reagovat. Toto chování může být užitečné během vývoje.

Související informace naleznete v tématu "QueryTimeout vlastnost" v nápovědě k DAO.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
