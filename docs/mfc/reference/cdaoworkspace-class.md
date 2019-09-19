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
ms.openlocfilehash: 3e4ded466b673bff3c0630e798877b69d1ca384d
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096070"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace – třída

Spravuje pojmenovanou relaci databáze chráněnou heslem od přihlášení po odhlášení jedním uživatelem.

## <a name="syntax"></a>Syntaxe

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Vytvoří objekt pracovního prostoru. Potom zavolejte `Create` nebo `Open`.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|Připojí nově vytvořený pracovní prostor ke kolekci pracovních prostorů databázového stroje.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Spustí novou transakci, která se vztahuje na všechny databáze otevřené v pracovním prostoru.|
|[CDaoWorkspace:: Close](#close)|Zavře pracovní prostor a všechny objekty, které obsahuje. Transakce, které čekají na vyřízení, se vrátí zpět.|
|[CDaoWorkspace:: CommitTrans](#committrans)|Dokončí aktuální transakci a uloží změny.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Komprimuje (nebo duplikuje) databázi.|
|[CDaoWorkspace::Create](#create)|Vytvoří nový objekt pracovního prostoru rozhraní DAO.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Vrátí počet databázových objektů DAO v kolekci databází v pracovním prostoru.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Vrátí informace o zadané databázi DAO definované v kolekci databází v pracovním prostoru.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Vrátí umístění inicializačního nastavení databázového stroje Microsoft Jet v registru systému Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Vrátí hodnotu, která označuje, zda více transakcí zahrnující stejný zdroj dat ODBC jsou izolované prostřednictvím vynuceného více připojení ke zdroji dat.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Vrátí počet sekund, než dojde k chybě, když se uživatel pokusí přihlásit k databázi ODBC.|
|[CDaoWorkspace:: GetName](#getname)|Vrátí uživatelsky definovaný název objektu pracovního prostoru.|
|[CDaoWorkspace::GetUserName](#getusername)|Vrátí uživatelské jméno zadané při vytvoření pracovního prostoru. Toto je jméno vlastníka pracovního prostoru.|
|[CDaoWorkspace:: GetVersion](#getversion)|Vrátí řetězec, který obsahuje verzi databázového stroje přidruženého k pracovnímu prostoru.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Vrátí počet objektů pracovního prostoru DAO v kolekci pracovních prostorů databázového stroje.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Vrátí informace o zadaném pracovním prostoru DAO definovaném v kolekci pracovních prostorů databázového stroje.|
|[CDaoWorkspace::Idle](#idle)|Umožňuje databázovému stroji provádět úlohy na pozadí.|
|[CDaoWorkspace::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud je pracovní prostor otevřen.|
|[CDaoWorkspace::Open](#open)|Explicitně otevře objekt pracovního prostoru přidružený k výchozímu pracovnímu prostoru rozhraní DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Pokusí se opravit poškozenou databázi.|
|[CDaoWorkspace:: Rollback](#rollback)|Ukončí aktuální transakci a změny neuloží.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Nastaví heslo, které databázový stroj používá, když se vytvoří objekt pracovního prostoru bez konkrétního hesla.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Nastaví uživatelské jméno, které databázový stroj používá, když se vytvoří objekt pracovního prostoru bez konkrétního uživatelského jména.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Nastaví umístění inicializačního nastavení databázového stroje Microsoft Jet v registru systému Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Určuje, zda více transakcí zahrnujících stejný zdroj dat ODBC jsou izolované tím, že vynutí více připojení ke zdroji dat.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund, než dojde k chybě, když se uživatel pokusí přihlásit ke zdroji dat ODBC.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Odkazuje na podkladový objekt pracovního prostoru DAO.|

## <a name="remarks"></a>Poznámky

Ve většině případů nebudete potřebovat více pracovních prostorů a nebudete muset vytvářet explicitní objekty pracovního prostoru. Když otevřete databázi a objekty sady záznamů, používají výchozí pracovní prostor rozhraní DAO. V případě potřeby však můžete najednou spustit více relací vytvořením dalších objektů pracovního prostoru. Každý objekt pracovního prostoru může obsahovat více objektů Open Database v kolekci vlastních databází. V knihovně MFC je pracovní prostor primárně správce transakcí, přičemž určení sady otevřených databází je vše ve stejném "prostoru transakce".

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd knihovny MFC založených na rozhraní ODBC (Open Database Connectivity). Všechny názvy databázových tříd DAO mají předponu "CDao". Obecně jsou třídy knihovny MFC založené na rozhraní DAO větší, než třídy knihovny MFC založené na rozhraní ODBC. Třídy založené na rozhraní DAO mají přístup k datům prostřednictvím databázového stroje Microsoft Jet, včetně ovladačů ODBC. Podporují také operace DDL (Data Definition Language), jako je vytváření databází a přidávání tabulek a polí přes třídy, aniž by museli volat rozhraní DAO přímo.

## <a name="capabilities"></a>Možnosti

Třída `CDaoWorkspace` poskytuje následující:

- V případě potřeby explicitní přístup k výchozímu pracovnímu prostoru vytvořenému inicializací databázového stroje. Obvykle se výchozí pracovní prostor pro rozhraní DAO používá implicitně vytvořením objektu databáze a sady záznamů.

- Místo transakce, ve kterém se transakce vztahují na všechny databáze otevřené v pracovním prostoru. Můžete vytvořit další pracovní prostory pro správu oddělených prostorů transakcí.

- Rozhraní pro mnoho vlastností základního databázového stroje Microsoft Jet (viz statické členské funkce). Otevřením nebo vytvořením pracovního prostoru nebo voláním statické členské funkce před otevřením nebo vytvořením inicializujete databázový stroj.

- Přístup ke kolekci pracovních prostorů databázového stroje, ve kterém jsou uloženy všechny aktivní pracovní prostory, které jsou k ní připojeny. Můžete také vytvořit pracovní prostory a pracovat s nimi bez jejich připojení ke kolekci.

## <a name="security"></a>Zabezpečení

Knihovna MFC neimplementuje kolekce uživatelů a skupin v rozhraní DAO, které se používají pro řízení zabezpečení. Pokud potřebujete tyto aspekty rozhraní DAO, je nutné je naprogramovat prostřednictvím přímých volání rozhraní DAO. Informace najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Použití

Třídu `CDaoWorkspace` můžete použít k těmto akcím:

- Explicitně otevřete výchozí pracovní prostor.

   Obvykle je používání výchozího pracovního prostoru implicitní – když otevřete nové objekty [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) . K tomu ale budete muset přistupovat explicitně – například pro přístup k vlastnostem databázového stroje nebo ke kolekci pracovních prostorů. Viz téma implicitní použití výchozího pracovního prostoru.

- Vytvořte nové pracovní prostory. Pokud je chcete přidat do kolekce pracovních prostorů, zavolejte [připojit](#append) .

- V kolekci pracovních prostorů otevřete existující pracovní prostor.

Vytvoření nového pracovního prostoru, který ještě neexistuje v kolekci pracovních prostorů, je popsán v části [Vytvoření](#create) členské funkce. Objekty pracovního prostoru nezůstávají mezi relacemi datababase Engine jakýmkoli způsobem. Pokud vaše aplikace propojuje knihovnu MFC staticky, aplikace ukončí inicializaci databázového stroje. Pokud je aplikace propojena s knihovnou MFC dynamicky, databázový stroj není inicializován při uvolnění knihovny MFC DLL.

Explicitní otevření výchozího pracovního prostoru nebo otevření existujícího pracovního prostoru v kolekci pracovních prostorů je popsáno v části [otevřená](#open) členská funkce.

Ukončení relace pracovního prostoru zavřením pracovního prostoru pomocí členské funkce [Close](#close) . `Close`zavře všechny databáze, které jste předtím nezavřeli, vrácení jakýchkoli nepotvrzených transakcí.

## <a name="transactions"></a>Transakce
Rozhraní DAO 3,6 je finální verze a je považována za zastaralou. spravuje transakce na úrovni pracovního prostoru. Proto se transakce v pracovním prostoru s více otevřenými databázemi vztahují na všechny databáze. Například pokud mají dvě databáze nepotvrzené aktualizace a zavoláte [CommitTrans](#committrans), všechny aktualizace se potvrdí. Pokud chcete omezit transakce na izolovanou databázi, potřebujete pro ni samostatný objekt pracovní prostor.

## <a name="implicit-use-of-the-default-workspace"></a>Implicitní použití výchozího pracovního prostoru

Knihovna MFC používá implicitně výchozí pracovní prostor rozhraní DAO za následujících okolností:

- Pokud vytvoříte nový `CDaoDatabase` objekt, ale neuděláte to prostřednictvím existujícího `CDaoWorkspace` objektu, knihovna MFC vytvoří pro vás dočasný objekt pracovního prostoru, který odpovídá výchozímu pracovnímu prostoru rozhraní DAO. Pokud tak učiníte pro více databází, všechny databázové objekty jsou přidruženy k výchozímu pracovnímu prostoru. K pracovnímu prostoru databáze můžete přistupovat prostřednictvím `CDaoDatabase` datového členu.

- Podobně pokud vytvoříte `CDaoRecordset` objekt bez zadání ukazatele `CDaoDatabase` na objekt, knihovna MFC vytvoří dočasný objekt databáze a pomocí rozšíření objekt dočasného pracovního prostoru. Můžete přistupovat k databázi sady záznamů a nepřímo její pracovní prostor prostřednictvím `CDaoRecordset` datového členu.

## <a name="other-operations"></a>Jiné operace

K dispozici jsou také další databázové operace, například oprava poškozené databáze nebo komprimace databáze.

Informace o přímém volání rozhraní DAO a o zabezpečení rozhraní DAO najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="append"></a>CDaoWorkspace:: Append

Po volání metody [Create](#create)volejte tuto členskou funkci.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

`Append`připojí nově vytvořený objekt pracovního prostoru k kolekci pracovních prostorů databázového stroje. Pracovní prostory nemusíte zachovávat mezi relacemi databázového stroje. jsou uloženy pouze v paměti, nikoli na disku. Nemusíte připojovat pracovní prostor. Pokud to neuděláte, můžete ho dál používat.

Připojený pracovní prostor zůstane v kolekci pracovních prostorů v aktivním otevřeném stavu, dokud nebudete volat jeho členskou funkci [Close](#close) .

Související informace naleznete v tématu "připojit metodu" v nápovědě k rozhraní DAO.

##  <a name="begintrans"></a>CDaoWorkspace::BeginTrans

Zavolejte tuto členskou funkci pro zahájení transakce.

```
void BeginTrans();
```

### <a name="remarks"></a>Poznámky

Po volání `BeginTrans`se aktualizace provedené v datech nebo struktuře databáze projeví po potvrzení transakce. Vzhledem k tomu, že pracovní prostor definuje jeden transakční prostor, transakce se vztahuje na všechny otevřené databáze v pracovním prostoru. Existují dva způsoby, jak transakci dokončit:

- Zavolejte členskou funkci [CommitTrans](#committrans) a potvrďte transakci a uložte změny do zdroje dat.

- Nebo zavolejte členskou funkci [vrácení zpět](#rollback) pro zrušení transakce.

Zavřením objektu pracovního prostoru nebo databázového objektu v době, kdy transakce čeká na vyřízení, se vrátí všechny probíhající transakce.

Pokud potřebujete izolovat transakce v jednom zdroji dat ODBC od těch na jiném zdroji dat ODBC, přečtěte si část členská funkce [SetIsolateODBCTrans](#setisolateodbctrans) .

##  <a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

`CDaoWorkspace` Vytvoří objekt.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Poznámky

Po sestavení C++ objektu máte dvě možnosti:

- Voláním [otevřené](#open) členské funkce objektu otevřete výchozí pracovní prostor nebo otevřete existující objekt v kolekci pracovních prostorů.

- Nebo zavolejte funkci [Vytvoření](#create) členské funkce objektu pro vytvoření nového objektu pracovního prostoru DAO. Tím se explicitně spustí nová relace pracovního prostoru, na kterou můžete odkazovat prostřednictvím `CDaoWorkspace` objektu. Po volání `Create`můžete zavolat příkaz [připojit](#append) , pokud chcete přidat pracovní prostor do kolekce pracovních prostorů databázového stroje.

Informace o tom, kdy [](../../mfc/reference/cdaoworkspace-class.md) potřebujete explicitně vytvořit `CDaoWorkspace` objekt, najdete v přehledu třídy pro CDaoWorkspace. Běžně se používají pracovní prostory vytvořené implicitně při otevření objektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) bez zadání pracovního prostoru nebo při otevření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) bez zadání databázového objektu. Objekty knihovny MFC DAO vytvořené tímto způsobem používají výchozí pracovní prostor rozhraní DAO, který je vytvořen jednou a znovu použit.

Chcete-li uvolnit pracovní prostor a jeho obsažené objekty, zavolejte členskou funkci [Close](#close) objektu pracovního prostoru.

##  <a name="close"></a>CDaoWorkspace:: Close

Chcete-li zavřít objekt pracovního prostoru, zavolejte tuto členskou funkci.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Zavřením otevřeného objektu pracovního prostoru uvolníte základní objekt DAO a, pokud je pracovní prostor členem kolekce pracovních prostorů, odeberete jej z kolekce. Volání `Close` je dobrým programovacím postupem.

> [!CAUTION]
>  Při zavření objektu pracovního prostoru se zavře všechny otevřené databáze v pracovním prostoru. To vede k tomu, že všechny sady záznamů jsou otevřeny i v zavřených databázích a všechny probíhající úpravy nebo aktualizace se vrátí zpět. Související informace naleznete v tématu [CDaoDatabase:: Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset:: Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef:: Close](../../mfc/reference/cdaotabledef-class.md#close)a [CDaoQueryDef:: Close](../../mfc/reference/cdaoquerydef-class.md#close) Member functions.

Objekty pracovního prostoru nejsou trvalé; Existují pouze v případě, že existují odkazy na ně. To znamená, že v případě, že dojde k ukončení relace databázového stroje, pracovní prostor a kolekce jeho databází nezůstanou zachovány. Pro další relaci je třeba je znovu vytvořit tak, že znovu otevřete pracovní prostor a databázi.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "Close Method".

##  <a name="committrans"></a>CDaoWorkspace:: CommitTrans

Zavolejte tuto členskou funkci pro potvrzení transakce – uložte skupinu úprav a aktualizací do jedné nebo více databází v pracovním prostoru.

```
void CommitTrans();
```

### <a name="remarks"></a>Poznámky

Transakce se skládá z řady změn dat databáze nebo její struktury, počínaje voláním [BeginTrans](#begintrans). Po dokončení transakce ji buď potvrďte, nebo vraťte zpět (změny) s [vrácením](#rollback)zpět. Ve výchozím nastavení bez transakcí jsou aktualizace záznamů potvrzeny okamžitě. Volání `BeginTrans` způsobí, že budou aktualizace zpožděny, dokud nebudete volat `CommitTrans`.

> [!CAUTION]
>  V rámci jednoho pracovního prostoru jsou transakce vždy globální k pracovnímu prostoru a nejsou omezeny pouze na jednu databázi nebo sadu záznamů. Pokud provádíte operace s více než jednou databází nebo sadou záznamů v rámci transakce pracovního `CommitTrans` prostoru, potvrdí všechny probíhající aktualizace a `Rollback` obnoví všechny operace s těmito databázemi a sadami záznamů.

Když zavřete databázi nebo pracovní prostor s nevyřízenými transakcemi, všechny transakce se vrátí zpět.

> [!NOTE]
>  Toto není dvoufázové mechanizmus potvrzení. V případě, že se jedna aktualizace nepodaří potvrdit, ostatní budou i nadále potvrzeny.

##  <a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

Zavolejte tuto členskou funkci pro komprimaci zadaného Microsoft Jet (. MDB) databáze.

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

*lpszSrcName*<br/>
Název existující uzavřené databáze. Může se jednat o úplnou cestu a název souboru, například "C:\\\MYDB. MDB ". Pokud má název souboru příponu, je nutné ji zadat. Pokud vaše síť podporuje konvence UNC (Uniform Naming Convention), můžete také zadat síťovou cestu, například "\\\\\\\\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB. MDB ". (V řetězcích cest jsou vyžadovány dvojité zpětné lomítko,\\protože "" C++ je řídicí znak.)

*lpszDestName*<br/>
Úplná cesta zkomprimované databáze, kterou vytváříte. Můžete také zadat síťovou cestu jako s *lpszSrcName*. Argument *lpszDestName* nelze použít k určení stejného databázového souboru jako *lpszSrcName*.

*lpszPassword*<br/>
Heslo, které se používá, když chcete zkomprimovat databázi chráněnou heslem. Všimněte si, že pokud používáte verzi `CompactDatabase` nástroje, která používá heslo, je nutné zadat všechny parametry. Vzhledem k tomu, že se jedná o parametr připojení, vyžaduje speciální formátování následujícím způsobem:; PWD = *lpszPassword*. Příklad:; PWD = "veselé". (Je vyžadován hlavní středník.)

*lpszLocale*<br/>
Řetězcový výraz, který slouží k zadání pořadí řazení pro vytváření *lpszDestName*. Pokud tento argument vynecháte tak, že přijmete `dbLangGeneral` výchozí hodnotu (viz níže), národní prostředí nové databáze je stejné jako u staré databáze. Možné hodnoty jsou:

- `dbLangGeneral`Angličtina, němčina, francouzština, portugalština, italština a moderní španělština

- `dbLangArabic`Arabština

- `dbLangCyrillic`Ruština

- `dbLangCzech`Čeština

- `dbLangDutch`Holandština

- `dbLangGreek`Řečtina

- `dbLangHebrew`Hebrejština

- `dbLangHungarian`Maďarština

- `dbLangIcelandic`Islandština

- `dbLangNordic`Severské jazyky (jenom databázový stroj Microsoft Jet verze 1,0)

- `dbLangNorwdan`Norština a Dánština

- `dbLangPolish`Polština

- `dbLangSpanish`Tradiční španělština

- `dbLangSwedfin`Švédština a finština

- `dbLangTurkish`Turečtina

*nOptions*<br/>
Označuje jednu nebo více možností pro cílovou databázi *lpszDestName*. Pokud tento argument vynecháte přijetím výchozí hodnoty, bude mít *lpszDestName* stejné šifrování a stejnou verzi jako *lpszSrcName*. Můžete zkombinovat `dbEncrypt` parametr nebo `dbDecrypt` s jednou z možností verze pomocí bitového operátoru OR. Možné hodnoty, které určují formát databáze, nikoli verzi databázového stroje, jsou:

- `dbEncrypt`Zašifruje databázi během komprimace.

- `dbDecrypt`Dešifrování databáze během komprimace.

- `dbVersion10`Vytvořte databázi, která při komprimaci používá databázový stroj Microsoft Jet verze 1,0.

- `dbVersion11`Vytvořte databázi, která při komprimaci používá databázový stroj Microsoft Jet verze 1,1.

- `dbVersion20`Vytvořte databázi, která při komprimaci používá databázový stroj Microsoft Jet verze 2,0.

- `dbVersion30`Vytvořte databázi, která při komprimaci používá databázový stroj Microsoft Jet verze 3,0.

Můžete použít `dbEncrypt` nebo `dbDecrypt` v argumentu Options (možnosti) k určení, jestli se má šifrovat nebo dešifrovat databáze během komprimace. Pokud vynecháte šifrovací konstantu nebo pokud zahrnete `dbDecrypt` `dbEncrypt`i, *lpszDestName* bude mít stejné šifrování jako *lpszSrcName*. K určení verze formátu dat pro zkomprimovanou databázi můžete použít jednu z konstant verze v argumentu Options. Tato konstanta má vliv pouze na verzi formátu dat *lpszDestName*. Můžete zadat jenom jednu konstantu verze. Pokud vynecháte konstantu verze, *lpszDestName* bude mít stejnou verzi jako *lpszSrcName*. *LpszDestName* lze zkomprimovat pouze na verzi, která je stejná nebo vyšší než u *lpszSrcName*.

> [!CAUTION]
>  Pokud není databáze šifrována, je možné, že i když implementujete zabezpečení uživatele nebo hesla, můžete přímo číst soubor binárního disku, který tvoří databázi.

### <a name="remarks"></a>Poznámky

Když měníte data v databázi, může se soubor databáze fragmentovat a použít více místa na disku, než je potřeba. Pravidelně byste měli zkomprimovat databázi pro defragmentaci databázového souboru. Zkomprimovaná databáze je obvykle menší. Můžete také změnit pořadí řazení, šifrování nebo verzi formátu dat při kopírování a komprimaci databáze.

> [!CAUTION]
>  `CompactDatabase` Členská funkce neprovede správně převod úplné databáze aplikace Microsoft Access z jedné verze na jinou. Převede se jenom datový formát. Objekty definované Microsoft Accessem, jako jsou například formuláře a sestavy, nejsou převedeny. Data jsou však správně převedena.

> [!TIP]
>  Můžete také použít `CompactDatabase` ke zkopírování databázového souboru.

Další informace o komprimaci databází naleznete v tématu "metoda CompactDatabase" v nápovědě pro rozhraní DAO.

##  <a name="create"></a>CDaoWorkspace:: Create

Zavolejte tuto členskou funkci pro vytvoření nového objektu pracovního prostoru DAO a přidružte jej k objektu knihovny `CDaoWorkspace` MFC.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězec s maximálně 14 znaky, který jedinečně pojmenovává nový objekt pracovního prostoru. Je nutné, abyste zadali jméno. Související informace najdete v tématu "vlastnost Name" v nápovědě k rozhraní DAO.

*lpszUserName*<br/>
Uživatelské jméno vlastníka pracovního prostoru Požadavky naleznete v parametru *lpszDefaultUser* členské funkce [SetDefaultUser](#setdefaultuser) . Související informace najdete v nápovědě k rozhraní DAO v tématu vlastnost UserName.

*lpszPassword*<br/>
Heslo nového objektu pracovního prostoru Heslo může mít délku až 14 znaků a může obsahovat libovolný znak kromě ASCII 0 (null). V heslech se rozlišují malá a velká písmena. Související informace naleznete v tématu "vlastnost hesla" v nápovědě k rozhraní DAO.

### <a name="remarks"></a>Poznámky

Celkový proces tvorby:

1. Sestavte objekt [CDaoWorkspace](#cdaoworkspace) .

1. Chcete-li vytvořit `Create` základní pracovní prostor DAO, zavolejte členskou funkci objektu. Je nutné zadat název pracovního prostoru.

1. Volitelně můžete zavolat [připojit](#append) , pokud chcete přidat pracovní prostor do kolekce pracovních prostorů databázového stroje. Pracovní prostor můžete pracovat bez jeho připojení.

`Create` Po volání je objekt pracovního prostoru v otevřeném stavu připravený k použití. Nevoláte `Open` se ani `Create`po. Nevoláte `Create` , pokud pracovní prostor už existuje v kolekci pracovních prostorů. `Create`Inicializuje databázový stroj, pokud ještě není pro vaši aplikaci inicializovaný.

##  <a name="getdatabasecount"></a>CDaoWorkspace::GetDatabaseCount

Voláním této členské funkce načtěte počet objektů databáze DAO v kolekci databází v pracovním prostoru – počet otevřených databází v pracovním prostoru.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet otevřených databází v pracovním prostoru.

### <a name="remarks"></a>Poznámky

`GetDatabaseCount`je užitečné v případě, že potřebujete projít všechny definované databáze v kolekci databází v pracovním prostoru. Informace o dané databázi v kolekci najdete v tématu [GetDatabaseInfo](#getdatabaseinfo). Typickým využitím je `GetDatabaseCount` zavolat na počet otevřených databází a potom použít toto číslo jako index smyčky pro opakovaná `GetDatabaseInfo`volání.

##  <a name="getdatabaseinfo"></a>CDaoWorkspace::GetDatabaseInfo

Tuto členskou funkci volejte pro získání různých druhů informací o databázi otevřené v pracovním prostoru.

```
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
Index objektu databáze v kolekci databází v pracovním prostoru založený na nule, pro vyhledávání podle indexu.

*dbinfo*<br/>
Odkaz na objekt [CDaoDatabaseInfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) , který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace databáze se mají načíst. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí:

- AFX_DAO_PRIMARY_INFO (výchozí) název, aktualizovatelné, transakce

- Primární informace AFX_DAO_SECONDARY_INFO plus: Verze, pořadí řazení, časový limit dotazu

- Primární a sekundární informace AFX_DAO_ALL_INFO plus: Síti

*lpszName*<br/>
Název databázového objektu pro vyhledávání podle názvu Název je řetězec s maximálně 14 znaky, který jedinečně pojmenuje nový objekt pracovního prostoru.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat databázi podle indexu. Druhá verze umožňuje vyhledat databázi podle názvu.

Popis informací vrácených v *dbinfo*najdete v tématu struktura [CDaoDatabaseInfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Když si vyžádáte informace na jedné úrovni, získáte informace také pro všechny předchozí úrovně.

##  <a name="getinipath"></a>CDaoWorkspace::GetIniPath

Tuto členskou funkci volejte pro získání umístění inicializačního nastavení databázového stroje Microsoft Jet v registru systému Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující umístění registru.

### <a name="remarks"></a>Poznámky

K získání informací o nastavení pro databázový stroj můžete použít umístění. Vrácené informace jsou ve skutečnosti názvem podklíče registru.

Související informace naleznete v tématech "IniPath Property" a "Přizpůsobení nastavení registru systému Windows pro přístup k datům" v nápovědě k rozhraním DAO.

##  <a name="getisolateodbctrans"></a>CDaoWorkspace::GetIsolateODBCTrans

Voláním této členské funkce získáte aktuální hodnotu vlastnosti DAO IsolateODBCTrans pro daný pracovní prostor.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou transakce rozhraní ODBC izolované; v opačném případě 0.

### <a name="remarks"></a>Poznámky

V některých situacích možná budete muset ve stejné databázi ODBC čekat na více souběžných transakcí. K tomu je třeba otevřít samostatný pracovní prostor pro každou transakci. Mějte na paměti, že přestože každý pracovní prostor může mít své vlastní připojení ODBC k databázi, zpomaluje výkon systému. Vzhledem k tomu, že se nepožaduje izolovaná transakce, budou se ve výchozím nastavení sdílet připojení ODBC z více objektů otevřených stejným uživatelem.

Některé servery ODBC, například Microsoft SQL Server, neumožňují souběžné transakce v jednom připojení. Pokud potřebujete mít v době čekání na takovou databázi více než jednu transakci, nastavte vlastnost IsolateODBCTrans na hodnotu TRUE v každém pracovním prostoru hned po jejím otevření. Tím se vynutí samostatné připojení ODBC pro každý pracovní prostor.

Související informace najdete v tématu "vlastnost IsolateODBCTrans" v nápovědě k rozhraní DAO.

##  <a name="getlogintimeout"></a>CDaoWorkspace::GetLoginTimeout

Voláním této členské funkce získáte aktuální hodnotu vlastnosti DAO LoginTimeout pro daný pracovní prostor.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC.

### <a name="remarks"></a>Poznámky

Tato hodnota představuje počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC. Výchozí nastavení LoginTimeout je 20 sekund. Když je LoginTimeout nastavené na 0, neproběhne žádný časový limit a komunikace se zdrojem dat může přestat reagovat.

Při pokusu o přihlášení k databázi ODBC, jako je například Microsoft SQL Server, může připojení selhat v důsledku chyb sítě nebo proto, že server není spuštěn. Místo toho, aby se čekalo na připojení výchozích 20 sekund, můžete určit, jak dlouho bude databázový stroj čekat před tím, než vyvolá chybu. Přihlášení k serveru probíhá implicitně jako součást řady různých událostí, jako je například spuštění dotazu na externí databázi serveru.

Související informace najdete v tématu "Vlastnost LoginTimeout" v nápovědě k rozhraní DAO.

##  <a name="getname"></a>CDaoWorkspace:: GetName

Zavolejte tuto členskou funkci, aby získala uživatelsky definovaný název objektu pracovního prostoru DAO, který `CDaoWorkspace` je základem objektu.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující uživatelsky definovaný název objektu pracovního prostoru rozhraní DAO.

### <a name="remarks"></a>Poznámky

Název je vhodný pro přístup k objektu pracovního prostoru DAO v kolekci pracovních prostorů databázového stroje podle názvu.

Související informace najdete v tématu "vlastnost Name" v nápovědě k rozhraní DAO.

##  <a name="getusername"></a>CDaoWorkspace:: getuživatelské_jméno

Zavolejte tuto členskou funkci, aby získala jméno vlastníka pracovního prostoru.

```
CString GetUserName();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) , která představuje vlastníka objektu pracovního prostoru.

### <a name="remarks"></a>Poznámky

Chcete-li získat nebo nastavit oprávnění vlastníka pracovního prostoru, zavolejte přímo rozhraní DAO a ověřte nastavení vlastnosti oprávnění; Tím určíte, jaká oprávnění uživatel má. K práci s oprávněními potřebujete systém. Soubor MDA.

Informace o přímém volání rozhraní DAO naleznete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Související informace najdete v nápovědě k rozhraní DAO v tématu vlastnost UserName.

##  <a name="getversion"></a>CDaoWorkspace:: GetVersion

Zavolejte tuto členskou funkci k určení používané verze databázového stroje Microsoft Jet.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) , která označuje verzi databázového stroje přidruženého k objektu.

### <a name="remarks"></a>Poznámky

Vrácená hodnota představuje číslo verze ve formátu "hlavní_verze. podverze"; například "3,0". Číslo verze produktu (například 3,0) se skládá z čísla verze (3), tečky a čísla vydání (0).

Související informace naleznete v tématu "vlastnost verze" v nápovědě rozhraní DAO.

##  <a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

Voláním této členské funkce načtěte počet objektů v pracovním prostoru DAO v kolekci pracovních prostorů databázového stroje.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet otevřených pracovních prostorů v kolekci pracovních prostorů.

### <a name="remarks"></a>Poznámky

Tento počet neobsahuje žádné otevřené pracovní prostory, které nejsou připojeny k této kolekci. `GetWorkspaceCount`je užitečná v případě, že potřebujete projít všemi definovanými pracovními prostory v kolekci pracovních prostorů. Informace o daném pracovním prostoru v kolekci najdete v tématu [GetWorkspaceInfo](#getworkspaceinfo). Typickým využitím je `GetWorkspaceCount` zavolat na počet otevřených pracovních prostorů a potom použít toto číslo jako index smyčky pro opakovaná `GetWorkspaceInfo`volání.

##  <a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

Tuto členskou funkci volejte pro získání různých druhů informací o pracovním prostoru otevřeném v relaci.

```
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
Index objektu databáze založený na nule v kolekci pracovních prostorů pro vyhledávání podle indexu.

*wkspcinfo*<br/>
Odkaz na objekt [CDaoWorkspaceInfo –](../../mfc/reference/cdaoworkspaceinfo-structure.md) , který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o pracovním prostoru mají být načteny. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí:

- AFX_DAO_PRIMARY_INFO (výchozí) název

- Primární informace AFX_DAO_SECONDARY_INFO plus: Uživatelské jméno

- Primární a sekundární informace AFX_DAO_ALL_INFO plus: Izolovat ODBCTrans

*lpszName*<br/>
Název objektu pracovního prostoru pro vyhledávání podle názvu Název je řetězec s maximálně 14 znaky, který jedinečně pojmenuje nový objekt pracovního prostoru.

### <a name="remarks"></a>Poznámky

Popis informací vrácených v *wkspcinfo*najdete v tématu struktura [CDaoWorkspaceInfo –](../../mfc/reference/cdaoworkspaceinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Když si vyžádáte informace na jedné úrovni, získáte informace i pro předchozí úrovně.

##  <a name="idle"></a>CDaoWorkspace:: Idle

Zavolejte `Idle` na poskytnutí databázového stroje s příležitostí k provádění úloh na pozadí, které nemusí být aktuální kvůli náročnému zpracování dat.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parametry

*Nvýstup akce*<br/>
Akce, která má být provedena během nečinného zpracování. V současné době se jedná `dbFreeLocks`o jedinou platnou akci.

### <a name="remarks"></a>Poznámky

To je často pravdivé v prostředích s více úlohami s více uživateli, ve kterých není dostatek času na zpracování na pozadí, aby bylo možné uchovávat všechny záznamy v aktuální sadě záznamů.

> [!NOTE]
>  Pro `Idle` databáze vytvořené s verzí 3,0 databázového stroje Microsoft Jet není volání nutné. Používejte `Idle` pouze pro databáze vytvořené s dřívějšími verzemi.

Obvykle jsou zámky čtení odebrány a data v místních dynamických sadách jsou aktualizována pouze v případě, že nedochází k žádné jiné akci (včetně pohybů myši). Pokud pravidelně voláte `Idle`, poskytnete databázovému stroji čas pro zachycení úloh zpracování na pozadí uvolněním nepotřebných zámků pro čtení. `dbFreeLocks` Určení konstanty jako zpoždění zpracování argumentů, dokud nejsou uvolněny všechny zámky pro čtení.

Tato členská funkce není potřebná v prostředích s jedním uživatelem, pokud není spuštěno více instancí aplikace. `Idle` Členská funkce může zvýšit výkon ve víceuživatelském prostředí, protože vynutí databázovému stroji vyprázdnit data na disk a uvolnit zámky paměti. Zámky pro čtení můžete také uvolnit tím, že provedete provozní část transakce.

Související informace naleznete v tématu "metoda nečinnosti" v nápovědě pro rozhraní DAO.

##  <a name="isopen"></a>CDaoWorkspace:: Open

Voláním této členské funkce určíte, `CDaoWorkspace` zda je objekt otevřen. to znamená, zda byl objekt knihovny MFC inicializován voláním metody [Open](#open) nebo voláním metody [Create](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je otevřen objekt pracovního prostoru; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Můžete zavolat kteroukoli z členských funkcí pracovního prostoru, který je v otevřeném stavu.

##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace

Ukazatel na podkladový objekt pracovního prostoru DAO.

### <a name="remarks"></a>Poznámky

Tento datový člen použijte v případě, že potřebujete přímý přístup k základnímu objektu DAO. Pomocí tohoto ukazatele můžete volat rozhraní objektu DAO.

Informace o přímý přístup k objektům DAO naleznete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>CDaoWorkspace:: Open

Explicitně otevře objekt pracovního prostoru přidružený k výchozímu pracovnímu prostoru rozhraní DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název objektu pracovního prostoru DAO, který se má otevřít – řetězec, který má až 14 znaků, který jedinečně pojmenovává pracovní prostor. Přijměte výchozí hodnotu NULL, aby se explicitně otevřel výchozí pracovní prostor. Požadavky na pojmenování najdete v parametru *lpszName* pro příkaz [Create](#create). Související informace najdete v tématu "vlastnost Name" v nápovědě k rozhraní DAO.

### <a name="remarks"></a>Poznámky

Po sestavení `CDaoWorkspace` objektu volejte tuto členskou funkci, aby provede jednu z následujících akcí:

- Explicitně otevřete výchozí pracovní prostor. Předat hodnotu NULL pro *lpszName*.

- Otevřete existující `CDaoWorkspace` objekt, člen kolekce pracovních prostorů podle názvu. Předejte platný název pro existující objekt pracovního prostoru.

`Open`Vloží objekt pracovního prostoru do otevřeného stavu a také inicializuje databázový stroj, pokud ještě nebyl pro vaši aplikaci inicializován.

I když `CDaoWorkspace` mnoho členských funkcí lze volat pouze po otevření pracovního prostoru, jsou následující členské funkce, které pracují s databázovým strojem, dostupné po konstrukci C++ objektu, ale před voláním `Open`:

||||
|-|-|-|
|[Vytvoření](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Volnoběž](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Pokud se potřebujete pokusit opravit poškozenou databázi, která přistupuje k databázovému stroji Microsoft Jet, volejte tuto členskou funkci.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Cesta a název souboru pro existující soubor databáze Microsoft Jet Engine. Pokud cestu vynecháte, bude prohledán pouze aktuální adresář. Pokud váš systém podporuje konvence UNC (Uniform Naming Convention), můžete také zadat síťovou cestu, například: "\\\\\\\\\MYSERVER\\\MYSHARE \MYDIR\\\MYDB. MDB ". (V řetězci cesty jsou vyžadovány dvojité zpětné lomítko, protože\\"" je C++ řídicí znak.)

### <a name="remarks"></a>Poznámky

Před opravou databáze musíte zavřít databázi určenou nástrojem *lpszName* . Ve víceuživatelském prostředí nemůžou jiní uživatelé mít *lpszName* otevřený, když ho opravíte. Pokud *lpszName* není uzavřený nebo není k dispozici pro výhradní použití, dojde k chybě.

Tato členská funkce se pokouší opravit databázi, která byla označena jako možná poškozená nekompletní operací zápisu. Tato situace může nastat, pokud je aplikace používající databázový stroj Microsoft Jet neočekávaně ukončena z důvodu výpadku napájení nebo problému s hardwarem počítače. Pokud dokončíte operaci a zavoláte členskou funkci [Close](../../mfc/reference/cdaodatabase-class.md#close) nebo neukončíte aplikaci obvyklým způsobem, databáze nebude označena jako možná poškozená.

> [!NOTE]
>  Po opravě databáze je také vhodné ji zkomprimovat pomocí členské funkce [CompactDatabase](#compactdatabase) k defragmentaci souboru a k obnovení místa na disku.

Další informace o opravách databází naleznete v tématu "metoda RepairDatabase" v nápovědě k rozhraní DAO.

##  <a name="rollback"></a>CDaoWorkspace:: Rollback

Zavolejte tuto členskou funkci pro ukončení aktuální transakce a obnovte všechny databáze v pracovním prostoru do podmínky před zahájením transakce.

```
void Rollback();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  V rámci jednoho objektu pracovního prostoru jsou transakce vždy globální k pracovnímu prostoru a nejsou omezeny pouze na jednu databázi nebo sadu záznamů. Pokud provádíte operace s více než jednou databází nebo sadou záznamů v rámci transakce pracovního `Rollback` prostoru, obnoví všechny operace ve všech těchto databázích a sadách záznamů.

Pokud zavřete objekt pracovního prostoru bez uložení nebo vrácení všech nevyřízených transakcí, transakce se automaticky vrátí zpět. Pokud zavoláte metodu `Rollback` [CommitTrans](#committrans) nebo bez prvního volání [BeginTrans](#begintrans), dojde k chybě.

> [!NOTE]
>  Po zahájení transakce se databázový stroj zaznamená jeho operace do souboru uchovávaného v adresáři určeném proměnnou prostředí TEMP v pracovní stanici. Pokud soubor protokolu transakcí vyčerpá dostupné úložiště na dočasném disku, vyvolá databázový stroj knihovnu MFC `CDaoException` (chyba rozhraní DAO 2004). V tomto okamžiku, pokud voláte `CommitTrans`, je potvrzen neurčitý počet operací, ale zbývající nedokončené operace jsou ztraceny a operace musí být restartována. Volání `Rollback` uvolní transakční protokol a vrátí všechny operace v transakci.

##  <a name="setdefaultpassword"></a>CDaoWorkspace::SetDefaultPassword

Zavolejte tuto členskou funkci pro nastavení výchozího hesla, které databázový stroj používá, když je vytvořen objekt pracovního prostoru bez konkrétního hesla.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszPassword*<br/>
Výchozí heslo Heslo může mít délku až 14 znaků a může obsahovat libovolný znak kromě ASCII 0 (null). V heslech se rozlišují malá a velká písmena.

### <a name="remarks"></a>Poznámky

Výchozí heslo, které nastavíte, se použije na nové pracovní prostory, které vytvoříte po volání. Při vytváření dalších pracovních prostorů není nutné zadávat heslo ve volání metody [Create](#create) .

Chcete-li použít tuto členskou funkci:

1. Vytvořte objekt, ale Nevolejte `Create`. `CDaoWorkspace`

1. Zavolejte `SetDefaultPassword` a, pokud chcete, [SetDefaultUser](#setdefaultuser).

1. Zavolejte `Create` pro tento objekt pracovního prostoru nebo následné, bez zadání hesla.

Ve výchozím nastavení je vlastnost DefaultUser nastavena na "admin" a vlastnost DefaultPassword je nastavena na prázdný řetězec ("").

Další informace o zabezpečení najdete v tématu "vlastnost oprávnění" v nápovědě k rozhraní DAO. Související informace najdete v nápovědě k rozhraní DAO v tématech "vlastnost DefaultPassword" a "DefaultUser Property".

##  <a name="setdefaultuser"></a>CDaoWorkspace::SetDefaultUser

Zavolejte tuto členskou funkci pro nastavení výchozího uživatelského jména, které databázový stroj používá, když je vytvořen objekt pracovního prostoru bez konkrétního uživatelského jména.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parametry

*lpszDefaultUser*<br/>
Výchozí uživatelské jméno. Uživatelské jméno může být 1-20 znaků dlouhé a obsahovat abecední znaky, znaky akcentů, číslice, mezery a symboly s výjimkou: "(uvozovky),/(lomítko), \ (zpětné lomítko), \[ \] (závorky),: (dvojtečka) &#124; , ( kanál), \< (znaménko menší než), > (větší než znaménko), + (znaménko plus), = (rovnítko),; (středník),, (čárka), (otazník \* ), (hvězdička), úvodní mezery a řídicí znaky (ASCII 00 až ASCII 31). Související informace najdete v nápovědě k rozhraní DAO v tématu vlastnost UserName.

### <a name="remarks"></a>Poznámky

Výchozí uživatelské jméno, které jste nastavili, se použije na nové pracovní prostory, které vytvoříte po volání. Když vytváříte další pracovní prostory, nemusíte zadávat uživatelské jméno ve volání metody [Create](#create) .

Chcete-li použít tuto členskou funkci:

1. Vytvořte objekt, ale Nevolejte `Create`. `CDaoWorkspace`

1. Zavolejte `SetDefaultUser` a, pokud chcete, [SetDefaultPassword](#setdefaultpassword).

1. Zavolejte `Create` pro tento objekt pracovního prostoru nebo následné, bez zadání uživatelského jména.

Ve výchozím nastavení je vlastnost DefaultUser nastavena na "admin" a vlastnost DefaultPassword je nastavena na prázdný řetězec ("").

Související informace naleznete v tématech "vlastnost DefaultUser" a "vlastnost DefaultPassword" v nápovědě rozhraní DAO.

##  <a name="setinipath"></a>CDaoWorkspace::SetIniPath

Zavolejte tuto členskou funkci, pokud chcete zadat umístění nastavení registru Windows pro databázový stroj Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistrySubkey*<br/>
Řetězec obsahující název podklíče registru systému Windows pro umístění nastavení nebo parametrů databázového stroje Microsoft Jet, které jsou potřeba pro Instalovatelné databáze ISAM.

### <a name="remarks"></a>Poznámky

Volejte `SetIniPath` pouze v případě, že je třeba zadat zvláštní nastavení. Další informace najdete v tématu "vlastnost IniPath" v nápovědě k rozhraní DAO.

> [!NOTE]
>  Volá `SetIniPath` během instalace aplikace, ne při spuštění aplikace. `SetIniPath`musí být volána před otevřením libovolných pracovních prostorů, databází nebo sad záznamů. v opačném případě knihovna MFC vyvolá výjimku.

Tento mechanismus můžete použít ke konfiguraci databázového stroje pomocí nastavení registru poskytnutého uživatelem. Rozsah tohoto atributu je omezen na vaši aplikaci a nelze jej změnit bez restartování aplikace.

##  <a name="setisolateodbctrans"></a>CDaoWorkspace::SetIsolateODBCTrans

Tuto členskou funkci zavolejte, pokud chcete nastavit hodnotu vlastnosti IsolateODBCTrans DAO pro daný pracovní prostor.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parametry

*bIsolateODBCTrans*<br/>
Předejte hodnotu TRUE, pokud chcete začít izolovat transakce rozhraní ODBC. Předejte hodnotu FALSE, pokud chcete zastavit izolaci transakcí ODBC.

### <a name="remarks"></a>Poznámky

V některých situacích možná budete muset ve stejné databázi ODBC čekat na více souběžných transakcí. K tomu je třeba otevřít samostatný pracovní prostor pro každou transakci. I když každý pracovní prostor může mít své vlastní připojení ODBC k databázi, tím se zpomaluje výkon systému. Vzhledem k tomu, že se nepožaduje izolovaná transakce, budou se ve výchozím nastavení sdílet připojení ODBC z více objektů otevřených stejným uživatelem.

Některé servery ODBC, například Microsoft SQL Server, neumožňují souběžné transakce v jednom připojení. Pokud potřebujete mít v době čekání na takovou databázi více než jednu transakci, nastavte vlastnost IsolateODBCTrans na hodnotu TRUE v každém pracovním prostoru hned po jejím otevření. Tím se vynutí samostatné připojení ODBC pro každý pracovní prostor.

##  <a name="setlogintimeout"></a>CDaoWorkspace::SetLoginTimeout

Tuto členskou funkci zavolejte, pokud chcete nastavit hodnotu vlastnosti LoginTimeout DAO pro daný pracovní prostor.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*nSeconds*<br/>
Počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC.

### <a name="remarks"></a>Poznámky

Tato hodnota představuje počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC. Výchozí nastavení LoginTimeout je 20 sekund. Když je LoginTimeout nastavené na 0, neproběhne žádný časový limit a komunikace se zdrojem dat může přestat reagovat.

Při pokusu o přihlášení k databázi ODBC, jako je například Microsoft SQL Server, může připojení selhat v důsledku chyb sítě nebo proto, že server není spuštěn. Místo toho, aby se čekalo na připojení výchozích 20 sekund, můžete určit, jak dlouho bude databázový stroj čekat před tím, než vyvolá chybu. Přihlášení k serveru probíhá implicitně jako součást řady různých událostí, jako je například spuštění dotazu na externí databázi serveru. Hodnota časového limitu je určena aktuálním nastavením vlastnosti LoginTimeout.

Související informace najdete v tématu "Vlastnost LoginTimeout" v nápovědě k rozhraní DAO.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
