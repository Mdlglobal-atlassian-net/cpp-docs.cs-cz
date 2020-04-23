---
title: CDaoWorkspace – třída
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: c492c806d64b1cfe0e4f73b3bb880ec7bd0a7e80
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754663"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace – třída

Spravuje pojmenované, heslem chráněné relace databáze od přihlášení k odhlášení, jedním uživatelem. DAO je podporováno prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé.

## <a name="syntax"></a>Syntaxe

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoPracovní prostor::CDaoPracovní prostor](#cdaoworkspace)|Vytvoří objekt pracovního prostoru. Poté `Create` zavolejte `Open`nebo .|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoWorkspace::Připojit](#append)|Připojí nově vytvořený pracovní prostor do kolekce pracovních prostorů databázového stroje.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Zahájí novou transakci, která platí pro všechny databáze otevřené v pracovním prostoru.|
|[CDaoWorkspace::Zavřít](#close)|Zavře pracovní prostor a všechny objekty, které obsahuje. Čekající transakce jsou vráceny zpět.|
|[CDaoWorkspace::CommitTrans](#committrans)|Dokončí aktuální transakci a uloží změny.|
|[Prostor CDaoWorkspace::CompactDatabase](#compactdatabase)|Komprimuje (nebo duplikáty) databáze.|
|[CDaoWorkspace::Vytvořit](#create)|Vytvoří nový objekt pracovního prostoru DAO.|
|[Prostor CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Vrátí počet databázových objektů DAO v kolekci databáze pracovního prostoru.|
|[Prostor CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Vrátí informace o zadané databázi DAO definované v kolekci databází pracovního prostoru.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Vrátí umístění nastavení inicializace databázového stroje Microsoft Jet v registru systému Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Vrátí hodnotu, která označuje, zda je více transakcí, které se týkají stejného zdroje dat ROZHRANÍ ODBC, izolováno prostřednictvím vynuceného více připojení ke zdroji dat.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Vrátí počet sekund před výskytem chyby, když se uživatel pokusí přihlásit k databázi ODBC.|
|[CDaoPracovní prostor::GetName](#getname)|Vrátí uživatelem definovaný název objektu pracovního prostoru.|
|[Prostor CDaoWorkspace::GetUserName](#getusername)|Vrátí uživatelské jméno určené při vytvoření pracovního prostoru. Toto je název vlastníka pracovního prostoru.|
|[CDaoWorkspace::GetVersion](#getversion)|Vrátí řetězec, který obsahuje verzi databázového stroje přidruženého k pracovnímu prostoru.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Vrátí počet objektů pracovního prostoru DAO v kolekci pracovních prostorů databázového stroje.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Vrátí informace o zadaném pracovním prostoru DAO definovaném v kolekci pracovních prostorů databázového stroje.|
|[CDaoPracovní prostor::Nečinnosti](#idle)|Umožňuje databázový stroj provádět úlohy na pozadí.|
|[CDaoWorkspace::IsOpen](#isopen)|Vrátí nenulovou, pokud je pracovní prostor otevřený.|
|[CDaoPracovní prostor::Otevřít](#open)|Explicitně otevře objekt pracovního prostoru přidružený k výchozímu pracovnímu prostoru DAO.|
|[CDaoWorkspace::Opravadatabáze](#repairdatabase)|Pokusí se opravit poškozenou databázi.|
|[CDaoWorkspace::Vrácení zpět](#rollback)|Ukončí aktuální transakci a neuloží změny.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Nastaví heslo, které databázový stroj používá při vytvoření objektu pracovního prostoru bez určitého hesla.|
|[Prostor CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Nastaví uživatelské jméno, které databázový stroj používá při vytvoření objektu pracovního prostoru bez určitého uživatelského jména.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Nastaví umístění nastavení inicializace databázového stroje Microsoft Jet v registru systému Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Určuje, zda je více transakcí, které se týkají stejného zdroje dat ROZHRANÍ ODBC, izolováno vynucením více připojení ke zdroji dat.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund před výskytem chyby, když se uživatel pokusí přihlásit ke zdroji dat ODBC.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoPracovní prostor::m_pDAOWorkspace](#m_pdaoworkspace)|Odkazuje na základní objekt pracovního prostoru DAO.|

## <a name="remarks"></a>Poznámky

Ve většině případů nebudete potřebovat více pracovních prostorů a nebudete muset vytvářet explicitní objekty pracovního prostoru; když otevřete databázi a objekty sady záznamů, používají výchozí pracovní prostor DAO. V případě potřeby však můžete spustit více relací najednou vytvořením dalších objektů pracovního prostoru. Každý objekt pracovního prostoru může obsahovat více otevřených databázových objektů ve vlastní kolekci databází. V knihovně MFC je pracovní prostor především správce transakcí, který specifikuje sadu otevřených databází ve stejném "transakčním prostoru".

> [!NOTE]
> Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Obecně platí, že třídy Knihovny MFC založené na DAO jsou schopnější než třídy Knihovny MFC založené na rozhraní ODBC. Třídy založené na DAO přístup k datům prostřednictvím databázového stroje Microsoft Jet, včetně ovladačů ODBC. Podporují také operace jazyka DDL (Data Definition Language), jako je vytváření databází a přidávání tabulek a polí prostřednictvím tříd, aniž by bylo třeba volat DAO přímo.

## <a name="capabilities"></a>Možnosti

Třída `CDaoWorkspace` poskytuje následující:

- Explicitní přístup, v případě potřeby k výchozímu pracovnímu prostoru, vytvořené inicializací databázového stroje. Obvykle používáte výchozí pracovní prostor DAO implicitně vytvořením objektů databáze a sady záznamů.

- Transakční prostor, ve kterém se transakce vztahují na všechny databáze otevřené v pracovním prostoru. Můžete vytvořit další pracovní prostory pro správu samostatných transakčních prostorů.

- Rozhraní pro mnoho vlastností základního databázového stroje Microsoft Jet (viz statické členské funkce). Otevření nebo vytvoření pracovního prostoru nebo volání statické členské funkce před otevřením nebo vytvořením inicializuje databázový stroj.

- Přístup ke kolekci pracovních prostorů databázového stroje, ve které jsou uloženy všechny aktivní pracovní prostory, které k němu byly připojeny. Můžete také vytvářet a pracovat s pracovními prostory bez jejich připojení ke sbírce.

## <a name="security"></a>Zabezpečení

Knihovna MFC neimplementuje kolekce Users and Groups v DAO, které se používají pro řízení zabezpečení. Pokud potřebujete tyto aspekty DAO, musíte je naprogramovat sami prostřednictvím přímých volání do rozhraní DAO. Další informace naleznete [v technické poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Využití

Třídu `CDaoWorkspace` můžete použít k:

- Explicitně otevřete výchozí pracovní prostor.

   Obvykle je použití výchozího pracovního prostoru implicitní – při otevření nových objektů [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) nebo [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) Ale možná budete muset získat přístup explicitně – například pro přístup k vlastnostem databázového stroje nebo pracovní prostory kolekce. Viz "Implicitní použití výchozího pracovního prostoru" níže.

- Vytvořte nové pracovní prostory. Volání [Připojit,](#append) pokud chcete přidat do kolekce pracovních prostorů.

- Otevřete existující pracovní prostor v kolekci pracovních prostorů.

Vytvoření nového pracovního prostoru, který ještě neexistuje v kolekci pracovních prostorů, je popsáno v části [Vytvořit](#create) členovou funkci. Objekty pracovního prostoru nepřetrvávají žádným způsobem mezi relacemi modulu datababase. Pokud vaše aplikace propojí knihovnu MFC staticky, ukončení aplikace uninitializes databázového stroje. Pokud vaše aplikace souvisí s knihovnou MFC dynamicky, databázový stroj je neinicializovánpři uvolnění knihovny DLL knihovny MFC.

Explicitní otevření výchozího pracovního prostoru nebo otevření existujícího pracovního prostoru v kolekci pracovních prostorů je popsáno v rámci funkce [Otevřít](#open) člen.

Ukončit relaci pracovního prostoru zavřením pracovního prostoru pomocí funkce [Zavřít](#close) člena. `Close`zavře všechny databáze, které jste dříve nezavřeli, vrácení zpět všechny nepotvrzené transakce.

## <a name="transactions"></a>Transakce

DAO spravuje transakce na úrovni pracovního prostoru; proto transakce na pracovním prostoru s více otevřenými databázemi platí pro všechny databáze. Například pokud dvě databáze mají nepotvrzené aktualizace a volání [CommitTrans](#committrans), všechny aktualizace jsou potvrzeny. Pokud chcete omezit transakce na jednu databázi, potřebujete pro ni samostatný objekt pracovního prostoru.

## <a name="implicit-use-of-the-default-workspace"></a>Implicitní použití výchozího pracovního prostoru

Knihovna MFC používá výchozí pracovní prostor DAO implicitně za následujících okolností:

- Pokud vytvoříte `CDaoDatabase` nový objekt, ale neprovedete tak prostřednictvím existujícího `CDaoWorkspace` objektu, knihovna MFC vytvoří dočasný objekt pracovního prostoru pro vás, který odpovídá výchozí pracovní prostor DAO. Pokud tak učiníte pro více databází, všechny databázové objekty jsou přidruženy k výchozímu pracovnímu prostoru. K pracovnímu prostoru databáze můžete `CDaoDatabase` přistupovat prostřednictvím datového člena.

- Podobně pokud vytvoříte `CDaoRecordset` objekt bez poskytnutí ukazatele `CDaoDatabase` na objekt, knihovna MFC vytvoří dočasný databázový objekt a potažmo dočasný objekt pracovního prostoru. Můžete přistupovat k databázi sady záznamů a nepřímo k `CDaoRecordset` jejímu pracovnímu prostoru prostřednictvím datového člena.

## <a name="other-operations"></a>Ostatní operace

K dispozici jsou také další databázové operace, například oprava poškozené databáze nebo komprimace databáze.

Informace o přímém volání dao a o zabezpečení DAO naleznete [v technické poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaoworkspaceappend"></a><a name="append"></a>CDaoWorkspace::Připojit

Volání této členské funkce po volání [Vytvořit](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

`Append`připojí nově vytvořený objekt pracovního prostoru do kolekce pracovních prostorů databázového stroje. Pracovní prostory nepřetrvávají mezi relacemi databázového stroje; jsou uloženy pouze v paměti, nikoli na disku. Není třeba připojit pracovní prostor; Pokud tak neučiníte, můžete jej stále používat.

Připojený pracovní prostor zůstane v kolekci pracovních prostorů v aktivním otevřeném stavu, dokud nezavoláte jeho člennou funkci [Close.](#close)

Související informace naleznete v tématu "Append Method" v nápovědě DAO.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a>CDaoWorkspace::BeginTrans

Volání této členské funkce k zahájení transakce.

```cpp
void BeginTrans();
```

### <a name="remarks"></a>Poznámky

Po volání `BeginTrans`se aktualizace dat nebo struktury databáze projeví při potvrzení transakce. Vzhledem k tomu, že pracovní prostor definuje jeden transakční prostor, transakce se vztahuje na všechny otevřené databáze v pracovním prostoru. Transakci lze dokončit dvěma způsoby:

- Volání [CommitTrans](#committrans) členské funkce potvrdit transakci a uložit změny do zdroje dat.

- Nebo volání [rollback](#rollback) členské funkce zrušit transakci.

Zavření objektu pracovního prostoru nebo databázového objektu v době, kdy transakce čeká na vyřízení, vrátí všechny čekající transakce.

Pokud potřebujete izolovat transakce na jednom zdroji dat ODBC od transakcí na jiném zdroji dat ODBC, přečtěte si viz členská funkce [SetIsolateODBCTrans.](#setisolateodbctrans)

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a>CDaoPracovní prostor::CDaoPracovní prostor

Vytvoří `CDaoWorkspace` objekt.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Poznámky

Po vytvoření objektu C++ máte dvě možnosti:

- Volání objektu [Open](#open) členská funkce otevřít výchozí pracovní prostor nebo otevřít existující objekt v kolekci pracovních prostorů.

- Nebo volání objektu [Vytvořit](#create) členská funkce vytvořit nový objekt pracovního prostoru DAO. To explicitně spustí novou relaci pracovního prostoru, `CDaoWorkspace` na kterou můžete odkazovat prostřednictvím objektu. Po `Create`volání můžete volat [Append,](#append) pokud chcete přidat pracovní prostor do kolekce pracovních prostorů databázového stroje.

Informace o tom, kdy potřebujete explicitně vytvořit `CDaoWorkspace` objekt, najdete v přehledu tříd pro [CDaoWorkspace.](../../mfc/reference/cdaoworkspace-class.md) Pracovní prostory vytvořené implicitně při otevření objektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) bez zadání pracovního prostoru nebo při otevření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez zadání databázového objektu. Objekty DAO knihovny MFC vytvořené tímto způsobem používají výchozí pracovní prostor DAO, který je vytvořen jednou a znovu použit.

Chcete-li uvolnit pracovní prostor a jeho obsažené objekty, zavolejte člennou funkci [Close](#close) objektu pracovního prostoru.

## <a name="cdaoworkspaceclose"></a><a name="close"></a>CDaoWorkspace::Zavřít

Volánítéto členské funkce zavřete objekt pracovního prostoru.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Zavření objektu otevřeného pracovního prostoru uvolní základní objekt DAO a pokud je pracovní prostor členem kolekce Pracovní prostory, odebere ho z kolekce. Volání `Close` je dobrá programovací praxe.

> [!CAUTION]
> Zavřením objektu pracovního prostoru zavřete všechny otevřené databáze v pracovním prostoru. Výsledkem jsou všechny sady záznamů otevřené v databázích, které jsou také uzavřeny, a všechny čekající úpravy nebo aktualizace jsou vráceny zpět. Související informace naleznete v [tématech CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), a [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) member functions.

Objekty pracovního prostoru nejsou trvalé. existují pouze v době, kdy na ně existují odkazy. To znamená, že po ukončení relace databázového stroje pracovní prostor a jeho databáze kolekce nepřetrvávají. Je nutné je znovu vytvořit pro další relaci opětovným otevřením pracovního prostoru a databází.

Související informace naleznete v tématu "Close Method" v nápovědě dao.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a>CDaoWorkspace::CommitTrans

Volání této členské funkce k potvrzení transakce – uložení skupiny úprav a aktualizací do jedné nebo více databází v pracovním prostoru.

```cpp
void CommitTrans();
```

### <a name="remarks"></a>Poznámky

Transakce se skládá z řady změn dat databáze nebo její struktury, počínaje [voláním BeginTrans](#begintrans). Po dokončení transakce ji potvrdíte nebo vraťte zpět (zrušíte změny) pomocí [vrácení zpět](#rollback). Ve výchozím nastavení bez transakcí jsou aktualizace záznamů potvrzeny okamžitě. Volání `BeginTrans` způsobí, že závazek aktualizací `CommitTrans`bude zpožděn, dokud nezavoláte .

> [!CAUTION]
> V rámci jednoho pracovního prostoru jsou transakce vždy globální pro pracovní prostor a nejsou omezeny pouze na jednu databázi nebo sadu záznamů. Pokud provádíte operace s více než jednou databází nebo `CommitTrans` sadou záznamů v `Rollback` rámci transakce pracovního prostoru, potvrdíte všechny čekající aktualizace a obnovíte všechny operace v těchto databázích a sadách záznamů.

Když zavřete databázi nebo pracovní prostor s čekajícími transakcemi, všechny transakce jsou vráceny zpět.

> [!NOTE]
> Nejedná se o dvoufázový mechanismus potvrzení. Pokud se jedna aktualizace nepodaří potvrdit, ostatní se stále potvrdí.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a>Prostor CDaoWorkspace::CompactDatabase

Volání této členské funkce komprimovat zadaný Microsoft Jet (. MDB).

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszSrcNázev*<br/>
Název existující uzavřené databáze. Může to být úplná cesta a název\\souboru, například "C: \MYDB. MDB". Pokud má název souboru příponu, musíte ji zadat. Pokud vaše síť podporuje jednotnou konvenci pojmenování (UNC),\\\\\\můžete\\také zadat\\síťovou\\cestu, například " \MYSERVER \MYSHARE \MYDIR \MYDB. MDB". (Dvojitá zpětná lomítka jsou\\vyžadována v řetězcích cesty, protože " " je řídicí znak jazyka C++.)

*lpszDestName*<br/>
Úplná cesta k zkomprimované databázi, kterou vytváříte. Můžete také zadat síťovou cestu jako *u lpszSrcName*. Argument *lpszDestName* nelze použít k určení stejného databázového souboru jako *lpszSrcName*.

*lpszPassword*<br/>
Heslo, které se používá, pokud chcete komprimovat databázi chráněnou heslem. Všimněte si, `CompactDatabase` že pokud používáte verzi, která má heslo, musíte zadat všechny parametry. Také proto, že se jedná o parametr connect, vyžaduje speciální formátování, a to následovně: ; PWD = *lpszPassword*. Například: ; PWD="Šťastný". (Je vyžadován úvodní středník.)

*lpszLocale*<br/>
Řetězec výraz používaný k určení pořadí řazení pro vytváření *lpszDestName*. Pokud tento argument vynesete přijetím výchozí hodnoty `dbLangGeneral` (viz níže), národní prostředí nové databáze je stejné jako u staré databáze. Možné hodnoty:

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

*nMožnosti*<br/>
Označuje jednu nebo více možností pro cílovou databázi *lpszDestName*. Pokud tento argument vynecháte přijetím výchozí hodnoty, *lpszDestName* bude mít stejné šifrování a stejnou verzi jako *lpszSrcName*. Můžete kombinovat `dbEncrypt` možnost `dbDecrypt` nebo s jednou z možností verze pomocí operátoru Bitwise-OR. Možné hodnoty, které určují formát databáze, nikoli verzi databázového stroje, jsou:

- `dbEncrypt`Šifrujte databázi při komprimaci.

- `dbDecrypt`Dešifrujte databázi při komprimaci.

- `dbVersion10`Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 1.0 při komprimaci.

- `dbVersion11`Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 1.1 při komprimaci.

- `dbVersion20`Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 2.0 při komprimaci.

- `dbVersion30`Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 3.0 při komprimaci.

Můžete použít `dbEncrypt` `dbDecrypt` nebo v argumentu možnosti určit, zda chcete šifrovat nebo dešifrovat databázi při komprimaci. Pokud vynecháte šifrovací konstantu nebo pokud zahrnete `dbDecrypt` obě `dbEncrypt`a , *lpszDestName* bude mít stejné šifrování jako *lpszSrcName*. Můžete použít jednu z konstant verze v argumentu options k určení verze formátu dat pro zkomprimovnětenou databázi. Tato konstanta ovlivňuje pouze verzi datového formátu *lpszDestName*. Můžete zadat pouze jednu konstantu verze. Pokud vynecháte konstantu verze, *lpszDestName* bude mít stejnou verzi jako *lpszSrcName*. Můžete *komprimovat lpszDestName* pouze na verzi, která je stejná nebo novější než *lpszSrcName*.

> [!CAUTION]
> Pokud databáze není šifrována, je možné, i když implementujete zabezpečení uživatele/hesla, přímo číst binární soubor disku, který tvoří databázi.

### <a name="remarks"></a>Poznámky

Při změně dat v databázi může být soubor databáze fragmentován a využívat více místa na disku, než je nutné. Pravidelně byste měli komprimovat databázi defragmentaci databázového souboru. Komprimovaná databáze je obvykle menší. Můžete také změnit pořadí řazení, šifrování nebo verzi formátu dat při kopírování a komprimaci databáze.

> [!CAUTION]
> Členská `CompactDatabase` funkce nebude správně převést úplnou databázi aplikace Microsoft Access z jedné verze na jinou. Je převeden pouze formát dat. Objekty definované aplikací Microsoft Access, například formuláře a sestavy, nejsou převedeny. Data jsou však správně převedena.

> [!TIP]
> Můžete také `CompactDatabase` zkopírovat soubor databáze.

Další informace o komprimaci databází naleznete v tématu "CompactDatabase Method" v nápovědě DAO.

## <a name="cdaoworkspacecreate"></a><a name="create"></a>CDaoWorkspace::Vytvořit

Volání této členské funkce k vytvoření nového objektu pracovního `CDaoWorkspace` prostoru DAO a přidružit jej k objektu knihovny MFC.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Řetězec s až 14 znaky, který jedinečně pojmenuje nový objekt pracovního prostoru. Musíte zadat jméno. Související informace naleznete v tématu "Name Property" v nápovědě dao.

*lpszUserName*<br/>
Uživatelské jméno vlastníka pracovního prostoru. Požadavky naleznete v parametru *lpszDefaultUser* na členské funkci [SetDefaultUser.](#setdefaultuser) Související informace naleznete v tématu "Vlastnost uživatelského_jména" v nápovědě dao.

*lpszPassword*<br/>
Heslo pro nový objekt pracovního prostoru. Heslo může mít až 14 znaků a může obsahovat libovolný znak kromě ASCII 0 (null). Hesla rozlišují malá a velká písmena. Související informace naleznete v tématu "Vlastnost hesla" v nápovědě dao.

### <a name="remarks"></a>Poznámky

Celkový proces vytváření je:

1. Vytvořte objekt [CDaoWorkspace.](#cdaoworkspace)

1. Volání `Create` členské funkce objektu k vytvoření základního pracovního prostoru DAO. Je nutné zadat název pracovního prostoru.

1. Volitelně volat [Append,](#append) pokud chcete přidat pracovní prostor do kolekce pracovních prostorů databázového stroje. S pracovním prostorem můžete pracovat, aniž byste ho připojováli.

Po `Create` volání je objekt pracovního prostoru v otevřeném stavu, připraven k použití. Nemusíte volat `Open` po `Create`. Nevolat, `Create` pokud pracovní prostor již existuje v kolekci pracovních prostorů. `Create`inicializuje databázový stroj, pokud již nebyl inicializován pro vaši aplikaci.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a>Prostor CDaoWorkspace::GetDatabaseCount

Volání této členské funkce načíst počet databázových objektů DAO v kolekci databáze pracovního prostoru – počet otevřených databází v pracovním prostoru.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet otevřených databází v pracovním prostoru.

### <a name="remarks"></a>Poznámky

`GetDatabaseCount`je užitečné, pokud potřebujete procházet všechny definované databáze v kolekci databáze pracovního prostoru. Informace o dané databázi v kolekci získáte v tématu [GetDatabaseInfo](#getdatabaseinfo). Typické použití je `GetDatabaseCount` volání počtu otevřených databází, pak použít toto číslo `GetDatabaseInfo`jako index smyčky pro opakované volání .

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a>Prostor CDaoWorkspace::GetDatabaseInfo

Volání této členské funkce získat různé druhy informací o databázi otevřené v pracovním prostoru.

```cpp
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index databázového objektu v kolekci databáze pracovního prostoru pro vyhledávání podle indexu.

*dbinfo*<br/>
Odkaz na objekt [CDaoDatabaseInfo,](../../mfc/reference/cdaodatabaseinfo-structure.md) který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o databázi načíst. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit:

- AFX_DAO_PRIMARY_INFO (Výchozí) Název, Aktualizovatelné, Transakce

- AFX_DAO_SECONDARY_INFO primární informace plus: Verze, pořadí řazení, časový limit dotazu

- AFX_DAO_ALL_INFO Primární a sekundární informace plus: Připojení

*název lpsz*<br/>
Název databázového objektu pro vyhledávání podle názvu. Název je řetězec s až 14 znaky, který jedinečně pojmenuje nový objekt pracovního prostoru.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat databázi podle indexu. Druhá verze umožňuje vyhledat databázi podle názvu.

Popis informací vrácených v *dbinfo*naleznete v tématu [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) struktura. Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Když požadujete informace na jedné úrovni, získáte také informace pro všechny předchozí úrovně.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a>CDaoWorkspace::GetIniPath

Volání této členské funkce získat umístění nastavení inicializace databázového stroje Microsoft Jet v registru systému Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující umístění registru.

### <a name="remarks"></a>Poznámky

Umístění můžete použít k získání informací o nastavení pro databázový stroj. Vrácené informace jsou ve skutečnosti názvem podklíče registru.

Související informace naleznete v tématech Vlastnostini IniPath a Přizpůsobení nastavení registru systému Windows pro přístup k datům v nápovědě dao.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Volání této členské funkce získat aktuální hodnotu DAO IsolateODBCTrans vlastnost pro pracovní prostor.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou transakce ROZHRANÍ ODBC izolovány; jinak 0.

### <a name="remarks"></a>Poznámky

V některých situacích může být nutné mít více souběžných transakcí čekajících na stejné databázi ODBC. Chcete-li to provést, musíte otevřít samostatný pracovní prostor pro každou transakci. Mějte na paměti, že i když každý pracovní prostor může mít vlastní připojení ODBC k databázi, to zpomaluje výkon systému. Vzhledem k tomu, že izolace transakcí není obvykle vyžadována, připojení ODBC z více objektů pracovního prostoru otevřených stejným uživatelem jsou ve výchozím nastavení sdílena.

Některé servery ODBC, například Microsoft SQL Server, neumožňují souběžné transakce v jednom připojení. Pokud potřebujete mít více než jednu transakci najednou čekající na tuto databázi, nastavte IsolateODBCTrans vlastnost TRUE na každém pracovním prostoru, jakmile ji otevřete. To vynutí samostatné připojení ODBC pro každý pracovní prostor.

Související informace naleznete v tématu "IsolateODBCTrans Property" v nápovědě dao.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Volání této členské funkce získat aktuální hodnotu DAO LoginTimeout vlastnost pro pracovní prostor.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Počet sekund před chybou dojde při pokusu o přihlášení k databázi ODBC.

### <a name="remarks"></a>Poznámky

Tato hodnota představuje počet sekund před výskytem chyby při pokusu o přihlášení k databázi ODBC. Výchozí nastavení LoginTimeout je 20 sekund. Pokud LoginTimeout je nastavena na 0, žádný časový limit dojde a komunikace se zdrojem dat může přestat reagovat.

Při pokusu o přihlášení k databázi ODBC, jako je například Microsoft SQL Server, může dojít k selhání připojení v důsledku chyb v síti nebo proto, že server není spuštěn. Místo čekání na výchozí 20 sekund připojení, můžete určit, jak dlouho databázový stroj čeká, než dojde k chybě. Přihlášení k serveru probíhá implicitně jako součást řady různých událostí, jako je například spuštění dotazu v databázi externího serveru.

Související informace naleznete v tématu "Vlastnost LoginTimeout" v nápovědě DAO.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a>CDaoPracovní prostor::GetName

Volání této členské funkce získat uživatelem definovaný název objektu pracovního prostoru DAO základní `CDaoWorkspace` objekt.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující uživatelem definovaný název objektu pracovního prostoru DAO.

### <a name="remarks"></a>Poznámky

Název je užitečný pro přístup k objektu pracovního prostoru DAO v kolekci pracovních prostorů databázového stroje podle názvu.

Související informace naleznete v tématu "Name Property" v nápovědě dao.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a>Prostor CDaoWorkspace::GetUserName

Volání této členské funkce získat jméno vlastníka pracovního prostoru.

```
CString GetUserName();
```

### <a name="return-value"></a>Návratová hodnota

[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který představuje vlastníka objektu pracovního prostoru.

### <a name="remarks"></a>Poznámky

Chcete-li získat nebo nastavit oprávnění pro vlastníka pracovního prostoru, zavolejte dao přímo a zkontrolujte nastavení vlastnosti Oprávnění; To určuje, jaká oprávnění má uživatel. Chcete-li pracovat s oprávněními, potřebujete systém. Soubor MDA.

Informace o přímém volání dao naleznete [v technické poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Související informace naleznete v tématu "Vlastnost uživatelského_jména" v nápovědě dao.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a>CDaoWorkspace::GetVersion

Volání této členské funkce k určení verze databázového stroje Microsoft Jet v provozu.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který označuje verzi databázového stroje přidruženéka k objektu.

### <a name="remarks"></a>Poznámky

Vrácená hodnota představuje číslo verze ve tvaru "major.minor"; například "3.0". Číslo verze produktu (například 3.0) se skládá z čísla verze (3), tečky a čísla verze (0).

Související informace naleznete v tématu "Vlastnost verze" v nápovědě dao.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Volání této členské funkce načíst počet objektů pracovního prostoru DAO v kolekci pracovních prostorů databázového stroje.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet otevřených pracovních prostorů v kolekci pracovních prostorů.

### <a name="remarks"></a>Poznámky

Tento počet nezahrnuje žádné otevřené pracovní prostory, které nejsou připojeny ke kolekci. `GetWorkspaceCount`je užitečné, pokud potřebujete procházet všechny definované pracovní prostory v kolekci pracovních prostorů. Informace o daném pracovním prostoru v kolekci získáte na webu [GetWorkspaceInfo.](#getworkspaceinfo) Typické použití je `GetWorkspaceCount` volání počtu otevřených pracovních prostorů a potom použijte `GetWorkspaceInfo`toto číslo jako index smyčky pro opakované volání .

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Volání této členské funkce získat různé druhy informací o pracovní ploše otevřené v relaci.

```cpp
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index databázového objektu založený na nule v kolekci Workspaces pro vyhledávání podle indexu.

*wkspcinfo*<br/>
Odkaz na objekt [CDaoWorkspaceInfo,](../../mfc/reference/cdaoworkspaceinfo-structure.md) který vrací požadované informace.

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o pracovním prostoru se mají načíst. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit:

- AFX_DAO_PRIMARY_INFO (výchozí) název

- AFX_DAO_SECONDARY_INFO primární informace plus: Uživatelské jméno

- AFX_DAO_ALL_INFO Primární a sekundární informace plus: Izolujte ODBCTrans

*název lpsz*<br/>
Název objektu pracovního prostoru pro vyhledávání podle názvu. Název je řetězec s až 14 znaky, který jedinečně pojmenuje nový objekt pracovního prostoru.

### <a name="remarks"></a>Poznámky

Popis informací vrácených v *wkspcinfo*naleznete v [cdaoworkspaceinfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) struktury. Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Když požadujete informace na jedné úrovni, získáte také informace pro předchozí úrovně.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a>CDaoPracovní prostor::Nečinnosti

Volání `Idle` poskytnout databázový stroj s možností provádět úlohy na pozadí, které nemusí být aktuální z důvodu intenzivní zpracování dat.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parametry

*nAkce*<br/>
Akce, která má být během zpracování nečinnosti. V současné době je `dbFreeLocks`jedinou platnou akcí .

### <a name="remarks"></a>Poznámky

To často platí ve víceuživatelských prostředích s více úlohami, ve kterých není dostatek času na zpracování na pozadí, aby byly všechny záznamy v aktuální sadě záznamů.

> [!NOTE]
> Volání `Idle` není nutné s databázemi vytvořenými pomocí verze 3.0 databázového stroje Microsoft Jet. Používejte `Idle` pouze pro databáze vytvořené v dřívějších verzích.

Zámky čtení jsou obvykle odebrány a data v objektech sady záznamů typu místní dynaset je aktualizován pouze v případě, že žádné jiné akce (včetně pohybu myši) dochází. Pokud pravidelně voláte `Idle`, poskytnete databázový stroj čas dohnat na úlohy zpracování na pozadí uvolněním nepotřebné zámky čtení. Zadání konstanty `dbFreeLocks` jako argument zpoždění zpracování, dokud jsou uvolněny všechny zámky čtení.

Tato členská funkce není potřeba v prostředích s jedním uživatelem, pokud nejsou spuštěny více instancí aplikace. Členská `Idle` funkce může zvýšit výkon ve víceuživatelském prostředí, protože vynutí vyprázdnění dat databázového stroje na disk a uvolnění zámků v paměti. Můžete také uvolnit zámky čtení tím, že operace součástí transakce.

Související informace naleznete v tématu "Metoda nečinnosti" v nápovědě dao.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a>CDaoWorkspace::IsOpen

Volání této členské funkce `CDaoWorkspace` k určení, zda je objekt otevřený – to znamená, zda byl objekt knihovny MFC inicializován voláním [Otevřít](#open) nebo [voláním Create](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je objekt pracovního prostoru otevřený; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete volat některou z členských funkcí pracovního prostoru, který je v otevřeném stavu.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a>CDaoPracovní prostor::m_pDAOWorkspace

Ukazatel na základní objekt pracovního prostoru DAO.

### <a name="remarks"></a>Poznámky

Tento datový člen použijte, pokud potřebujete přímý přístup k podkladovému objektu DAO. Můžete volat rozhraní objektu DAO prostřednictvím tohoto ukazatele.

Informace o přímém přístupu k objektům DAO naleznete [v technické poznámce 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="cdaoworkspaceopen"></a><a name="open"></a>CDaoPracovní prostor::Otevřít

Explicitně otevře objekt pracovního prostoru přidružený k výchozímu pracovnímu prostoru DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Název objektu pracovního prostoru DAO, který se má otevřít – řetězec s až 14 znaky, který jedinečně pojmenuje pracovní prostor. Přijměte výchozí hodnotu NULL a explicitně otevřete výchozí pracovní prostor. Požadavky na pojmenování naleznete v parametru *lpszName* pro [příkaz Vytvořit](#create). Související informace naleznete v tématu "Name Property" v nápovědě dao.

### <a name="remarks"></a>Poznámky

Po vytvoření `CDaoWorkspace` objektu, volání této členské funkce provést jednu z následujících akcí:

- Explicitně otevřete výchozí pracovní prostor. Předat hodnotu NULL pro *lpszName*.

- Otevřete `CDaoWorkspace` existující objekt, člen kolekce Pracovní prostory, podle názvu. Předajte platný název existujícího objektu pracovního prostoru.

`Open`vloží objekt pracovního prostoru do otevřeného stavu a také inicializuje databázový stroj, pokud ještě nebyl inicializován pro vaši aplikaci.

Přestože `CDaoWorkspace` mnoho členských funkcí lze volat až po otevření pracovního prostoru, následující členské funkce, které pracují v databázovém stroji, jsou k dispozici po konstrukci objektu C++, ale před voláním `Open`:

||||
|-|-|-|
|[Vytvořit](#create)|[GetVersion](#getversion)|[Nastavitvýchozího uživatele](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Období](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a>CDaoWorkspace::Opravadatabáze

Volání této členské funkce, pokud potřebujete pokusit se opravit poškozenou databázi, která přistupuje k databázový stroj Microsoft Jet.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Cesta a název souboru pro existující databázový soubor motoru Microsoft Jet. Pokud cestu vynesete, bude prohledán pouze aktuální adresář. Pokud váš systém podporuje jednotnou konvenci pojmenování (UNC),\\\\\\můžete také\\zadat\\síťovou\\cestu, například: " \MYSERVER \MYSHARE \MYDIR \MYDB. MDB". (Dvojitá zpětná lomítka jsou\\vyžadována v řetězci cesty, protože " " je řídicí znak jazyka C++.)

### <a name="remarks"></a>Poznámky

Před opravou je nutné zavřít databázi určenou *společností lpszName.* Ve víceuživatelském prostředí nemohou mít ostatní uživatelé při opravě *lpszName otevřenou.* Pokud *lpszName* není uzavřena nebo není k dispozici pro výhradní použití, dojde k chybě.

Tato členská funkce se pokusí opravit databázi, která byla označena jako pravděpodobně poškozena neúplnou operací zápisu. Tato situace může nastat, pokud je aplikace používající databázový stroj Microsoft Jet neočekávaně uzavřena z důvodu výpadku napájení nebo problému s hardwarem počítače. Pokud dokončíte operaci a zavoláte [členovou](../../mfc/reference/cdaodatabase-class.md#close) funkci Zavřít nebo ukončíte aplikaci obvyklým způsobem, databáze nebude označena jako pravděpodobně poškozená.

> [!NOTE]
> Po opravě databáze je také vhodné ji komprimovat pomocí členské funkce [CompactDatabase](#compactdatabase) k defragmentaci souboru a obnovení místa na disku.

Další informace o opravách databází naleznete v tématu "RepairDatabase Method" v nápovědě dao.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a>CDaoWorkspace::Vrácení zpět

Volání této členské funkce ukončit aktuální transakci a obnovit všechny databáze v pracovním prostoru do jejich stavu před zahájením transakce.

```cpp
void Rollback();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> V rámci jednoho objektu pracovního prostoru jsou transakce vždy globální pro pracovní prostor a nejsou omezeny pouze na jednu databázi nebo sadu záznamů. Pokud provádíte operace s více než jednou databází nebo `Rollback` sadou záznamů v rámci transakce pracovního prostoru, obnoví všechny operace ve všech těchto databázích a sadách záznamů.

Pokud zavřete objekt pracovního prostoru bez uložení nebo vrácení zpět všechny čekající transakce, transakce jsou automaticky vráceny zpět. Pokud zavoláte [CommitTrans](#committrans) nebo `Rollback` bez prvního volání [BeginTrans](#begintrans), dojde k chybě.

> [!NOTE]
> Když zahájíte transakci, databázový stroj zaznamená své operace do souboru uchovávaném v adresáři určeném proměnnou prostředí TEMP na pracovní stanici. Pokud soubor protokolu transakcí vyčerpá dostupné úložiště na jednotce TEMP, databázový stroj způsobí, že knihovna `CDaoException` MFC vyvolá chybu (chyba DAO 2004). V tomto okamžiku, `CommitTrans`pokud zavoláte , neurčitý počet operací jsou potvrzeny, ale zbývající nedokončené operace jsou ztraceny a operace musí být restartován. Volání `Rollback` uvolní transakční protokol a vrátí zpět všechny operace v transakci.

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Volání této členské funkce nastavit výchozí heslo, které databázový stroj používá při vytvoření objektu pracovního prostoru bez určitého hesla.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszPassword*<br/>
Výchozí heslo. Heslo může mít až 14 znaků a může obsahovat libovolný znak kromě ASCII 0 (null). Hesla rozlišují malá a velká písmena.

### <a name="remarks"></a>Poznámky

Výchozí heslo, které nastavíte, se vztahuje na nové pracovní prostory, které vytvoříte po volání. Při vytváření následujících pracovních prostorů není nutné zadat heslo ve volání [Vytvořit.](#create)

Použití této členské funkce:

1. Vytvořte `CDaoWorkspace` objekt, ale `Create`nevolejte .

1. Volání `SetDefaultPassword` a, pokud chcete, [SetDefaultUser](#setdefaultuser).

1. Volání `Create` tohoto objektu pracovního prostoru nebo následné objekty bez zadání hesla.

Ve výchozím nastavení je vlastnost DefaultUser nastavena na "admin" a vlastnost DefaultPassword je nastavena na prázdný řetězec ("").

Další informace o zabezpečení najdete v tématu "Vlastnost oprávnění" v nápovědě dao. Související informace naleznete v tématech "Vlastnost DefaultPassword" a "Vlastnost defaultuser" v nápovědě DAO.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a>Prostor CDaoWorkspace::SetDefaultUser

Volánítéto členské funkce nastavit výchozí uživatelské jméno, které databázový stroj používá při vytvoření objektu pracovního prostoru bez konkrétního uživatelského jména.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parametry

*lpszDefaultUser*<br/>
Výchozí uživatelské jméno. Uživatelské jméno může mít velikost 1 až 20 znaků a může obsahovat abecední znaky, znaky s diakritikou, čísla, \[ \] mezery a symboly kromě: \< " (uvozovky), / (lomítko), \ (zpětné lomítko), (závorky), : (dvojtečka), &#124; (potrubí), (znaménko menší než), > (znaménko větší než), + (znaménko plus), = (rovnítko), ; (středník), , ( čárka), \* (otazník), (hvězdička), úvodní mezery a řídicí znaky (ASCII 00 až ASCII 31). Související informace naleznete v tématu "Vlastnost uživatelského_jména" v nápovědě dao.

### <a name="remarks"></a>Poznámky

Výchozí uživatelské jméno, které nastavíte, se vztahuje na nové pracovní prostory, které vytvoříte po volání. Při vytváření následujících pracovních prostorů není nutné zadat uživatelské jméno ve volání [Vytvořit.](#create)

Použití této členské funkce:

1. Vytvořte `CDaoWorkspace` objekt, ale `Create`nevolejte .

1. Volání `SetDefaultUser` a, pokud se vám líbí, [SetDefaultPassword](#setdefaultpassword).

1. Volání `Create` tohoto objektu pracovního prostoru nebo následujících objektů bez zadání uživatelského jména.

Ve výchozím nastavení je vlastnost DefaultUser nastavena na "admin" a vlastnost DefaultPassword je nastavena na prázdný řetězec ("").

Související informace naleznete v tématech "Vlastnost defaultuser" a "Vlastnost DefaultPassword" v nápovědě dao.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a>CDaoWorkspace::SetIniPath

Volání této členské funkce určit umístění nastavení registru systému Windows pro databázový stroj Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistryPodklíč*<br/>
Řetězec obsahující název podklíče registru systému Windows pro umístění nastavení databázového stroje Microsoft Jet nebo parametrů potřebných pro instalovatelné databáze ISAM.

### <a name="remarks"></a>Poznámky

Volejte `SetIniPath` pouze v případě, že potřebujete zadat speciální nastavení. Další informace naleznete v tématu "Vlastnost IniPath" v nápovědě DAO.

> [!NOTE]
> Volání `SetIniPath` během instalace aplikace, ne při spuštění aplikace. `SetIniPath`před otevřením pracovních prostorů, databází nebo sad záznamů musí být volána. v opačném případě knihovna MFC vyvolá výjimku.

Tento mechanismus můžete použít ke konfiguraci databázového stroje s uživatelským nastavením registru. Rozsah tohoto atributu je omezen na vaši aplikaci a nelze jej změnit bez restartování aplikace.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Volání této členské funkce nastavit hodnotu DAO IsolateODBCTrans vlastnost pro pracovní prostor.

```cpp
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parametry

*b IzololátODBCTrans*<br/>
Pokud chcete začít izolovat transakce ODBC, předajte hodnotu PRAVDA. Pokud chcete zastavit izolaci transakcí ODBC, předejte false.

### <a name="remarks"></a>Poznámky

V některých situacích může být nutné mít více souběžných transakcí čekajících na stejné databázi ODBC. Chcete-li to provést, musíte otevřít samostatný pracovní prostor pro každou transakci. Přestože každý pracovní prostor může mít vlastní připojení ODBC k databázi, zpomaluje to výkon systému. Vzhledem k tomu, že izolace transakcí není obvykle vyžadována, připojení ODBC z více objektů pracovního prostoru otevřených stejným uživatelem jsou ve výchozím nastavení sdílena.

Některé servery ODBC, například Microsoft SQL Server, neumožňují souběžné transakce v jednom připojení. Pokud potřebujete mít více než jednu transakci najednou čekající na tuto databázi, nastavte IsolateODBCTrans vlastnost TRUE na každém pracovním prostoru, jakmile ji otevřete. To vynutí samostatné připojení ODBC pro každý pracovní prostor.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout

Volání této členské funkce nastavit hodnotu DAO LoginTimeout vlastnost pro pracovní prostor.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSekundy*<br/>
Počet sekund před chybou dojde při pokusu o přihlášení k databázi ODBC.

### <a name="remarks"></a>Poznámky

Tato hodnota představuje počet sekund před výskytem chyby při pokusu o přihlášení k databázi ODBC. Výchozí nastavení LoginTimeout je 20 sekund. Pokud LoginTimeout je nastavena na 0, žádný časový limit dojde a komunikace se zdrojem dat může přestat reagovat.

Při pokusu o přihlášení k databázi ODBC, jako je například Microsoft SQL Server, může dojít k selhání připojení v důsledku chyb v síti nebo proto, že server není spuštěn. Místo čekání na výchozí 20 sekund připojení, můžete určit, jak dlouho databázový stroj čeká, než dojde k chybě. Přihlášení k serveru probíhá implicitně jako součást řady různých událostí, jako je například spuštění dotazu v databázi externího serveru. Hodnota časového limitu je určena aktuální nastavení LoginTimeout vlastnost.

Související informace naleznete v tématu "Vlastnost LoginTimeout" v nápovědě DAO.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
