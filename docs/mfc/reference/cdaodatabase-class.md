---
title: Třída CDaoDatabase | Microsoft Docs
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
ms.openlocfilehash: 30e6ac1f1ed780415e7f0a10d82175c2b287fb29
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953893"
---
# <a name="cdaodatabase-class"></a>CDaoDatabase – třída
Reprezentuje připojení k databázi, pomocí kterého lze provozovat na data.  
  
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
|[CDaoDatabase::CanTransact](#cantransact)|Vrátí nenulové hodnoty, pokud databáze podporuje transakce.|  
|[CDaoDatabase::CanUpdate](#canupdate)|Vrátí nenulové hodnoty, pokud `CDaoDatabase` objekt je v aktualizovatelné (ne jen pro čtení).|  
|[CDaoDatabase::Close](#close)|Zavře připojení k databázi.|  
|[CDaoDatabase::Create](#create)|Vytvoří podkladového databázového objektu rozhraní DAO a inicializuje `CDaoDatabase` objektu.|  
|[CDaoDatabase::CreateRelation](#createrelation)|Definuje nový vztah mezi tabulkami v databázi.|  
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Odstraní objekt querydef uloží do databáze querydefs – kolekce.|  
|[CDaoDatabase::DeleteRelation](#deleterelation)|Odstraní existující relace mezi tabulkami v databázi.|  
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Odstraní definici tabulky v databázi. To odstraní skutečné tabulky a všem jeho datům.|  
|[CDaoDatabase::Execute](#execute)|Provede dotaz akce. Volání metody `Execute` pro dotaz, který vrátí výsledky vyvolá výjimku.|  
|[CDaoDatabase::GetConnect](#getconnect)|Vrátí připojovací řetězec použitý k připojení `CDaoDatabase` objekt do databáze. Použít pro ODBC.|  
|[CDaoDatabase::GetName](#getname)|Vrací název databáze aktuálně používá.|  
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Vrátí počet dotazů, které jsou definovány pro databázi.|  
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Vrací informace o zadaný dotaz definované v databázi.|  
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Vrátí počet sekund, po které databázové dotaz operace bude časový limit. Ovlivňuje všechny následné otevřete, přidat nové, aktualizovat a upravit operace a další operace na zdroje dat ODBC (pouze), jako `Execute` volání.|  
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů vliv poslední aktualizace, úprava nebo přidání operace nebo voláním `Execute`.|  
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Vrátí počet vztahy definované mezi tabulkami v databázi.|  
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Vrací informace o zadaný vztah definované mezi tabulkami v databázi.|  
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Vrátí počet tabulek, které jsou definované v databázi.|  
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Vrací informace o zadané tabulky v databázi.|  
|[CDaoDatabase::GetVersion](#getversion)|Vrátí verzi databázový stroj, který je přidružený k databázi.|  
|[CDaoDatabase::IsOpen](#isopen)|Vrátí nenulové hodnoty, pokud `CDaoDatabase` objektu je aktuálně připojen k databázi.|  
|[CDaoDatabase::Open](#open)|Naváže připojení k databázi.|  
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Nastaví počet sekund, po které databázové dotaz operací (na zdroje dat ODBC pouze) bude časový limit. Ovlivňuje všechny následné otevřete, přidat nové, aktualizovat a odstranit operace.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Ukazatel na podkladového databázového objektu DAO.|  
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Ukazatel [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objekt, který obsahuje databázi a definuje jeho místo transakce.|  
  
## <a name="remarks"></a>Poznámky  
 Informace o formátech databáze podporované, najdete v článku [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) – členská funkce. Může mít jeden nebo více `CDaoDatabase` objekty v každém okamžiku aktivní v dané "pracovního prostoru," reprezentována [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objektu. V pracovním prostoru udržuje kolekci otevřete databázové objekty, názvem databáze kolekce.  
  
> [!NOTE]
>  Databázové třídy MFC rozhraní DAO se liší od třídami databází MFC založené na rozhraní ODBC. Všechny názvy tříd DAO databáze mít předponu "CDao". Třída `CDaoDatabase` poskytuje rozhraní podobná třídě ODBC [CDatabase](../../mfc/reference/cdatabase-class.md). Hlavní rozdíl je, že `CDatabase` přistupuje databázového systému prostřednictvím připojení ODBC (Open Database) a ovladač ODBC pro tento databázového systému. `CDaoDatabase` získá přístup k datům prostřednictvím objekt DAO (Data Access) podle databázový stroj Microsoft Jet. Obecně platí třídy MFC založené na rozhraní DAO schopné více než třídy MFC založené na rozhraní ODBC; třídy založené na rozhraní DAO přístup k datům, včetně prostřednictvím ovladače ODBC prostřednictvím svých vlastních databázového stroje. Třídy založené na rozhraní DAO také podporují jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy, aniž by museli DAO volat přímo.  
  
## <a name="usage"></a>Použití  
 Objekty databáze. můžete vytvořit implicitně, při vytváření objektů sady záznamů. Ale můžete také vytvořit databázové objekty explicitně. Chcete-li použít existující databázi explicitně s `CDaoDatabase`, proveďte jednu z následujících akcí:  
  
-   Vytvořit `CDaoDatabase` objekt, předání ukazatel otevřenou [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objektu.  
  
-   Nebo vytvořit `CDaoDatabase` objektu bez zadání prostoru (MFC vytvoří objekt dočasného prostoru).  
  
 Chcete-li vytvořit nové Microsoft Jet (. Databáze MDB), vytvořit `CDaoDatabase` objekt a volání jeho [vytvořit](#create) – členská funkce. Proveďte *není* volání `Open` po `Create`.  
  
 Chcete-li otevřít existující databázi, vytvořit `CDaoDatabase` objekt a volání jeho [otevřete](#open) – členská funkce.  
  
 Tyto techniky databázový objekt DAO připojí k pracovním prostoru kolekce databází a otevře připojení k datům. Když potom vytvoříte [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), nebo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objekty pro provoz v připojené databázi, předat konstruktory pro tyto objekty ukazatel na vaše `CDaoDatabase` objektu. Po dokončení práce připojení, volejte [Zavřít](#close) členské funkce a zrušení `CDaoDatabase` objektu. `Close` Zavře všechny sady záznamů, které nebyly dříve uzavřen.  
  
## <a name="transactions"></a>Transakce  
 Zpracování transakcí databáze je dodána na úrovni pracovního prostoru – najdete v článku [metody BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), a [vrácení zpět](../../mfc/reference/cdaoworkspace-class.md#rollback) členské funkce třídy `CDaoWorkspace` .  
  
## <a name="odbc-connections"></a>Připojení ODBC  
 Doporučeným způsobem, jak pracovat s zdroje dat ODBC se připojit k Microsoft Jet externí tabulky (. Databáze MDB).  
  
## <a name="collections"></a>Kolekce  
 Každá databáze udržuje vlastní kolekce tabledef, querydef, sady záznamů a objekty relace. Třída `CDaoDatabase` poskytuje členské funkce pro manipulaci s tyto objekty.  
  
> [!NOTE]
>  Objekty jsou uloženy v rozhraní DAO, není v MFC databázový objekt. MFC poskytuje třídy pro objekty tabledef, querydef a sady záznamů, ale není pro objekty relace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="cantransact"></a>  CDaoDatabase::CanTransact  
 Volání této funkce člen k určení, zda databáze umožňuje transakce.  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud databáze podporuje transakce; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Transakce jsou spravovány v prostoru databáze.  
  
##  <a name="canupdate"></a>  CDaoDatabase::CanUpdate  
 Volání této funkce člen můžete určit, zda `CDaoDatabase` objekt umožňuje aktualizace.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě `CDaoDatabase` aktualizace umožňuje objektu; jinak 0, která buď, které určuje předán **TRUE** v *bReadOnly* při otevření `CDaoDatabase` objekt, nebo že je samotná databáze jen pro čtení. Najdete v článku [otevřete](#open) – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Informace o databázi aktualizační naleznete v tématu "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="cdaodatabase"></a>  CDaoDatabase::CDaoDatabase  
 Vytvoří `CDaoDatabase` objektu.  
  
```  
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pWorkspace*  
 Ukazatel `CDaoWorkspace` objekt, který bude obsahovat nový objekt databáze. Pokud přijmete výchozí hodnotu **NULL**, konstruktoru vytvoří dočasný `CDaoWorkspace` objekt, který používá výchozí DAO pracovní prostor. Můžete získat ukazatele na objekt prostoru prostřednictvím [m_pWorkspace](#m_pworkspace) – datový člen.  
  
### <a name="remarks"></a>Poznámky  
 Poté, co vytvořen objekt, pokud vytváříte novou Microsoft Jet (. MDB) k databázi, volání objektu [vytvořit](#create) – členská funkce. Pokud jste místo toho otevření existující databázi, volání objektu [otevřete](#open) – členská funkce.  
  
 Až skončíte s daným objektem, by měly volat jeho [Zavřít](#close) členské funkce a pak odstraňte `CDaoDatabase` objektu.  
  
 Vám může být výhodné pro vložení `CDaoDatabase` objekt ve třídě dokumentů.  
  
> [!NOTE]
>  A `CDaoDatabase` je taky vytvořit objekt implicitně Pokud můžete otevřít [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu bez předávání ukazatel na stávající `CDaoDatabase` objektu. Tento objekt databáze je uzavřít, když zavřete objekt sady záznamů.  
  
##  <a name="close"></a>  CDaoDatabase::Close  
 Volání této funkce člen odpojit z databáze a zavřete všechny otevřené sady záznamů, tabledefs – a querydefs – přidružený k databázi.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Je vhodné zavřít tyto objekty sami volání této funkce člen. Zavřením `CDaoDatabase` objekt odstraní ji z kolekce databází v přidruženém [prostoru](../../mfc/reference/cdaoworkspace-class.md). Protože `Close` nezničí `CDaoDatabase` objekt, můžete opakovaně použít objekt otevřením stejné databáze nebo jinou databázi.  
  
> [!CAUTION]
>  Volání [aktualizace](../../mfc/reference/cdaorecordset-class.md#update) – členská funkce (pokud existují čekající úpravy) a `Close` – členská funkce pro všechny objekty otevřete záznamů před zavřením databáze. Pokud opustíte funkce, který deklaruje [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) nebo `CDaoDatabase` objekty v zásobníku, databázi je uzavřen, veškeré neuložené změny budou ztraceny, všechny čekající transakce vrácena zpět a všechny neuložené úpravy data se ztratí.  
  
> [!CAUTION]
>  Pokud se pokusíte zavřít databázového objektu, dokud všechny objekty sady záznamů jsou otevřené nebo pokud se pokusíte zavření objektu pracovního prostoru, zatímco všechny databázové objekty, které patří do této konkrétní pracovního prostoru jsou otevřené, tyto objekty sady záznamů se zavřou a budou všechny čekající aktualizace nebo úpravy vrátit zpět. Když zkusíte zavřít objekt pracovního prostoru, když jsou otevřené žádné databázové objekty, které patří k němu, operace se ukončí všechny databázové objekty, které patří k objektu určitý pracovní prostor, což může vést k objekty uzavřené sady záznamů dochází k uzavření. Pokud jste nezavírejte databázového objektu, MFC hlásí chybu assertion v sestavení pro ladění.  
  
 Pokud objekt databáze je definován v oboru funkce, a ukončete funkce aniž by se zavřel, databázový objekt zůstane otevřené, dokud se explicitně nezavře nebo modul, ve kterém je definovaný je mimo rozsah.  
  
##  <a name="create"></a>  CDaoDatabase::Create  
 Chcete-li vytvořit nové Microsoft Jet (. MDB) k databázi, volání této funkce člen, co vytvoříte `CDaoDatabase` objektu.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszLocale = dbLangGeneral,  
    int dwOptions = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Výraz řetězec, který je název souboru databáze, kterou vytváříte. Úplná cesta a název souboru, může být například "C:\\\MYDB. MDB". Je třeba zadat název. Pokud nezadáte příponu názvu souboru. Připojí se MDB. Pokud síť podporuje uniform zásady vytváření názvů (UNC), bude můžete také určit síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Pouze Microsoft Jet (. Soubory databáze MDB) lze vytvořit pomocí této funkce člen. (Dvojitá zpětná lomítka jsou potřeba v textové literály, protože "\\" je řídicí znak C++.)  
  
 *lpszLocale*  
 Výraz řetězec použitý pro určení pořadí třídění pro vytvoření databáze. Výchozí hodnota je **dbLangGeneral**. Možné hodnoty jsou:  
  
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
  
 *dwOptions*  
 Celé číslo, které určuje jeden nebo více možností. Možné hodnoty jsou:  
  
- **dbEncrypt** vytvoření šifrované databáze.  
  
- **dbVersion10** vytvoření databáze pomocí Microsoft Jet databáze verze 1.0.  
  
- **dbVersion11** vytvoření databáze pomocí Microsoft Jet databáze verze 1.1.  
  
- **dbVersion20** vytvoření databáze pomocí Microsoft Jet databáze verze 2.0.  
  
- **dbVersion30** vytvoření databáze pomocí Microsoft Jet databáze ve verzi 3.0.  
  
 Pokud vynecháte konstanta šifrování, se vytvoří nezašifrované databáze. Můžete zadat pouze jednu verzi konstanta. Pokud vynecháte konstanta verze, se vytvoří databáze, která používá Microsoft Jet databáze ve verzi 3.0.  
  
> [!CAUTION]
>  Pokud databáze nebude zašifrován, je možné, i v případě, že implementujete zabezpečení uživatele a hesla přímo čtení disku binární soubor, který představuje databázi.  
  
### <a name="remarks"></a>Poznámky  
 `Create` Vytvoří soubor databáze a podkladového databázového objektu rozhraní DAO a inicializuje objekt C++. Objekt se připojuje k kolekce přidružené prostoru databází. Objekt databáze je v otevřeném stavu; Nevolejte `Open*` po `Create`.  
  
> [!NOTE]
>  S `Create`, můžete vytvořit pouze Microsoft Jet (. Databáze MDB). Nelze vytvořit ISAM databáze nebo databáze ODBC.  
  
##  <a name="createrelation"></a>  CDaoDatabase::CreateRelation  
 Volání této funkce člen se vytvoří vztah mezi minimálně jedno pole v primární tabulce v databázi a jedno či více polí v cizí tabulce (jiné tabulky v databázi).  
  
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
 *lpszName*  
 Jedinečný název objektu relace. Název musí začínat písmenem a může obsahovat nejvýše 40 znaků. Může obsahovat čísla a podtržítka znaků však nemůže obsahovat interpunkční znaménka nebo mezery.  
  
 *lpszTable*  
 Název v primární tabulce v vztah. Pokud tabulka neexistuje, MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 *lpszForeignTable*  
 Název cizí tabulky vztah. Pokud tabulka neexistuje, MFC vyvolá výjimku typu `CDaoException`.  
  
 *lAttributes*  
 Dlouhou hodnotu, která obsahuje informace o typu relace. Tato hodnota slouží k vynucení referenční integrity, mimo jiné. Můžete použít operátor bitové operace OR ( **&#124;**) kombinovat některý z následujících hodnot (Pokud je kombinace smysl):  
  
- **dbRelationUnique** je relace 1: 1.  
  
- **dbRelationDontEnforce** relace není vynucena (žádné referenční integrity).  
  
- **dbRelationInherited** existuje relace v fixní databázi, která obsahuje dvě připojené tabulky.  
  
- **dbRelationUpdateCascade** aktualizace budou přeneseny (Další informace o cascades, najdete v části poznámky).  
  
- **dbRelationDeleteCascade** budou přeneseny odstranění.  
  
 *lpszField*  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje název pole v primární tabulce (s názvem podle *lpszTable*).  
  
 *lpszForeignField*  
 Ukazatel na obsahující název pole v tabulce cizího řetězce ukončené hodnotou null (s názvem podle *lpszForeignTable*).  
  
 *relinfo*  
 Odkaz na [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objekt, který obsahuje informace o vztahu, kterou chcete vytvořit.  
  
### <a name="remarks"></a>Poznámky  
 Relaci nelze zahrnovat dotazu nebo připojené tabulky z externí databáze.  
  
 Vztah součástí je jedno pole v těchto dvou tabulek, použijte první verzi funkce. Druhá verze použijte, když vztah zahrnuje několik polí. Maximální počet polí v vztah je 14.  
  
 Tato akce vytvoří základní objekt relace rozhraní DAO, ale toto je podrobností implementace MFC, protože je MFC zapouzdření objektů vztah je obsažena v rámci třídy `CDaoDatabase`. MFC neposkytuje třídu pro vztahy.  
  
 Pokud jste nastavili vztah atributů objektu k aktivaci kaskádovými operacemi, databázový stroj automatické aktualizace nebo odstraní záznamy v jednom nebo několika tabulkách, provedení změn související primární klíč tabulky.  
  
 Předpokládejme například, že je vytvořit vztah cascade delete mezi tabulkou Zákazníci a objednávky. Při odstraňování záznamů z tabulky Zákazníci budou odstraněny také záznamy v tabulce objednávky týkající se tohoto zákazníka. Kromě toho pokud vytvoříte cascade odstranit relace mezi tabulkou objednávky a jiné tabulky, záznamy z těchto tabulek jsou automaticky odstraněny při odstraňování záznamů z tabulky zákazníků.  
  
 Související informace naleznete v tématu "CreateRelation způsob" v nápovědě rozhraní DAO.  
  
##  <a name="deletequerydef"></a>  CDaoDatabase::DeleteQueryDef  
 Volání této funkce člena odstranit zadaný querydef – uložit dotazu – z `CDaoDatabase` querydefs – kolekce objektu.  
  
```  
void DeleteQueryDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Název uloženého dotazu, chcete-li odstranit.  
  
### <a name="remarks"></a>Poznámky  
 Později tento dotaz již není definováno v databázi.  
  
 Informace o vytváření objektů querydef najdete v tématu třídy [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Objekt querydef se sváže s konkrétní `CDaoDatabase` objektu, když vytvoříte `CDaoQueryDef` objekt, předání ukazatele na objekt databáze.  
  
##  <a name="deleterelation"></a>  CDaoDatabase::DeleteRelation  
 Volání této funkce člena odstranit stávající relation z kolekce vztahů objekt databáze.  
  
```  
void DeleteRelation(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Název relace odstranit.  
  
### <a name="remarks"></a>Poznámky  
 Pak se vztah již existuje.  
  
 Související informace naleznete v tématu "Odstranit metodu" v nápovědě rozhraní DAO.  
  
##  <a name="deletetabledef"></a>  CDaoDatabase::DeleteTableDef  
 Volání této funkce člena odstranit, pokud má zadaná tabulka a všem jeho datům z `CDaoDatabase` tabledefs – kolekce objektu.  
  
```  
void DeleteTableDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Název tabledef odstranit.  
  
### <a name="remarks"></a>Poznámky  
 Pak se tato tabulka je již definována v databázi.  
  
> [!NOTE]
>  Buďte velmi opatrní nechcete odstranit systémové tabulky.  
  
 Informace o vytváření objektů tabledef najdete v tématu třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Objekt tabledef se sváže s konkrétní `CDaoDatabase` objektu, když vytvoříte `CDaoTableDef` objekt, předání ukazatele na objekt databáze.  
  
 Související informace naleznete v tématu "Odstranit metodu" v nápovědě rozhraní DAO.  
  
##  <a name="execute"></a>  CDaoDatabase::Execute  
 Volání této funkce člen spustit dotaz akce nebo spuštění příkazu jazyka SQL v databázi.  
  
```  
void Execute(
    LPCTSTR lpszSQL,  
    int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSQL*  
 Ukazatel na ukončené hodnotou null řetězec obsahující platný příkaz SQL k provedení.  
  
 *nOptions*  
 Celé číslo, které určuje možnosti týkající se integrity dotazu. Můžete použít operátor bitové operace OR ( **&#124;**) kombinovat některý z následujících konstant (Zadaná kombinace smysl – například nebude kombinovat **dbInconsistent** s **dbConsistent**):  
  
- **dbDenyWrite** odepřít oprávnění k zápisu do jiných uživatelů.  
  
- **dbInconsistent** nekonzistentní aktualizace (výchozí).  
  
- **dbConsistent** konzistentní aktualizace.  
  
- **dbSQLPassThrough** průchozí SQL. Způsobí, že příkaz jazyka SQL, které mají být předány zdroje dat ODBC pro zpracování.  
  
- **dbFailOnError** aktualizace vrátit zpět, pokud dojde k chybě.  
  
- **dbSeeChanges** jiného uživatele je změna dat upravujete generovat chybu spuštění.  
  
> [!NOTE]
>  Pokud oba **dbInconsistent** a **dbConsistent** jsou zahrnuty nebo pokud žádná není součástí, výsledkem je výchozí hodnota. Další informace o těchto konstanty naleznete v tématu "Spustit metodu" v nápovědě rozhraní DAO.  
  
### <a name="remarks"></a>Poznámky  
 `Execute` platí jenom pro dotazy akce nebo průchozí dotazy SQL, které nevracejí výsledky. Nefunguje pro vyberte dotazy, které vrací záznamy.  
  
 Definice a informace o dotazech akce najdete v tématech "Dotaz akce" a "Spustit metodu" v nápovědě rozhraní DAO.  
  
> [!TIP]
>  Zadaná syntakticky správnou příkazu jazyka SQL a příslušná oprávnění, `Execute` – členská funkce nebudou i není-li jeden řádek můžete upravit nebo odstranit. Proto vždy použít **dbFailOnError** možnost při použití `Execute` – členská funkce Spustit aktualizaci nebo odstranění dotazu. Tato možnost způsobí, že MFC má být vyvolána výjimka typu [CDaoException](../../mfc/reference/cdaoexception-class.md) a vrátí zpět všechny změny úspěšné, pokud žádný vliv na záznamy jsou zamčené a nelze aktualizovat ani odstranit. Všimněte si, že můžete vždy volat `GetRecordsAffected` zobrazíte počet záznamů situace měla vliv na.  
  
 Volání [GetRecordsAffected](#getrecordsaffected) – členská funkce databázového objektu, můžete určit počet záznamů ovlivněný pomocí nejnovější `Execute` volání. Například `GetRecordsAffected` vrací informace o počet záznamů odstraněny, aktualizaci nebo vložení při provádění dotazu. Vrátí počet nebude projeví změny v související tabulky při cascade aktualizací nebo odstraní jsou platné.  
  
 `Execute` nevrací sadě záznamů. Pomocí `Execute` v dotazu, který vybere záznamy způsobí, že má být vyvolána výjimka typu MFC `CDaoException`. (Není žádná `ExecuteSQL` – členská funkce podobá `CDatabase::ExecuteSQL`.)  
  
##  <a name="getconnect"></a>  CDaoDatabase::GetConnect  
 Volání této funkce člen načíst připojovací řetězec použitý k připojení `CDaoDatabase` objekt do databáze ODBC nebo ISAM.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Připojení řetězci, pokud [otevřete](#open) byl úspěšně na zdroje dat ODBC volané; v opačném prázdný řetězec. Pro Microsoft Jet (. Databáze MDB) řetězec je vždy prázdné, pokud ji nastavíte pro použití s **dbSQLPassThrough** možnost použít s [Execute](#execute) – členská funkce nebo použít v otevírání sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec obsahuje informace o zdroji této otevřenou databázi nebo databázi použít v předávací dotaz. Připojovací řetězec se skládá z specifikátor typu databáze a nula nebo více parametrů, které jsou oddělené středníky.  
  
> [!NOTE]
>  Použití tříd MFC rozhraní DAO pro připojení ke zdroji dat pomocí rozhraní ODBC je míň efektivní než připojování přes připojené tabulky.  
  
> [!NOTE]
>  Připojovací řetězec se používá k předávání Další informace k rozhraní ODBC a určité ovladače databází podle potřeby. Pro se nepoužívá. Databáze MDB. Pro základní tabulky databáze Microsoft Jet připojovací řetězec je prázdný řetězec ("") s výjimkou použijete ji pro průchozí dotaz SQL jak je popsáno v části vrátit hodnotu.  
  
 Najdete v článku [otevřete](#open) – členská funkce Popis vytvoření připojovacího řetězce. Jakmile byl v nastaven připojovací řetězec `Open` volání později můžete ho zkontrolovat nastavení k určení typu, cesta, uživatelské ID, heslo nebo ODBC zdroj dat databáze.  
  
##  <a name="getname"></a>  CDaoDatabase::GetName  
 Volání této funkce člen načíst název databáze aktuálně otevřené, což je název stávající soubor databáze nebo název registrované zdroje dat ODBC.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplná cesta a název souboru databáze v případě úspěšného; v opačném prázdnou [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Pokud síť podporuje uniform zásady vytváření názvů (UNC), můžete také zadat síťovou cestu – například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojitá zpětná lomítka jsou potřeba v textové literály, protože "\\" je řídicí znak C++.)  
  
 Můžete například zobrazit tento název v nadpisu. Pokud dojde k chybě při načítání názvu, MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
> [!NOTE]
>  Pro lepší výkon při přistupuje externí databáze, doporučujeme připojení tabulky externí databáze k databázi Microsoft Jet (. MDB) namísto připojení ke zdroji dat přímo.  
  
 Typ databáze je indikován soubor nebo adresář, který cesta odkazuje na, a to takto:  
  
|Název cesty odkazuje na...|Typ databáze|  
|--------------------------|-------------------|  
|. Soubor MDB|Databáze Microsoft Jet (Microsoft Access)|  
|Adresář, který obsahuje. Soubory DBF|databáze dBASE|  
|Adresář, který obsahuje. Soubor XLS|Databáze aplikace Microsoft Excel|  
|Adresář, který obsahuje. PDX soubory|Databázový stroj|  
|Adresář, který obsahuje soubory databáze správně formátovaný text|Databáze ve formátu textu|  
  
 Připojovací řetězec databáze pro databáze ODBC, jako je například SQL Server a Oracle, identifikuje název zdroje dat (DSN), která je zaregistrovaná pomocí rozhraní ODBC.  
  
##  <a name="getquerydefcount"></a>  CDaoDatabase::GetQueryDefCount  
 Volání této funkce člen načíst počet dotazů, které jsou definované v databáze querydefs – kolekce.  
  
```  
short GetQueryDefCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet dotazů, které jsou definované v databázi.  
  
### <a name="remarks"></a>Poznámky  
 `GetQueryDefCount` je užitečné, pokud je třeba projít všechny querydefs – v querydefs – kolekce. Pokud chcete získat informace o daný dotaz v kolekci, najdete v části [GetQueryDefInfo](#getquerydefinfo).  
  
##  <a name="getquerydefinfo"></a>  CDaoDatabase::GetQueryDefInfo  
 Volání této funkce člen získat různých typů informací o dotazu definované v databázi.  
  
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
 *nIndex*  
 Index předdefinovaný dotaz do databáze querydefs – kolekce, pro vyhledávání podle indexu.  
  
 *querydefinfo*  
 Odkaz na [cdaoquerydefinfo –](../../mfc/reference/cdaoquerydefinfo-structure.md) objekt, který vrátí požadované informace.  
  
 *dwInfoOptions*  
 Možnosti, které určují, které informace o sadě záznamů k načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit o sada záznamů:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, typ  
  
- `AFX_DAO_SECONDARY_INFO` Primární informace plus: data vytvořená, datum poslední aktualizace, vrátí záznamy, možností aktualizace  
  
- `AFX_DAO_ALL_INFO` Primární a sekundární informace plus: SQL, připojení, odezvy  
  
 *lpszName*  
 Řetězec, který obsahuje název dotazu definované v databázi, pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 Dvě verze funkce se zadávají, takže můžete vybrat dotaz podle indexu v querydefs – kolekce databáze nebo název dotazu.  
  
 Popis vrácené v informace *querydefinfo*, najdete v článku [cdaoquerydefinfo –](../../mfc/reference/cdaoquerydefinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popis *dwInfoOptions*. Jestliže požádáte o jednu úroveň informací, můžete získat žádné předchozí úrovně také informace.  
  
##  <a name="getquerytimeout"></a>  CDaoDatabase::GetQueryTimeout  
 Volání této funkce člen načíst aktuální počet sekund před následných operací v připojené databázi jsou vypršel časový limit.  
  
```  
short GetQueryTimeout();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Krátké celé číslo obsahující hodnotu časového limitu v sekundách.  
  
### <a name="remarks"></a>Poznámky  
 Operace může vypršení časového limitu z důvodu problémy se síťovým přístupem, doba zpracování nadměrné dotazu a tak dále. Když nastavení, ovlivňuje všechny otevřené, přidat nové, aktualizovat a odstranit operací na všechny sady záznamů přidružený k tomuto `CDaoDatabase` objektu. Můžete změnit aktuální nastavení časového limitu voláním [SetQueryTimeout](#setquerytimeout). Změna časový limit dotazu pro sadu záznamů po počáteční hodnotu pro sadu záznamů nezmění. Například následující [přesunout](../../mfc/reference/cdaorecordset-class.md#move) operations nepoužívejte novou hodnotu. Výchozí hodnota je nastavena původně při inicializaci databázového stroje.  
  
 Výchozí hodnota pro vypršení časových limitů dotazu je převzat ze registru systému Windows. Pokud neexistuje žádné nastavení registru, výchozí hodnota je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, dojde k bez časového limitu; a komunikaci s databází může přestat reagovat. Toto chování může být užitečné při vývoji. Pokud volání selže, MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Související informace naleznete v tématu "QueryTimeout vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getrecordsaffected"></a>  CDaoDatabase::GetRecordsAffected  
 Volání této funkce člen můžete určit počet záznamů ovlivněný nejnovější voláním z [Execute](#execute) – členská funkce.  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Dlouhé celé číslo obsahující počet záznamů ovlivněný.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vrácená obsahuje několik záznamů odstraněny, aktualizaci nebo vložení dotazem akce spustit s `Execute`. Vrátí počet nebude projeví změny v související tabulky při cascade aktualizací nebo odstraní jsou platné.  
  
 Související informace naleznete v tématu "RecordsAffected vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getrelationcount"></a>  CDaoDatabase::GetRelationCount  
 Volání této funkce člen získat počet vztahy definované mezi tabulkami v databázi.  
  
```  
short GetRelationCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet vztahy definované mezi tabulkami v databázi.  
  
### <a name="remarks"></a>Poznámky  
 **GetRelationCount** je užitečné, pokud je třeba projít všechny vztahy definované v kolekce vztahů databáze. Pokud chcete získat informace o dané relace v kolekci, najdete v části [GetRelationInfo](#getrelationinfo).  
  
 K objasnění konceptu vztah, zvažte tabulky Dodavatelé a tabulky produktů, které může mít vztah jeden mnoho. V této relaci jednoho dodavatele můžete zadat více než jeden produkt. Další vztahy jsou 1: 1 a m: n.  
  
##  <a name="getrelationinfo"></a>  CDaoDatabase::GetRelationInfo  
 Volání této funkce člen získat informace o zadané relace v kolekci vztahy databázi.  
  
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
 *nIndex*  
 Index objektu relace v kolekci vztahů databáze, pro vyhledávání podle indexu.  
  
 *relinfo*  
 Odkaz na [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) objekt, který vrátí požadované informace.  
  
 *dwInfoOptions*  
 Možnosti, které určují, které informace o vztahu k načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit o vztah:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název tabulky, cizí tabulky  
  
- `AFX_DAO_SECONDARY_INFO` Atributy pole informace  
  
 Informace o pole [cdaorelationfieldinfo –](../../mfc/reference/cdaorelationfieldinfo-structure.md) objekt obsahující pole z účastnících se vztah primární tabulce.  
  
 *lpszName*  
 Řetězec obsahující název objekt relace, pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 Dvě verze této funkce poskytnout přístup pomocí indexu nebo podle názvu. Popis vrácené v informace *relinfo*, najdete v článku [cdaorelationinfo –](../../mfc/reference/cdaorelationinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popis *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, také získat informace v žádné předchozí úrovně.  
  
> [!NOTE]
>  Pokud nastavíte vztah atributů objektu k aktivaci kaskádovými operacemi ( **dbRelationUpdateCascades** nebo **dbRelationDeleteCascades**), databázový stroj Microsoft Jet automaticky aktualizuje nebo Odstraní záznamy v jednom nebo několika tabulkách, provedení změn související primární klíč tabulky. Předpokládejme například, že je vytvořit vztah cascade delete mezi tabulkou Zákazníci a objednávky. Při odstraňování záznamů z tabulky Zákazníci budou odstraněny také záznamy v tabulce objednávky týkající se tohoto zákazníka. Kromě toho pokud vytvoříte cascade odstranit relace mezi tabulkou objednávky a jiné tabulky, záznamy z těchto tabulek jsou automaticky odstraněny při odstraňování záznamů z tabulky zákazníků.  
  
##  <a name="gettabledefcount"></a>  CDaoDatabase::GetTableDefCount  
 Volání této funkce člen načíst počet tabulek, které jsou definované v databázi.  
  
```  
short GetTableDefCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet tabledefs – definované v databázi.  
  
### <a name="remarks"></a>Poznámky  
 `GetTableDefCount` je užitečné, pokud je třeba projít všechny tabledefs – v této databáze tabledefs – kolekce. Pokud chcete získat informace o dané tabulce v kolekci, najdete v části [GetTableDefInfo](#gettabledefinfo).  
  
##  <a name="gettabledefinfo"></a>  CDaoDatabase::GetTableDefInfo  
 Volání této funkce člen získat různých typů informací o tabulky definované v databázi.  
  
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
 *nIndex*  
 Index objektu tabledef ve databáze tabledefs – kolekce, pro vyhledávání podle indexu.  
  
 *tabledefinfo*  
 Odkaz na [cdaotabledefinfo –](../../mfc/reference/cdaotabledefinfo-structure.md) objekt, který vrátí požadované informace.  
  
 *dwInfoOptions*  
 Možnosti, které určují, které informace o tabulce k načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit o vztah:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, aktualizovat, atributy  
  
- `AFX_DAO_SECONDARY_INFO` Primární informace plus: data vytvořená, datum poslední aktualizace, názvu zdrojové tabulky Connect  
  
- `AFX_DAO_ALL_INFO` Primární a sekundární informace plus: počet záznamů ověřovací pravidlo, Text pro ověření,  
  
 *lpszName*  
 Název objektu tabledef, pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 Dvě verze funkce se zadávají, takže můžete vybrat tabulky indexu v tabledefs – kolekce databáze nebo název tabulky.  
  
 Popis vrácené v informace *tabledefinfo*, najdete v článku [cdaotabledefinfo –](../../mfc/reference/cdaotabledefinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popis *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, získáte informace o všech předchozích úrovní.  
  
> [!NOTE]
>  `AFX_DAO_ALL_INFO` Možnost poskytuje informace, které může být pomalé získat. Počítání záznamy v tabulce v takovém případě může být časově velmi náročné Pokud jsou k dispozici mnoho záznamy.  
  
##  <a name="getversion"></a>  CDaoDatabase::GetVersion  
 Volání této funkce člen zjistíte verzi souboru databáze Microsoft Jet.  
  
```  
CString GetVersion();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) určující verzi souboru databáze přidružený k objektu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vrácená představuje číslo verze ve tvaru "major.minor"; například "3.0". Číslo verze produktu (například 3.0) se skládá z číslo verze (3), tečku a číslo verze (0). Verze k datu jsou 1.0, 1.1, 2.0 a 3.0.  
  
 Související informace naleznete v tématu "Verze vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="isopen"></a>  CDaoDatabase::IsOpen  
 Volání této funkce člen můžete určit, zda `CDaoDatabase` objektu je aktuálně otevřený v databázi.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CDaoDatabase` objekt je aktuálně otevřených; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_pdaodatabase"></a>  CDaoDatabase::m_pDAODatabase  
 Obsahuje ukazatel na rozhraní OLE pro základní objekt DAO databáze `CDaoDatabase` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud potřebujete získat přímo přístup k rozhraní DAO, použijte tento ukazatel.  
  
 Informace o volání rozhraní DAO přímo, najdete v části [Technická poznámka 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="m_pworkspace"></a>  CDaoDatabase::m_pWorkspace  
 Obsahuje odkazy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objekt, který obsahuje objekt databáze.  
  
### <a name="remarks"></a>Poznámky  
 Pokud potřebujete získat přímo přístup k pracovním prostoru, použijte tento ukazatel – například k získání ukazatele na další objekty databáze v pracovním prostoru databáze kolekce.  
  
##  <a name="open"></a>  CDaoDatabase::Open  
 Musí volání této funkce člen k chybě při inicializaci nově vytvořený `CDaoDatabase` objekt, který představuje existující databázi.  
  
```  
virtual void Open(
    LPCTSTR lpszName,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T(""));
```  
  
### <a name="parameters"></a>Parametry  
 *lpszName*  
 Výraz řetězec, který je název existující Microsoft Jet (. Soubor databáze MDB). Pokud název souboru s příponou, není potřeba. Pokud síť podporuje uniform zásady vytváření názvů (UNC), bude můžete také určit síťovou cestu, například "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Dvojitá zpětná lomítka jsou potřeba v textové literály, protože "\\" je řídicí znak C++.)  
  
 Některé aspekty platí při použití *lpszName*. Pokud ho:  
  
-   Odkazuje na databázi, která je již otevřeno pro výhradní přístup k jiným uživatelem, generuje MFC se výjimka typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Depeše této výjimky, aby mohl váš uživatel vědět, že databáze není k dispozici.  
  
-   Prázdný řetězec ("") a *lpszConnect* je "ODBC", takže uživatel může vybrat databázi, zobrazí se dialogové okno výpis všech registrovaných názvy zdrojů dat ODBC. Neměli byste přímé připojení ke zdrojům dat ODBC; Místo toho použijte připojené tabulky.  
  
-   V opačném případě neodkazuje na existující databázi nebo platný název zdroje dat ODBC, generuje MFC se výjimka typu `CDaoException`.  
  
> [!NOTE]
>  Podrobnosti o chybových kódech DAO najdete v tématu DAOERR. Soubor H. Související informace naleznete v tématu "Zachytitelné chyb přístupu k datům" v nápovědě rozhraní DAO.  
  
 *bExclusive*  
 Logická hodnota, která je **TRUE** Pokud databáze má být otevřen pro výhradní (sdíleném) a **FALSE** Pokud má být otevřen pro sdílené databáze. Pokud tento argument vynecháte, je pro přístup ke sdílenému otevřít databázi.  
  
 *bReadOnly*  
 Logická hodnota, která je **TRUE** Pokud databáze má být otevřen pro čtení a **FALSE** Pokud databáze má být otevřen pro čtení a zápis. Pokud vynecháte tento argument, databázi otevřít pro čtení a zápis. Všechny závislé sady záznamů zdědí tento atribut.  
  
 *lpszConnect*  
 Použít pro databázi otevřít řetězcového výrazu. Tento řetězec představuje ODBC připojit argumenty. Je třeba zadat argumenty výhradní a jen pro čtení k poskytování zdrojový řetězec. Pokud se databáze nachází databáze Microsoft Jet (. MDB), tento řetězec je prázdný (""). Syntaxe pro výchozí hodnota – **_T**("") – poskytuje přenositelnosti znakové sady Unicode, jakož i ANSI sestavení vaší aplikace.  
  
### <a name="remarks"></a>Poznámky  
 **Otevřete** přidruží základní objekt DAO databáze. Databázový objekt nelze použít k vytvoření sady záznamů, tabledef nebo querydef objekty, dokud není inicializována. **Otevřete** připojí databázový objekt do kolekce přidružené pracovní prostor databáze.  
  
 Použití parametrů následujícím způsobem:  
  
-   Pokud chcete otevřít Microsoft Jet (. Databáze MDB), použijte *lpszName* parametr a předejte jí prázdnou řetězec *lpszConnect* , nebo parametr předejte heslo řetězec ve formátu "; PWD = heslo "Pokud se databáze nachází chráněný heslem (. MDB pouze pro databáze).  
  
-   Pokud chcete otevřít zdroje dat ODBC, předejte platný připojovací řetězec ODBC v *lpszConnect* a prázdný řetězec v *lpszName*.  
  
 Související informace naleznete v tématu "OpenDatabase způsob" v nápovědě rozhraní DAO.  
  
> [!NOTE]
>  Pro lepší výkon při přístupu k externí databází, včetně ISAM a zdroje dat ODBC, je doporučeno připojení tabulky externí databáze k databázi Microsoft Jet engine (. MDB) namísto připojení ke zdroji dat přímo.  
  
 Je možné pro pokus o připojení k vypršení časového limitu, pokud například hostitel databázového systému nedostupný. Pokud se nezdaří pokus o připojení, `Open` vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Zbývající poznámky platí pouze pro databáze ODBC:  
  
 Pokud databáze je databáze ODBC a parametry ve vaší `Open` volání neobsahují dostatek informací pro připojení, ovladač ODBC otevře dialogové okno se získat potřebné informace od uživatele. Při volání `Open`, připojovací řetězec, *lpszConnect*, je uložen soukromě a je k dispozici při volání [GetConnect](#getconnect) – členská funkce.  
  
 Pokud chcete, můžete otevřít dialogové okno Vlastní před voláním `Open` získat informace o od uživatele, jako například heslo, pak přidejte tyto informace do připojovacího řetězce je předat do `Open`. Nebo můžete chtít uložit připojovací řetězec, předáte (třeba v registru systému Windows), takže můžete opakovaně použít ho na další čas voláními aplikace `Open` na `CDaoDatabase` objektu.  
  
 Můžete také použít připojovací řetězec pro více úrovní ověřování přihlášení (jednotlivých jiné `CDaoDatabase` objektu) nebo vyjádřit jiné informace specifické pro databázi.  
  
##  <a name="setquerytimeout"></a>  CDaoDatabase::SetQueryTimeout  
 Volání této funkce člena přepsat výchozí počet sekund před následných operací v připojené databázi časový limit.  
  
```  
void SetQueryTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 *Počet_sekund*  
 Počet sekund před pokusu o dotaz vyprší časový limit.  
  
### <a name="remarks"></a>Poznámky  
 Operace může vypršení časového limitu z důvodu problémy se síťovým přístupem, doba zpracování nadměrné dotazu a tak dále. Volání `SetQueryTimeout` před otevřením sady záznamů nebo před voláním sady záznamů [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [aktualizace](../../mfc/reference/cdaorecordset-class.md#update), nebo [odstranit](../../mfc/reference/cdaorecordset-class.md#delete) členské funkce, pokud chcete změnit dotaz Hodnota časového limitu. Toto nastavení ovlivňuje všechny následné [otevřete](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, `Update`, a `Delete` volání všechny sady záznamů přidružený k tomuto `CDaoDatabase` objektu. Změna časový limit dotazu pro sadu záznamů po počáteční hodnotu pro sadu záznamů nezmění. Například následující [přesunout](../../mfc/reference/cdaorecordset-class.md#move) operations nepoužívejte novou hodnotu.  
  
 Výchozí hodnota pro vypršení časových limitů dotazu je 60 sekund. Ne všechny databáze podporují možnost nastavit hodnotu časového limitu dotazu. Pokud nastavíte hodnotu časového limitu dotazu 0, dojde k bez časového limitu; komunikace s databází může přestat reagovat. Toto chování může být užitečné při vývoji.  
  
 Související informace naleznete v tématu "QueryTimeout vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)   
 [CDatabase – třída](../../mfc/reference/cdatabase-class.md)   
 [CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
