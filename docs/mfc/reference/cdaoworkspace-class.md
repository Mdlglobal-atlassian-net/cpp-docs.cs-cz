---
title: Třída CDaoWorkspace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b249f8069ba12772d21d170b67236a5f013290ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377211"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace – třída
Spravuje relaci databáze s názvem, chráněný heslem z přihlášení a odhlášení, jedním uživatelem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoWorkspace : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|Vytvoří objekt pracovního prostoru. Později, volání **vytvořit** nebo **otevřete**.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoWorkspace::Append](#append)|Nově vytvořeným pracovním prostorem připojí k kolekce pracovních prostorů databázového stroje.|  
|[CDaoWorkspace::BeginTrans](#begintrans)|Spustí novou transakci, která se vztahuje na všechny databáze, otevřete v pracovním prostoru.|  
|[CDaoWorkspace::Close](#close)|Zavře pracovním prostoru a všechny objekty, které obsahuje. Čekající transakce je vrácena zpět.|  
|[CDaoWorkspace::CommitTrans](#committrans)|Dokončení aktuální transakci a uloží změny.|  
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|Zkomprimuje (nebo duplikuje) do databáze.|  
|[CDaoWorkspace::Create](#create)|Vytvoří nový objekt DAO pracovního prostoru.|  
|[CDaoWorkspace::GetDatabaseCount](#getdatabasecount)|Vrátí počet DAO databázové objekty v pracovním prostoru databáze kolekce.|  
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|Vrací informace o zadaná databáze DAO definované v pracovním prostoru databáze kolekce.|  
|[CDaoWorkspace::GetIniPath](#getinipath)|Vrátí umístění databáze Microsoft Jet nastavení inicializace modulu v registru systému Windows.|  
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|Vrátí hodnotu, která určuje, jestli jsou izolované prostřednictvím více transakcí, které zahrnují stejný zdroj dat ODBC vynutit více připojení ke zdroji dat.|  
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|Vrátí počet sekund, než dojde k chybě, když se uživatel pokusí přihlásit k databázi ODBC.|  
|[CDaoWorkspace::GetName](#getname)|Vrátí uživatelem definovaný název pro objekt pracovního prostoru.|  
|[CDaoWorkspace::GetUserName](#getusername)|Vrátí že uživatelské jméno zadané vytvoření pracovního prostoru. Toto je název vlastníka pracovního prostoru.|  
|[CDaoWorkspace::GetVersion](#getversion)|Vrátí řetězec, který obsahuje verzi databázového stroje přidružené k pracovním prostoru.|  
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|Vrátí počet DAO prostoru objektů v kolekci pracovních prostorů databázový stroj.|  
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|Vrátí informace o zadané prostoru DAO definované v kolekci pracovních prostorů databázového stroje.|  
|[CDaoWorkspace::Idle](#idle)|Umožňuje databázový stroj k provedení úlohy na pozadí.|  
|[CDaoWorkspace::IsOpen](#isopen)|Vrátí nenulové hodnoty, pokud je v pracovním prostoru otevřete.|  
|[CDaoWorkspace::Open](#open)|Otevře se explicitně objekt prostoru přidružené k rozhraní DAO na výchozí pracovní prostor.|  
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|Pokusy o opravu poškozené databáze.|  
|[CDaoWorkspace::Rollback](#rollback)|Ukončí aktuální transakci a není uložte změny.|  
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|Nastaví heslo, které databázový stroj používá po vytvoření pracovního prostoru objektu bez konkrétní heslo.|  
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|Nastaví uživatelské jméno, které používá databázový stroj při objekt pracovního prostoru je vytvořen bez určité uživatelské jméno.|  
|[CDaoWorkspace::SetIniPath](#setinipath)|Nastaví umístění databáze Microsoft Jet nastavení inicializace modulu v registru systému Windows.|  
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|Určuje, zda vynucením víc připojení ke zdroji dat jsou izolované více transakcí, které zahrnují stejný zdroj dat ODBC.|  
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|Nastaví počet sekund, než dojde k chybě, když se uživatel pokusí přihlásit k zdroje dat ODBC.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|Odkazuje na základní objekt DAO pracovního prostoru.|  
  
## <a name="remarks"></a>Poznámky  
 Ve většině případů nebude nutné několik pracovních prostorů a nemusíte vytvářet objekty explicitní prostoru; Když otevřete objekty databáze a sady záznamů, používají rozhraní DAO na výchozí pracovní prostor. Ale v případě potřeby můžete spustit více relací najednou vytvořením pracovního prostoru další objekty. Každý objekt prostoru může obsahovat více objektů otevřenou databázi v kolekci vlastní databáze. V prostředí MFC pracovní prostor je primárně správce transakcí, zadání sadu databází, otevřete ve stejném "transakce prostor."  
  
> [!NOTE]
>  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Obecně platí třídy MFC založené na rozhraní DAO schopné více než třídy MFC založené na rozhraní ODBC. Třídy založené na rozhraní DAO přístup k datům prostřednictvím databázový stroj Microsoft Jet, včetně ovladačů ODBC. Také podporují operace jazyka DDL (Data Definition), například vytváření databází a přidávání tabulek a polí pomocí třídy, aniž by museli DAO volat přímo.  
  
## <a name="capabilities"></a>Možnosti  
 Třída `CDaoWorkspace` poskytuje následující:  
  
-   Explicitní přístup, v případě potřeby do pracovního prostoru výchozí, vytvořené Inicializace databázového stroje. Obvykle můžete použít rozhraní DAO na výchozí pracovní prostor implicitně vytvořením objekty databáze a sady záznamů.  
  
-   Transakce místa, ve kterém transakce použít pro všechny databáze, otevřete v pracovním prostoru. Můžete vytvořit další pracovních prostorů můžete spravovat prostory oddělené transakci.  
  
-   Rozhraní pro mnoho vlastností podkladového databázového stroje Microsoft Jet (viz statické členské funkce). Otevírání nebo vytváření pracovního prostoru nebo volání funkce statický člen před otevřít nebo vytvořit, inicializuje databázového stroje.  
  
-   Přístup k kolekce pracovních prostorů databázový stroj, která ukládá všechny aktivní pracovní prostory, které se připojí k němu. Můžete také vytvořit a práce s nimi bez jejich připojování ke kolekci.  
  
## <a name="security"></a>Zabezpečení  
 MFC neimplementuje kolekcí uživatelů a skupin v rozhraní DAO, které se používají pro řízení zabezpečení. Pokud potřebujete těchto aspektů DAO, je nutné programovat sami prostřednictvím přímé volání rozhraní DAO. Informace najdete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="usage"></a>Použití  
 Třídu můžete použít `CDaoWorkspace` na:  
  
-   Explicitně otevřete pracovní prostor výchozí.  
  
     Použití výchozí pracovní prostor je obvykle implicitní – při otevření nové [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekty. Ale možná budete muset k němu přístup explicitně – například pro přístup k vlastnosti modul databáze nebo kolekce pracovních prostorů. Níže najdete v části "Implicitní použití výchozí pracovní prostor".  
  
-   Vytvořte nové pracovní prostory. Volání [připojení](#append) Pokud chcete přidat je do kolekce pracovních prostorů.  
  
-   Otevřete existujícímu pracovnímu prostoru v kolekci pracovních prostorů.  
  
 Vytvoření nového pracovního prostoru, který neexistuje v kolekci je popsáno v části pracovní prostory [vytvořit](#create) – členská funkce. Objekty prostoru žádným způsobem mezi relacemi modul datababase nezachovají. Pokud vaše aplikace staticky odkazuje MFC a ukončení aplikace uninitializes databázového stroje. Pokud aplikace odkazuje dynamicky MFC a databázového stroje není inicializován po odpojen MFC DLL.  
  
 Explicitně otevírání výchozí pracovní prostor nebo otevírání existujícímu pracovnímu prostoru v kolekci pracovních prostorů, je popsaný v části [otevřete](#open) – členská funkce.  
  
 Ukončení relace pracovního prostoru pracovní prostor s ukončením [Zavřít](#close) – členská funkce. **Zavřít** zavře všechny databáze, které jste to ještě dříve, zavřeli, vrácení zpět všechny nepotvrzené transakce.  
  
## <a name="transactions"></a>Transakce  
 DAO spravuje transakce na úrovni pracovního prostoru. transakce v pracovním prostoru s více databází otevřete proto platí pro všechny databáze. Například pokud dvě databáze mít nepotvrzené aktualizace a můžete volat [CommitTrans](#committrans), jsou všechny aktualizace. Pokud chcete omezit transakce na jedné databáze, musíte pro něj objekt samostatné prostoru.  
  
## <a name="implicit-use-of-the-default-workspace"></a>Implicitní použití výchozí pracovní prostor  
 Používá MFC rozhraní DAO na výchozí pracovní prostor implicitně podle následujících okolností:  
  
-   Pokud vytvoříte novou `CDaoDatabase` objektu, ale není prováděna prostřednictvím existující `CDaoWorkspace` objektu MFC vytvoří objekt dočasného prostoru pro vás, který odpovídá na DAO výchozí pracovní prostor. Pokud to uděláte v případě více databází, všechny databázové objekty jsou přidružena výchozí pracovní prostor. Můžete přístup databázi pracovního prostoru prostřednictvím `CDaoDatabase` – datový člen.  
  
-   Podobně pokud vytvoříte `CDaoRecordset` objektu bez nutnosti zadávat ukazatel na `CDaoDatabase` objektu MFC vytvoří objekt dočasné databáze a rozšíření, objekt dočasného prostoru. Sady záznamů databáze a nepřímo jeho prostoru k dispozici prostřednictvím `CDaoRecordset` – datový člen.  
  
## <a name="other-operations"></a>Jiné operace  
 Jiné operace databáze jsou také uvedeny, opravy poškozené databáze nebo kompresi databáze.  
  
 Informace o volání rozhraní DAO přímo a DAO zabezpečení najdete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoWorkspace`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="append"></a>  CDaoWorkspace::Append  
 Volání této funkce člen po zavolání metody [vytvořit](#create).  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Poznámky  
 **Připojit** připojí objekt nově vytvořeným pracovním prostorem pro databázový stroj kolekce pracovních prostorů. Pracovní prostory nezůstanou zachována mezi relacemi modul databáze; jsou uložené pouze v paměti, nikoli na disk. Nemáte připojení pracovního prostoru; Pokud ho použít nechcete, můžete ji přesto použít.  
  
 Připojením pracovního prostoru zůstane v kolekci pracovních prostorů, v aktivní, otevřeném stavu, dokud nebude zavoláte jeho [Zavřít](#close) – členská funkce.  
  
 Související informace naleznete v tématu "Připojit způsob" v nápovědě rozhraní DAO.  
  
##  <a name="begintrans"></a>  CDaoWorkspace::BeginTrans  
 Volání této funkce člen k zahájení transakce.  
  
```  
void BeginTrans();
```  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání metody **metody BeginTrans**, aktualizace, které provedete strukturu dat nebo databáze projeví, jakmile potvrzení transakce. Protože pracovním prostoru definuje místo jedné transakce, transakce se vztahuje na všechny otevřené databáze v pracovním prostoru. K dokončení transakce dvěma způsoby:  
  
-   Volání [CommitTrans](#committrans) – členská funkce Uložit změny pro zdroj dat a potvrzení transakce.  
  
-   Nebo volejte [vrácení zpět](#rollback) – členská funkce zrušit transakce.  
  
 Zavřením prostoru objektu nebo objekt databáze transakce je očekávána vrátí zpět všechny čekající transakce.  
  
 Pokud potřebujete izolace transakce na jeden zdroj dat ODBC od těch, na jiné zdroje dat ODBC, přečtěte si [SetIsolateODBCTrans](#setisolateodbctrans) – členská funkce.  
  
##  <a name="cdaoworkspace"></a>  CDaoWorkspace::CDaoWorkspace  
 Vytvoří `CDaoWorkspace` objektu.  
  
```  
CDaoWorkspace();
```  
  
### <a name="remarks"></a>Poznámky  
 Poté, co vytvořen objekt C++, máte dvě možnosti:  
  
-   Volání objektu [otevřete](#open) – členská funkce otevřete pracovní prostor výchozí nebo otevřete stávající objekt v kolekci pracovních prostorů.  
  
-   Nebo volání objektu [vytvořit](#create) – členská funkce vytvořit nový objekt DAO pracovního prostoru. Explicitně spustí novou relaci pracovního prostoru, které mohou odkazovat na prostřednictvím `CDaoWorkspace` objektu. Po volání **vytvořit**, můžete volat [připojení](#append) Pokud chcete přidat do kolekce pracovních prostorů databázový stroj pracovním prostoru.  
  
 Naleznete v přehledu třídy pro [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) informace o když je potřeba explicitně vytvořit `CDaoWorkspace` objektu. Obvykle použijete pracovních prostorů vytvořit implicitně při otevření [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt bez zadání pracovního prostoru nebo při otevření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu bez zadání objekt databáze. Knihovny MFC rozhraní DAO objekty vytvořené tímto způsobem použít pracovní prostor výchozí DAO společnosti, který se vytvoří jednou a znovu použít.  
  
 Uvolnění pracovního prostoru a obsažené objekty, volání objektu prostoru [Zavřít](#close) – členská funkce.  
  
##  <a name="close"></a>  CDaoWorkspace::Close  
 Volání této funkce člen zavřete objekt pracovního prostoru.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Zavření objektu otevřete pracovní prostor uvolní základní objekt DAO a pokud pracovní prostor je členem kolekce pracovních prostorů, jeho odstranění z kolekce. Volání metody **Zavřít** je dobrým programovacím postupem.  
  
> [!CAUTION]
>  Zavření objektu prostoru zavře všechny otevřené databáze v pracovním prostoru. Výsledkem je otevřené žádné sady záznamů v databázích dochází k uzavření také a všechny neuložené úpravy nebo aktualizace jsou vráceny zpět. Související informace najdete v tématu [CDaoDatabase::Close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset::Close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef::Close](../../mfc/reference/cdaotabledef-class.md#close), a [CDaoQueryDef::Close](../../mfc/reference/cdaoquerydef-class.md#close) členské funkce.  
  
 Pracovní prostor objekty nejsou trvalé; Existují jenom když existují odkazy na ně. To znamená, že při ukončení relace modul databáze, pracovním prostoru a jeho databáze kolekce se nezachovají. Vytvořte znovu v další relaci tak, že znovu otevřete pracovní prostor a databází.  
  
 Související informace naleznete v tématu "Zavřít způsob" v nápovědě rozhraní DAO.  
  
##  <a name="committrans"></a>  CDaoWorkspace::CommitTrans  
 Volání této funkce člen potvrzení transakce – uložte skupinu úpravy a aktualizací na jeden nebo více databází v pracovním prostoru.  
  
```  
void CommitTrans();
```  
  
### <a name="remarks"></a>Poznámky  
 Transakce se skládá z řady změny dat databázi nebo jeho strukturu začínající volání [metody BeginTrans](#begintrans). Po dokončení transakce buď potvrdit ho nebo vraťte zpátky (zrušit změny) s [vrácení zpět](#rollback). Ve výchozím nastavení bez transakcí záznamy se aktualizace potvrdí okamžitě. Volání metody **metody BeginTrans** způsobí, že plánuje aktualizace odloží až zavoláte **CommitTrans**.  
  
> [!CAUTION]
>  Transakce v rámci jednoho pracovního prostoru, jsou vždy globální do pracovního prostoru a nejsou omezeny pouze jedné databáze nebo sada záznamů. Pokud provádíte operace u více než jedné databáze nebo sada záznamů v rámci transakce pracovního prostoru, **CommitTrans** potvrzení všechny čekající aktualizace, a **vrácení zpět** obnoví všechny operace v těchto databází a sady záznamů.  
  
 Při zavření databáze nebo pracovní prostor se čekající transakce transakce jsou všechny vrácena zpět.  
  
> [!NOTE]
>  Toto není mechanismus dvoufázový zápis. Pokud se jedna aktualizace se nepodaří potvrdit, ostatní stále se potvrzení.  
  
##  <a name="compactdatabase"></a>  CDaoWorkspace::CompactDatabase  
 Volání této funkce člen, chcete-li komprimovat zadaný Microsoft Jet (. Databáze MDB).  
  
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
 `lpszSrcName`  
 Název stávající uzavřít databáze. Úplná cesta a název souboru, může být například "C:\\\MYDB. MDB". Název souboru s příponou, je nutné zadat. Pokud síť podporuje uniform zásady vytváření názvů (UNC), bude můžete také určit síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojitá zpětná lomítka se vyžadují v řetězcích cestu, protože "\\" je řídicí znak C++.)  
  
 `lpszDestName`  
 Úplná cesta komprimovaná databáze, kterou vytváříte. Můžete také zadat síťovou cestu jako s `lpszSrcName`. Nelze použít `lpszDestName` ke specifikaci souboru databáze stejné jako `lpszSrcName`.  
  
 `lpszPassword`  
 Heslo použít, pokud chcete komprimovat databáze chráněné heslem. Všimněte si, že pokud používáte verzi `CompactDatabase` , která má heslo, je nutné zadat všechny parametry. Navíc vzhledem k tomu, že je parametr připojit, vyžaduje speciální formátování, následujícím způsobem:; PWD = `lpszPassword`. Například:; PWD = "Radostí". (Požaduje se středník před.)  
  
 `lpszLocale`  
 Výraz řetězec použitý pro určení pořadí pro vytvoření třídění `lpszDestName`. Pokud je tento argument vynechat přijetím na výchozí hodnotu **dbLangGeneral** (viz níže), národní prostředí nové databáze je stejný jako původní databáze. Možné hodnoty jsou:  
  
- **dbLangGeneral** angličtina, němčina, francouzština, portugalština, italština a moderní španělština  
  
- **dbLangArabic** arabština  
  
- **dbLangCyrillic** ruština  
  
- **dbLangCzech** čeština  
  
- **dbLangDutch** holandština  
  
- **dbLangGreek** řečtina  
  
- **dbLangHebrew** hebrejština  
  
- **dbLangHungarian** maďarština  
  
- **dbLangIcelandic** islandském  
  
- **dbLangNordic** skandinávské jazyky (Microsoft databázový stroj Jet verze 1.0 pouze)  
  
- **dbLangNorwdan** norština a dánština  
  
- **dbLangPolish** polština  
  
- **dbLangSpanish** tradiční Španělština  
  
- **dbLangSwedfin** švédština a finština  
  
- **dbLangTurkish** turečtina  
  
 `nOptions`  
 Určuje jeden nebo více možností pro cílovou databázi, `lpszDestName`. Pokud tento argument vynecháte přijetím výchozí hodnota `lpszDestName` budou mít stejné šifrování a stejnou verzi jako `lpszSrcName`. Můžete kombinovat **dbEncrypt** nebo **dbDecrypt** možnost jednou z možností verze pomocí operátoru bitové operace OR. Možné hodnoty, které určují formát databáze, ne verzi modulu databáze, jsou:  
  
- **dbEncrypt** šifrování databáze při kompresi.  
  
- **dbDecrypt** dešifrování databáze při kompresi.  
  
- **dbVersion10** vytvořit databázi, která používá databázový stroj Microsoft Jet verze 1.0 při kompresi.  
  
- **dbVersion11** vytvořit databázi, která používá databázový stroj Microsoft Jet verze 1.1 při kompresi.  
  
- **dbVersion20** vytvořit databázi, která používá databázový stroj Microsoft Jet verze 2.0 při kompresi.  
  
- **dbVersion30** vytvořit databázi, která používá databázový stroj Microsoft Jet verze 3.0 při kompresi.  
  
 Můžete použít **dbEncrypt** nebo **dbDecrypt** v argumentu Možnosti určete, jestli se k šifrování nebo dešifrování databáze, protože se zkomprimuje. Pokud vynecháte šifrování konstanta, nebo pokud současně obsahovat **dbDecrypt** a **dbEncrypt**, `lpszDestName` budou mít stejné šifrování jako `lpszSrcName`. Jeden z verze konstanty způsobem můžete v argumentu Možnosti zadejte verzi formát dat pro komprimovaná databáze. Tato konstanta ovlivňuje pouze verze formátu dat `lpszDestName`. Můžete zadat pouze jednu verzi konstanta. Pokud vynecháte verze konstantu, `lpszDestName` bude mít stejnou verzi jako `lpszSrcName`. Můžete také provést kompresi `lpszDestName` pouze na verzi, která je stejná nebo vyšší než `lpszSrcName`.  
  
> [!CAUTION]
>  Pokud databáze nebude zašifrován, je možné, i v případě, že implementujete zabezpečení uživatele a hesla přímo čtení disku binární soubor, který představuje databázi.  
  
### <a name="remarks"></a>Poznámky  
 Při změně dat v databázi se příslušný soubor databáze se může fragmentovat a použít více místa na disku než je nutné. Měli byste pravidelně zkomprimovat databázi defragmentaci souboru databáze. Zkomprimovaná databáze je obvykle menší. Můžete také změnit pořadí třídění, šifrování nebo verzi formátu dat při kopírování a komprese databáze.  
  
> [!CAUTION]
>  `CompactDatabase` – Členská funkce neprovede konverzi správně dokončení databázi aplikace Microsoft Access z jedné verze do jiné. Formát dat je převést. Microsoft přístup definované objekty, jako je například formulářů a sestav, nejsou převést. Data však správně převede.  
  
> [!TIP]
>  Můžete také použít `CompactDatabase` se zkopírovat soubor databáze.  
  
 Další informace o komprimaci databází naleznete v tématu "CompactDatabase způsob" v nápovědě rozhraní DAO.  
  
##  <a name="create"></a>  CDaoWorkspace::Create  
 Volání této funkce člen chcete vytvořit nový objekt DAO prostoru a přidružit ho MFC `CDaoWorkspace` objektu.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszUserName,  
    LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Řetězec s maximálně 14 znaků, který jedinečně názvy nový objekt pracovního prostoru. Je třeba zadat název. Související informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 *lpszUserName*  
 Uživatelské jméno vlastníka pracovním prostoru. Požadavky najdete `lpszDefaultUser` parametru [SetDefaultUser](#setdefaultuser) – členská funkce. Související informace naleznete v tématu "Vlastnost UserName" v nápovědě rozhraní DAO.  
  
 `lpszPassword`  
 Heslo pro nový objekt pracovního prostoru. Heslo může mít až 14 znaků a může obsahovat jakémukoli znaku kromě ASCII 0 (null). Hesla rozlišují malá a velká písmena. Související informace naleznete v tématu "Vlastnost hesla" v nápovědě rozhraní DAO.  
  
### <a name="remarks"></a>Poznámky  
 Celkový proces vytváření je:  
  
1.  Vytvořit [CDaoWorkspace](#cdaoworkspace) objektu.  
  
2.  Volání objektu **vytvořit** – členská funkce vytvořit základní rozhraní DAO prostoru. Musíte zadat název pracovního prostoru.  
  
3.  Volitelně můžete volat [připojení](#append) Pokud chcete přidat do kolekce pracovních prostorů databázový stroj pracovním prostoru. V pracovním prostoru můžete pracovat bez připojování ho.  
  
 Po **vytvořit** volání, je objekt prostoru v otevřeném stavu, připravený k použití. Nevolejte **otevřete** po **vytvořit**. Nevolejte **vytvořit** Pokud pracovním prostoru již existuje v kolekci pracovních prostorů. **Vytvoření** inicializuje databázový stroj, pokud ji už nebyla inicializována pro vaše aplikace.  
  
##  <a name="getdatabasecount"></a>  CDaoWorkspace::GetDatabaseCount  
 Volání této funkce člen načíst počet objektů DAO databáze v pracovním prostoru databáze kolekci – počet databází, otevřete v pracovním prostoru.  
  
```  
short GetDatabaseCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet databází, otevřete v pracovním prostoru.  
  
### <a name="remarks"></a>Poznámky  
 `GetDatabaseCount` je užitečné, pokud je třeba projít všechny databáze definované v pracovním prostoru databáze kolekce. Pokud chcete získat informace o na danou databázi v kolekci, najdete v části [GetDatabaseInfo](#getdatabaseinfo). Typická využití je volání `GetDatabaseCount` pro počet databází, otevřít, potom použijte toto číslo jako index smyčky pro opakovaná volání `GetDatabaseInfo`.  
  
##  <a name="getdatabaseinfo"></a>  CDaoWorkspace::GetDatabaseInfo  
 Volání této funkce člen získat různých typů informací o databázi otevřete v pracovním prostoru.  
  
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
 `nIndex`  
 Index založený na nule databázového objektu, v pracovním prostoru databáze kolekci, pro vyhledávání podle indexu.  
  
 `dbinfo`  
 Odkaz na [cdaodatabaseinfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) objekt, který vrátí požadované informace.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o databázi pro načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, aktualizovat, transakce  
  
- `AFX_DAO_SECONDARY_INFO` Primární informace plus: časový limit dotazu verze, pořadí řazení  
  
- `AFX_DAO_ALL_INFO` Primární a sekundární informace plus: připojení  
  
 `lpszName`  
 Název databázového objektu, pro vyhledávání podle názvu. Název je řetězec s maximálně 14 znaků, který jedinečně názvy nový objekt pracovního prostoru.  
  
### <a name="remarks"></a>Poznámky  
 Jedna verze funkce umožňuje vyhledat databáze podle indexu. Na další verzi umožňuje hledat podle názvu databáze.  
  
 Popis vrácené v informace `dbinfo`, najdete v článku [cdaodatabaseinfo –](../../mfc/reference/cdaodatabaseinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popisu `dwInfoOptions`. Pokud budete požadovat informace na jedné úrovni, získáte informace o všech předchozích úrovní.  
  
##  <a name="getinipath"></a>  CDaoWorkspace::GetIniPath  
 Volání této funkce člen získat umístění databáze Microsoft Jet nastavení inicializace modulu v registru systému Windows.  
  
```  
static CString PASCAL GetIniPath();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující umístění v registru.  
  
### <a name="remarks"></a>Poznámky  
 Umístění můžete použít k získání informací o nastavení pro databázový stroj. Vrácené informace je ve skutečnosti název podklíče registru.  
  
 Související informace najdete v tématech "IniPath vlastnost" a "Přizpůsobení Windows registru nastavení pro Data Access" v nápovědě rozhraní DAO.  
  
##  <a name="getisolateodbctrans"></a>  CDaoWorkspace::GetIsolateODBCTrans  
 Volání této funkce člen získat aktuální hodnotu vlastnosti DAO IsolateODBCTrans pro pracovní prostor.  
  
```  
BOOL GetIsolateODBCTrans();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou izolované; ODBC – transakce jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V některých situacích může být nutné mít více souběžných transakcí čekající na stejnou databázi ODBC. K tomu potřebujete otevřete samostatné pracovní prostor pro každou transakci. Uvědomte si, že i když každý pracovní prostor může mít svůj vlastní ODBC připojení k databázi, zpomalí výkon systému. Protože izolace transakce není obvykle nutné, připojení ODBC z více objektů prostoru otevřen stejným uživatelem jsou sdíleny ve výchozím nastavení.  
  
 Některé servery ODBC, jako jsou Microsoft SQL Server nepovolují souběžných transakcí na jednoho připojení. Pokud je potřeba mít více než jedna transakce v době čekající na vyřízení oproti takovou databázi, nastavte vlastnost IsolateODBCTrans na **TRUE** v každém pracovním prostoru, jakmile ji otevřete. Vynutí samostatného připojení rozhraní ODBC pro každý pracovní prostor.  
  
 Související informace naleznete v tématu "IsolateODBCTrans vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getlogintimeout"></a>  CDaoWorkspace::GetLoginTimeout  
 Volání této funkce člen získat aktuální hodnotu vlastnosti DAO LoginTimeout pro pracovní prostor.  
  
```  
static short PASCAL GetLoginTimeout();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota představuje počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC. LoginTimeout výchozí nastavení je 20 sekund. Pokud LoginTimeout je nastavená na hodnotu 0, proběhne bez časového limitu a komunikaci se zdrojem dat může přestat reagovat.  
  
 Když se pokoušíte přihlásit do databáze ODBC, jako je Microsoft SQL Server, může připojení selhat v důsledku chyby sítě nebo proto, že server není spuštěn. Místo čekání pro výchozí 20 sekund na připojení, můžete určit, jak dlouho databázový stroj čeká, než vyvolá chybu. Přihlášení na server se stane, implicitně jako součást množství různých událostí, jako je například spuštění dotazu na databázi externího serveru.  
  
 Související informace naleznete v tématu "LoginTimeout vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getname"></a>  CDaoWorkspace::GetName  
 Volání této funkce člen získat název definovaný uživatelem základní objekt DAO prostoru `CDaoWorkspace` objektu.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název definovaný uživatelem objekt DAO pracovního prostoru.  
  
### <a name="remarks"></a>Poznámky  
 Název je užitečné pro přístup k objekt DAO prostoru v kolekci pracovních prostorů databázový stroj podle názvu.  
  
 Související informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getusername"></a>  CDaoWorkspace::GetUserName  
 Volání této funkce člen získat jméno vlastníka pracovního prostoru.  
  
```  
CString GetUserName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) představující vlastník objektu pracovního prostoru.  
  
### <a name="remarks"></a>Poznámky  
 Pro získání nebo nastavení oprávnění pro vlastníka pracovního prostoru, volání rozhraní DAO přímo chcete nastavit vlastnost oprávnění; Určuje, jaká oprávnění má. Chcete-li pracovat s oprávněními, musíte systém. Soubor (mda).  
  
 Informace o volání rozhraní DAO přímo, najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md). Související informace naleznete v tématu "Vlastnost UserName" v nápovědě rozhraní DAO.  
  
##  <a name="getversion"></a>  CDaoWorkspace::GetVersion  
 Volání této funkce člen zjistit verzi databázového stroje Microsoft Jet používán.  
  
```  
static CString PASCAL GetVersion();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) určující verzi databázový stroj, který je přidružený k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vrácená představuje číslo verze ve tvaru "major.minor"; například "3.0". Číslo verze produktu (například 3.0) se skládá z číslo verze (3), tečku a číslo verze (0).  
  
 Související informace naleznete v tématu "Verze vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getworkspacecount"></a>  CDaoWorkspace::GetWorkspaceCount  
 Volání této funkce člen načíst počet objektů DAO prostoru v kolekci pracovních prostorů databázového stroje.  
  
```  
short GetWorkspaceCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet otevřít pracovní prostory v kolekci pracovních prostorů.  
  
### <a name="remarks"></a>Poznámky  
 Tento počet nezahrnuje žádné otevřít pracovní prostory, není připojena ke kolekci. `GetWorkspaceCount` je užitečné, pokud je třeba projít všechny definované pracovní prostory v kolekci pracovních prostorů. Pokud chcete získat informace o daném prostoru v kolekci, najdete v části [GetWorkspaceInfo](#getworkspaceinfo). Typická využití je volání `GetWorkspaceCount` pro počet otevřít pracovní prostory, potom použijte toto číslo jako index smyčky pro opakovaná volání `GetWorkspaceInfo`.  
  
##  <a name="getworkspaceinfo"></a>  CDaoWorkspace::GetWorkspaceInfo  
 Volání této funkce člen získat různých typů informací o otevřete pracovní prostor v relaci.  
  
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
 `nIndex`  
 Index založený na nule objektu databáze v kolekci pracovních prostorů, pro vyhledávání podle indexu.  
  
 `wkspcinfo`  
 Odkaz na [cdaoworkspaceinfo –](../../mfc/reference/cdaoworkspaceinfo-structure.md) objekt, který vrátí požadované informace.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o pracovním prostoru pro načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Jméno  
  
- `AFX_DAO_SECONDARY_INFO` Primární informace plus: uživatelské jméno  
  
- `AFX_DAO_ALL_INFO` Primární a sekundární informace plus: izolovat ODBCTrans  
  
 `lpszName`  
 Název objektu prostoru pro vyhledávání podle názvu. Název je řetězec s maximálně 14 znaků, který jedinečně názvy nový objekt pracovního prostoru.  
  
### <a name="remarks"></a>Poznámky  
 Popis vrácené v informace `wkspcinfo`, najdete v článku [cdaoworkspaceinfo –](../../mfc/reference/cdaoworkspaceinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popisu `dwInfoOptions`. Pokud budete požadovat informace na jedné úrovni, získáte informace i předchozí úrovně.  
  
##  <a name="idle"></a>  CDaoWorkspace::Idle  
 Volání **nečinnosti** databázový stroj poskytnout možnost provádět úlohy na pozadí, které z důvodu intenzivní zpracování dat nemusí být aktuální.  
  
```  
static void PASCAL Idle(int nAction = dbFreeLocks);
```  
  
### <a name="parameters"></a>Parametry  
 `nAction`  
 Akce, aby v průběhu zpracování nečinnosti. Aktuálně je platné pouze akce **dbFreeLocks**.  
  
### <a name="remarks"></a>Poznámky  
 Často to platí v prostředí s více uživateli, multitasking, ve kterých není dostatek doba zpracování na pozadí udržovat všechny záznamy v sadě záznamů aktuální.  
  
> [!NOTE]
>  Volání metody **nečinnosti** není nutné s databází vytvořených pomocí verze 3.0 databázového stroje Microsoft Jet. Použití **nečinnosti** pouze u databází vytvořených s předchozími verzemi.  
  
 Obvykle čtení, které jsou odebrány zámky a datům v objektech místní dynamické sady záznamů je aktualizováno pouze v případě, že dochází k žádné další akce (včetně pohyb myši). Když zavoláte pravidelně **nečinnosti**, poskytovat databázový stroj s časem prací s uvolněním zpracování úlohy na pozadí nepotřebné číst zámky. Určení **dbFreeLocks** konstanta jako argument zpozdí zpracovávání, dokud všechny čtení zámky neuvolní.  
  
 Tato funkce člen není potřeba v prostředí jednoho uživatele, není-li více instancí aplikace běží. **Nečinnosti** – členská funkce může zvýšit výkon v prostředí s více uživateli, tím, že vynucuje databázový stroj zápis dat na disk, uvolnění uzamčení v paměti. Můžete také uvolnit zámky čtení tak, že operace součástí transakce.  
  
 Související informace naleznete v tématu "Nečinnosti způsob" v nápovědě rozhraní DAO.  
  
##  <a name="isopen"></a>  CDaoWorkspace::IsOpen  
 Volání této funkce člen můžete určit, zda `CDaoWorkspace` je otevřen objekt – to znamená, zda objekt MFC byla inicializována voláním do [otevřete](#open) nebo volání [vytvořit](#create).  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je objekt pracovní prostor otevřít; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Bude možné volat žádný člena funkce pracovního prostoru, který je v otevřeném stavu.  
  
##  <a name="m_pdaoworkspace"></a>  CDaoWorkspace::m_pDAOWorkspace  
 Ukazatel na základní objekt DAO pracovního prostoru.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen dat použijte, pokud potřebují přímý přístup k základní objekt DAO. Můžete volat rozhraní DAO objekt prostřednictvím tento ukazatel.  
  
 Informace o přístup k objektům DAO přímo najdete v tématu [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="open"></a>  CDaoWorkspace::Open  
 Otevře se explicitně objekt prostoru přidružené k rozhraní DAO na výchozí pracovní prostor.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Název objektu prostoru DAO otevřete – řetězec s maximálně 14 znaků, který jedinečně názvy pracovním prostoru. Přijměte výchozí hodnotu **NULL** explicitně otevřete pracovní prostor výchozí. Pojmenování požadavky, najdete v článku `lpszName` parametr pro [vytvořit](#create). Související informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `CDaoWorkspace` objektu, volání této funkce člen provedete jednu z následujících akcí:  
  
-   Explicitně otevřete pracovní prostor výchozí. Předat **NULL** pro `lpszName`.  
  
-   Otevřete existující `CDaoWorkspace` objektu, členem kolekce pracovních prostorů, podle názvu. Předejte platný název pro existující objekt pracovního prostoru.  
  
 **Otevřete** převádí objekt prostoru v otevřeném stavu a také inicializuje databázový stroj, pokud ji už nebyla inicializována pro vaše aplikace.  
  
 I když mnoho `CDaoWorkspace` členské funkce lze volat jen po otevření pracovního prostoru, následující členské funkce, které fungují na databázového stroje, jsou po vytváření objektu C++, ale před voláním dostupné **otevřít** :  
  
||||  
|-|-|-|  
|[Vytvoření](#create)|[GetVersion –](#getversion)|[SetDefaultUser](#setdefaultuser)|  
|[GetIniPath](#getinipath)|[Nečinnosti](#idle)|[SetIniPath](#setinipath)|  
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|  
  
##  <a name="repairdatabase"></a>  CDaoWorkspace::RepairDatabase  
 Volání této funkce člen, pokud je potřeba se pokusí o opravu poškození databáze, který přistupuje k databázový stroj Microsoft Jet.  
  
```  
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Cesta a název souboru pro soubor databáze stroje Microsoft Jet. Pokud vynecháte cestu, prohledají se jenom aktuální adresář. Pokud systém podporuje uniform zásady vytváření názvů (UNC), můžete také zadáte síťovou cestu, jako například: "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojitá zpětná lomítka jsou potřeba v řetězec cesty, protože "\\" je řídicí znak C++.)  
  
### <a name="remarks"></a>Poznámky  
 Je třeba nejprve zavřít do databáze určené parametrem `lpszName` před jeho opravy. V prostředí s více uživateli nemůže mít ostatní uživatelé `lpszName` otevřít, ačkoli jsou opravu ho. Pokud `lpszName` není uzavřený, nebo není k dispozici pro výhradní použití, dojde k chybě.  
  
 Tato funkce člen se pokusí opravit databázi, která byla označena jako může být poškozený neúplné zápisu operace. Tato situace může nastat, pokud aplikace pomocí databázový stroj Microsoft Jet se neočekávaně uzavřelo kvůli problému hardwaru výpadku nebo počítač napájení. Pokud dokončení operace a volání [Zavřít](../../mfc/reference/cdaodatabase-class.md#close) – členská funkce nebo můžete ukončit aplikaci obvyklým způsobem, databázi nebudou označeny jako pravděpodobně poškozen.  
  
> [!NOTE]
>  Po dokončení opravy databáze, je také vhodné compact pomocí [CompactDatabase](#compactdatabase) – členská funkce defragmentace souboru a obnovení místa na disku.  
  
 Další informace o opravě databází naleznete v tématu "RepairDatabase způsob" v nápovědě rozhraní DAO.  
  
##  <a name="rollback"></a>  CDaoWorkspace::Rollback  
 Volání této funkce člen ukončit aktuální transakci a obnovení všechny databáze v pracovním prostoru pro jejich stavu, než bylo spuštěno transakce.  
  
```  
void Rollback();
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Transakce v rámci jednoho objektu pracovního prostoru, jsou vždy globální do pracovního prostoru a nejsou omezeny pouze jedné databáze nebo sada záznamů. Pokud provádíte operace u více než jedné databáze nebo sada záznamů v rámci transakce pracovního prostoru, **vrácení zpět** obnoví všechny operace u všech těchto databází a sady záznamů.  
  
 Pokud zavřete objekt prostoru bez uložení nebo vrácení zpět všechny čekající transakce, transakce se automaticky vrácena zpět. Když zavoláte [CommitTrans](#committrans) nebo **vrácení zpět** bez první volání [metody BeginTrans](#begintrans), dojde k chybě.  
  
> [!NOTE]
>  Když začnete transakce, databázový stroj zaznamenává jeho operací v souboru uchovává se v adresáři zadaném proměnnou prostředí TEMP na pracovní stanici. Pokud soubor protokolu transakcí vyčerpá úložiště k dispozici na dočasné jednotce, databázový stroj způsobí, že má být vyvolána MFC `CDaoException` (Chyba DAO 2004). V tomto okamžiku, když zavoláte **CommitTrans**, neurčitém počet operací potvrzeny, ale zbývající nedokončené operace budou ztraceny a operaci je třeba znovu spustit. Volání metody **vrácení zpět** uvolní transakční protokol a vrátí zpět všechny operace v transakci.  
  
##  <a name="setdefaultpassword"></a>  CDaoWorkspace::SetDefaultPassword  
 Volání této funkce člen nastavit výchozí heslo, které používá databázový stroj při objekt pracovního prostoru je vytvořen bez konkrétní heslo.  
  
```  
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPassword`  
 Výchozí heslo. Heslo může mít až 14 znaků a může obsahovat jakémukoli znaku kromě ASCII 0 (null). Hesla rozlišují malá a velká písmena.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí heslo, které nastavení se vztahuje na nové pracovní prostory, které jste vytvořili po volání. Když vytvoříte další pracovní prostory, není potřeba zadat heslo v [vytvořit](#create) volání.  
  
 Použití této funkce člen:  
  
1.  Vytvořit `CDaoWorkspace` objektu, ale Nevolejte **vytvořit**.  
  
2.  Volání `SetDefaultPassword` a, pokud chcete, můžete [SetDefaultUser](#setdefaultuser).  
  
3.  Volání **vytvořit** pro tento objekt pracovního prostoru nebo následné těch bez zadání hesla.  
  
 Ve výchozím nastavení, DefaultUser vlastnost nastavena na "admin" a DefaultPassword vlastnost nastavena na prázdný řetězec ("").  
  
 Další informace o zabezpečení naleznete v tématu "Oprávnění vlastnost" v nápovědě rozhraní DAO. Související informace najdete v tématech "DefaultPassword vlastnost" a "DefaultUser vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="setdefaultuser"></a>  CDaoWorkspace::SetDefaultUser  
 Volání této funkce člen nastavit výchozí uživatelské jméno, které modul databáze používá po vytvoření pracovního prostoru objektu bez určité uživatelské jméno.  
  
```  
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDefaultUser`  
 Výchozí uživatelské jméno. Uživatelské jméno může být 1-20 znaků a obsahovat abecední znaky, znaky s diakritikou, číslice, mezery a symboly s výjimkou: "(uvozovek), / (lomítko), \ (zpětné lomítko), \[ \] (závorky): (dvojtečka), &#124; () kanálu) \< (méně – než přihlašovací), > (větší – znaménko), + (znaménko plus), = (rovnat přihlašovací), (středníkem), (čárkami) (otazník) * (hvězdička) úvodní mezery a řídicí znaky (ASCII 00 do 31, ASCII). Související informace naleznete v tématu "Vlastnost UserName" v nápovědě rozhraní DAO.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí uživatelské jméno, které nastavení se vztahuje na nové pracovní prostory, které jste vytvořili po volání. Když vytvoříte další pracovní prostory, není potřeba zadat uživatelské jméno ve [vytvořit](#create) volání.  
  
 Použití této funkce člen:  
  
1.  Vytvořit `CDaoWorkspace` objektu, ale Nevolejte **vytvořit**.  
  
2.  Volání `SetDefaultUser` a, pokud chcete, můžete [SetDefaultPassword](#setdefaultpassword).  
  
3.  Volání **vytvořit** pro tento objekt pracovního prostoru nebo následné těch bez zadání uživatelského jména.  
  
 Ve výchozím nastavení, DefaultUser vlastnost nastavena na "admin" a DefaultPassword vlastnost nastavena na prázdný řetězec ("").  
  
 Související informace najdete v tématech "DefaultUser vlastnost" a "DefaultPassword vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="setinipath"></a>  CDaoWorkspace::SetIniPath  
 Volání této funkce člen a zadejte umístění, nastavení registru Windows pro databázový stroj Microsoft Jet.  
  
```  
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRegistrySubkey*  
 Řetězec obsahující název podklíče registru systému Windows pro umístění nastavení databázového stroje Microsoft Jet nebo parametry, které jsou potřebné pro instalovatelných ISAM databáze.  
  
### <a name="remarks"></a>Poznámky  
 Volání `SetIniPath` pouze v případě, že budete muset zadat speciální nastavení. Další informace naleznete v tématu "IniPath vlastnost" v nápovědě rozhraní DAO.  
  
> [!NOTE]
>  Volání `SetIniPath` během instalace aplikace, není při spuštění aplikace. `SetIniPath` musí být voláno před otevřením žádné pracovní prostory, databáze nebo sady záznamů; MFC, jinak vyvolá výjimku.  
  
 Tento mechanismus můžete nakonfigurovat nastavení registru zadaný uživatelem databázového stroje. Obor tohoto atributu je omezený na vaší aplikace a nejde ho změnit bez restartování aplikace.  
  
##  <a name="setisolateodbctrans"></a>  CDaoWorkspace::SetIsolateODBCTrans  
 Volání této funkce člen nastavit hodnotu vlastnosti DAO IsolateODBCTrans pro pracovní prostor.  
  
```  
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```  
  
### <a name="parameters"></a>Parametry  
 *bIsolateODBCTrans*  
 Předat **TRUE** Pokud chcete začít izolace ODBC – transakce. Předat **FALSE** Pokud budete chtít zastavit izolace ODBC – transakce.  
  
### <a name="remarks"></a>Poznámky  
 V některých situacích může být nutné mít více souběžných transakcí čekající na stejnou databázi ODBC. K tomu potřebujete otevřete samostatné pracovní prostor pro každou transakci. I když každý pracovní prostor může mít svůj vlastní ODBC připojení k databázi, to zpomalí výkon systému. Protože izolace transakce není obvykle nutné, připojení ODBC z více objektů prostoru otevřen stejným uživatelem jsou sdíleny ve výchozím nastavení.  
  
 Některé servery ODBC, jako jsou Microsoft SQL Server nepovolují souběžných transakcí na jednoho připojení. Pokud je potřeba mít více než jedna transakce v době čekající na vyřízení oproti takovou databázi, nastavte vlastnost IsolateODBCTrans na **TRUE** v každém pracovním prostoru, jakmile ji otevřete. Vynutí samostatného připojení rozhraní ODBC pro každý pracovní prostor.  
  
##  <a name="setlogintimeout"></a>  CDaoWorkspace::SetLoginTimeout  
 Volání této funkce člen nastavit hodnotu vlastnosti DAO LoginTimeout pro pracovní prostor.  
  
```  
static void PASCAL SetLoginTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `nSeconds`  
 Počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota představuje počet sekund, než dojde k chybě při pokusu o přihlášení k databázi ODBC. LoginTimeout výchozí nastavení je 20 sekund. Pokud LoginTimeout je nastavená na hodnotu 0, proběhne bez časového limitu a komunikaci se zdrojem dat může přestat reagovat.  
  
 Když se pokoušíte přihlásit do databáze ODBC, jako je Microsoft SQL Server, může připojení selhat v důsledku chyby sítě nebo proto, že server není spuštěn. Místo čekání pro výchozí 20 sekund na připojení, můžete určit, jak dlouho databázový stroj čeká, než vyvolá chybu. Protokolování na server se stane, implicitně jako součást množství různých událostí, jako je například spuštění dotazu na databázi externího serveru. Hodnota časového limitu je určen podle aktuální nastavení vlastnosti LoginTimeout.  
  
 Související informace naleznete v tématu "LoginTimeout vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
