---
title: Cdaoworkspace – třída
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
ms.openlocfilehash: 92b2827d556583524b46f88f8bd9efeb57a5d83a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472862"
---
# <a name="cdaoworkspace-class"></a>Cdaoworkspace – třída

Spravuje relace s názvem databáze chráněné heslem od přihlášení po odhlášení jednoho uživatele.

## <a name="syntax"></a>Syntaxe

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Vytvoří objekt pracovního prostoru. Potom zavolejte `Create` nebo `Open`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoWorkspace::Append](#append)|Přidá nově vytvořeného pracovního prostoru do kolekce pracovních prostorů databázový stroj.|
|[CDaoWorkspace::BeginTrans](#begintrans)|Spustí novou transakci, která se vztahuje na všechny databáze otevřené v pracovním prostoru.|
|[CDaoWorkspace::Close](#close)|Zavře pracovní prostor a všechny objekty, které obsahuje. Čekající transakce jsou vrácena zpět.|
|[CDaoWorkspace::CommitTrans](#committrans)|Dokončí aktuální transakci a uloží změny.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Komprimuje (nebo duplikuje) databáze.|
|[CDaoWorkspace::Create](#create)|Vytvoří nový objekt DAO pracovního prostoru.|
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Vrátí počet objektů DAO databáze v pracovním prostoru databáze kolekce.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Vrátí informace o zadanou databázi DAO definované v pracovním prostoru databáze kolekce.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Vrátí umístění databáze Microsoft Jet inicializace nastavení v registru Windows.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Vrátí hodnotu určující, zda jsou izolované prostřednictvím více transakcí, které se týkají stejného zdroje dat ODBC vynucené několik připojení ke zdroji dat.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Vrátí počet sekund, než dojde k chybě, když se uživatel pokusí přihlásit k databázi pro ODBC.|
|[CDaoWorkspace::GetName](#getname)|Vrátí uživatelem definovaný název pro objekt pracovního prostoru.|
|[CDaoWorkspace::GetUserName](#getusername)|Vrátí že uživatelské jméno zadané, kdy byla vytvořena pracovní prostor. Toto je jméno vlastníka pracovního prostoru.|
|[CDaoWorkspace::GetVersion](#getversion)|Vrátí řetězec, který obsahuje verzi databázového stroje, který je přidružený k pracovnímu prostoru.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Vrátí počet objektů DAO pracovního prostoru v kolekci pracovních prostorů databázový stroj.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Vrátí informace o zadaný pracovní prostor DAO definovanému v kolekci pracovních prostorů databázový stroj.|
|[CDaoWorkspace::Idle](#idle)|Umožňuje databázového stroje pro provedení úlohy na pozadí.|
|[CDaoWorkspace::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud je pracovní prostor otevřít.|
|[CDaoWorkspace::Open](#open)|Explicitně otevře objekt pracovní prostor, přidružené k výchozím pracovním prostoru pro rozhraní DAO.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Se pokusí opravit poškozené databáze.|
|[CDaoWorkspace::Rollback](#rollback)|Ukončí aktuální transakci a nedojde k uložení změn.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Nastaví heslo, které využívá databázový stroj při vytvoření pracovního prostoru objektu bez určité heslo.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Nastaví uživatelské jméno, která používá databázový stroj při vytvoření pracovního prostoru objektu bez určité uživatelské jméno.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Nastaví umístění databáze Microsoft Jet inicializace nastavení v registru Windows.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Určuje, zda vynucením několik připojení ke zdroji dat jsou izolované více transakcí, které se týkají stejného zdroje dat ODBC.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund, než dojde k chybě, když se uživatel pokusí přihlásit ke zdroji dat rozhraní ODBC.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Odkazuje na základní objekt rozhraní DAO pracovního prostoru.|

## <a name="remarks"></a>Poznámky

Ve většině případů nebudete potřebovat víc pracovních prostorů a nebude je potřeba vytvořit pracovní prostor explicitní objekty. Při otevření databáze a sady záznamů objekty používají pro rozhraní DAO výchozího pracovního prostoru. Ale v případě potřeby můžete spustit více relací najednou tak, že vytvoříte pracovní prostor další objekty. Každého objektu prostoru může obsahovat více otevřít databázové objekty v kolekci svou vlastní databází. V knihovně MFC pracovní prostor je primárně správce transakcí, určení sady open databází ve stejném "transakce znaky".

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Obecně třídy knihovny MFC rozhraní DAO podle podporují více než třídy knihovny MFC založená na rozhraní ODBC. Třídy založené na rozhraní DAO přístup k datům prostřednictvím databázový stroj Microsoft Jet, včetně ovladačů rozhraní ODBC. Podporují také jazyka DDL (Data Definition) operace, jako je vytváření databází a přidávání tabulek a polí prostřednictvím třídy rozhraní, aniž byste museli přímo volat rozhraní DAO.

## <a name="capabilities"></a>Možnosti

Třída `CDaoWorkspace` poskytuje následující:

- Explicitní přístup, v případě potřeby s výchozím pracovním prostorem, vytvořil inicializace databázový stroj. Obvykle použijete rozhraní DAO od výchozího pracovního prostoru implicitně vytvořením objektů databáze a sady záznamů.

- Transakce místa, ve kterém transakce platí pro všechny databáze, otevřete v pracovním prostoru. Můžete vytvořit další pracovních prostorů ke správě prostorů oddělené transakci.

- Rozhraní pro mnoho vlastností podkladový databázový stroj Microsoft Jet (viz statické členské funkce). Otevření nebo vytvoření pracovního prostoru nebo statické členské funkce. před voláním otevření nebo vytvoření, inicializuje databázový stroj.

- Přístup ke kolekci pracovních prostorů databázový stroj, který uchovává všechny aktivní pracovní prostory, které se připojí k němu. Můžete také vytvořit a pracovat s pracovními prostory bez připojení ke kolekci.

## <a name="security"></a>Zabezpečení

MFC neimplementuje kolekcí uživatelů a skupin v rozhraní DAO, které se používají pro řízení zabezpečení. Pokud potřebujete tyto aspekty rozhraní DAO, je nutné programovat sami prostřednictvím přímého volání rozhraní DAO. Informace najdete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="usage"></a>Použití

Můžete použít třídu `CDaoWorkspace` na:

- Explicitně otevřete výchozího pracovního prostoru.

   Použití výchozího pracovního prostoru je obvykle implicitní – při otevření nové [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekty. Ale můžete potřebovat pro přístup k explicitně – například k přístupu k vlastnosti modul databáze nebo kolekce pracovních prostorů. Níže naleznete v tématu "Implicitního použití výchozího pracovního prostoru".

- Vytvoření nové pracovní prostory. Volání [připojit](#append) Pokud chcete přidat do kolekce pracovních prostorů.

- Otevřete existující pracovní prostor v kolekci pracovních prostorů.

Vytváří se nový pracovní prostor, který ještě neexistuje v kolekci je popsáno v části pracovní prostory [vytvořit](#create) členskou funkci. Objekty pracovního prostoru nezůstanou zachována žádným způsobem mezi relacemi datababase modul. Pokud vaše aplikace staticky propojuje knihovnu MFC, ukončením aplikace zruší inicializaci modulu databáze. Pokud aplikace odkazuje dynamicky pomocí knihovny MFC, databázový stroj není inicializován po uvolnění knihovny DLL MFC.

Explicitně otevírání výchozího pracovního prostoru, nebo otevřete existující pracovní prostor v kolekci pracovních prostorů je popsaný v části [otevřít](#open) členskou funkci.

Ukončení relace pracovního prostoru po zavření pracovního prostoru s [Zavřít](#close) členskou funkci. `Close` Zavře všechny databáze, které jste ještě dříve, zavřeli, vrácení zpět všechny nepotvrzené transakce.

## <a name="transactions"></a>Transakce

DAO – spravuje transakcí na úrovni pracovního prostoru. proto transakce v pracovním prostoru s více databázemi otevřít platí pro všechny databáze. Například pokud dvě databáze mají nepotvrzené aktualizace a volat [CommitTrans](#committrans), všechny aktualizace jsou potvrzeny. Pokud chcete omezit transakce do jediné databáze, musíte pro něj objekt samostatný pracovní prostor.

## <a name="implicit-use-of-the-default-workspace"></a>Implicitní použití výchozího pracovního prostoru

Knihovna MFC používá pro rozhraní DAO výchozího pracovního prostoru implicitně za následujících okolností:

- Pokud vytvoříte nový `CDaoDatabase` objektu, ale není to udělat prostřednictvím existující `CDaoWorkspace` objektu MFC vytvoří objekt dočasný pracovní prostor, která odpovídá vaší DAO výchozího pracovního prostoru. Pokud to uděláte tak, aby v případě několika databází všechny databázové objekty byly spojeny s výchozím pracovním prostoru. Můžete přistupovat databáze pracovního prostoru prostřednictvím `CDaoDatabase` datový člen.

- Podobně pokud vytvoříte `CDaoRecordset` bez poskytnutí ukazatel na objekt `CDaoDatabase` objekt, vytvoří objekt dočasné databáze knihovny MFC a při rozšíření i pro objekt dočasný pracovní prostor. Sada záznamů databáze a nepřímo její pracovní prostor, můžete přistupovat prostřednictvím `CDaoRecordset` datový člen.

## <a name="other-operations"></a>Ostatní operace

Ostatní databázové operace také její součástí jsou například oprava poškození databáze nebo komprimování databáze.

Informace o volání rozhraní DAO přímo a zabezpečení rozhraní DAO, najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="append"></a>  CDaoWorkspace::Append

Voláním této členské funkce po zavolání [vytvořit](#create).

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

`Append` Přidá do nově vytvořeného prostoru objektu do kolekce pracovních prostorů databázový stroj. Mezi relacemi databázový stroj; nezůstanou zachována pracovními prostory ukládají se jenom v paměti, nikoli na disk. Nemáte pracovní prostor; připojit Pokud ho nevidíte, můžete ji dál používat.

Připojený pracovní prostor zůstává v kolekci pracovních prostorů v aktivní, otevřeného stavu, dokud nezavoláte jeho [Zavřít](#close) členskou funkci.

Související informace naleznete v tématu "Metodu" v nápovědě k DAO.

##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans

Voláním této členské funkce k zahájení transakce.

```
void BeginTrans();
```

### <a name="remarks"></a>Poznámky

Po zavolání `BeginTrans`, provedete do struktury dat nebo databáze aktualizace se projeví, když potvrzení transakce. Vzhledem k tomu, že pracovní prostor definuje prostor jediné transakce, transakce platí pro všechny otevřené databáze v pracovním prostoru. Existují dva způsoby, jak dokončit transakce:

- Volání [CommitTrans](#committrans) členské funkce k potvrzení transakce a uložte změny do zdroje dat.

- Zavolat [vrácení zpět](#rollback) členské funkce pro zrušení transakce.

Zavření pracovního prostoru objektu nebo objekt databáze při čekající transakce vrátí zpět všechny probíhající transakce.

Pokud potřebujete izolaci transakcí na jeden zdroj dat rozhraní ODBC od těch, které na jiné zdroje dat ODBC, přečtěte si [SetIsolateODBCTrans](#setisolateodbctrans) členskou funkci.

##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace

Vytvoří `CDaoWorkspace` objektu.

```
CDaoWorkspace();
```

### <a name="remarks"></a>Poznámky

Po vytváření objekt jazyka C++, máte dvě možnosti:

- Volání objektu [otevřete](#open) členská funkce Otevřít výchozího pracovního prostoru nebo otevřete existující objekt v kolekci pracovních prostorů.

- Zavolat objekt [vytvořit](#create) členskou funkci pro vytvoření nového objektu rozhraní DAO pracovního prostoru. Tím se explicitně spustí novou relaci pracovního prostoru můžete projít přes `CDaoWorkspace` objektu. Po volání `Create`, můžete volat [připojit](#append) Pokud chcete přidat pracovní prostor do kolekce pracovních prostorů databázový stroj.

Naleznete v přehledu třídy pro [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md) informace o tom, kdy je potřeba explicitně vytvořit `CDaoWorkspace` objektu. Obvykle použijete pracovní prostory vytvořené implicitně při otevření [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt bez zadání pracovního prostoru nebo při otevření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu bez zadání databázový objekt. Knihovny MFC rozhraní DAO objekty vytvořené tímto způsobem použít pracovní prostor výchozí pro rozhraní DAO, což je vytvořit jednou a znovu použít.

Uvolnění pracovního prostoru a obsažené objekty, volání objektu pracovního prostoru [Zavřít](#close) členskou funkci.

##  <a name="close"></a>  CDaoWorkspace::Close

Voláním této členské funkce pro zavření pracovního prostoru objektu.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Zavření objektu otevřít pracovní prostor uvolní základní objekt rozhraní DAO a pokud pracovní prostor je členem kolekce pracovních prostorů, odebere ho z kolekce. Volání `Close` programování je dobrým zvykem.

> [!CAUTION]
>  Zavření pracovního prostoru objektu zavře všechny otevřené databáze v pracovním prostoru. Výsledkem je otevřených sady záznamů v databázích a zavírá a všechny čekající změny nebo aktualizace jsou vráceny zpět. Související informace naleznete v tématu [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), a [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) členské funkce.

Pracovní prostor objekty nejsou trvalý. existují pouze při existují odkazy na ně. To znamená, že při ukončení relace modul databáze pracovního prostoru a jeho databáze kolekce nezůstanou zachována. Budete muset znovu vytvořit je u další relace tak, že znovu otevřete pracovní prostor a databáze.

Související informace naleznete v tématu "Metoda Close" v nápovědě k DAO.

##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans

Voláním této členské funkce k potvrzení transakce, uložit skupinu úpravy a aktualizací pro jeden nebo více databází v pracovním prostoru.

```
void CommitTrans();
```

### <a name="remarks"></a>Poznámky

Transakce se skládá z řady změn dat databázi nebo jeho strukturu, počínaje volání [BeginTrans](#begintrans). Po dokončení transakce buď potvrďte nebo vraťte ji zpět (zrušit změny) s [vrácení zpět](#rollback). Ve výchozím nastavení, aniž by transakce záznamů se aktualizace potvrdí okamžitě. Volání `BeginTrans` způsobí, že závazku aktualizace zpozdit až do okamžiku volání `CommitTrans`.

> [!CAUTION]
>  Transakce v rámci jednoho pracovního prostoru, jsou vždy globální do pracovního prostoru a nejsou omezeny pouze jednu databázi nebo sadu záznamů. Pokud provádění operací ve více než jednu databázi nebo sadu záznamů v rámci transakce pracovního prostoru, `CommitTrans` potvrzení všechny čekající aktualizace, a `Rollback` obnoví všechny operace na tyto databáze a sady záznamů.

Při zavření databáze nebo pracovního prostoru s nevyřízené transakce, transakce jsou všechny vrácena zpět.

> [!NOTE]
>  Toto není mechanismus dvoufázového potvrzení. Pokud se potvrzení nezdaří jednu aktualizaci, ostatní stále bude potvrzení.

##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase

Voláním této členské funkce ke komprimaci zadanou Microsoft Jet (. Databáze MDB).

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
Název existujícího, uzavřen databáze. Úplná cesta a název souboru, může být například "C:\\\MYDB. MDB". Název souboru má příponu, je nutné zadat. Pokud vaše síť podporuje jednotné pojmenování (UNC), můžete taky zadat síťovou cestu jako "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojité zpětná lomítka jsou nutné v řetězci cesty, proto, že "\\" je znak escape jazyka C++.)

*lpszDestName*<br/>
Úplná cesta komprimovaná databáze, kterou vytváříte. Můžete taky zadat síťovou cestu jako s *lpszSrcName*. Nelze použít *lpszDestName* argumentu pro zadání souboru databáze stejné jako *lpszSrcName*.

*lpszPassword*<br/>
Heslo použité při chcete komprimovat databáze chráněné heslem. Poznámka: Pokud používáte verzi `CompactDatabase` , která přebírá heslo, je nutné zadat všechny parametry. Navíc vzhledem k tomu, že je parametr připojit, vyžaduje zvláštní formátování, následujícím způsobem:; PWD = *lpszPassword*. Například:; PWD = "Všechno nejlepší". (Vyžaduje se počáteční středník.)

*lpszLocale*<br/>
Používá se k určení pořadí řazení pro vytvoření řetězcového výrazu *lpszDestName*. Pokud je tento argument vynechat a přijměte výchozí hodnotu `dbLangGeneral` (viz níže), národní prostředí nové databáze je stejné jako u původní databáze. Možné hodnoty jsou:

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

*nOptions*<br/>
Určuje jednu nebo více možností pro cílovou databázi *lpszDestName*. Pokud tento argument vynecháte a přijměte výchozí hodnotu *lpszDestName* budou mít stejné šifrování a stejnou verzi jako *lpszSrcName*. Můžete kombinovat `dbEncrypt` nebo `dbDecrypt` možnost s některou z možností verze pomocí operátoru bitového operátoru OR. Možné hodnoty, které určují formát databáze, ne verzi modulu databáze, jsou:

- `dbEncrypt` Šifrování databáze při kompresi.

- `dbDecrypt` Dešifrování databáze při kompresi.

- `dbVersion10` Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 1.0 při kompresi.

- `dbVersion11` Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 1.1 při kompresi.

- `dbVersion20` Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 2.0 při kompresi.

- `dbVersion30` Vytvořte databázi, která používá databázový stroj Microsoft Jet verze 3.0 při kompresi.

Můžete použít `dbEncrypt` nebo `dbDecrypt` v argumentu Možnosti určete, jestli se k šifrování a dešifrování databáze, jako je komprimovat. Pokud vynecháte konstantu šifrování, nebo zadáte-li obě `dbDecrypt` a `dbEncrypt`, *lpszDestName* budou mít stejné šifrování jako *lpszSrcName*. Některou z konstant verze můžete použít v argumentu možnosti určit verzi formátu dat pro zkomprimovanou databázi. Tato konstanta má vliv pouze verzi formátu dat *lpszDestName*. Můžete zadat pouze jednu verzi konstanta. Pokud vynecháte konstantu verze *lpszDestName* bude mít stejnou verzi jako *lpszSrcName*. Můžete komprimovat *lpszDestName* pouze na verzi, která je stejná nebo vyšší než u *lpszSrcName*.

> [!CAUTION]
>  Pokud databáze není zašifrovaný, je možné, i pokud se rozhodnete implementovat zabezpečení uživatele a hesla k přímému čtení disku binární soubor, který představuje databáze.

### <a name="remarks"></a>Poznámky

Při změně dat v databázi, databázový soubor se může fragmentovat a více místa na disku než je nutné použít. Měli byste pravidelně, zkomprimovat databáze defragmentace databázový soubor. Komprimovaná databáze je obvykle menší. Můžete také změnit pořadí řazení, šifrování nebo verzi formátu dat během kopírování a komprese databáze.

> [!CAUTION]
>  `CompactDatabase` Členská funkce neprovede konverzi správně kompletní databáze Microsoft Access z jedné verze do jiného. Formát dat je převeden. Microsoft Access definované objekty, jako jsou formuláře a sestavy, nebudou převedeny. Nicméně data správně převést.

> [!TIP]
>  Můžete také použít `CompactDatabase` zkopírovat databázový soubor.

Další informace o komprimaci databází naleznete v tématu "CompactDatabase metodu" v nápovědě k DAO.

##  <a name="create"></a>  CDaoWorkspace::Create

Voláním této členské funkce vytvořit nový pracovní prostor objekt DAO a přidružte jej k MFC `CDaoWorkspace` objektu.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Řetězec se znaky až 14, který jednoznačně pojmenuje objekt nového pracovního prostoru. Je nutné zadat název. Související informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*lpszUserName*<br/>
Uživatelské jméno vlastníka pracovního prostoru. Požadavky najdete v tématu *lpszDefaultUser* parametr [SetDefaultUser](#setdefaultuser) členskou funkci. Související informace naleznete v tématu "Vlastnost UserName" v nápovědě k DAO.

*lpszPassword*<br/>
Heslo pro nový objekt pracovního prostoru. Heslo může mít až 14 znaků a může obsahovat libovolný znak s výjimkou ASCII 0 (null). Hesla jsou malá a velká písmena. Související informace naleznete v tématu "Heslo vlastnost" v nápovědě k DAO.

### <a name="remarks"></a>Poznámky

Celkový proces vytváření je:

1. Vytvoření [cdaoworkspace –](#cdaoworkspace) objektu.

1. Volání objektu `Create` členskou funkci pro vytvoření základního pracovního prostoru DAO. Musíte zadat název pracovního prostoru.

1. Volitelně můžete volat [připojit](#append) Pokud chcete přidat pracovní prostor do kolekce pracovních prostorů databázový stroj. Bez připojení ho můžete práci s pracovním prostorem.

Po `Create` volání, je objektu pracovního prostoru v otevřeném stavu, připravené k použití. Nevolejte `Open` po `Create`. Nevolejte `Create` Pokud pracovní prostor už existuje v kolekci pracovních prostorů. `Create` Inicializuje databázový stroj, pokud ho ještě nebyl inicializován pro vaši aplikaci.

##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount

Voláním této členské funkce se načíst počet objektů DAO databáze v pracovním prostoru databáze kolekce – počet otevřených databází v pracovním prostoru.

```
short GetDatabaseCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet otevřených databází v pracovním prostoru.

### <a name="remarks"></a>Poznámky

`GetDatabaseCount` je užitečné, pokud budete potřebovat k prosmyčkování všech databází definované v pracovním prostoru databáze kolekce. Pokud chcete získat informace o dané databázi v kolekci, najdete v článku [GetDatabaseInfo](#getdatabaseinfo). Typické použití je volat `GetDatabaseCount` pro počet otevřených databází, pak použijte toto číslo jako index smyčky pro opakovaná volání `GetDatabaseInfo`.

##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo

Voláním této členské funkce získat různé druhy informací o databázi otevřít v pracovním prostoru.

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
Index založený na nule databázový objekt v pracovním prostoru databází kolekci, pro vyhledávání podle indexu.

*informace o databázi*<br/>
Odkaz na [cdaodatabaseinfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, které informace o databázi k načtení. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrátit:

- Název AFX_DAO_PRIMARY_INFO (výchozí), aktualizovat, transakce

- Informace o primárním AFX_DAO_SECONDARY_INFO plus: časový limit dotazu verze, pořadí řazení

- AFX_DAO_ALL_INFO primární a sekundární informace plus: připojení

*lpszName*<br/>
Název databázového objektu, pro vyhledávání podle názvu. Název je řetězec s až 14 znaků, který jednoznačně pojmenuje objekt nového pracovního prostoru.

### <a name="remarks"></a>Poznámky

Jednu verzi funkce umožňuje vyhledat databázi indexem. Jiné verze umožňuje vyhledávání podle názvu databáze.

Popis informací, v *informace o databázi*, najdete v článku [cdaodatabaseinfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, můžete získat informace o všech předchozích úrovní.

##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath

Voláním této členské funkce získat umístění Microsoft Jet databáze vyhledávacího stroje inicializace nastavení v registru Windows.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující umístění registru.

### <a name="remarks"></a>Poznámky

Umístění můžete použít k získání informací o nastavení pro databázový stroj. Vrácené informace se ve skutečnosti název podklíče registru.

Související informace naleznete v tématech "IniPath vlastnost" a "Přizpůsobení Windows registru nastavení pro přístup k datům" v nápovědě k DAO.

##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans

Voláním této členské funkce k získání aktuální hodnoty vlastností rozhraní DAO IsolateODBCTrans pro pracovní prostor.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou izolované; ODBC – transakce jinak 0.

### <a name="remarks"></a>Poznámky

V některých případech můžete potřebovat mít více souběžných transakcí čekající na stejné databáze ODBC. K tomuto účelu, budete muset otevřít samostatný pracovní prostor pro každou transakci. Uvědomte si, že i když každý pracovní prostor může mít svůj vlastní ODBC připojení k databázi, zpomalí výkon systému. Protože izolace transakce není obvykle vyžaduje, jsou ve výchozím nastavení sdílené připojení ODBC z více objektů pracovní prostor otevřen stejným uživatelem.

Některé servery ODBC, jako je například Microsoft SQL Server, neumožňují souběžné transakce na jedno připojení. Pokud je potřeba mít více transakcí najednou čekající na takové databázi, nastavte vlastnost IsolateODBCTrans na hodnotu TRUE v každém pracovním prostoru, co nejdříve ho otevřete. To přinutí samostatného připojení rozhraní ODBC za každý pracovní prostor.

Související informace naleznete v tématu "IsolateODBCTrans vlastnost" v nápovědě k DAO.

##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout

Voláním této členské funkce k získání aktuální hodnoty vlastností rozhraní DAO LoginTimeout pro pracovní prostor.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>Návratová hodnota

Počet sekund, než dojde k chybě při pokusu o přihlášení k databázi pro ODBC.

### <a name="remarks"></a>Poznámky

Tato hodnota představuje počet sekund, než dojde k chybě při pokusu o přihlášení k databázi pro ODBC. Ve výchozím nastavení LoginTimeout je 20 sekund. Pokud LoginTimeout je nastaven na hodnotu 0, proběhne žádný časový limit a komunikaci se zdrojem dat může přestat reagovat.

Když se pokoušíte přihlásit ke službě database ODBC, jako je například Microsoft SQL Server, může připojení selhat v důsledku chyby sítě nebo proto, že server není spuštěn. Nečekejte na výchozí 20 sekund na připojení, můžete určit, jak dlouho databázový stroj čeká předtím, než dojde k chybě. Přihlášení k serveru se stane, implicitně jako součást množství různých událostí, jako je například spuštění dotazu na databázi externího serveru.

Související informace naleznete v tématu "LoginTimeout vlastnost" v nápovědě k DAO.

##  <a name="getname"></a>  CDaoWorkspace::GetName

Voláním této členské funkce a získat tak název definovaný uživatelem základní objekt rozhraní DAO pracovního prostoru `CDaoWorkspace` objektu.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující uživatelem definovaný název objektu pracovního prostoru DAO.

### <a name="remarks"></a>Poznámky

Název je užitečné pro přístup k objektu rozhraní DAO pracovního prostoru v kolekci pracovních prostorů databázový stroj podle názvu.

Související informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

##  <a name="getusername"></a>  CDaoWorkspace::GetUserName

Voláním této členské funkce získat jméno vlastníka pracovního prostoru.

```
CString GetUserName();
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , která představuje vlastníka pracovního prostoru objektu.

### <a name="remarks"></a>Poznámky

Pro získání nebo nastavení oprávnění pro vlastníka pracovního prostoru, volání rozhraní DAO přímo ke kontrole oprávnění nastavení vlastnosti; Určuje, jaká oprávnění má uživatel. Pokud chcete pracovat s oprávněními, potřebujete systému. Soubor MDA.

Informace o volání rozhraní DAO přímo, naleznete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Související informace naleznete v tématu "Vlastnost UserName" v nápovědě k DAO.

##  <a name="getversion"></a>  CDaoWorkspace::GetVersion

Voláním této členské funkce se určit verzi databázového stroje Microsoft Jet používá.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který určuje verzi databázového stroje, který je přidružený k objektu.

### <a name="remarks"></a>Poznámky

Vrácená hodnota představuje číslo verze ve formátu "hlavní.vedlejší"; například "3.0". Číslo verze produktu (například 3.0) se skládá z číslo verze (3), tečku a číslo verze (0).

Související informace naleznete v tématu "Verze vlastnost" v nápovědě k DAO.

##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount

Voláním této členské funkce se načíst počet objektů DAO pracovního prostoru v kolekci pracovních prostorů databázový stroj.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet otevřených pracovních prostorů v kolekci pracovních prostorů.

### <a name="remarks"></a>Poznámky

Tento počet neobsahuje žádné otevřené pracovní prostory, nejsou připojeny ke kolekci. `GetWorkspaceCount` je užitečné, pokud budete muset projít všechny pracovní prostory definovaných v kolekci pracovních prostorů. Pokud chcete získat informace o daný pracovní prostor v kolekci, najdete v článku [GetWorkspaceInfo](#getworkspaceinfo). Typické použití je volat `GetWorkspaceCount` pro počet otevřených pracovních prostorů, pak použijte toto číslo jako index smyčky pro opakovaná volání `GetWorkspaceInfo`.

##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo

Voláním této členské funkce získat různé druhy informací o pracovní prostor otevřít v relaci.

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
Index založený na nule databázový objekt v kolekci pracovních prostorů pro vyhledávání podle indexu.

*wkspcinfo*<br/>
Odkaz na [cdaoworkspaceinfo –](../../mfc/reference/cdaoworkspaceinfo-structure.md) objektu, který vrací požadované informace.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o pracovním prostoru pro načtení. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrátit:

- Název AFX_DAO_PRIMARY_INFO (výchozí)

- Informace o primárním AFX_DAO_SECONDARY_INFO plus: uživatelské jméno

- AFX_DAO_ALL_INFO primární a sekundární informace plus: izolovat ODBCTrans

*lpszName*<br/>
Název objektu pracovního prostoru pro vyhledávání podle názvu. Název je řetězec s až 14 znaků, který jednoznačně pojmenuje objekt nového pracovního prostoru.

### <a name="remarks"></a>Poznámky

Popis informací, v *wkspcinfo*, najdete v článku [cdaoworkspaceinfo –](../../mfc/reference/cdaoworkspaceinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, získat informace o předchozích úrovních.

##  <a name="idle"></a>  CDaoWorkspace::Idle

Volání `Idle` poskytnout příležitosti k provedení úlohy na pozadí, nemusí mít aktuální kvůli intenzivní zpracování dat databázový stroj.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>Parametry

*nAction*<br/>
Akce při nečinnosti zpracování. V současné době je platné pouze akce `dbFreeLocks`.

### <a name="remarks"></a>Poznámky

To je často v prostředí s více uživateli, multitaskingu, ve kterých není dostatek času zpracování na pozadí zachovat všechny záznamy v sadě záznamů aktuální hodnotu true.

> [!NOTE]
>  Volání `Idle` s databází vytvořených pomocí verze 3.0 databázový stroj Microsoft Jet není nutné. Použití `Idle` jenom pro databáze vytvořené pomocí předchozích verzí.

Obvykle čtení, které jsou odebrány zámky a datům v objektech místní dynamické sady záznamů se aktualizuje jenom v případě, že dochází k žádné další akce (včetně pohyb myši). Pokud pravidelně volala `Idle`, zadejte databázový stroj s časem můžete dohnat díky vydávání zpracování úloh na pozadí nepotřebné čtení zámků. Zadání `dbFreeLocks` – konstanta jako argument zpoždění zpracování, dokud uvolnění všech zámků pro čtení.

Tato členská funkce není potřeba v prostředí jednoho uživatele, pokud běží více instancí aplikace. `Idle` Členská funkce může zvýšení výkonu v prostředí, protože vynutí databázový stroj Vyprázdnit data na disk, uvolnění zámků v paměti. Můžete také uvolnit zámky pro čtení tak, že operace součástí transakce.

Související informace naleznete v tématu "Nečinnosti metodu" v nápovědě k DAO.

##  <a name="isopen"></a>  CDaoWorkspace::IsOpen

Zavolat tuto členskou funkci k určení, zda `CDaoWorkspace` je otevřen objekt – to znamená, zda MFC objekt byl inicializován voláním [otevřete](#open) nebo volání [vytvořit](#create).

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud objekt pracovní prostor je otevřená. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete volat žádné členské funkce pracovní prostor, který je v otevřeném stavu.

##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace

Ukazatel na základní objekt rozhraní DAO pracovního prostoru.

### <a name="remarks"></a>Poznámky

Pokud třeba přímý přístup k základní objekt rozhraní DAO, použijte tomuto datovému členu. Můžete volat rozhraní DAO objektu pomocí tohoto ukazatele.

Informace o získání přístupu k objektům rozhraní DAO přímo najdete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).

##  <a name="open"></a>  CDaoWorkspace::Open

Explicitně otevře objekt pracovní prostor, přidružené k výchozím pracovním prostoru pro rozhraní DAO.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Název pracovního prostoru objektu rozhraní DAO a otevřete – řetězec s až 14 znaků, který jedinečně označuje pracovního prostoru. Přijměte výchozí hodnotu NULL a explicitně otevřete výchozího pracovního prostoru. Požadavky na pojmenování, najdete v článku *lpszName* parametr pro [vytvořit](#create). Související informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

### <a name="remarks"></a>Poznámky

Po sestavení `CDaoWorkspace` objektu, zavolat tuto členskou funkci, proveďte jednu z následujících akcí:

- Explicitně otevřete výchozího pracovního prostoru. Předat hodnotu NULL pro *lpszName*.

- Otevřít existující `CDaoWorkspace` objektu, členem kolekce pracovních prostorů, podle názvu. Předejte platný název pro existující objekt pracovního prostoru.

`Open` Vloží objektu pracovního prostoru do otevřeného stavu a také inicializuje databázový stroj, pokud ho ještě nebyl inicializován pro vaši aplikaci.

Ačkoli mnoho `CDaoWorkspace` členské funkce lze volat pouze po otevření pracovního prostoru, následující členské funkce, které fungují na databázovém stroji, jsou po konstrukci objektu C++, ale před voláním dostupné `Open`:

||||
|-|-|-|
|[Vytvoření](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[Nečinnosti](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase

Pokud je potřeba se pokusí o opravu poškození databáze, který přistupuje k databázovém stroji Microsoft Jet Zavolejte tuto členskou funkci.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Cesta a název souboru pro existující soubor databáze Microsoft leteckého motoru. Pokud ji vynecháte, je prohledána pouze aktuální adresář. Pokud váš systém podporuje jednotné pojmenování (UNC), můžete taky zadat síťovou cestu jako: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojité zpětná lomítka jsou nutné v řetězci cesty, proto, že "\\" je znak escape jazyka C++.)

### <a name="remarks"></a>Poznámky

Musí se zavřít databázi podle *lpszName* předtím, než ji opravit. V prostředí, ostatní uživatelé nemohou mít *lpszName* otevřít, zatímco jsou opravy. Pokud *lpszName* není uzavřený nebo není k dispozici pro výhradní použití, dojde k chybě.

Tato členská funkce se pokusí opravit databázi, která byla označena jako může být poškozený neúplný zápis operace. Tato situace může nastat, pokud aplikace pomocí databázový stroj Microsoft Jet neočekávaně zavře kvůli problému hardwaru výpadku nebo počítač napájení. Pokud dokončení operace a volání [Zavřít](../../mfc/reference/cdaodatabase-class.md#close) členská funkce nebo ukončete aplikaci obvyklým způsobem, databázi nebudou označeny jako může být poškozený.

> [!NOTE]
>  Po dokončení opravy databáze, je také vhodné compact pomocí [CompactDatabase](#compactdatabase) členskou funkci defragmentaci souboru a obnovení místa na disku.

Další informace o opravě databází naleznete v tématu "RepairDatabase metodu" v nápovědě k DAO.

##  <a name="rollback"></a>  CDaoWorkspace::Rollback

Voláním této členské funkce ukončit aktuální transakci a obnovení všech databází v pracovním prostoru do stavu před transakce byla zahájena.

```
void Rollback();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Transakce v rámci jednoho objektu pracovního prostoru, jsou vždy globální do pracovního prostoru a nejsou omezeny pouze jednu databázi nebo sadu záznamů. Pokud provádění operací ve více než jednu databázi nebo sadu záznamů v rámci transakce pracovního prostoru, `Rollback` obnoví všechny operace na všechny tyto databáze a sady záznamů.

Pokud objekt workspace zavřete bez uložení nebo vrácení zpět všechny čekající transakce, transakce se automaticky vrátí zpět. Při volání [CommitTrans](#committrans) nebo `Rollback` bez první volání [BeginTrans](#begintrans), dojde k chybě.

> [!NOTE]
>  Při zahájení transakce databázový stroj zaznamenává jeho operace v souboru v adresáři určeném argumentem proměnná prostředí TEMP na pracovní stanici. Pokud soubor protokolu transakcí vyčerpá dostupné úložiště na disku TEMP, databázový stroj způsobí MFC vyvolávat `CDaoException` (Chyba 2004 DAO). V tuto chvíli při volání `CommitTrans`usilujeme o to neurčitý počet operací, ale zbývající nedokončené operace jsou ztraceny a operaci, musí se restartovat. Volání `Rollback` uvolní transakční protokol a vrátí zpět všechny operace v transakci.

##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword

Voláním této členské funkce pro nastavení výchozí heslo, která používá databázový stroj při vytvoření pracovního prostoru objektu bez určité heslo.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>Parametry

*lpszPassword*<br/>
Výchozí heslo. Heslo může mít až 14 znaků a může obsahovat libovolný znak s výjimkou ASCII 0 (null). Hesla jsou malá a velká písmena.

### <a name="remarks"></a>Poznámky

Výchozí heslo, které jste nastavili platí pro nové pracovní prostory vytvořené po volání. Při vytváření dalších pracovních prostorů, není nutné zadat heslo [vytvořit](#create) volání.

Chcete-li použít tuto funkci člena:

1. Vytvoření `CDaoWorkspace` objektu, ale Nevolejte `Create`.

1. Volání `SetDefaultPassword` a pokud chcete, [SetDefaultUser](#setdefaultuser).

1. Volání `Create` pro tento objekt pracovního prostoru nebo další balíčky bez zadávání hesla.

Ve výchozím nastavení je vlastnost DefaultUser nastavena na "admin" a DefaultPassword vlastnost je nastavena na prázdný řetězec ("").

Další informace o zabezpečení najdete v tématu "Oprávnění vlastnost" v nápovědě rozhraní DAO. Související informace naleznete v tématech "DefaultPassword vlastnosti" a "DefaultUser" v nápovědě k DAO.

##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser

Voláním této členské funkce pro nastavení výchozí uživatelské jméno, která používá databázový stroj při vytvoření pracovního prostoru objektu bez určité uživatelské jméno.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>Parametry

*lpszDefaultUser*<br/>
Výchozí uživatelské jméno. Uživatelské jméno může mít délku 1 až 20 znaků a obsahovat abecední znaky, znaky s diakritikou, čísla, mezery a symboly, s výjimkou: "(uvozovky) / (lomítko), \ (zpětné lomítko), \[ \] (závorek): (dvojtečka), &#124; () kanál), \< (méně – znaménko), > (větší – znaménko), + (znaménko plus) = (rovná znaménko), (středník), (čárka) (otazník), \* (hvězdička) úvodní mezery a řídicí znaky (ASCII 00 do ASCII 31). Související informace naleznete v tématu "Vlastnost UserName" v nápovědě k DAO.

### <a name="remarks"></a>Poznámky

Výchozí uživatelské jméno, které jste nastavili platí pro nové pracovní prostory vytvořené po volání. Při vytváření dalších pracovních prostorů, není nutné zadat uživatelské jméno [vytvořit](#create) volání.

Chcete-li použít tuto funkci člena:

1. Vytvoření `CDaoWorkspace` objektu, ale Nevolejte `Create`.

1. Volání `SetDefaultUser` a pokud chcete, [SetDefaultPassword](#setdefaultpassword).

1. Volání `Create` pro tento objekt pracovního prostoru nebo další balíčky bez zadání uživatelského jména.

Ve výchozím nastavení je vlastnost DefaultUser nastavena na "admin" a DefaultPassword vlastnost je nastavena na prázdný řetězec ("").

Související informace naleznete v tématech "DefaultUser vlastnosti" a "DefaultPassword" v nápovědě k DAO.

##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath

Voláním této členské funkce a určí tak umístění, nastavení registru Windows pro databázový stroj Microsoft Jet.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>Parametry

*lpszRegistrySubkey*<br/>
Řetězec obsahující název podklíče registru Windows pro umístění nastavení databázový stroj Microsoft Jet nebo parametry potřebné pro Instalovatelné ISAM databáze.

### <a name="remarks"></a>Poznámky

Volání `SetIniPath` pouze v případě, že budete muset zadat speciální nastavení. Další informace naleznete v tématu "IniPath vlastnost" v nápovědě k DAO.

> [!NOTE]
>  Volání `SetIniPath` během instalace aplikace, není při spuštění aplikace. `SetIniPath` musí být volána před otevřením žádné pracovní prostory, databáze nebo sady záznamů; knihovny MFC, jinak dojde k výjimce.

Tento mechanismus můžete nakonfigurovat nastavení registru uživatelského databázový stroj. Obor tohoto atributu je omezený na aplikaci a bez restartování aplikace se nedá změnit.

##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans

Voláním této členské funkce pro nastavení hodnoty vlastnosti DAO IsolateODBCTrans pro pracovní prostor.

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>Parametry

*bIsolateODBCTrans*<br/>
Předejte hodnotu TRUE, pokud chcete začít, izolace transakce rozhraní ODBC. Předat hodnotu FALSE, pokud chcete zastavit izolace transakce rozhraní ODBC.

### <a name="remarks"></a>Poznámky

V některých případech můžete potřebovat mít více souběžných transakcí čekající na stejné databáze ODBC. K tomuto účelu, budete muset otevřít samostatný pracovní prostor pro každou transakci. I když každý pracovní prostor může mít svůj vlastní ODBC připojení k databázi, toto zpomalí výkon systému. Protože izolace transakce není obvykle vyžaduje, jsou ve výchozím nastavení sdílené připojení ODBC z více objektů pracovní prostor otevřen stejným uživatelem.

Některé servery ODBC, jako je například Microsoft SQL Server, neumožňují souběžné transakce na jedno připojení. Pokud je potřeba mít více transakcí najednou čekající na takové databázi, nastavte vlastnost IsolateODBCTrans na hodnotu TRUE v každém pracovním prostoru, co nejdříve ho otevřete. To přinutí samostatného připojení rozhraní ODBC za každý pracovní prostor.

##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout

Voláním této členské funkce pro nastavení hodnoty vlastnosti DAO LoginTimeout pro pracovní prostor.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>Parametry

*Počet_sekund*<br/>
Počet sekund, než dojde k chybě při pokusu o přihlášení k databázi pro ODBC.

### <a name="remarks"></a>Poznámky

Tato hodnota představuje počet sekund, než dojde k chybě při pokusu o přihlášení k databázi pro ODBC. Ve výchozím nastavení LoginTimeout je 20 sekund. Pokud LoginTimeout je nastaven na hodnotu 0, proběhne žádný časový limit a komunikaci se zdrojem dat může přestat reagovat.

Když se pokoušíte přihlásit ke službě database ODBC, jako je například Microsoft SQL Server, může připojení selhat v důsledku chyby sítě nebo proto, že server není spuštěn. Nečekejte na výchozí 20 sekund na připojení, můžete určit, jak dlouho databázový stroj čeká předtím, než dojde k chybě. Připojování k serveru se stane, implicitně jako součást množství různých událostí, jako je například spuštění dotazu na databázi externího serveru. Hodnota časového limitu je určeno aktuální nastavení vlastnosti LoginTimeout.

Související informace naleznete v tématu "LoginTimeout vlastnost" v nápovědě k DAO.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
