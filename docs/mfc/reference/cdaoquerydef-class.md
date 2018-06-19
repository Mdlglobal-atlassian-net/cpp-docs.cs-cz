---
title: Třída CDaoQueryDef | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81e7d3b093da8127887878b2ac5f2af652f549c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375791"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef – třída
Představuje definici dotazu, nebo "querydef", obvykle 1, které jsou uloženy v databázi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Vytvoří **CDaoQueryDef** objektu. Další volání **otevřete** nebo **vytvořit**, v závislosti na vašich potřebách.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|Připojí querydef databáze querydefs – kolekce jako uložený dotaz.|  
|[CDaoQueryDef::CanUpdate](#canupdate)|Vrátí nenulové hodnoty, pokud dotaz můžete aktualizovat databázi.|  
|[CDaoQueryDef::Close](#close)|Zavře querydef objekt. Zrušte objekt C++ po dokončení s ním.|  
|[CDaoQueryDef::Create](#create)|Vytvoří základní querydef objekt DAO. Použít querydef jako dočasné dotazu nebo volání **připojení** ji uložit v databázi.|  
|[CDaoQueryDef::Execute](#execute)|Provede dotaz objektu querydef definované.|  
|[CDaoQueryDef::GetConnect](#getconnect)|Vrátí přidružený querydef připojovací řetězec. Připojovací řetězec Určuje zdroj dat. (Pro SQL průchozí dotazuje pouze; v opačném případě prázdný řetězec.)|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Vrátí datum vytvoření uloženého dotazu.|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum poslední aktualizace uloženého dotazu.|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Vrátí počet polí, které jsou definované querydef.|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Vrací informace o zadané pole definovaných v dotazu.|  
|[CDaoQueryDef::GetName](#getname)|Vrací název querydef.|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Vrátí hodnotu časového limitu používá rozhraní ODBC (pro dotaz rozhraní ODBC) Pokud se spustí querydef. Určuje, jak dlouho umožňující na dokončení akce dotazu.|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Vrátí počet parametrů definovaných pro dotaz.|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Vrátí informace o zadaný parametr dotazu.|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Vrátí hodnotu zadaného parametru do dotazu.|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Vrátí počet záznamů vliv dotaz akce.|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Vrátí nenulové hodnoty, pokud dotaz definované querydef vrátí záznamy.|  
|[CDaoQueryDef::GetSQL](#getsql)|Vrátí řetězec SQL, který určuje definované querydef dotazu.|  
|[CDaoQueryDef::GetType](#gettype)|Vrátí typ dotazu: odstranění, aktualizovat, připojit, vytvořit tabulku a tak dále.|  
|[CDaoQueryDef::IsOpen](#isopen)|Vrátí nenulové hodnoty, pokud querydef je otevřený a mohou být provedeny.|  
|[CDaoQueryDef::Open](#open)|Otevře se existující querydef uložené v databáze querydefs – kolekce.|  
|[CDaoQueryDef::SetConnect](#setconnect)|Nastaví připojovací řetězec pro předávací dotaz SQL na zdroje dat ODBC.|  
|[CDaoQueryDef::SetName](#setname)|Nastaví název uloženého dotazu, pokud byla vytvořena querydef nahraďte název používá.|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Nastaví hodnotu časového limitu používá rozhraní ODBC (pro dotaz rozhraní ODBC) Pokud se spustí querydef.|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Nastaví hodnotu zadaného parametru do dotazu.|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Určuje, zda querydef vrátí záznamy. Nastavení tohoto atributu na **TRUE** je platná pouze pro průchozí dotazy SQL.|  
|[CDaoQueryDef::SetSQL](#setsql)|Nastaví řetězec SQL, který určuje definované querydef dotazu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Ukazatel rozhraní OLE pro základní objekt DAO querydef.|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Ukazatel `CDaoDatabase` objekt, ke kterému je přiřazeno querydef. Querydef mít třeba uložené v databázi, nebo ne.|  
  
## <a name="remarks"></a>Poznámky  
 Querydef je datový objekt, který obsahuje příkaz jazyka SQL, který popisuje dotazu a její vlastnosti, jako je například "Datum vytvoření" a "Časový limit ODBC." Můžete také vytvořit dočasný querydef objekty bez uložení, ale je vhodné – a mnohem efektivnější – uložení běžně znovu dotazů v databázi. A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt udržuje kolekci volat querydefs – kolekce, která obsahuje její uložené querydefs –.  
  
> [!NOTE]
>  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Můžete i nadále přístup ke zdrojům dat ODBC s třídy DAO. Obecně platí třídy MFC založené na rozhraní DAO schopné více než třídy MFC založené na rozhraní ODBC; třídy založené na rozhraní DAO přístup k datům, včetně prostřednictvím ovladače ODBC prostřednictvím svých vlastních databázového stroje. Třídy založené na rozhraní DAO také podporují jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy, aniž by museli DAO volat přímo.  
  
## <a name="usage"></a>Použití  
 Querydef objekty použijte buď pro práci s stávající uložený dotaz nebo vytvořit nový uložili dotazu nebo dočasné dotazu:  
  
1.  Ve všech případech se nejprve vytvořit `CDaoQueryDef` objekt, poskytuje odkazy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu, ke které patří dotazu.  
  
2.  Proveďte následující kroky, v závislosti na tom, co chcete použít:  
  
    -   Pokud chcete použít stávající uložený dotaz, volání objektu querydef [otevřete](#open) – členská funkce, zadávání názvu uloženého dotazu.  
  
    -   Pokud chcete vytvořit nový uložený dotaz, volání objektu querydef [vytvořit](#create) – členská funkce, poskytuje název dotazu. Potom zavolejte [připojení](#append) Uložte dotaz jejich přidáním do databáze querydefs – kolekce. **Vytvořit** umístí querydef do otevřeném stavu, takže po volání **vytvořit** Nevolejte **otevřete**.  
  
    -   Chcete-li vytvořit dočasný querydef, volejte **vytvořit**. Zadat prázdný řetězec pro název dotazu. Nevolejte **připojení**.  
  
 Po dokončení pomocí objektu querydef volat jeho [Zavřít](#close) členské funkce; pak odstraňte objekt querydef.  
  
> [!TIP]
>  Nejjednodušší způsob, jak vytvořit uložené dotazy je jejich vytvoření a uložit je do databáze pomocí aplikace Microsoft Access. Pak můžete otevřít a použít je v kódu MFC.  
  
## <a name="purposes"></a>Pro účely  
 Objekt querydef můžete použít pro žádné z těchto důvodů:  
  
-   Chcete-li vytvořit `CDaoRecordset` objektu  
  
-   Volání objektu **Execute** – členská funkce se přímo spustit dotaz akce nebo předávací dotaz SQL  
  
 Můžete použít objekt querydef pro jakýkoli typ dotazu, včetně vyberte akci, sestavě křížových tabulek, odstranění, aktualizace, připojit, vytvořit tabulku, definice dat, SQL průchozí, union a hromadně dotazy. Typ dotazu je určen podle obsahu příkazu SQL, který zadáte. Informace o typech dotazů najdete v tématu **Execute** a [GetType](#gettype) členské funkce. Sady záznamů se běžně používají pro vrácení řádek dotazy, obvykle ty pomocí **vyberte... Z** klíčová slova. **Spuštění** se nejčastěji používá pro hromadné operace. Další informace najdete v tématu [Execute](#execute) a [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
## <a name="querydefs-and-recordsets"></a>Querydefs – a sady záznamů  
 Použití objektu querydef k vytvoření `CDaoRecordset` objektu, obvykle vytvořit nebo otevřít querydef, jak je popsáno výše. Pak vytvořte objekt sady záznamů, předání ukazatel objektu querydef při volání [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Querydef, kterou předáte musí být v otevřeném stavu. Další informace najdete v tématu třídy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Querydef nelze použít k vytvoření sady záznamů (nejčastěji používá pro querydef), pokud je v otevřeném stavu. Převést querydef do otevřeném stavu voláním buď **otevřete** nebo **vytvořit**.  
  
## <a name="external-databases"></a>Externí databáze  
 QueryDef objekty jsou upřednostňovaný způsob, jak používat nativní SQL dialekt motoru externí databáze. Můžete například vytvořit dotaz Transact SQL (jak je použita v systému Microsoft SQL Server) a uložte ji do querydef objektu. Když budete muset použít příkazu jazyka SQL není založen na databázový stroj Microsoft Jet, musíte zadat připojovací řetězec, který ukazuje na externí zdroj dat. Dotazy s platný připojovací řetězce vynechat databázový stroj a předat dotaz přímo do externího databázový server pro zpracování.  
  
> [!TIP]
>  Upřednostňovaný způsob práce s tabulkami ODBC je připojte je k Microsoft Jet (. Databáze MDB).  
  
 Související informace najdete v tématech "QueryDef objekt", "Querydefs – kolekce" a "CdbDatabase objekt" v sadě SDK rozhraní DAO.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="append"></a>  CDaoQueryDef::Append  
 Volání této funkce člen po zavolání metody [vytvořit](#create) k vytvoření nového objektu querydef.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Poznámky  
 **Připojit** uloží querydef v databázi připojením objekt do databáze querydefs – kolekce. Můžete použít querydef jako dočasný objekt bez připojování ji, ale pokud se má zachovat, musí volat **připojení**.  
  
 Pokud se pokusíte připojit objektu dočasné querydef, MFC vyvolá výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate  
 Volání této funkce člen k určení, zda lze upravit querydef – jako je například změna jeho názvu nebo řetězec SQL.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou povolena k úpravě querydef; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Querydef můžete upravit, pokud:  
  
-   Ji není založena na databázi, která je otevřená jen pro čtení.  
  
-   Nemáte oprávnění k aktualizaci databáze.  
  
     To závisí na tom, jestli jste implementovali funkce zabezpečení. MFC neposkytuje podporu pro zabezpečení; je nutné implementovat ho sami pomocí volání rozhraní DAO přímo nebo pomocí aplikace Microsoft Access. Naleznete v tématu "Oprávnění vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef  
 Vytvoří **CDaoQueryDef** objektu.  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Ukazatel na otevřenou [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Objekt může představovat existující querydef uložení do databáze querydefs – kolekce, nový dotaz se neukládají v kolekci nebo dočasné dotaz, tak, aby se neukládaly. Dalším krokem, závisí na typu querydef:  
  
-   Pokud objekt představuje existující querydef, volání objektu [otevřete](#open) – členská funkce k chybě při inicializaci ho.  
  
-   Pokud objekt představuje nový querydef uložit, volání objektu [vytvořit](#create) – členská funkce. Tento postup přidá objekt do databáze querydefs – kolekce. Potom zavolejte `CDaoQueryDef` členské funkce nastavit atributy objektu. Nakonec volání [připojení](#append).  
  
-   Pokud objekt představuje dočasné querydef (nesmí být uloženy v databázi), volání **vytvořit**, předávání prázdný řetězec pro název dotazu. Po volání **vytvořit**, inicializovat querydef přímo nastavením jeho atributy. Nevolejte **připojení**.  
  
 Pokud chcete nastavit atributy querydef, můžete použít [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)a [SetReturnsRecords](#setreturnsrecords) členské funkce.  
  
 Po dokončení s objektem querydef volat jeho [Zavřít](#close) – členská funkce. Pokud máte ukazatel querydef, použijte **odstranit** operátor zničit objekt C++.  
  
##  <a name="close"></a>  CDaoQueryDef::Close  
 Po dokončení práce objektu querydef, volání této funkce člen.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Zavření querydef uvolní základní objekt DAO ale nezničí uložené querydef objekt DAO nebo C++ `CDaoQueryDef` objektu. Toto není stejný jako [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), což querydef odstraní z databáze querydefs – kolekce v rozhraní DAO (Pokud není dočasný querydef).  
  
##  <a name="create"></a>  CDaoQueryDef::Create  
 Volání této funkce člen k vytvoření nové uložený dotaz nebo nové dočasné dotazu.  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Jedinečný název dotazu, které jsou uloženy v databázi. Podrobnosti o řetězce naleznete v tématu "CreateQueryDef způsob" v nápovědě rozhraní DAO. Pokud přijměte výchozí hodnotu, prázdný řetězec, vytvoří se dočasné querydef. Takový dotaz není uložen v querydefs – kolekce.  
  
 `lpszSQL`  
 Řetězec SQL, který definuje dotaz. Pokud přijmete výchozí hodnotu **NULL**, musí volat později [SetSQL](#setsql) nastavit řetězec. Do té doby se dotaz není definován. Ale můžete nedefinované dotaz otevřít sadu záznamů; Podrobnosti najdete v části poznámky. Příkaz jazyka SQL musí být definován, než querydef můžete připojit k querydefs – kolekce.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte název v `lpszName`, potom můžete volat [připojení](#append) uložení querydef do databáze querydefs – kolekce. Objekt, jinak je dočasný querydef a neukládají. V obou případech querydef je v otevřeném stavu, a můžete použít buď ji k vytvoření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu nebo volejte querydef [Execute](#execute) – členská funkce.  
  
 Pokud nezadáte příkazu SQL v `lpszSQL`, nelze spustit dotaz s **Execute** ale můžete ji použít k vytvoření sady záznamů. V takovém případě MFC používá příkaz SQL výchozí sady záznamů.  
  
##  <a name="execute"></a>  CDaoQueryDef::Execute  
 Volání této funkce člen ke spuštění dotazu objektu querydef definované.  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parametry  
 `nOptions`  
 Celé číslo, které určuje charakteristiky dotazu. Související informace naleznete v tématu "Spustit metodu" v nápovědě rozhraní DAO. Můžete použít operátor bitové operace OR ( **&#124;**) kombinovat následující konstanty pro tento argument:  
  
- **dbDenyWrite** odepřít oprávnění k zápisu do jiných uživatelů.  
  
- **dbInconsistent** nekonzistentní aktualizace.  
  
- **dbConsistent** konzistentní aktualizace.  
  
- **dbSQLPassThrough** průchozí SQL. Způsobí, že příkaz jazyka SQL, které mají být předány databáze ODBC pro zpracování.  
  
- **dbFailOnError** výchozí hodnota. Vrátit zpět aktualizace, pokud dojde k chybě a sestava Chyba uživateli.  
  
- **dbSeeChanges** jiného uživatele je změna dat upravujete generovat chybu spuštění.  
  
> [!NOTE]
>  Vysvětlení podmínky "nekonzistentní" a "konzistentní", naleznete v tématu "Spustit metodu" v nápovědě rozhraní DAO.  
  
### <a name="remarks"></a>Poznámky  
 Objekty QueryDef používané pro provedení tímto způsobem může představovat pouze jeden z následujících typů dotazu:  
  
-   Akce dotazy  
  
-   Předávací dotazy SQL  
  
 **Spuštění** nefunguje pro dotazy, které vracejí záznamy, jako je například vyberte dotazy. **Spuštění** obvykle se používá pro hromadné operace dotazů, jako například **aktualizace**, **vložit**, nebo **SELECT INTO**, nebo pro data definice jazyka DDL operace.  
  
> [!TIP]
>  Upřednostňovaný způsob práce s zdroje dat ODBC se připojit k Microsoft Jet tabulky (. Databáze MDB). Další informace naleznete v tématu "Přístup k externí databáze s DAO" v nápovědě rozhraní DAO.  
  
 Volání [GetRecordsAffected](#getrecordsaffected) členské funkce objektu querydef můžete určit počet záznamů ovlivněný pomocí nejnovější **Execute** volání. Například `GetRecordsAffected` vrací informace o počet záznamů odstraněny, aktualizaci nebo vložení při provádění dotazu. Vrátí počet nebude projeví změny v související tabulky při cascade aktualizací nebo odstraní jsou platné.  
  
 Pokud současně obsahovat **dbInconsistent** a **dbConsistent** nebo pokud zahrnete ani jeden z nich, výsledkem je výchozí, **dbInconsistent**.  
  
 **Spuštění** nevrací sadě záznamů. Pomocí **Execute** v dotazu, který vybere záznamy způsobí, že má být vyvolána výjimka typu MFC [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect  
 Volání této funkce člen získat připojovací řetězec související se zdrojem dat querydef.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující připojovací řetězec pro querydef.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží pouze s zdroje dat ODBC a ovladači určité ISAM. Není-li použít s Microsoft Jet (. Databáze MDB); v takovém případě `GetConnect` vrátí prázdný řetězec. Další informace najdete v tématu [SetConnect](#setconnect).  
  
> [!TIP]
>  Upřednostňovaný způsob práce s tabulek ODBC se mohly připojit. Databáze MDB. Další informace naleznete v tématu "Přístup k externí databáze s DAO" v nápovědě rozhraní DAO.  
  
 Informace o připojovacích řetězcích naleznete v tématu "Připojit vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated  
 Volání této funkce člen získat datum vytvoření objektu querydef.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas querydef byla vytvořena.  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated  
 Volání této funkce člen GET pro objekt querydef datum poslední aktualizace – Pokud některý z jeho vlastnosti byly změněny, například jeho název, jeho řetězec SQL nebo jeho připojovací řetězec.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas poslední aktualizace querydef.  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount  
 Volání této funkce člen načíst počet polí v dotazu.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet polí definovaných v dotazu.  
  
### <a name="remarks"></a>Poznámky  
 `GetFieldCount` je užitečné pro všechna pole v querydef ve smyčce. K tomuto účelu použít `GetFieldCount` ve spojení s [GetFieldInfo](#getfieldinfo).  
  
##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo  
 Volání této funkce člen získat různých typů informací o pole definovaná v querydef.  
  
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
 `nIndex`  
 Index založený na nule požadované pole v kolekci polí querydef, pro vyhledávání podle indexu.  
  
 `fieldinfo`  
 Odkaz na `CDaoFieldInfo` objekt, který vrátí požadované informace.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o pole, které chcete načíst. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, typ, velikost, atributy  
  
- `AFX_DAO_SECONDARY_INFO` Primární informace plus: pořadové číslo pozice, vyžaduje, Povolit nulovou délku, pole zdroje, název cizího, zdrojová tabulka, pořadí řazení  
  
- `AFX_DAO_ALL_INFO` Primární a sekundární informace plus: výchozí hodnotu Text pro ověření, ověřovacího pravidla  
  
 `lpszName`  
 Řetězec obsahující název požadované pole pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Popis vrácené v informace `fieldinfo`, najdete v článku [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura. Tato struktura má členy, které odpovídají popisné informace v části `dwInfoOptions` výše. Jestliže požádáte o jednu úroveň informací, můžete získat žádné předchozí úrovně také informace.  
  
##  <a name="getname"></a>  CDaoQueryDef::GetName  
 Volání této funkce člen načíst název dotazu reprezentována querydef.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název dotazu.  
  
### <a name="remarks"></a>Poznámky  
 Názvy QueryDef jsou jedinečné názvy definovaný uživatelem. Další informace o názvech querydef naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout  
 Volání této funkce člen načíst aktuální časový limit, než vyprší časový limit dotazu na zdroji dat rozhraní ODBC.  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet sekund, než dotazu vyprší časový limit.  
  
### <a name="remarks"></a>Poznámky  
 Informace o této časový limit naleznete v tématu "Odezvy vlastnost" v nápovědě rozhraní DAO.  
  
> [!TIP]
>  Upřednostňovaný způsob práce s tabulkami ODBC je připojte je k Microsoft Jet (. Databáze MDB). Další informace naleznete v tématu "Přístup k externí databáze s DAO" v nápovědě rozhraní DAO.  
  
##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount  
 Volání této funkce člen načíst počet parametrů v uloženého dotazu.  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet parametrů definovaných v dotazu.  
  
### <a name="remarks"></a>Poznámky  
 `GetParameterCount` je užitečné pro všechny parametry v querydef ve smyčce. K tomuto účelu použít `GetParameterCount` ve spojení s [getparameterinfo –](#getparameterinfo).  
  
 Související informace najdete v tématech "Parametr objekt", "Kolekce parametrů" a "parametry deklarace (SQL)" v nápovědě rozhraní DAO.  
  
##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo  
 Volání této funkce člen ke získání informací o parametr definovaný v querydef.  
  
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
 `nIndex`  
 Index založený na nule požadovaného parametru v kolekci parametrů querydef, pro vyhledávání podle indexu.  
  
 `paraminfo`  
 Odkaz na [cdaoparameterinfo –](../../mfc/reference/cdaoparameterinfo-structure.md) objekt, který vrátí požadované informace.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o parametru pro načtení. K dispozici možnost je zde uvedena spolu s co ho způsobuje, že funkce vrátit:  
  
- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, typ  
  
 `lpszName`  
 Řetězec, který obsahuje název požadovaného parametru, pro vyhledávání podle názvu. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Popis vrácené v informace `paraminfo`, najdete v článku [cdaoparameterinfo –](../../mfc/reference/cdaoparameterinfo-structure.md) struktura. Tato struktura má členy, které odpovídají popisné informace v části `dwInfoOptions` výše.  
  
 Související informace naleznete v tématu "parametry deklarace (SQL)" v nápovědě rozhraní DAO.  
  
##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue  
 Volání této funkce člen načíst aktuální hodnota zadaný parametr uložené v kolekci parametrů querydef.  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Název parametru, jehož hodnotu chcete pro vyhledávání podle názvu.  
  
 `nIndex`  
 Index založený na nule parametru v kolekci parametrů querydef, pro vyhledávání podle indexu. Můžete získat tuto hodnotu pomocí volání [GetParameterCount](#getparametercount) a [getparameterinfo –](#getparameterinfo).  
  
### <a name="return-value"></a>Návratová hodnota  
 Třída objektu [COleVariant](../../mfc/reference/colevariant-class.md) obsahující hodnoty parametru.  
  
### <a name="remarks"></a>Poznámky  
 Parametr můžete přistupovat pomocí názvu nebo pomocí jeho pořadové číslo pozice v kolekci.  
  
 Související informace naleznete v tématu "parametry deklarace (SQL)" v nápovědě rozhraní DAO.  
  
##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected  
 Volání této funkce člen k určení, kolik záznamů situace měla vliv na poslední volání [Execute](#execute).  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet záznamů ovlivněný.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí počet nebude projeví změny v související tabulky při cascade aktualizací nebo odstraní jsou platné.  
  
 Související informace naleznete v tématu "RecordsAffected vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords  
 Volání této funkce člen k určení, zda querydef je založena na dotaz, který vrátí záznamy.  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je querydef založené na dotazu, který vrátí záznamy; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen se používá pouze pro průchozí dotazy SQL. Další informace o dotazech SQL najdete v tématu [Execute](#execute) – členská funkce. Další informace o práci s předávací dotazy SQL najdete v tématu [SetReturnsRecords](#setreturnsrecords) – členská funkce.  
  
 Související informace naleznete v tématu "Vlastnost vrací záznamy" v nápovědě rozhraní DAO.  
  
##  <a name="getsql"></a>  CDaoQueryDef::GetSQL  
 Volání této funkce člen načíst příkaz jazyka SQL, který definuje dotaz, na kterých je založena querydef.  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Příkaz jazyka SQL, který definuje dotaz, na kterých je založena querydef.  
  
### <a name="remarks"></a>Poznámky  
 Pak nebude pravděpodobně analyzovat řetězec pro klíčová slova, názvy tabulek a tak dále.  
  
 Související informace najdete v tématech "Vlastnost SQL", "Porovnání z Microsoft Jet databáze stroj SQL a ANSI SQL" a "Dotazování databázi s SQL v kódu" v nápovědě rozhraní DAO.  
  
##  <a name="gettype"></a>  CDaoQueryDef::GetType  
 Volání této funkce člen určit typ dotazu querydef.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ dotazu, které jsou definované querydef. Hodnoty najdete v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Typ dotazu je nastaven podle co zadáte v řetězci querydef SQL při vytváření querydef nebo volání existující querydef [SetSQL](#setsql) – členská funkce. Dotaz typ vrácený pomocí této funkce může být jedna z následujících hodnot:  
  
- **dbQSelect** vyberte  
  
- **dbQAction** akce  
  
- **dbQCrosstab** sestavě křížových tabulek  
  
- **dbQDelete** odstranit  
  
- **dbQUpdate** aktualizace  
  
- **dbQAppend** připojení  
  
- **dbQMakeTable** vytvářecí  
  
- **dbQDDL** definice dat  
  
- **dbQSQLPassThrough** průchozí  
  
- **dbQSetOperation** sjednocení  
  
- **dbQSPTBulk** použít s **dbQSQLPassThrough** zadat dotaz, který nevrací záznamy.  
  
> [!NOTE]
>  Pokud chcete vytvořit předávací dotaz SQL, není nastavený **dbSQLPassThrough** konstantní. Je nastavena automaticky pro databázový stroj Microsoft Jet při vytváření objektu querydef a nastavit připojovací řetězec.  
  
 Informace o řetězce SQL najdete v tématu [GetSQL](#getsql). Informace o typech dotazů najdete v tématu [Execute](#execute).  
  
##  <a name="isopen"></a>  CDaoQueryDef::IsOpen  
 Volání této funkce člen můžete určit, zda `CDaoQueryDef` objektu je aktuálně otevřený.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CDaoQueryDef` objekt je aktuálně otevřených; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Querydef musí být v otevřeném stavu, než ho použijete k volání [Execute](#execute) nebo k vytvoření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu. Převést querydef do volání na otevřeném stavu buď [vytvořit](#create) (pro nové querydef) nebo [otevřete](#open) (pro existující querydef).  
  
##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase  
 Obsahuje odkazy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt přidružený k objektu querydef.  
  
### <a name="remarks"></a>Poznámky  
 Pokud potřebujete získat přímo přístup k databázi, použijte tento ukazatel – například k získání ukazatele na další querydef nebo sada záznamů objekty v kolekcích databáze.  
  
##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef  
 Ukazatel rozhraní OLE pro základní objekt DAO querydef obsahuje.  
  
### <a name="remarks"></a>Poznámky  
 Tento ukazatel je poskytuje pro úplnost a konzistence s jiné třídy. Ale protože MFC místo plně zapouzdří querydefs – DAO, se pravděpodobně ho potřebovat. Pokud používáte, učinit opatrně – konkrétně, neměňte hodnotu ukazatele Pokud si nejste jisti, co dělají.  
  
##  <a name="open"></a>  CDaoQueryDef::Open  
 Volání této funkce člen otevřete querydef, dříve uložené do databáze querydefs – kolekce.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Řetězec, který obsahuje název uloženého querydef otevřete. Můžete použít [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Jakmile querydef je otevřená, můžete volat jeho [Execute](#execute) – členská funkce nebo použijte querydef k vytvoření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu.  
  
##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect  
 Volání této funkce člen nastavit objektu querydef připojovací řetězec.  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszConnect`  
 Řetězec, který obsahuje připojovací řetězec pro přidruženého [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Připojovací řetězec se používá k předávání Další informace k rozhraní ODBC a určité ovladače databází podle potřeby. Pro Microsoft Jet se nepoužívá (. Databáze MDB).  
  
> [!TIP]
>  Upřednostňovaný způsob práce s tabulek ODBC se mohly připojit. Databáze MDB.  
  
 Před provedením querydef, který představuje předávací dotaz SQL pro zdroj dat ODBC, nastavení připojovacího řetězce s `SetConnect` a volání [SetReturnsRecords](#setreturnsrecords) k určení, zda dotaz vrátí záznamy.  
  
 Další informace o struktuře a příklady komponent řetězec připojení připojovací řetězec naleznete v tématu "Připojit vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="setname"></a>  CDaoQueryDef::SetName  
 Volání této funkce člen, pokud chcete změnit název querydef, který není dočasný.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Řetězec, který obsahuje nový název pro nontemporary dotazu v přidruženém [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 QueryDef názvy jsou názvy jedinečný, uživatelem definované. Můžete volat `SetName` před querydef objekt přidán do querydefs – kolekce.  
  
##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout  
 Volání této funkce člen nastavit časový limit, než vyprší časový limit dotazu na zdroji dat rozhraní ODBC.  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>Parametry  
 *nODBCTimeout*  
 Počet sekund, než dotazu vyprší časový limit.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen umožňuje potlačit výchozí počet sekund před dalších operacích na připojených zdrojů dat "časový limit." Operace může vypršení časového limitu z důvodu problémy se síťovým přístupem, doba zpracování nadměrné dotazu a tak dále. Volání `SetODBCTimeout` před spuštěním dotazu s Tento querydef, pokud chcete změnit hodnotu časového limitu dotazu. (Jako ODBC opětovně používá připojení, hodnota časového limitu je stejný pro všechny klienty na stejné připojení.)  
  
 Výchozí hodnota pro vypršení časových limitů dotazu je 60 sekund.  
  
##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue  
 Volání této funkce člen k nastavení hodnoty parametru v querydef za běhu.  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Název parametru, jehož hodnota, kterou chcete nastavit.  
  
 `varValue`  
 Hodnota k nastavení; v části poznámky.  
  
 `nIndex`  
 Pořadové číslo pozice parametr v kolekci Parameters querydef. Můžete získat tuto hodnotu pomocí volání [GetParameterCount](#getparametercount) a [getparameterinfo –](#getparameterinfo).  
  
### <a name="remarks"></a>Poznámky  
 Parametr musí již byly vytvořeny jako součást řetězce querydef SQL. Parametr můžete přistupovat pomocí názvu nebo pomocí jeho pořadové číslo pozice v kolekci.  
  
 Zadejte hodnotu pro nastavení jako `COleVariant` objektu. Informace o nastavení požadovanou hodnotu a pak zadejte vaše `COleVariant` objektů najdete v tématu třídy [COleVariant](../../mfc/reference/colevariant-class.md).  
  
##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords  
 Volání této funkce člen jako součást procesu nastavení předávací dotaz SQL na externí databáze.  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>Parametry  
 *bReturnsRecords*  
 Předat **TRUE** Pokud dotaz na externí databáze vrátí záznamy; jinak **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 V takovém případě musíte vytvořit querydef a nastavit jeho vlastnosti pomocí jiných `CDaoQueryDef` členské funkce. Popis externí databáze najdete v tématu [SetConnect](#setconnect).  
  
##  <a name="setsql"></a>  CDaoQueryDef::SetSQL  
 Volání této funkce člen nastavit příkaz jazyka SQL, které provádí querydef.  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSQL`  
 Řetězec obsahující úplný příkazu jazyka SQL, vhodné pro spuštění. Syntaxe tento řetězec závisí na databázového systému, vaše cíle dotazu. Informace o syntaxi použít v databázovém stroji Microsoft Jet naleznete v tématu "Vytváření příkazů v kódu SQL" v nápovědě rozhraní DAO.  
  
### <a name="remarks"></a>Poznámky  
 Typické použití `SetSQL` je nastavení objektu querydef pro použití v předávací dotaz SQL. (Syntaxe průchozí dotazů SQL na cílovém databázového systému, najdete v dokumentaci k vaší databázového systému.)  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoException – třída](../../mfc/reference/cdaoexception-class.md)
