---
title: CDaoRecordset Class
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 96118645aa656e97fcb93a0fd223045208ab03a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206356"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset Class

Představuje sadu záznamů ze zdroje dat vybrané.

## <a name="syntax"></a>Syntaxe

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|Vytvoří `CDaoRecordset` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoRecordset::AddNew](#addnew)|Připraví pro přidání nového záznamu. Volání [aktualizace](#update) k dokončení přidání.|
|[CDaoRecordset::CanAppend](#canappend)|Vrátí nenulovou hodnotu, pokud nové záznamy může být přidána do sady záznamů prostřednictvím [AddNew](#addnew) členskou funkci.|
|[CDaoRecordset::CanBookmark](#canbookmark)|Vrátí nenulovou hodnotu, pokud sada záznamů podporuje záložky.|
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Zruší všechny čekající aktualizace z důvodu [upravit](#edit) nebo [AddNew](#addnew) operace.|
|[CDaoRecordset::CanRestart](#canrestart)|Vrátí nenulovou hodnotu, pokud [Requery](#requery) může být volána znovu spustit dotaz sadu záznamů.|
|[CDaoRecordset::CanScroll](#canscroll)|Vrátí nenulovou hodnotu, pokud při procházení záznamů.|
|[CDaoRecordset::CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud zdroj dat podporuje transakce.|
|[CDaoRecordset::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud je možné aktualizovat sadu záznamů (můžete přidat, aktualizaci nebo odstranění záznamů).|
|[CDaoRecordset::Close](#close)|Zavře sadu záznamů.|
|[CDaoRecordset::Delete](#delete)|Odstraní aktuální záznam ze sady záznamů. Po odstranění se musí explicitně přechod na jiný záznam.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Volá se pro výměnu dat (v obou směrech) mezi datové členy polí sady záznamů a odpovídající záznam ve zdroji dat. Implementuje rozhraní DAO zaznamenat výměna polí (DFX).|
|[CDaoRecordset::Edit](#edit)|Připraví změn aktuálního záznamu. Volání `Update` dokončete úpravu.|
|[CDaoRecordset::FillCache](#fillcache)|Výplně všechny nebo část místní mezipaměti pro objekt sady záznamů, který obsahuje data ze zdroje dat ODBC.|
|[CDaoRecordset::Find](#find)|Vyhledá první, další, předchozí nebo poslední umístění znamének určitého řetězce v dynamické sady záznamů, který splňuje zadaná kritéria a díky, které zaznamenávají aktuální záznam.|
|[CDaoRecordset::FindFirst](#findfirst)|Vyhledá první záznam v dynamických sad typ nebo typ snímku záznamů, která vyhovuje zadaným kritériím a využívá, které zaznamenávají aktuální záznam.|
|[CDaoRecordset::FindLast](#findlast)|Vyhledá poslední záznam v dynamických sad typ nebo typ snímku záznamů, která vyhovuje zadaným kritériím a využívá, které zaznamenávají aktuální záznam.|
|[CDaoRecordset::FindNext](#findnext)|Vyhledá další záznam v dynamických sad typ nebo typ snímku záznamů, která vyhovuje zadaným kritériím a využívá, které zaznamenávají aktuální záznam.|
|[CDaoRecordset::FindPrev](#findprev)|Vyhledá předchozí záznam v dynamických sad typ nebo typ snímku záznamů, která vyhovuje zadaným kritériím a využívá, které zaznamenávají aktuální záznam.|
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Vrátí číslo záznamu aktuální záznam objekt sady záznamů.|
|[CDaoRecordset::GetBookmark](#getbookmark)|Vrátí hodnotu, která představuje záložku na záznam.|
|[CDaoRecordset::GetCacheSize](#getcachesize)|Vrátí hodnotu, která určuje počet záznamů v dynamické sady záznamů obsahující data do místní mezipaměti ze zdroje dat ODBC.|
|[CDaoRecordset::GetCacheStart](#getcachestart)|Vrátí hodnotu, která určuje záložku první záznam v sadě záznamů ukládat do mezipaměti.|
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Vrátí `CString` nedávno obsahující název indexu použít u indexovaného, typ tabulky `CDaoRecordset`.|
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Vrátí datum a čas v základní tabulce podkladových `CDaoRecordset` objekt byl vytvořen|
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny v návrhu základní tabulka základní `CDaoRecordset` objektu.|
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Vrátí název výchozí zdroj dat.|
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Volá za účelem získání výchozí řetězec SQL k provedení.|
|[CDaoRecordset::GetEditMode](#geteditmode)|Vrátí hodnotu, která označuje stav úpravy pro požadovaný aktuální záznam.|
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v sadě záznamů.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Vrátí určité druhy informací o polích v sadě záznamů.|
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|
|[CDaoRecordset::GetIndexCount](#getindexcount)|Získá počet indexů v základní sadě záznamů tabulky.|
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Vrátí různé druhy informací o index.|
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Slouží k určení nejčastěji přidali nebo aktualizovali nedávno záznamu.|
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Vrátí hodnotu, která určuje typ uzamčení, který je v platnosti při úpravách.|
|[CDaoRecordset::GetName](#getname)|Vrátí `CString` obsahující název sady záznamů.|
|[CDaoRecordset::GetParamValue](#getparamvalue)|Načte aktuální hodnota uložená v základní objekt DAOParameter zadaný parametr.|
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|Vrátí pozici aktuální záznam jako procento z celkového počtu záznamů.|
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Vrátí počet záznamů, které jsou přístupné v objektu sady záznamů.|
|[CDaoRecordset::GetSQL](#getsql)|Získá řetězec SQL použít pro výběr záznamů pro sady záznamů.|
|[CDaoRecordset::GetType](#gettype)|Voláno k určení typu Sada záznamů: typ tabulky, dynamická sada typ nebo typ snímku.|
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Vrátí `CString` obsahující hodnotu, která ověřuje data, jako je zadání do pole.|
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Načte text, který se zobrazí, když ověřovací pravidlo není splněná.|
|[CDaoRecordset::IsBOF](#isbof)|Vrátí nenulovou hodnotu, pokud sada záznamů obsahuje byl umístěn před první záznam. Neexistuje aktuální záznam.|
|[CDaoRecordset::IsDeleted](#isdeleted)|Vrátí nenulovou hodnotu, pokud sada záznamů je umístěn na odstraněný záznam.|
|[CDaoRecordset::IsEOF](#iseof)|Vrátí nenulovou hodnotu, pokud sada záznamů zařadila po posledním záznamu. Neexistuje aktuální záznam.|
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Vrátí nenulovou hodnotu, pokud byl změněn v zadaném poli aktuální záznam.|
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Vrátí nenulovou hodnotu, pokud zadané pole v záznamu o aktuální hodnotu Null (s žádná hodnota).|
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Vrátí nenulovou hodnotu, pokud zadané pole v aktuální záznam lze nastavit na hodnotu Null (s žádná hodnota).|
|[CDaoRecordset::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud [otevřít](#open) se zavolala dříve.|
|[CDaoRecordset::Move](#move)|Nastaví pozici sady záznamů na zadaný počet záznamů z aktuální záznam v obou směrech.|
|[CDaoRecordset::MoveFirst](#movefirst)|Aktuální záznam se umístí na první záznam v sadě záznamů.|
|[CDaoRecordset::MoveLast](#movelast)|Aktuální záznam se umístí na poslední záznam v sadě záznamů.|
|[CDaoRecordset::MoveNext](#movenext)|Aktuální záznam se umístí na další záznam v sadě záznamů.|
|[CDaoRecordset::MovePrev](#moveprev)|Aktuální záznam se umístí na předchozí záznam v sadě záznamů.|
|[CDaoRecordset::Open](#open)|Vytvoří novou sadu záznamů z tabulky, dynamická sada nebo snímku.|
|[CDaoRecordset::Requery](#requery)|Spustí dotaz sady záznamů znovu a aktualizujte vybrané záznamy.|
|[CDaoRecordset::Seek](#seek)|Vyhledá záznam v objektu sady záznamů indexovaný typ tabulky, která vyhovuje zadaným kritériím pro aktuální index a vytvoří, které zaznamenávají aktuální záznam.|
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Nastaví číslo aktuální záznam objekt sady záznamů.|
|[CDaoRecordset::SetBookmark](#setbookmark)|Nastaví pozici sady záznamů na záznam obsahující zadanou záložkou.|
|[CDaoRecordset::SetCacheSize](#setcachesize)|Nastaví hodnotu, která určuje počet záznamů v dynamické sady záznamů obsahující data do místní mezipaměti ze zdroje dat ODBC.|
|[CDaoRecordset::SetCacheStart](#setcachestart)|Nastaví hodnotu, která určuje záložku první záznam v sadě záznamů ukládat do mezipaměti.|
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Volá se, aby nastavit index v sadě záznamů typ tabulky.|
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|V zadaném poli aktuální záznam označuje, jak změnit.|
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuální záznam na hodnotu Null (s žádná hodnota).|
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Nastaví hodnotu pole v sadě záznamů.|
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Nastaví hodnotu pole v sadě záznamů na hodnotu Null. (s žádná hodnota).|
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Nastaví hodnotu, která určuje typ zamykání začíná platit při úpravách.|
|[CDaoRecordset::SetParamValue](#setparamvalue)|Nastaví aktuální hodnota uložená v základní objekt DAOParameter zadaný parametr|
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Nastaví aktuální hodnotu zadaného parametru na hodnotu Null (s žádná hodnota).|
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Nastaví pozici aktuální záznam do umístění odpovídající procento celkový počet záznamů v sadě záznamů.|
|[CDaoRecordset::Update](#update)|Dokončení `AddNew` nebo `Edit` operace uložením nových nebo upravených dat ve zdroji dat.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Obsahuje příznak označující, zda pole jsou automaticky označeny jako změnit.|
|[CDaoRecordset::m_nFields](#m_nfields)|Obsahuje číslo pole datových členů ve třídě sady záznamů a počet sloupců vybraných funkcí sady záznamů ze zdroje dat.|
|[CDaoRecordset::m_nParams](#m_nparams)|Obsahuje číslo parametru datové členy třídy sady záznamů – předaný počet parametrů pomocí dotazu sadu záznamů|
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Ukazatel na základní objekt sady záznamů rozhraní DAO.|
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Nastavit zdrojové databáze pro tento výsledek. Obsahuje ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.|
|[CDaoRecordset::m_strFilter](#m_strfilter)|Obsahuje řetězec použitý k vytvoření SQL **kde** příkazu.|
|[CDaoRecordset::m_strSort](#m_strsort)|Obsahuje řetězec použitý k vytvoření SQL **klauzule ORDER BY** příkazu.|

## <a name="remarks"></a>Poznámky

Označuje jako "sady záznamů" `CDaoRecordset` objekty jsou k dispozici v následujících třech forem:

- Sady záznamů typ tabulky představují základní tabulky, který vám pomůže zkontrolovat, přidat, změnit nebo odstranit záznamy z tabulky izolované databáze.

- Dynamické sady záznamů jsou výsledkem dotazu, který může mít aktualizovatelné záznamy. Tyto sady záznamů jsou sadou záznamů, které můžete zkontrolovat, přidat, změnit nebo odstranit záznamy z podkladové databázové tabulky nebo tabulek. Dynamické sady záznamů můžou obsahovat pole z jednoho nebo více tabulek v databázi.

- Typ snímku sady záznamů jsou statické kopie sady záznamů, které vám umožní najít data nebo generování sestav. Tyto sady záznamů můžou obsahovat pole z jedné nebo více tabulek v databázi, ale nejde aktualizovat.

Každý formulář sada záznamů představuje sadu záznamů stanoveno v době otevření sady záznamů. Při posouvání se záznamem v typ tabulka záznamů nebo typ dynamická sada záznamů odráží změny záznamu po otevření sady záznamů jiných uživatelů nebo jiné sady záznamů ve vaší aplikaci. (Sada záznamů typu snímek se nedá aktualizovat.) Můžete použít `CDaoRecordset` přímo nebo odvozovat třídu specifické pro aplikaci záznamů z `CDaoRecordset`. Pak můžete:

- Projděte si záznamy.

- Nastavit index a rychle najít záznamy pomocí [Seek](#seek) (pouze typ tabulky záznamů).

- Vyhledání záznamů na základě porovnání řetězce: "<","\<=", "=", "> =", nebo ">" (dynamická sada type a sad záznamů typu snímek).

- Aktualizovat záznamy a zadat režim uzamčení (kromě sad záznamů typu snímek).

- Filtrování záznamů záznamy, které vybere z dostupných ve zdroji dat omezit.

- Řazení záznamů.

- Parametrizace sady záznamů s informacemi, které nejsou známé až do běhu přizpůsobit jeho výběr.

Třída `CDaoRecordset` poskytuje podobné třídy rozhraní `CRecordset`. Hlavní rozdíl je v dané třídy `CDaoRecordset` přistupuje k datům prostřednictvím objekt DAO (Data Access) podle OLE. Třída `CRecordset` DBMS přistupuje prostřednictvím připojení ODBC (Open Database) a ovladač ODBC pro tento systém DBMS.

> [!NOTE]
> Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Můžete si pořád přístup ke zdrojům dat ODBC s tříd DAO; třídy DAO obecně nabízejí vynikající možnosti, protože jsou specifické pro databázový stroj Microsoft Jet.

Můžete buď používat `CDaoRecordset` přímo nebo odvodit třídu z `CDaoRecordset`. Použití třídy sady záznamů v obou případech, otevření databáze a vytvořit objekt sady záznamů, předá konstruktoru ukazatel na váš `CDaoDatabase` objektu. Můžete také sestavit `CDaoRecordset` objektu a nechat knihovny MFC vytvořte dočasnou `CDaoDatabase` objekt za vás. Poté zavolejte sady záznamů [otevřít](#open) členská funkce určující, zda je objekt typ tabulky záznamů, typ dynamických sad záznamů nebo typ snímku záznamů. Volání `Open` vybere data z databáze a načte první záznam.

Projděte si záznamy a pracovat s nimi pomocí objektu členské funkce a datovým členům. Dostupné operace závisí na Určuje, zda je objekt typ tabulky záznamů, typ dynamických sad záznamů nebo typ snímku záznamů a zda je možné aktualizovat nebo jen pro čtení – záleží na schopnost databázi nebo připojení ODBC (Open Database) zdroj dat. Chcete-li aktualizovat záznamy, které mohou mít se změnily nebo přibyly od `Open` volání, volání objektu [Requery](#requery) členskou funkci. Volání objektu `Close` členské funkce a zničte objekt, když dokončíte s ním.

`CDaoRecordset` používá výměna polí záznamu DAO (DFX) pro podporu pro čtení a aktualizaci polí záznamů prostřednictvím členy C++ zajišťující bezpečnost typů vašeho `CDaoRecordset` nebo `CDaoRecordset`-odvozené třídy. Můžete také implementovat dynamické vazby sloupců v databázi bez použití pomocí mechanismu DFX [getfieldvalue –](#getfieldvalue) a [SetFieldValue](#setfieldvalue).

Související informace naleznete v tématu "Objekt sady záznamů" v nápovědě rozhraní DAO.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="addnew"></a>  CDaoRecordset::AddNew

Voláním této členské funkce, chcete-li přidat nový záznam do table-type nebo dynamické sady záznamů.

```
virtual void AddNew();
```

### <a name="remarks"></a>Poznámky

Pole záznamu jsou zpočátku hodnotu Null. (V terminologii databáze s hodnotou Null znamená "mít žádná hodnota" a není stejná jako hodnota NULL v jazyce C++.) K dokončení operace, musí volat [aktualizace](#update) členskou funkci. `Update` Uloží změny do zdroje dat.

> [!CAUTION]
>  Pokud chcete záznam upravit a potom přejděte na jiný záznam bez volání `Update`, změny se ztratí bez předchozího upozornění.

Pokud přidáte záznam pro dynamické sady záznamů voláním [AddNew](#addnew), záznam je viditelný v sadě záznamů a zahrnuty v podkladové tabulce, kam bude viditelná pro žádného nové `CDaoRecordset` objekty.

Umístění nového záznamu závisí na typu Sada záznamů:

- V typu dynamických sad záznamů, kde se vloží nový záznam není zaručena. Toto chování změnit Microsoft Jet 3.0 z důvodů výkonu a souběžnosti. Pokud je vaším cílem je, aby nově přidaný záznam aktuální záznam, získejte záložky poslední změny záznamu a přesunout na tuto záložku:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- V sadě záznamů typ tabulky, pro který byl zadán indexu vrátí se záznamy v jejich správné místo v pořadí řazení. Pokud nebyl zadán žádný index, nové záznamy budou vráceny na konci sady záznamů.

Záznam, který byl aktuální před použitím `AddNew` zůstává aktuální. Pokud chcete nastavit jako aktuální nový záznam a sady záznamů podporuje záložky, volání [SetBookmark](#setbookmark) na záložku identifikovaný nastavení vlastnosti LastModified základního objektu sady záznamů rozhraní DAO. To je užitečné pro určující hodnotu pro čítač (automatické zvyšování čísla) pole v přidaný záznam. Další informace najdete v tématu [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Pokud databáze podporuje transakce, můžete vytvořit vaše `AddNew` volání součástí transakce. Další informace o transakcích, naleznete v tématu třídy [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md). Všimněte si, že byste měli volat [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) před voláním `AddNew`.

Je neplatné volat `AddNew` pro sadu záznamů jehož [otevřít](#open) nebyla volána členská funkce. A `CDaoException` je vyvolána, pokud zavoláte `AddNew` pro sadu záznamů, které se nejde připojit. Můžete určit, jestli je sada záznamů aktualizovatelné voláním [CanAppend](#canappend).

Značky framework změnit pole datové členy zajistit, že se budou zapisovat do záznamu ve zdroji dat exchange (DFX) mechanismem DAO pole záznamu. Změna hodnoty pole obecně nastaví pole změny automaticky, tedy zřídka bude nutné zavolat [SetFieldDirty](#setfielddirty) sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to jaká hodnota je v datovém členu pole. DFX mechanismus využívá i použití **PSEUDO NULL**. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud mechanismus dvojité ukládání do vyrovnávací paměti není používáno, pak změníte hodnotu pole nenastaví automaticky pole označeni jako neaktualizovaní. V takovém případě bude nutné explicitně nastavit změny pole. Příznak součástí [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tuto kontrolu automatického pole.

> [!NOTE]
> Pokud jsou záznamy dvojitou vyrovnávací pamětí (to znamená, pole Automatická kontrola je povolena), volání `CancelUpdate` obnoví členské proměnné na hodnoty měli před `AddNew` nebo `Edit` byla volána.

Související informace naleznete v tématech "Metodu AddNew", "CancelUpdate metoda", "LastModified vlastnost" a "EditMode vlastnost" v nápovědě k DAO.

##  <a name="canappend"></a>  CDaoRecordset::CanAppend

Voláním této členské funkce k určení, zda dřív otevřených záznamů slouží k přidání nových záznamů pomocí volání [AddNew](#addnew) členskou funkci.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů umožňuje přidávání nových záznamů; jinak 0. `CanAppend` Vrátí hodnotu 0-li otevřít sadu záznamů jen pro čtení.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Metodu" v nápovědě k DAO.

##  <a name="canbookmark"></a>  CDaoRecordset::CanBookmark

Voláním této členské funkce k určení, zda dřív otevřených záznamů umožňuje jednotlivě označit záznamů pomocí záložky.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů podporuje záložky, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud používáte sady záznamů zcela podle tabulky stroj Microsoft Jet databáze, lze použít záložky s výjimkou v sadách záznamů typ snímku označení pouze posouvací vpřed. Další produkty databáze (externí zdroje dat rozhraní ODBC) nemusí podporovat záložky.

Související informace naleznete v tématu "Bookmarkable vlastnost" v nápovědě k DAO.

##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate

`CancelUpdate` Členská funkce zruší případné čekající aktualizace z důvodu [upravit](#edit) nebo [AddNew](#addnew) operace.

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Poznámky

Například, pokud aplikace zavolá `Edit` nebo `AddNew` členské funkce a nebyla zavolána [aktualizace](#update), `CancelUpdate` zruší všechny změny provedené po `Edit` nebo `AddNew` byla volána.

> [!NOTE]
>  Pokud jsou záznamy dvojitou vyrovnávací pamětí (to znamená, pole Automatická kontrola je povolena), volání `CancelUpdate` obnoví členské proměnné na hodnoty měli před `AddNew` nebo `Edit` byla volána.

Pokud není žádný `Edit` nebo `AddNew` probíhá, operace `CancelUpdate` způsobí, že knihovny MFC k vyvolání výjimky. Volání [GetEditMode](#geteditmode) členské funkce k určení, zda je čekající operace, která se dá zrušit.

Související informace naleznete v tématu "CancelUpdate metodu" v nápovědě k DAO.

##  <a name="canrestart"></a>  CDaoRecordset::CanRestart

Voláním této členské funkce k určení, zda sada záznamů umožňuje restartovat dotaz (Chcete-li aktualizovat své záznamy) voláním `Requery` členskou funkci.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `Requery` lze volat pro sady záznamů dotaz spustit znovu, jinak 0.

### <a name="remarks"></a>Poznámky

Sady záznamů typ tabulky nepodporují `Requery`.

Pokud `Requery` není podporován, volání [Zavřít](#close) pak [otevřít](#open) aktualizovat data. Můžete volat `Requery` aktualizovat objekt sady záznamů podkladového parametrický dotaz po byly změněny hodnoty parametrů.

Související informace naleznete v tématu "Restartovatelnou službu vlastnost" v nápovědě k DAO.

##  <a name="canscroll"></a>  CDaoRecordset::CanScroll

Voláním této členské funkce k určení, zda sada záznamů umožňuje posouvání.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud při procházení záznamů, jinak 0.

### <a name="remarks"></a>Poznámky

Při volání [otevřít](#open) s `dbForwardOnly`, sadu záznamů můžete posouvat pouze vpřed.

Související informace naleznete v tématu "Umístění aktuální záznam ukazatele pomocí rozhraní DAO" v nápovědě rozhraní DAO.

##  <a name="cantransact"></a>  CDaoRecordset::CanTransact

Voláním této členské funkce k určení, zda sada záznamů umožňuje transakce.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud podkladový zdroj dat podporuje transakce, jinak 0.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Transakce vlastnost" v nápovědě k DAO.

##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate

Voláním této členské funkce k určení, zda je možné aktualizovat sady záznamů.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je možné aktualizovat sadu záznamů (přidání, aktualizace a odstranění záznamů), jinak 0.

### <a name="remarks"></a>Poznámky

Sada záznamů může být jen pro čtení, pokud podkladový zdroj dat je jen pro čtení, nebo pokud jste zadali `dbReadOnly` pro *nOptions* když jste volali [otevřít](#open) sady záznamů.

Související informace naleznete v tématech "Metodu AddNew", "Upravit metodu", "Metodu Delete", "Metodu aktualizace" a "Aktualizovat vlastnost" v nápovědě k DAO.

##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset

Vytvoří `CDaoRecordset` objektu.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Obsahuje ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt nebo hodnotu NULL. Pokud není NULL a `CDaoDatabase` objektu `Open` členská funkce se nevolala pro připojení ke zdroji dat, sada záznamů se pokusí otevřít ho za vás během své vlastní [otevřete](#open) volání. Pokud předáte hodnotu NULL, `CDaoDatabase` objekt je vytvořen a připojené pomocí informace o zdroji dat jste zadali, pokud je odvozená vaší třídy sady záznamů z `CDaoRecordset`.

### <a name="remarks"></a>Poznámky

Můžete buď používat `CDaoRecordset` přímo nebo odvozovat třídu specifické pro aplikaci z `CDaoRecordset`. ClassWizard můžete použít k odvození třídy sady záznamů.

> [!NOTE]
>  Pokud odvozujete `CDaoRecordset` třídy vaší odvozené třídy musí zadat vlastní konstruktor. V konstruktoru odvozené třídy volání konstruktoru `CDaoRecordset::CDaoRecordset`, předáním příslušné parametry společně.

Předat hodnotu NULL do konstruktoru sady záznamů mít `CDaoDatabase` objekt vytvořen a připojení automaticky za vás. To je užitečné zástupce, který není nutné vytvořit a připojit `CDaoDatabase` objektu před sestavením sady záznamů. Pokud `CDaoDatabase` objektu není otevřený, [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md) objekt se vytvoří taky, který používá výchozí pracovní prostor. Další informace najdete v tématu [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

##  <a name="close"></a>  CDaoRecordset::Close

Zavření `CDaoRecordset` odebere objekt z kolekce otevřené sady záznamů do příslušné databáze.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Protože `Close` nezničí `CDaoRecordset` objektu, můžete znovu použít objekt voláním `Open` na stejný zdroj dat nebo jinému zdroji dat.

Všechna nevyřízená [AddNew](#addnew) nebo [upravit](#edit) zrušení příkazů a všechny čekající transakce jsou vrácena zpět. Pokud chcete zachovat probíhající dodatky nebo změny, zavolejte [aktualizace](#update) před voláním `Close` pro každou sadu záznamů.

Můžete volat `Open` znovu po volání `Close`. Díky tomu můžete znovu použít objekt sady záznamů. Lepší alternativou je volání [Requery](#requery), pokud je to možné.

Související informace naleznete v tématu "Metoda Close" v nápovědě k DAO.

##  <a name="delete"></a>  CDaoRecordset::Delete

Voláním této členské funkce, chcete-li odstranit aktuální záznam v otevřený objekt sady záznamů dynamická sada typ nebo typ tabulky.

```
virtual void Delete();
```

### <a name="remarks"></a>Poznámky

Po úspěšném odstranění sady záznamů pole datových členů jsou nastaveny na hodnotu Null a musí explicitně voláním členské funkce navigace sady záznamů ( [přesunout](#move), [Seek](#seek), [ SetBookmark](#setbookmark), a tak dále) aby bylo možné přesunout mimo odstraněný záznam. Při odstraňování záznamů ze sady záznamů, musí být aktuální záznam v sadě záznamů před voláním `Delete`; v opačném případě vyvolá výjimku, knihovny MFC.

`Delete` Odstraní aktuální záznam a zpřístupňuje je nedostupný. I když se nedají upravit ani použít odstraněným záznamem, zůstane aktuální. Jakmile přesunete na jiný záznam, však nelze provádět odstraněným záznamem aktuální znovu.

> [!CAUTION]
>  Sada záznamů třeba umožnit aktualizaci modelové a musí být platný záznam v sadě záznamů při volání `Delete`. Například pokud odstranit záznam, ale ne přejděte na nový záznam, před voláním `Delete` znovu `Delete` vyvolá [cdaoexception –](../../mfc/reference/cdaoexception-class.md).

Záznam můžete obnovit, pokud používáte transakce a volání [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) členskou funkci. Pokud základní tabulka je v primární tabulce v kaskádové odstranění relace, odstranění aktuální záznam může také odstranit jeden nebo více záznamů v tabulce cizího. Další informace najdete v tématu v definici "kaskádové odstranění" v nápovědě k DAO.

Na rozdíl od `AddNew` a `Edit`, volání `Delete` nenásleduje volání `Update`.

Související informace naleznete v tématech "Metodu AddNew", "Upravit metodu", "Metodu Delete", "Metodu aktualizace" a "Aktualizovat vlastnost" v nápovědě k DAO.

##  <a name="dofieldexchange"></a>  CDaoRecordset::DoFieldExchange

Tato členská funkce pro automaticky výměnu dat mezi datové členy polí objektu sady záznamů a odpovídající sloupce aktuální záznam ve zdroji dat. volá framework.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Obsahuje ukazatel `CDaoFieldExchange` objektu. Rozhraní se už nastavili tento objekt k určení kontextu pro operaci exchange pole.

### <a name="remarks"></a>Poznámky

Také vytvoří vazbu mezi parametry datových členů, pokud chcete parametr zástupné texty v řetězci příkaz SQL pro výběr sady záznamů. Výměna dat pole, kterým se říká výměna polí záznamu DAO (DFX), funguje v obou směrech: z objektu sady záznamů datoví členové pole na pole záznamu ve zdroji dat a z tohoto záznamu ve zdroji dat do objektu sady záznamů. Pokud jsou dynamické vazby sloupců, není nutné implementovat `DoFieldExchange`.

Pouze akce je obvykle třeba provést při implementaci `DoFieldExchange` pro sady záznamů odvozené třídy je vytvořte třídu s ClassWizard a zadejte názvy a datové typy pole datových členů. Je také přidat kód do ClassWizard zapisuje zadat parametry datových členů. Pokud všechna pole jsou dynamicky potvrzujete, tato funkce bude neaktivní, pokud nezadáte parametry datových členů.

Při deklaraci vaší třídy odvozené sady záznamů s ClassWizard Průvodce provádí zápis přepsání `DoFieldExchange` , který vypadá podobně jako v následujícím příkladu:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>  CDaoRecordset::Edit

Voláním této členské funkce k povolení změn na aktuální záznam.

```
virtual void Edit();
```

### <a name="remarks"></a>Poznámky

Po volání `Edit` členskou funkci, změny provedené na aktuální záznam pole se zkopírují do vyrovnávací paměti kopírování. Po provedení požadované změny k záznamu volání `Update` uložte provedené změny. `Edit` uloží hodnoty datových členů sady záznamů. Při volání `Edit`, provést změny, potom zavolejte `Edit` znovu, budou obnoveny hodnoty záznamu tak byly před první `Edit` volání.

> [!CAUTION]
>  Pokud chcete záznam upravit a pak provést jakékoli operaci, která se přesune na jiný záznam bez první volání `Update`, změny se ztratí bez předchozího upozornění. Kromě toho pokud zavřete databáze nadřazeného nebo sady záznamů, se zahodí upravený záznam bez předchozího upozornění.

V některých případech můžete aktualizovat sloupec tak, že ji s hodnotou Null (obsahující žádná data). Chcete-li tak učinit, zavolejte `SetFieldNull` s parametrem hodnoty true označíte pole hodnotu Null; to taky způsobí, že sloupec, který se aktualizovat. Pokud chcete pole, které chcete zapsat do zdroje dat i v případě, že nedošlo ke změně jeho hodnoty, volejte `SetFieldDirty` s parametrem hodnotu TRUE. Tento postup funguje i v případě, že pole má hodnotu Null.

Značky framework změnit pole datové členy zajistit, že se budou zapisovat do záznamu ve zdroji dat exchange (DFX) mechanismem DAO pole záznamu. Změna hodnoty pole obecně nastaví pole změny automaticky, tedy zřídka bude nutné zavolat [SetFieldDirty](#setfielddirty) sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to jaká hodnota je v datovém členu pole. DFX mechanismus využívá i použití **PSEUDO NULL**. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud mechanismus dvojité ukládání do vyrovnávací paměti není používáno, pak změníte hodnotu pole nenastaví automaticky pole označeni jako neaktualizovaní. V takovém případě bude nutné explicitně nastavit změny pole. Příznak součástí [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tuto kontrolu automatického pole.

Pokud objekt sady záznamů je uzamčené pessimistically v prostředí, zůstane uzamčen od okamžiku záznamu `Edit` slouží, až do dokončení aktualizace. Pokud sada záznamů optimisticky je uzamčen, záznam je uzamčen a ve srovnání s předem upravený záznam těsně před plánovaným je aktualizována v databázi. Pokud záznam byl změněn, protože jste volali `Edit`, `Update` vyvolá výjimku, operace se nezdaří a knihovny MFC. Můžete změnit režim uzamčení s `SetLockingMode`.

> [!NOTE]
>  Se používá optimistické uzamykání vždy o formátech externí databáze, jako je například rozhraní ODBC a jazyku Instalovatelné ISAM.

Aktuální záznam zůstává aktuálním po zavolání `Edit`. Chcete-li volat `Edit`, musí být aktuální záznam. Pokud neexistuje aktuální záznam nebo pokud sada záznamů neodkazuje na otevřený typ tabulky nebo objektu dynamické sady záznamů, dojde k výjimce. Volání `Edit` způsobí, že `CDaoException` vyvolání za následujících podmínek:

- Neexistuje aktuální záznam.

- Databáze nebo sada záznamů je jen pro čtení.

- Žádná pole v záznamu je možné aktualizovat.

- Databáze nebo sada záznamů byla otevřena pro výhradní použití jiným uživatelem.

- Stránka obsahující váš záznam uzamknul jiný uživatel.

Pokud je zdroj dat podporuje transakce, lze provádět `Edit` volání součástí transakce. Všimněte si, že byste měli volat `CDaoWorkspace::BeginTrans` před voláním `Edit` a po otevření sady záznamů. Všimněte si také, že volání `CDaoWorkspace::CommitTrans` není náhradou za volání `Update` Dokončit `Edit` operace. Další informace o transakcích, naleznete v tématu třídy `CDaoWorkspace`.

Související informace naleznete v tématech "Metodu AddNew", "Upravit metodu", "Metodu Delete", "Metodu aktualizace" a "Aktualizovat vlastnost" v nápovědě k DAO.

##  <a name="fillcache"></a>  CDaoRecordset::FillCache

Voláním této členské funkce pro ukládání do mezipaměti zadaný počet záznamů ze sady záznamů.

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parametry

*pSize*<br/>
Určuje počet řádků, tak, aby vyplnil v mezipaměti. Pokud tento parametr vynecháte, je hodnota určena nastavením vlastnosti CacheSize základního objektu rozhraní DAO.

*pBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) zadání záložku. Mezipaměť se naplní od záznam indikován tuto záložku. Pokud tento parametr vynecháte, mezipaměť naplní od záznam indikován vlastnost CacheStart základní objekt rozhraní DAO.

### <a name="remarks"></a>Poznámky

Ukládání do mezipaměti zvyšuje výkon aplikace, která získá nebo načte data ze vzdáleného serveru. Mezipaměť je místo v místní paměti, která obsahuje data, jako poslední načtený ze serveru na předpokladu, že data se pravděpodobně o ni požádat znovu když je spuštěná aplikace. Pokud se požaduje data, databázový stroj Microsoft Jet mezipaměti dat nejprve zkontroluje místo načítání ze serveru, který trvá déle. Pomocí dat, ukládání do mezipaměti na zdroje dat – rozhraní ODBC nemá žádný vliv data není ukládána v mezipaměti.

Nečekejte pro ukládání do mezipaměti pro vyplnění se záznamy, jako jsou načteny, můžete explicitně přejít k vyplnění mezipaměti kdykoli po zavolání `FillCache` členskou funkci. Toto je rychlejší způsob, jak mezipaměť zaplní, protože `FillCache` načte několik záznamů současně namísto postupně po jednom. Například při každé screenful záznamů, které se zobrazí, můžete mít vaše aplikace volání `FillCache` načíst další screenful záznamy.

Všechny databáze ODBC k němu přistupovat pomocí objektů sady záznamů může mít místní mezipaměti. Pokud chcete vytvořit mezipaměť, otevřete objekt sady záznamů ze vzdáleného zdroje dat a poté zavolejte `SetCacheSize` a `SetCacheStart` členské funkce sady záznamů. Pokud *lSize* a *lBookmark* vytvoření rozsah, který je mimo rozsah určený částečně nebo zcela `SetCacheSize` a `SetCacheStart`, část záznamů mimo tento rozsah je ignorována a není načíst do mezipaměti. Pokud `FillCache` žádosti více záznamů, než zůstanou v vzdálený zdroj dat, načtení jenom zbývající záznamů a není vyvolána žádná výjimka.

Záznamy načtené z mezipaměti neodrážejí změny provedené současně na zdroj dat jinými uživateli.

`FillCache` načte jenom záznamy, které ještě není v mezipaměti. Chcete-li vynutit aktualizaci všech dat uložených v mezipaměti, zavolejte `SetCacheSize` členskou funkci s *lSize* parametr rovná 0, volání `SetCacheSize` znovu s *lSize* parametr roven velikosti mezipaměti původně požadovali a poté zavolejte `FillCache`.

Související informace naleznete v tématu "FillCache metodu" v nápovědě k DAO.

##  <a name="find"></a>  CDaoRecordset::Find

Voláním této členské funkce k vyhledání konkrétního řetězce v sadě záznamů typu dynamická sada nebo snímek pomocí operátoru porovnání.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lFindType*<br/>
Hodnota určující typ požadovaného operace Find. Možné hodnoty jsou:

- AFX_DAO_NEXT najít další umístění pro odpovídající řetězce.

- AFX_DAO_PREV najdete předchozí umístění odpovídající řetězec.

- AFX_DAO_FIRST najít první umístění odpovídající řetězec.

- AFX_DAO_LAST najít odpovídající řetězec poslední umístění.

*lpszFilter*<br/>
Výraz řetězce (stejně jako **kde** klauzule v příkazu SQL bez slovo **kde**) používaná k nalezení záznam. Příklad:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud najde odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Můžete najít první, další, předchozí nebo poslední instance řetězce. `Find` je virtuální funkce, takže můžete přepsat a přidat vlastní implementaci. `FindFirst`, `FindLast`, `FindNext`, A `FindPrev` členské funkce volání `Find` členskou funkci, abyste mohli používat `Find` můžete řídit chování všechny operace Find.

Chcete-li vyhledat záznam do sady záznamů, typ tabulky, zavolejte [Seek](#seek) členskou funkci.

> [!TIP]
>  Čím menší sadu záznamů, budete mít, zefektivnit `Find` bude. Obecně platí a zejména s dat ODBC je lepší vytvořit nový dotaz, který načte záznamy, které chcete.

Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě k DAO.

##  <a name="findfirst"></a>  CDaoRecordset::FindFirst

Voláním této členské funkce k vyhledání prvního záznamu, který odpovídá zadané podmínky.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Výraz řetězce (stejně jako **kde** klauzule v příkazu SQL bez slovo **kde**) používaná k nalezení záznam.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud najde odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

`FindFirst` Členskou funkci začíná hledání od začátku této sady záznamů a hledání na konec objektu sady záznamů.

Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky) pomocí jedné z operací přesunu přesunout ze záznamu. Chcete-li vyhledat záznam do sady záznamů, typ tabulky, zavolejte `Seek` členskou funkci.

Pokud záznam odpovídající kritériím, která se nenacházejí, aktuální ukazatel záznamu neurčená, a `FindFirst` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje daná kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá následující výskyt a tak dále.

> [!CAUTION]
>  Při úpravě aktuální záznam, nezapomeňte si uložit změny voláním `Update` členskou funkci před přesunutím na jiný záznam. Pokud přesunete na jiný záznam bez aktualizace, změny se ztratí bez předchozího upozornění.

`Find` Členské funkce vyhledávání z umístění a ve směru uvedená v následující tabulce:

|Operace hledání|začít|Směr hledání|
|---------------------|-----------|----------------------|
|`FindFirst`|Začátek sady záznamů|Konec sady záznamů|
|`FindLast`|Konec sady záznamů|Začátek sady záznamů|
|`FindNext`|Aktuální záznam|Konec sady záznamů|
|`FindPrevious`|Aktuální záznam|Začátek sady záznamů|

> [!NOTE]
>  Při volání `FindLast`, databázový stroj Microsoft Jet plně naplní sady záznamů před zahájením vyhledávání, pokud to ještě neudělali. První vyhledávání může trvat déle než následné hledání.

Pomocí jedné z operací hledání není stejný jako volání funkce `MoveFirst` nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete postupovat podle operace hledání se operace přesunu.

Mějte následující při použití operace hledání:

- Pokud `Find` vrátí nenulovou hodnotu, není definován aktuální záznam. V takovém případě je třeba umístit ukazatel aktuální záznam zpět na platný záznam.

- Operace hledání nelze použít s posouváním pouze posouvání typ snímku záznamů.

- Používejte formát USA data (rok měsíc den) při hledání polí, které obsahují data, i pokud nepoužíváte verzi US databázový stroj Microsoft Jet; v opačném případě odpovídající záznamy nemusejí být nalezeny.

- Při práci s databázemi ODBC a dynamické velké sady, můžete zjistit, že pomocí operace Find je pomalé, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrické dotazy nebo `CDaoQuerydef` objekty, které načítají konkrétních indexované záznamů.

Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě k DAO.

##  <a name="findlast"></a>  CDaoRecordset::FindLast

Voláním této členské funkce k vyhledání poslední záznam, který odpovídá zadané podmínky.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Výraz řetězce (stejně jako **kde** klauzule v příkazu SQL bez slovo **kde**) používaná k nalezení záznam.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud najde odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

`FindLast` Členskou funkci začíná hledání na konci sady záznamů a hledání zpětně spíš na začátku sady záznamů.

Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky) pomocí jedné z operací přesunu přesunout ze záznamu. Chcete-li vyhledat záznam do sady záznamů, typ tabulky, zavolejte `Seek` členskou funkci.

Pokud záznam odpovídající kritériím, která se nenacházejí, aktuální ukazatel záznamu neurčená, a `FindLast` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje daná kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá následující výskyt po první výskyt a tak dále.

> [!CAUTION]
>  Pokud aktuální záznam upravte, je nutné uložit změny voláním `Update` členskou funkci před přesunutím na jiný záznam. Pokud přesunete na jiný záznam bez aktualizace, změny se ztratí bez předchozího upozornění.

Pomocí jedné z operací hledání není stejný jako volání funkce `MoveFirst` nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete postupovat podle operace hledání se operace přesunu.

Mějte následující při použití operace hledání:

- Pokud `Find` vrátí nenulovou hodnotu, není definován aktuální záznam. V takovém případě je třeba umístit ukazatel aktuální záznam zpět na platný záznam.

- Operace hledání nelze použít s posouváním pouze posouvání typ snímku záznamů.

- Používejte formát USA data (rok měsíc den) při hledání polí, které obsahují data, i pokud nepoužíváte verzi US databázový stroj Microsoft Jet; v opačném případě odpovídající záznamy nemusejí být nalezeny.

- Při práci s databázemi ODBC a dynamické velké sady, můžete zjistit, že pomocí operace Find je pomalé, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrické dotazy nebo `CDaoQuerydef` objekty, které načítají konkrétních indexované záznamů.

Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě k DAO.

##  <a name="findnext"></a>  CDaoRecordset::FindNext

Voláním této členské funkce k vyhledání další záznam, který odpovídá zadané podmínky.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Výraz řetězce (stejně jako **kde** klauzule v příkazu SQL bez slovo **kde**) používaná k nalezení záznam.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud najde odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

`FindNext` Členskou funkci začíná hledání na aktuální záznam a vyhledá na konec objektu sady záznamů.

Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky) pomocí jedné z operací přesunu přesunout ze záznamu. Chcete-li vyhledat záznam do sady záznamů, typ tabulky, zavolejte `Seek` členskou funkci.

Pokud záznam odpovídající kritériím, která se nenacházejí, aktuální ukazatel záznamu neurčená, a `FindNext` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje daná kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá následující výskyt a tak dále.

> [!CAUTION]
>  Pokud aktuální záznam upravte, je nutné uložit změny voláním `Update` členskou funkci před přesunutím na jiný záznam. Pokud přesunete na jiný záznam bez aktualizace, změny se ztratí bez předchozího upozornění.

Pomocí jedné z operací hledání není stejný jako volání funkce `MoveFirst` nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete postupovat podle operace hledání se operace přesunu.

Mějte následující při použití operace hledání:

- Pokud `Find` vrátí nenulovou hodnotu, není definován aktuální záznam. V takovém případě je třeba umístit ukazatel aktuální záznam zpět na platný záznam.

- Operace hledání nelze použít s posouváním pouze posouvání typ snímku záznamů.

- Používejte formát USA data (rok měsíc den) při hledání polí, které obsahují data, i pokud nepoužíváte verzi US databázový stroj Microsoft Jet; v opačném případě odpovídající záznamy nemusejí být nalezeny.

- Při práci s databázemi ODBC a dynamické velké sady, můžete zjistit, že pomocí operace Find je pomalé, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrické dotazy nebo `CDaoQuerydef` objekty, které načítají konkrétních indexované záznamů.

Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě k DAO.

##  <a name="findprev"></a>  CDaoRecordset::FindPrev

Voláním této členské funkce Najít předchozí záznam, který odpovídá zadané podmínky.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Výraz řetězce (stejně jako **kde** klauzule v příkazu SQL bez slovo **kde**) používaná k nalezení záznam.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud najde odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

`FindPrev` Členskou funkci začíná hledání na aktuální záznam a hledá zpětně spíš na začátku sady záznamů.

Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky) pomocí jedné z operací přesunu přesunout ze záznamu. Chcete-li vyhledat záznam do sady záznamů, typ tabulky, zavolejte `Seek` členskou funkci.

Pokud záznam odpovídající kritériím, která se nenacházejí, aktuální ukazatel záznamu neurčená, a `FindPrev` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje daná kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá následující výskyt a tak dále.

> [!CAUTION]
>  Pokud aktuální záznam upravte, je nutné uložit změny voláním `Update` členskou funkci před přesunutím na jiný záznam. Pokud přesunete na jiný záznam bez aktualizace, změny se ztratí bez předchozího upozornění.

Pomocí jedné z operací hledání není stejný jako volání funkce `MoveFirst` nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete postupovat podle operace hledání se operace přesunu.

Mějte následující při použití operace hledání:

- Pokud `Find` vrátí nenulovou hodnotu, není definován aktuální záznam. V takovém případě je třeba umístit ukazatel aktuální záznam zpět na platný záznam.

- Operace hledání nelze použít s posouváním pouze posouvání typ snímku záznamů.

- Používejte formát USA data (rok měsíc den) při hledání polí, které obsahují data, i pokud nepoužíváte verzi US databázový stroj Microsoft Jet; v opačném případě odpovídající záznamy nemusejí být nalezeny.

- Při práci s databázemi ODBC a dynamické velké sady, můžete zjistit, že pomocí operace Find je pomalé, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrické dotazy nebo `CDaoQuerydef` objekty, které načítají konkrétních indexované záznamů.

Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě k DAO.

##  <a name="getabsoluteposition"></a>  CDaoRecordset::GetAbsolutePosition

Vrátí číslo záznamu aktuální záznam objekt sady záznamů.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo od 0 do počet záznamů v sadě záznamů. Odpovídá pořadí aktuální záznam v sadě záznamů.

### <a name="remarks"></a>Poznámky

Je založený na nule; hodnota vlastnosti AbsolutePosition základního objektu rozhraní DAO nastavení 0 znamená první záznam v sadě záznamů. Můžete určit počet naplněných záznamy v sadě záznamů voláním [getrecordcount –](#getrecordcount). Volání `GetRecordCount` může nějakou dobu trvat, vzhledem k tomu, že potřebuje přístup k všechny záznamy k určení počtu.

Pokud neexistuje aktuální záznam, jako když neexistují žádné záznamy v sadě záznamů – vrátí hodnotu 1. Pokud je aktuální záznam odstranit, není definována hodnota vlastnosti AbsolutePosition a MFC vyvolá výjimku, pokud se na ni odkazuje. Pro dynamické sady záznamů se přidají nové záznamy na konci sekvence.

> [!NOTE]
>  Tato vlastnost není určena pro použití jako číslo náhradní záznam. Záložky jsou stále doporučený způsob uchování a vrácení k dané pozici a jediný způsob, jak umístit aktuální záznam napříč všemi typy objektů sady záznamů. Konkrétně se změny pozice daného záznamu při odstranění záznamů před. K dispozici je také žádnou záruku, že daný záznam budou mít stejné absolutní pozici, pokud sada záznamů se znovu vytvoří znovu vzhledem k tomu, že pokud není vytvořené pomocí příkazu SQL není zaručeno, že pořadí jednotlivých záznamů v rámci sady záznamů  **Řadit podle** klauzuli.

> [!NOTE]
>  Tato členská funkce je platná pouze pro dynamické sady a sady záznamů typ snímku.

Související informace naleznete v tématu "AbsolutePosition vlastnost" v nápovědě k DAO.

##  <a name="getbookmark"></a>  CDaoRecordset::GetBookmark

Voláním této členské funkce k získání hodnoty záložku v určitém záznamu.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu představující záložku na aktuální záznam.

### <a name="remarks"></a>Poznámky

Při vytvoření nebo otevření objekt sady záznamů jednotlivých záznamů jeho jedinečné záložku už má, pokud je podporuje. Volání `CanBookmark` k určení, zda sada záznamů podporuje záložky.

Můžete uložit záložku pro požadovaný aktuální záznam přiřazením hodnoty Záložka `COleVariant` objektu. Chcete-li snadno vrátit na daném záznamu kdykoli po přechod na jiný záznam, zavolejte `SetBookmark` s parametrem odpovídající hodnotě, která `COleVariant` objektu.

> [!NOTE]
>  Volání [Requery](#requery) změní DAO záložky.

Související informace naleznete v tématu "Záložku vlastnost" v nápovědě k DAO.

##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize

Voláním této členské funkce získat počet záznamů v mezipaměti.

```
long GetCacheSize();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje počet záznamů v dynamické sady záznamů obsahující data do místní mezipaměti ze zdroje dat ODBC.

### <a name="remarks"></a>Poznámky

Ukládání dat zlepšuje výkon aplikace, která načte data ze vzdáleného serveru prostřednictvím objektů dynamické sady záznamů. Mezipaměť je mezera v místní paměti, která obsahuje data naposled načetli ze serveru, v případě, že data požádat znovu, když je spuštěná aplikace. Pokud se požaduje data, databázový stroj Microsoft Jet mezipaměti požadovaných dat nejprve zkontroluje místo načítání ze serveru, který trvá déle. Data, která nepochází ze zdroje dat ODBC není uložená v mezipaměti.

Všechny zdroje dat ODBC, jako je například připojené tabulky, můžete mít místní mezipaměti.

Související informace naleznete v tématu "CacheSize CacheStart vlastnosti" v nápovědě k DAO.

##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart

Voláním této členské funkce k získání hodnoty záložku prvního záznamu v sadě záznamů ukládat do mezipaměti.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Návratová hodnota

A `COleVariant` záložku první záznam, který určuje v sadě záznamů ukládat do mezipaměti.

### <a name="remarks"></a>Poznámky

Databázový stroj Microsoft Jet vyžádá záznamy rozsahu mezipaměti z mezipaměti a vyžádá záznamů mimo rozsah mezipaměti ze serveru.

> [!NOTE]
>  Záznamy načíst z mezipaměti neodrážejí změny provedené současně na zdroj dat jinými uživateli.

Související informace naleznete v tématu "CacheSize CacheStart vlastnosti" v nápovědě k DAO.

##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex

Voláním této členské funkce určit index aktuálně používána v indexovaných typ tabulky `CDaoRecordset` objektu.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` obsahující název indexu aktuálně používané pro sady záznamů typ tabulky. Pokud byl nastaven žádný index, vrátí prázdný řetězec.

### <a name="remarks"></a>Poznámky

Tento index je základem pro řazení záznamů v sadě záznamů tabulky typu a používají [Seek](#seek) členské funkce k vyhledání záznamů.

A `CDaoRecordset` objekt může mít více než jeden index, ale můžete použít pouze jeden index najednou (i když [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md) objekt může mít několik indexů definovanou).

Související informace naleznete v tématu "Objekt indexu" a definice "aktuální index" v nápovědě rozhraní DAO.

##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated

Voláním této členské funkce a získejte datum a čas vytvoření základní tabulky.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje datum a čas vytvoření základní tabulky.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozeny z počítače, na kterém byla vytvořena v základní tabulce.

Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated

Voláním této členské funkce k načtení datum a čas poslední aktualizace schématu.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje datum a čas poslední aktualizace struktura základní tabulky (schéma).

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozeny z počítače, na kterém byl naposledy aktualizován struktura základní tabulky (schéma).

Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName

Voláním této členské funkce, chcete-li zjistit název databáze pro tuto sadu záznamů.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` , který obsahuje cestu a název databáze, odkud pochází tato sada záznamů.

### <a name="remarks"></a>Poznámky

Pokud sada záznamů se vytvoří bez ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), pak tato cesta se používá sadou záznamů otevřít výchozí databázi. Ve výchozím nastavení tato funkce vrací prázdný řetězec. Když ClassWizard odvozuje na novou sadu záznamů z `CDaoRecordset`, tato funkce vytvoří za vás.

Následující příklad ukazuje použití dvojité zpětné lomítko (\\\\) v řetězci, jako je třeba použít řetězec, který má být správně interpretovat.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL

Rozhraní volá tuto funkci člena se získat výchozí příkaz SQL, na kterých je založena sadu záznamů.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` , která obsahuje výchozí příkaz SQL.

### <a name="remarks"></a>Poznámky

Může to být název tabulky nebo SQL **vyberte** příkazu.

Nepřímo definovat výchozí příkaz SQL. tím, že deklarujete třídu sady záznamů s ClassWizard a ClassWizard tento úkol provede za vás.

Pokud předáte prázdný řetězec SQL pro [otevřít](#open), pak tato funkce je volána k určení názvu tabulky nebo SQL pro sady záznamů.

##  <a name="geteditmode"></a>  CDaoRecordset::GetEditMode

Voláním této členské funkce k určení stavu úprav, což je jedna z následujících hodnot:

```
short GetEditMode();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která označuje stav úpravy pro požadovaný aktuální záznam.

### <a name="remarks"></a>Poznámky

|Value|Popis|
|-----------|-----------------|
|`dbEditNone`|Žádné úpravy operace probíhá.|
|`dbEditInProgress`|`Edit` byla volána.|
|`dbEditAdd`|`AddNew` byla volána.|

Související informace naleznete v tématu "EditMode vlastnost" v nápovědě k DAO.

##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount

Voláním této členské funkce se načíst počet polí (sloupců) definované v sadě záznamů.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v sadě záznamů.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Vlastnosti" v nápovědě k DAO.

##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo

Voláním této členské funkce získat informace o polích v sadě záznamů.

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

*nIndex*<br/>
Index založený na nule předdefinované pole v kolekci polí sady záznamů, pro vyhledávání podle indexu.

*fieldinfo*<br/>
Odkaz na [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o sadě záznamů pro načtení. Dostupné možnosti jsou zde uvedeny společně s způsobí funkce, která se vrátí. Pro zajištění nejlepšího výkonu načtěte jenom úroveň informací, které potřebujete:

- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, typ, velikosti, atributy

- `AFX_DAO_SECONDARY_INFO` Primární informace, a navíc: Pořadí, povinné, umožňují nulovou délku, Kolační pořadí, cizí název, zdrojové pole, zdrojová tabulka

- `AFX_DAO_ALL_INFO` Informace o primární a sekundární, a navíc: Výchozí hodnota, ověřovací pravidlo, Text pro ověření

*lpszName*<br/>
Název pole.

### <a name="remarks"></a>Poznámky

Jednu verzi funkce umožňuje vyhledat pole podle indexu. Jiné verze umožňuje vyhledávání podle názvu pole.

Popis informací, najdete v tématu [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, můžete získat informace o všech předchozích úrovní.

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="getfieldvalue"></a>  CDaoRecordset::GetFieldValue

Voláním této členské funkce k načtení dat v sadě záznamů.

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který obsahuje název pole.

*varValue*<br/>
Odkaz na `COleVariant` objekt, který bude uchovávat hodnotu pole.

*nIndex*<br/>
Z nuly vycházející index pole v kolekci polí sady záznamů, pro vyhledávání podle indexu.

### <a name="return-value"></a>Návratová hodnota

Dvě verze `GetFieldValue` návratový návratovou hodnotu [COleVariant](../../mfc/reference/colevariant-class.md) objekt, který obsahuje hodnotu pole.

### <a name="remarks"></a>Poznámky

Pole můžete vyhledávat podle názvu nebo podle pořadí.

> [!NOTE]
>  Je mnohem efektivnější volat jednu z verzí tato členská funkce, která přijímá `COleVariant` jako parametr namísto volání verzi, která vrátí odkaz na objekt `COleVariant` objektu. Z důvodu zpětné kompatibility jsou zachovány druhé verze této funkce.

Použití `GetFieldValue` a [SetFieldValue](#setfieldvalue) dynamicky vytvořit vazbu pole v době běhu místo staticky vazeb sloupců pomocí [DoFieldExchange](#dofieldexchange) mechanismus.

`GetFieldValue` a `DoFieldExchange` mechanismus mohou být kombinovány pro zlepšení výkonu. Například použít `GetFieldValue` načíst hodnotu, která potřebujete jenom na vyžádání a přiřaďte toto volání na tlačítko ". Další informace" v rozhraní.

Související informace naleznete v tématech "Pole objektu" a "Hodnota vlastnosti" v nápovědě k DAO.

##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount

Voláním této členské funkce k určení počtu indexy, které jsou k dispozici v sadě záznamů typ tabulky.

```
short GetIndexCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet indexů v sadě záznamů typ tabulky.

### <a name="remarks"></a>Poznámky

`GetIndexCount` je užitečné pro opakování ve smyčce prostřednictvím všech indexů v sadě záznamů. Pro tento účel použít `GetIndexCount` ve spojení s [GetIndexInfo](#getindexinfo). Pokud zavolat tuto členskou funkci na typ dynamická sada nebo typ snímku sady záznamů, MFC vyvolá výjimku.

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo

Voláním této členské funkce získat různé druhy informací o index definovaný v základní tabulce základní sady záznamů.

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule v kolekci indexy v tabulce, pro vyhledávání na základě číselných pozic.

*indexinfo*<br/>
Odkaz na [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o index k načtení. Dostupné možnosti jsou zde uvedeny společně s způsobí funkce, která se vrátí. Pro zajištění nejlepšího výkonu načtěte jenom úroveň informací, které potřebujete:

- `AFX_DAO_PRIMARY_INFO` (Výchozí) Pole se jménem, informace o poli

- `AFX_DAO_SECONDARY_INFO` Primární informace, a navíc: Primární, jedinečné, clusteru, Ignorovat hodnoty Null, povinné, cizí

- `AFX_DAO_ALL_INFO` Informace o primární a sekundární, a navíc: Počet jedinečných položek

*lpszName*<br/>
Ukazatel na název objektu indexu pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jednu verzi funkce umožňuje vyhledat index podle jeho pozice v kolekci. Jiné verze umožňuje vyhledávání podle názvu indexu.

Popis informací, najdete v tématu [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, můžete získat informace o všech předchozích úrovní.

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark

Voláním této členské funkce k načtení záložky záznam nejvíce nedávno přidané nebo aktualizované.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Návratová hodnota

A `COleVariant` obsahující záložku, která určuje naposledy přidání či změně záznamu.

### <a name="remarks"></a>Poznámky

Při vytvoření nebo otevření objekt sady záznamů jednotlivých záznamů jeho jedinečné záložku už má, pokud je podporuje. Volání [GetBookmark](#getbookmark) k určení, jestli sadu záznamů podporuje záložky. Pokud sada záznamů nepodporuje záložky, `CDaoException` je vyvolána výjimka.

Po přidání záznamu na konci sady záznamů se zobrazuje a není aktuální záznam. Chcete-li vytvořit nový záznam aktuální, zavolejte `GetLastModifiedBookmark` a následně zavolat `SetBookmark` se vraťte do nově přidaný záznam.

Související informace naleznete v tématu "LastModified vlastnost" v nápovědě k DAO.

##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode

Voláním této členské funkce k určení typu uzamčení platit pro sadu záznamů.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je typ uzamčení pesimistické, jinak 0 pro záznam optimistického zamykání.

### <a name="remarks"></a>Poznámky

Když pesimistické zamykání v důsledku toho stránka dat obsahující záznam, který upravujete je uzamčeno ihned poté, co zavoláte [upravit](#edit) členskou funkci. Na stránce se odemkne při volání [aktualizace](#update) nebo [Zavřít](#close) členská funkce nebo kteroukoli z operací přesunutí nebo najít.

Při optimistického zamykání je v platnosti, stránky dat obsahující záznam je uzamčen, pouze když probíhá aktualizace záznamu `Update` členskou funkci.

Při práci se zdroji dat rozhraní ODBC, je vždy optimistické režim uzamčení.

Související informace naleznete v tématech "LockEdits vlastnost" a "Uzamčení chování ve víceuživatelském prostředí aplikace" v nápovědě k DAO.

##  <a name="getname"></a>  CDaoRecordset::GetName

Voláním této členské funkce, aby se načetl název sady záznamů.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` obsahující název sady záznamů.

### <a name="remarks"></a>Poznámky

Název sady záznamů musí začínat písmenem a může obsahovat nejvýše 40 znaků. Může obsahovat čísla a podtržítka znaků, ale nemůže obsahovat interpunkční znaménka nebo mezery.

Související informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue

Voláním této členské funkce načte aktuální hodnota uložená v základní objekt DAOParameter zadaný parametr.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Číselné pozice parametru v základní objekt DAOParameter.

*lpszName*<br/>
Název parametru, jehož hodnotu chcete.

### <a name="return-value"></a>Návratová hodnota

Objekt třídy [COleVariant](../../mfc/reference/colevariant-class.md) , který obsahuje hodnoty parametru.

### <a name="remarks"></a>Poznámky

Tento parametr můžete přistupovat pomocí názvu nebo na základě jeho číselných pozic v kolekci.

Související informace naleznete v tématu "Parametr objekt" v nápovědě k DAO.

##  <a name="getpercentposition"></a>  CDaoRecordset::GetPercentPosition

Při práci s typem dynamická sada nebo sada záznamů typ snímku, pokud zavoláte `GetPercentPosition` před plně naplnění sady záznamů, množství přesun je relativní vzhledem k počtu záznamů získat přístup, jak je uvedeno voláním [getrecordcount –](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Návratová hodnota

Číslo od 0 do 100 určující Přibližná poloha aktuální záznam v objektu sady záznamů podle procentuální podíl záznamů v sadě záznamů.

### <a name="remarks"></a>Poznámky

Můžete přesunout na poslední záznam volání [MoveLast](#movelast) k úplné naplnění všechny sady záznamů, ale to může trvat značné množství času.

Můžete volat `GetPercentPosition` na všechny tři typy objektů sady záznamů, včetně tabulky s indexy. Však nelze volat `GetPercentPosition` na dopředné posouvání snímky nebo v sadě záznamů otevřena z předávací dotaz proti externí databáze. Pokud neexistuje aktuální záznam nebo odstranila he aktuální záznam `CDaoException` je vyvolána výjimka.

Související informace naleznete v tématu "PercentPosition vlastnost" v nápovědě k DAO.

##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount

Voláním této členské funkce a zjistěte, kolik záznamů v sadě záznamů si někdo zobrazil.

```
long GetRecordCount();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet záznamů, které jsou přístupné v objektu sady záznamů.

### <a name="remarks"></a>Poznámky

`GetRecordCount` nenaznačuje, že počet záznamů, jsou obsaženy v dynamických sad typ nebo typ snímku, záznamů, dokud si někdo zobrazil všechny záznamy. Toto volání funkce členů může trvat značné množství času k dokončení.

Jakmile se použil poslední záznam návratová hodnota označuje celkový počet neodstraněných záznamů v sadě záznamů. Chcete-li vynutit poslední záznam, který chcete získat přístup, zavolejte `MoveLast` nebo `FindLast` členskou funkci pro sadu záznamů. Počet SQL můžete použít také k určení přibližný počet záznamů, které dotaz vrátí.

Jak aplikace odstraní záznamy v dynamické sady záznamů, návratová hodnota `GetRecordCount` snižuje. Nicméně se neprojeví záznamy odstraněné jinými uživateli ve `GetRecordCount` dokud aktuální záznam je umístěn na odstraněný záznam. Pokud spustíte transakci, která má vliv na počet záznamů a následně vrácení zpět transakcí, `GetRecordCount` skutečný počet zbývajících záznamů se neprojeví.

Hodnota `GetRecordCount` ze sady záznamů typ snímku není ovlivněny změnami v podkladové tabulky.

Hodnota `GetRecordCount` z tabulky typu Sada záznamů odráží přibližný počet záznamů v tabulce a má vliv okamžitě, jako jsou přidané a odstraněné záznamy tabulky.

Sada záznamů s žádné záznamy, vrátí hodnotu 0. Při práci s tabulkami v připojené nebo ODBC databází, `GetRecordCount` vždy vrátí hodnotu - 1. Volání `Requery` členské funkce v sadě záznamů resetuje hodnotu `GetRecordCount` tak, jako kdyby byly znovu provést dotaz.

Související informace naleznete v tématu "PočetZáznamů vlastnost" v nápovědě k DAO.

##  <a name="getsql"></a>  CDaoRecordset::GetSQL

Voláním této členské funkce, chcete-li získat příkazu SQL, která byla použita k výběru záznamů sady záznamů, když se otevřel.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CString` , která obsahuje příkaz jazyka SQL.

### <a name="remarks"></a>Poznámky

Obecně to bude SQL **vyberte** příkazu.

Řetězec vrácený funkcí `GetSQL` se obvykle liší od libovolný řetězec, kterou jste předali do sady záznamů v *Ipszsql* parametr [otevřít](#open) členskou funkci. Důvodem je, že sada záznamů sestavuje úplný příkaz SQL na předané na základě `Open`zadaným ClassWizard a co jste zadali v [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) datové členy.

> [!NOTE]
>  Voláním této členské funkce pouze po volání `Open`.

Související informace naleznete v tématu "Vlastnosti SQL" v nápovědě k DAO.

##  <a name="gettype"></a>  CDaoRecordset::GetType

Voláním této členské funkce po otevření sady záznamů určit typ objektu sady záznamů.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Jeden z následujících hodnot, které označuje typ sady záznamů:

- `dbOpenTable` Sada záznamů typ tabulky

- `dbOpenDynaset` Dynaset-type recordset

- `dbOpenSnapshot` Sada záznamů typu snímek

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Vlastnost typu" v nápovědě k DAO.

##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule

Voláním této členské funkce k určení pravidlo použité k ověření dat.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje hodnotu, která ověřuje data v záznamu, jak změnit nebo přidat do tabulky.

### <a name="remarks"></a>Poznámky

Toto pravidlo je založený na textu a použití pokaždé, když se změní podkladové tabulky. Pokud data není platný, MFC vyvolá výjimku. Vrácená chybová zpráva je text vlastnost ověřovací podkladové pole objektu, pokud zadaný nebo textu výrazu určeném vlastností Ověřovací pravidlo základního objektu pole. Můžete volat [GetValidationText](#getvalidationtext) získat text chybové zprávy.

Například pole v záznamu, který vyžaduje den v měsíci může mít ověřovací pravidlo jako "BETWEEN dne 1 a 31."

Související informace naleznete v tématu "Ověřovací pravidlo vlastnost" v nápovědě k DAO.

##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText

Voláním této členské funkce k načtení textu vlastnost ověřovací základního objektu pole.

```
CString GetValidationText();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt obsahující text zprávy, která se zobrazí v případě hodnoty pole nevyhovuje ověřovacího pravidla na základní objekt pole.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Ověřovací vlastnost" v nápovědě k DAO.

##  <a name="isbof"></a>  CDaoRecordset::IsBOF

Voláním této členské funkce před přejít z záznam do záznamu zjistěte, zda jste došli před první záznam sady záznamů.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přesunuli zpět před první záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete také volat `IsBOF` spolu s `IsEOF` k určení, zda sada záznamů obsahuje záznamy, nebo je prázdný. Ihned poté, co zavoláte `Open`, pokud sada záznamů neobsahuje žádné záznamy `IsBOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, který má alespoň jeden záznam, první záznam je aktuální záznam a `IsBOF` vrátí hodnotu 0.

Pokud je první záznam aktuální záznam a zavoláte `MovePrev`, `IsBOF` následně vrátí nenulovou hodnotu. Pokud `IsBOF` vrátí nenulovou hodnotu a můžete volat `MovePrev`, je vyvolána výjimka. Pokud `IsBOF` vrátí nenulovou hodnotu, je definován aktuální záznam a žádné akce, které aktuální záznam způsobí výjimku.

Účinek specifických metod na `IsBOF` a `IsEOF` nastavení:

- Volání `Open*` interně provede první záznam v sadě záznamů aktuální záznam voláním `MoveFirst`. Proto volání `Open` na prázdnou sadu záznamů příčiny `IsBOF` a `IsEOF` vrátit nenulovou hodnotu. (Viz následující tabulka pro chování nezdařené `MoveFirst` nebo `MoveLast` volání.)

- Všechny operace přesunutí, které úspěšně vyhledat záznam způsobit, že oba `IsBOF` a `IsEOF` vrátit 0.

- `AddNew` Volání za nímž následuje `Update` způsobí, že volání, které úspěšně vloží nový záznam `IsBOF` vrátit 0, ale pouze v případě `IsEOF` není nenulová. Stav `IsEOF` vždy zůstane beze změny. Dle databázový stroj Microsoft Jet, je aktuální záznam ukazatel prázdnou sadu záznamů na konci souboru, tak všechny nový záznam se vkládá aktuální záznam.

- Žádné `Delete` volání, i v případě, že odebere jenom zbývající záznam ze záznamů, nedojde ke změně hodnoty `IsBOF` nebo `IsEOF`.

Tato tabulka zobrazuje operace přesunu, které jsou povolené s různými kombinacemi `IsBOF` /  `IsEOF`.

||MoveFirst MoveLast|MovePrev,<br /><br /> Přesunout < 0|Přesunout 0|MoveNext,<br /><br /> Přesunout > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= nenulovou hodnotu,<br /><br /> `IsEOF`=0|Povoleno|Výjimka|Výjimka|Povoleno|
|`IsBOF`=0,<br /><br /> `IsEOF`= nenulovou hodnotu|Povoleno|Povoleno|Výjimka|Výjimka|
|Obojí nenulové|Výjimka|Výjimka|Výjimka|Výjimka|
|Obě 0|Povoleno|Povoleno|Povoleno|Povoleno|

Umožní operace přesunu neznamená, že operace úspěšně najít záznam. Znamená pouze to, že pokus o provedení zadané operace přesunu je povolen a nebude generovat výjimku. Hodnota `IsBOF` a `IsEOF` členské funkce mohou změnit jako výsledek pokusu o přesun.

Vliv operací přesunu, které nelze vyhledat záznam na základě hodnoty `IsBOF` a `IsEOF` nastavení je uveden v následující tabulce.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nenulový|Nenulový|
|`Move` 0|Žádné změny|Žádné změny|
|`MovePrev`, `Move` < 0|Nenulový|Žádné změny|
|`MoveNext`, `Move` > 0|Žádné změny|Nenulový|

Související informace naleznete v tématu "BOF, EOF vlastnosti" v nápovědě k DAO.

##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted

Voláním této členské funkce k určení, zda aktuální záznam byl odstraněn.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů je umístěn na odstraněný záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud se posunete na záznam a `IsDeleted` vrátí hodnotu TRUE (nenulový), pak musí přejít k jinému záznamu před provedením jakékoli další operace, sada záznamů.

> [!NOTE]
>  Není nutné zkontrolovat stav odstraněné záznamy v sadě záznamů snímku nebo typ tabulky. Protože záznamy nelze odstranit ze snímku, není nutné volat `IsDeleted`. Pro typ tabulky sady záznamů se ve skutečnosti odstraněné záznamy odeberou ze sady záznamů. Jakmile byl odstraněn záznam, u vás a jiným uživatelem nebo v jiné sady záznamů, nelze přejděte zpět k tomuto záznamu. Proto není nutné volat `IsDeleted`.

Když odstraníte záznam z dynamická sada, odebere se ze sady záznamů a nelze přejděte zpět k tomuto záznamu. Pokud však záznam v dynamická sada je odstraněna jiným uživatelem nebo v jiné sady záznamů na základě stejné tabulky `IsDeleted` se vrací TRUE, pokud později přejděte k záznamu.

Související informace naleznete v tématech "Metodu Delete", "LastModified vlastnost" a "EditMode vlastnost" v nápovědě k DAO.

##  <a name="iseof"></a>  CDaoRecordset::IsEOF

Voláním této členské funkce při posunutí ze záznamu záznamu Další informace, jestli jste došli za poslední záznam sady záznamů.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přešli za poslední záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete také volat `IsEOF` k určení, zda sada záznamů obsahuje záznamy, nebo je prázdný. Ihned poté, co zavoláte `Open`, pokud sada záznamů neobsahuje žádné záznamy `IsEOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, který má alespoň jeden záznam, první záznam je aktuální záznam a `IsEOF` vrátí hodnotu 0.

Pokud je poslední záznam aktuální záznam při volání `MoveNext`, `IsEOF` následně vrátí nenulovou hodnotu. Pokud `IsEOF` vrátí nenulovou hodnotu a můžete volat `MoveNext`, je vyvolána výjimka. Pokud `IsEOF` vrátí nenulovou hodnotu, je definován aktuální záznam a žádné akce, které aktuální záznam způsobí výjimku.

Účinek specifických metod na `IsBOF` a `IsEOF` nastavení:

- Volání `Open` interně provede první záznam v sadě záznamů aktuální záznam voláním `MoveFirst`. Proto volání `Open` na prázdnou sadu záznamů příčiny `IsBOF` a `IsEOF` vrátit nenulovou hodnotu. (Viz následující tabulka pro chování nezdařené `MoveFirst` volání.)

- Všechny operace přesunutí, které úspěšně vyhledat záznam způsobit, že oba `IsBOF` a `IsEOF` vrátit 0.

- `AddNew` Volání za nímž následuje `Update` způsobí, že volání, které úspěšně vloží nový záznam `IsBOF` vrátit 0, ale pouze v případě `IsEOF` není nenulová. Stav `IsEOF` vždy zůstane beze změny. Dle databázový stroj Microsoft Jet, je aktuální záznam ukazatel prázdnou sadu záznamů na konci souboru, tak všechny nový záznam se vkládá aktuální záznam.

- Žádné `Delete` volání, i v případě, že odebere jenom zbývající záznam ze záznamů, nedojde ke změně hodnoty `IsBOF` nebo `IsEOF`.

Tato tabulka zobrazuje operace přesunu, které jsou povolené s různými kombinacemi `IsBOF` /  `IsEOF`.

||MoveFirst MoveLast|MovePrev,<br /><br /> Přesunout < 0|Přesunout 0|MoveNext,<br /><br /> Přesunout > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= nenulovou hodnotu,<br /><br /> `IsEOF`=0|Povoleno|Výjimka|Výjimka|Povoleno|
|`IsBOF`=0,<br /><br /> `IsEOF`= nenulovou hodnotu|Povoleno|Povoleno|Výjimka|Výjimka|
|Obojí nenulové|Výjimka|Výjimka|Výjimka|Výjimka|
|Obě 0|Povoleno|Povoleno|Povoleno|Povoleno|

Umožní operace přesunu neznamená, že operace úspěšně najít záznam. Znamená pouze to, že pokus o provedení zadané operace přesunu je povolen a nebude generovat výjimku. Hodnota `IsBOF` a `IsEOF` členské funkce mohou změnit jako výsledek pokusu o přesun.

Vliv operací přesunu, které nelze vyhledat záznam na základě hodnoty `IsBOF` a `IsEOF` nastavení je uveden v následující tabulce.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nenulový|Nenulový|
|`Move` 0|Žádné změny|Žádné změny|
|`MovePrev`, `Move` < 0|Nenulový|Žádné změny|
|`MoveNext`, `Move` > 0|Žádné změny|Nenulový|

Související informace naleznete v tématu "BOF, EOF vlastnosti" v nápovědě k DAO.

##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty

Voláním této členské funkce, chcete-li zjistit, jestli zadané pole datový člen dynamická sada byl označen jako "nečisté" (změnit).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Ukazatel na pole datového člena, jehož stav chcete zkontrolovat nebo NULL, pokud chcete zjistit, zda jsou změny libovolné pole.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadané pole datového člena je označena jako chybná; jinak 0.

### <a name="remarks"></a>Poznámky

Data ve všech datových členů nečistých polí se přesunou do záznamu ve zdroji dat. Pokud aktuální záznam se aktualizuje pomocí volání `Update` členskou funkci `CDaoRecordset` (po volání `Edit` nebo `AddNew`). S tyto znalosti, můžete provést další kroky, například unflagging datový člen pole k označení sloupci, se zapíšou do zdroje dat.

`IsFieldDirty` se implementuje pomocí `DoFieldExchange`.

##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull

Voláním této členské funkce k určení, zda zadaná pole datového člena sady záznamů byl označen jako hodnota Null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Ukazatel na pole datového člena, jehož stav chcete zkontrolovat nebo NULL, pokud chcete zjistit, zda libovolné pole jsou Null.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadané pole datového člena je označený jako hodnota Null. jinak 0.

### <a name="remarks"></a>Poznámky

(V terminologii databáze s hodnotou Null znamená "mít žádná hodnota" a není stejná jako hodnota NULL v jazyce C++.) Pokud pole datového člena je označený jako hodnota Null, je interpretován jako sloupec aktuální záznam, pro kterou neexistuje žádná hodnota.

> [!NOTE]
>  V některých situacích pomocí `IsFieldNull` může být neefektivní, jak ukazuje následující příklad kódu:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  Pokud používáte dynamické vazby záznamu, bez odvozený od `CDaoRecordset`, nezapomeňte použít VT_NULL, jak je znázorněno v příkladu.

##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable

Voláním této členské funkce určuje, jestli je zadané pole datového člena "null" (může být nastavena na hodnotu Null; C++ NULL není stejná jako hodnota Null, tzn., v, řečeno terminologií databáze, "s žádnou hodnotu").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Ukazatel na pole datového člena, jehož stav chcete zkontrolovat nebo NULL, pokud chcete zjistit, zda libovolné pole jsou Null.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadané pole datového člena, které můžete provést hodnota Null. jinak 0.

### <a name="remarks"></a>Poznámky

Pole, které nemůže mít hodnotu Null musí mít hodnotu. Pokud se pokusíte nastavit toto pole na hodnotu Null při přidávání nebo aktualizaci záznamu, odmítne zdroj dat je přidání nebo aktualizace, a `Update` vyvolá výjimku. Vyvolá se výjimka při volání `Update`, ne v případě, že zavoláte `SetFieldNull`.

##  <a name="isopen"></a>  CDaoRecordset::IsOpen

Voláním této členské funkce k určení, zda je otevřít sadu záznamů.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud objekt sady záznamů `Open` nebo `Requery` dříve byla volána členská funkce a sady záznamů nebyla uzavřena; jinak 0.

### <a name="remarks"></a>Poznámky

##  <a name="m_bcheckcachefordirtyfields"></a>  CDaoRecordset::m_bCheckCacheForDirtyFields

Obsahuje příznak označující, zda v mezipaměti pole jsou automaticky označeny jako nesprávné (změněné) a hodnotu Null.

### <a name="remarks"></a>Poznámky

Příznak, výchozí hodnota je TRUE. Nastavení v tomuto datovému členu řídí celý mechanismus dvojité ukládání do vyrovnávací paměti. Pokud nastavíte příznak na hodnotu TRUE, můžete vypnout ukládání do mezipaměti na základě pole pomocí pole pomocí mechanismu DFX. Pokud nastavíte příznak na hodnotu FALSE, musí volat `SetFieldDirty` a `SetFieldNull` sami.

Nastavit tento datový člen před voláním `Open`. Tento mechanismus je primárně pro snadné použití. Může být výkon nižší z důvodu dvě vyrovnávací paměti polí, jakmile jsou provedeny změny.

##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields

Obsahuje číslo pole datových členů ve třídě sady záznamů a počet sloupců vybraných funkcí sady záznamů ze zdroje dat.

### <a name="remarks"></a>Poznámky

Konstruktor pro třídu sady záznamů musí inicializovat `m_nFields` s správný počet staticky vázaného pole. ClassWizard zapíše tuto inicializaci za vás, když ji použijete k deklaraci vaší třídy sady záznamů. Můžete je zapsat také ručně.

Rozhraní používá ke správě interakcí mezi datové členy polí a odpovídající sloupce aktuální záznam ve zdroji dat. Toto číslo.

> [!NOTE]
>  Tato hodnota musí odpovídat počet výstupních sloupců zaregistrovaný v `DoFieldExchange` po volání `SetFieldType` s parametrem `CDaoFieldExchange::outputColumn`.

Můžete vytvořit vazbu sloupců dynamicky podle své `CDaoRecordset::GetFieldValue` a `CDaoRecordset::SetFieldValue`. Pokud tak učiníte, není potřeba zvýšit počet v `m_nFields` tak, aby odrážely počet DFX funkce volání vaší `DoFieldExchange` členskou funkci.

##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams

Obsahuje číslo parametru datové členy třídy sady záznamů – předaný počet parametrů pomocí dotazu sadu záznamů.

### <a name="remarks"></a>Poznámky

Pokud vaše sada záznamů třída nemá žádné parametry datových členů, konstruktor pro třídu musí inicializovat *m_nParams* správné číslo. Hodnota *m_nParams* výchozí hodnota je 0. Pokud chcete přidat parametry datových členů – které musíte udělat ručně – inicializace je nutné přidat také ručně v konstruktoru třídy tak, aby odrážely počet parametrů (který musí být přinejmenším stejně velká jako počet "zástupné symboly ve vaší *m_strFilter*  nebo *m_strSort* řetězec).

Rozhraní používá toto číslo při parametrizuje dotaz sady záznamů.

> [!NOTE]
>  Tato hodnota musí odpovídat jako počet "parametrů" zaregistrované v `DoFieldExchange` po volání `SetFieldType` s parametrem `CFieldExchange::param`.

Související informace naleznete v tématu "Parametr objekt" v nápovědě k DAO.

##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset

Obsahuje ukazatel na rozhraní OLE pro podkladové objekt sady záznamů rozhraní DAO `CDaoRecordset` objektu.

### <a name="remarks"></a>Poznámky

Pokud je potřeba získat přímo přístup k rozhraní DAO, použijte tento ukazatel.

Související informace naleznete v tématu "Objekt sady záznamů" v nápovědě rozhraní DAO.

##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase

Obsahuje ukazatel `CDaoDatabase` objekt, jehož prostřednictvím sady záznamů je připojený ke zdroji dat.

### <a name="remarks"></a>Poznámky

Tato proměnná je nastavená dvěma způsoby. Obvykle můžete předat ukazatel už otevřené `CDaoDatabase` objektu při vytvoření objektu sady záznamů. Pokud místo toho předáte NULL `CDaoRecordset` vytvoří `CDaoDatabase` objekt a otevře jej. V obou případech `CDaoRecordset` ukládá ukazatel v této proměnné.

Obvykle nebudete muset přímo pomocí ukazatele uložené v `m_pDatabase`. Pokud Tvorba vlastních rozšíření pro `CDaoRecordset`, ale budete muset použít ukazatele. Například můžete potřebovat ukazatel pokud vyvoláte vlastní `CDaoException`(s).

Související informace naleznete v tématu "Databázový objekt" v nápovědě k DAO.

##  <a name="m_strfilter"></a>  CDaoRecordset::m_strFilter

Obsahuje řetězec, který se používá ke konstrukci **kde** klauzuli příkazu SQL.

### <a name="remarks"></a>Poznámky

Nezahrnuje rezervované slovo **kde** k filtrování sady záznamů. Použijte tento datový člen neplatí pro sady záznamů typ tabulky. Použití `m_strFilter` nemá žádný vliv při otevření sady záznamů pomocí `CDaoQueryDef` ukazatele.

Použijte formát USA data (rok měsíc den) při filtrování pole, která obsahují data, i pokud nepoužíváte verzi US databázový stroj Microsoft Jet; v opačném případě nemusí data filtrovat podle očekávání.

Související informace naleznete v tématu "Vlastnost filtr" v nápovědě k DAO.

##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort

Obsahuje řetězec obsahující **ORDERBY** klauzuli příkazu SQL bez vyhrazených slov **ORDERBY**.

### <a name="remarks"></a>Poznámky

Můžete seřadit objekty sada záznamů typu dynamická a snímek.

Nelze řadit typ tabulky objektů sady záznamů. Chcete-li určit pořadí řazení sady záznamů typ tabulky, zavolejte [SetCurrentIndex](#setcurrentindex).

Použití *m_strSort* nemá žádný vliv při otevření sady záznamů pomocí `CDaoQueryDef` ukazatele.

Související informace naleznete v tématu "Vlastnost řazení" v nápovědě k DAO.

##  <a name="move"></a>  CDaoRecordset::Move

Zavolat tuto členskou funkci na pozici sady záznamů *lRows* záznamy z aktuální záznam.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parametry

*lRows*<br/>
Počet záznamů pro přesun vpřed nebo vzad. Kladné hodnoty pokračovat dál a na konci sady záznamů. Záporné hodnoty zpět, přesuňte směrem k začátku.

### <a name="remarks"></a>Poznámky

Můžete přesunout vpřed nebo vzad. `Move( 1 )` je ekvivalentní `MoveNext`, a `Move( -1 )` je ekvivalentní `MovePrev`.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně platí, obě volání `IsBOF` a `IsEOF` před přesunutím k určení, zda sada záznamů obsahuje všechny záznamy. Po zavolání `Open` nebo `Requery`, volání buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud jste přešli po začátku nebo konci sady záznamů ( `IsBOF` nebo `IsEOF` vrátí nenulovou hodnotu), volání `Move` vyvolá `CDaoException`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Při volání `Move` na dopředné posouvání snímku *lRows* parametr musí být kladné celé číslo a záložky nejsou povoleny, takže můžete pokračovat pouze.

Chcete-li první, poslední, další nebo předchozí záznam v sadě záznamů aktuální záznam, volání `MoveFirst`, `MoveLast`, `MoveNext`, nebo `MovePrev` členskou funkci.

Související informace naleznete v tématech "Metoda Move" a "MoveFirst MoveLast, MoveNext, MovePrevious metod" v nápovědě k DAO.

##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst

Voláním této členské funkce, aby první záznam v sadě záznamů (pokud existuje) aktuální záznam.

```
void MoveFirst();
```

### <a name="remarks"></a>Poznámky

Není nutné volat `MoveFirst` ihned po otevření sady záznamů. V tu chvíli první záznam (pokud existuje) je automaticky aktuální záznam.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně platí, obě volání `IsBOF` a `IsEOF` před přesunutím k určení, zda sada záznamů obsahuje všechny záznamy. Po zavolání `Open` nebo `Requery`, volání buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Použití `Move` funkce přesunout ze záznamu bez použití podmínku. Pomocí operace Find k vyhledání záznamů v dynamických sad typ nebo typ snímku, záznamů objektů, které splňují určité podmínky. Chcete-li vyhledat záznam v objektu typ tabulky záznamů, zavolejte `Seek`.

Pokud sada záznamů odkazuje na typ tabulka záznamů, přesun sleduje aktuální index v tabulce. Aktuální index můžete nastavit pomocí vlastnosti indexu základní objekt rozhraní DAO. Pokud aktuální index nenastavíte, není definováno pořadí vrácených záznamů.

Při volání `MoveLast` na objekt sady záznamů na základě dotazů SQL nebo querydef, dotaz musí k dokončení a plně naplní objekt sady záznamů.

Nelze volat `MoveFirst` nebo `MovePrev` členskou funkci s dopředné posouvání snímku.

Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů určitého počtu záznamů vpřed nebo vzad, zavolejte `Move`.

Související informace naleznete v tématech "Metoda Move" a "MoveFirst MoveLast, MoveNext, MovePrevious metod" v nápovědě k DAO.

##  <a name="movelast"></a>  CDaoRecordset::MoveLast

Voláním této členské funkce, aby poslední záznam (pokud existuje) v sadě záznamů aktuální záznam.

```
void MoveLast();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně platí, obě volání `IsBOF` a `IsEOF` před přesunutím k určení, zda sada záznamů obsahuje všechny záznamy. Po zavolání `Open` nebo `Requery`, volání buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Použití `Move` funkce přesunout ze záznamu bez použití podmínku. Pomocí operace Find k vyhledání záznamů v dynamických sad typ nebo typ snímku, záznamů objektů, které splňují určité podmínky. Chcete-li vyhledat záznam v objektu typ tabulky záznamů, zavolejte `Seek`.

Pokud sada záznamů odkazuje na typ tabulka záznamů, přesun sleduje aktuální index v tabulce. Aktuální index můžete nastavit pomocí vlastnosti indexu základní objekt rozhraní DAO. Pokud aktuální index nenastavíte, není definováno pořadí vrácených záznamů.

Při volání `MoveLast` na objekt sady záznamů na základě dotazů SQL nebo querydef, dotaz musí k dokončení a plně naplní objekt sady záznamů.

Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů určitého počtu záznamů vpřed nebo vzad, zavolejte `Move`.

Související informace naleznete v tématech "Metoda Move" a "MoveFirst MoveLast, MoveNext, MovePrevious metod" v nápovědě k DAO.

##  <a name="movenext"></a>  CDaoRecordset::MoveNext

Voláním této členské funkce, aby se další záznam v sadě záznamů aktuální záznam.

```
void MoveNext();
```

### <a name="remarks"></a>Poznámky

Doporučuje se, že zavoláte `IsBOF` předtím, než zkusíte přesunout na předchozí záznam. Volání `MovePrev` vyvolá výjimku `CDaoException` Pokud `IsBOF` vrátí nenulovou hodnotu, která udává, že jste již přešli před první záznam nebo že sadou záznamů nevybraly se žádné záznamy.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně platí, obě volání `IsBOF` a `IsEOF` před přesunutím k určení, zda sada záznamů obsahuje všechny záznamy. Po zavolání `Open` nebo `Requery`, volání buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Použití `Move` funkce přesunout ze záznamu bez použití podmínku. Pomocí operace Find k vyhledání záznamů v dynamických sad typ nebo typ snímku, záznamů objektů, které splňují určité podmínky. Chcete-li vyhledat záznam v objektu typ tabulky záznamů, zavolejte `Seek`.

Pokud sada záznamů odkazuje na typ tabulka záznamů, přesun sleduje aktuální index v tabulce. Aktuální index můžete nastavit pomocí vlastnosti indexu základní objekt rozhraní DAO. Pokud aktuální index nenastavíte, není definováno pořadí vrácených záznamů.

Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů určitého počtu záznamů vpřed nebo vzad, zavolejte `Move`.

Související informace naleznete v tématech "Metoda Move" a "MoveFirst MoveLast, MoveNext, MovePrevious metod" v nápovědě k DAO.

##  <a name="moveprev"></a>  CDaoRecordset::MovePrev

Voláním této členské funkce, aby předchozího záznamu v sadě záznamů aktuální záznam.

```
void MovePrev();
```

### <a name="remarks"></a>Poznámky

Doporučuje se, že zavoláte `IsBOF` předtím, než zkusíte přesunout na předchozí záznam. Volání `MovePrev` vyvolá výjimku `CDaoException` Pokud `IsBOF` vrátí nenulovou hodnotu, která udává, že jste již přešli před první záznam nebo že sadou záznamů nevybraly se žádné záznamy.

> [!CAUTION]
>  Některé z volání `Move` funkce vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně platí, obě volání `IsBOF` a `IsEOF` před přesunutím k určení, zda sada záznamů obsahuje všechny záznamy. Po zavolání `Open` nebo `Requery`, volání buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud některý z volání `Move` funkce při aktuální záznam aktualizovány nebo přidány, aktualizace bude ztracen bez předchozího upozornění.

Použití `Move` funkce přesunout ze záznamu bez použití podmínku. Pomocí operace Find k vyhledání záznamů v dynamických sad typ nebo typ snímku, záznamů objektů, které splňují určité podmínky. Chcete-li vyhledat záznam v objektu typ tabulky záznamů, zavolejte `Seek`.

Pokud sada záznamů odkazuje na typ tabulka záznamů, přesun sleduje aktuální index v tabulce. Aktuální index můžete nastavit pomocí vlastnosti indexu základní objekt rozhraní DAO. Pokud aktuální index nenastavíte, není definováno pořadí vrácených záznamů.

Nelze volat `MoveFirst` nebo `MovePrev` členskou funkci s dopředné posouvání snímku.

Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů určitého počtu záznamů vpřed nebo vzad, zavolejte `Move`.

Související informace naleznete v tématech "Metoda Move" a "MoveFirst MoveLast, MoveNext, MovePrevious metod" v nápovědě k DAO.

##  <a name="open"></a>  CDaoRecordset::Open

Musíte zavolat tuto členskou funkci načíst záznamy pro sady záznamů.

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>Parametry

*nOpenType*<br/>
Jeden z následujících hodnot:

- `dbOpenDynaset` Dynamické sady záznamů s posouváním obousměrné. Toto nastavení je výchozí.

- `dbOpenTable` Typ tabulky záznamů s posouváním obousměrné.

- `dbOpenSnapshot` Typ snímku sada záznamů s posouváním obousměrné.

*lpszSQL*<br/>
Ukazatel řetězce obsahující jedno z následujících:

- Ukazatel s hodnotou NULL.

- Název jedné nebo více tabledefs – a/nebo querydefs – (oddělené čárkami).

- SQL **vyberte** – příkaz (volitelně spolu s SQL **kde** nebo **ORDERBY** klauzule).

- Předávací dotaz.

*nOptions*<br/>
Jeden nebo více možností uvedených níže. Výchozí hodnota je 0. Možné hodnoty jsou následující:

- `dbAppendOnly` Můžete přidat jenom nové záznamy (pouze pro dynamické sady záznamů). Tato možnost doslova znamená, že může pouze přidávat záznamy. Databázové třídy MFC rozhraní ODBC máte nabízí jen možnost, která umožňuje záznamů, které mají být načten a připojen.

- `dbForwardOnly` Sady záznamů je snímek dopředné posouvání.

- `dbSeeChanges` Pokud se mění data, která jsou úpravy jiný uživatel generují výjimku.

- `dbDenyWrite` Ostatní uživatelé nemůžete upravovat ani přidat záznamy.

- `dbDenyRead` Ostatní uživatelé nebudou moct zobrazit záznamy (pouze sada typ tabulky záznamů).

- `dbReadOnly` Můžete zobrazit pouze záznamy; ostatní uživatelé mohou upravovat je.

- `dbInconsistent` Nekonzistentní aktualizace jsou povoleny (pouze pro dynamické sady záznamů).

- `dbConsistent` (Pouze pro dynamické sady záznamů) jsou povoleny pouze konzistentní aktualizace.

> [!NOTE]
>  Konstanty `dbConsistent` a `dbInconsistent` se vzájemně vylučují. Můžete použít jednu nebo druhou, ale nikoli oba současně ve danou instanci `Open`.

*pTableDef*<br/>
Ukazatel [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md) objektu. Tato verze je platná pouze pro sady záznamů typ tabulky. Při použití této možnosti `CDaoDatabase` použitý k vytvoření ukazatele `CDaoRecordset` se nepoužívá; místo toho použít databázi, ve kterém se nachází tabledef.

*pQueryDef*<br/>
Ukazatel [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md) objektu. Tato verze je platná pouze pro dynamické sady a sady záznamů typ snímku. Při použití této možnosti `CDaoDatabase` použitý k vytvoření ukazatele `CDaoRecordset` se nepoužívá; místo toho použít databázi, ve kterém se nachází querydef.

### <a name="remarks"></a>Poznámky

Před voláním `Open`, musíte vytvořit objekt sady záznamů. Chcete-li to provést několika způsoby:

- Při vytváření objektu sady záznamů, můžete předat ukazatel `CDaoDatabase` objekt, který je již otevřen.

- Při vytváření objektu sady záznamů, můžete předat ukazatel `CDaoDatabase` objekt, který není otevřený. Otevře sadu záznamů `CDaoDatabase` objektu, ale nebude zavřete ho po zavření objektu sady záznamů.

- Při vytváření objektu sady záznamů předejte ukazatel s hodnotou NULL. Volání objektu sady záznamů `GetDefaultDBName` a získat tak název aplikace Microsoft Access. Otevřete soubor MDB. Potom otevře sadu záznamů `CDaoDatabase` objekt a zachová otevřít jako sady záznamů je otevřený. Při volání `Close` v sadě záznamů, `CDaoDatabase` také objekt je zavřený.

    > [!NOTE]
    >  Při otevření sady záznamů `CDaoDatabase` objektu, otevře se zdroji dat s nevýhradní přístup.

Pro verzi `Open` , která používá *Ipszsql* parametr, jakmile se otevře sadu záznamů můžete načíst záznamy v jednom z několika způsoby. První možností je, aby DFX – funkce vaší `DoFieldExchange`. Druhou možností je použití dynamické vazby voláním `GetFieldValue` členskou funkci. Tyto možnosti se dají implementovat samostatně nebo v kombinaci. Pokud se zkombinují, bude mít a zajistěte tak předání příkaz jazyka SQL sami při volání `Open`.

Při použití druhou verzi `Open` kde předáním `CDaoTableDef` objektu, výsledné sloupce budou k dispozici pro vázání prostřednictvím `DoFieldExchange` a DFX mechanismus, a/nebo vazby dynamicky prostřednictvím `GetFieldValue`.

> [!NOTE]
>  Lze volat pouze `Open` pomocí `CDaoTableDef` objekt pro sady záznamů typ tabulky.

Při použití třetí verzi `Open` ve kterém můžete předat `CDaoQueryDef` , že dotaz bude proveden a výsledné sloupce budou k dispozici pro vázání prostřednictvím objektů `DoFieldExchange` a DFX mechanismus, a/nebo vazby dynamicky prostřednictvím `GetFieldValue`.

> [!NOTE]
>  Lze volat pouze `Open` pomocí `CDaoQueryDef` objekt pro dynamické sady a sady záznamů typ snímku.

Pro první verzi `Open` , která používá `lpszSQL` parametr záznamy jsou vybrané na základě kritérií uvedených v následující tabulce.

|Hodnota `lpszSQL` parametr|Zvolené záznamy jsou určeny|Příklad|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Řetězec vrácený funkcí `GetDefaultSQL`.||
|Čárkou oddělený seznam jednoho nebo více tabledefs – a/nebo názvy querydef.|Všechny sloupce v reprezentována `DoFieldExchange`.|`"Customer"`|
|**Vyberte** seznam sloupců **FROM** seznam tabulek|Zadané sloupce ze zadané tabledef(s) a/nebo querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Obvyklým postupem je předat hodnotu NULL na `Open`; v takovém případě `Open` volání `GetDefaultSQL`, přepisovatelné členské funkce, která ClassWizard vygeneruje při vytváření `CDaoRecordset`-odvozené třídy. Tuto hodnotu poskytuje tabledef(s) a/nebo querydef názvy, které jste zadali v nástroji ClassWizard. Místo toho můžete zadat jiné informace v *Ipszsql* parametru.

Bez ohledu na předané, `Open` vytvoří konečný řetězec SQL pro dotaz (řetězec může obsahovat SQL **kde** a **ORDERBY** klauzule připojí *Ipszsql* řetězec je předán) a potom tento dotaz spustí. Můžete prozkoumat sestavený řetězec voláním `GetSQL` po volání `Open`.

Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Pokud chcete nastavit možnosti sady záznamů, například filtr nebo řazení, nastavte `m_strSort` nebo `m_strFilter` po vytvoření objektu sady záznamů, ale před voláním `Open`. Pokud chcete aktualizovat záznamy v sadě záznamů po sady záznamů je již otevřen, zavolejte `Requery`.

Při volání `Open` na typ dynamická sada nebo sada záznamů typ snímku, nebo pokud zdroj dat odkazuje na příkazu SQL nebo tabledef, představující připojené tabulky, nemůžete použít `dbOpenTable` pro argument typu; Pokud tak učiníte, MFC vyvolá výjimku. Pokud chcete zjistit, zda objekt tabledef představuje připojené tabulky, vytvořte [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md) objektu a volání jeho [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) členskou funkci.

Použití `dbSeeChanges` příznak, pokud chcete zachytit změny provedené jiným uživatelem nebo jiné aplikace na svém počítači při úpravách nebo odstraňování stejný záznam. Například, pokud dva uživatele můžete začít upravovat stejný záznam, první uživatel, který volání `Update` členské funkce úspěšná. Když `Update` je volán druhého uživatele, `CDaoException` je vyvolána výjimka. Podobně pokud se druhý uživatel pokusí o volání `Delete` odstranit záznam a již byl změněn na prvního uživatele, `CDaoException` vyvolá.

Obvykle Pokud uživatel získá to `CDaoException` při aktualizaci, váš kód by měl aktualizovat obsah polí a načíst nově upravené hodnoty. Pokud probíhá odstraňování dojde k výjimce, váš kód může zobrazit nových záznamů dat uživateli a zprávu s oznámením, že data byla nedávno změněna. V tuto chvíli váš kód může požádat o potvrzení, že stále chce uživatel záznam odstranit.

> [!TIP]
>  Použijte možnost posouvání dopředné (`dbForwardOnly`) ke zlepšení výkonu, pokud vaše aplikace odešle jednom průchodu přes sadu záznamů otevřené ze zdroje dat ODBC.

Související informace naleznete v tématu "OpenRecordset metodu" v nápovědě k DAO.

##  <a name="requery"></a>  CDaoRecordset::Requery

Voláním této členské funkce k opětovnému sestavení (Aktualizovat) na sadu záznamů.

```
virtual void Requery();
```

### <a name="remarks"></a>Poznámky

Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

V pořadí záznamů reflektování přidání a odstranění, které vám a dalším uživatelům, aby ke zdroji dat, je nutné znovu vytvořit sadu záznamů voláním `Requery`. Pokud je dynamická sada záznamů, automaticky zobrazuje aktualizace, které vy nebo ostatní uživatelé provést existujících záznamů (ale ne doplňky). Pokud je sada záznamů snímku, musíte zavolat `Requery` tak, aby odrážely změny podle jiných uživatelů a přidání a odstranění.

Pro dynamická sada nebo snímku volání `Requery` kdykoli chcete znovu vytvořit sadu záznamů pomocí hodnoty parametrů. Nastavte nový filtr nebo řazení nastavením [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) před voláním `Requery`. Nastavit nové parametry přiřazením nových hodnot pro parametry datových členů před voláním `Requery`.

Pokud se nezdaří pokus o opětovné vytvoření sady záznamů, sady záznamů je zavřený. Před voláním `Requery`, můžete určit, jestli sadu záznamů můžete fokusu voláním [CanRestart](#canrestart) členskou funkci. `CanRestart` není zaručeno, že `Requery` proběhne úspěšně.

> [!CAUTION]
>  Volání `Requery` pouze poté, co jste volali `Open`.

> [!NOTE]
>  Volání [Requery](#requery) změní DAO záložky.

Nejde volat `Requery` na typ dynamická sada nebo sada záznamů typu snímek volání `CanRestart` vrátí hodnotu 0, můžete si ho na typ tabulka záznamů, ani.

Pokud mají oba `IsBOF` a `IsEOF` vrátí nenulovou hodnotu, po zavolání `Requery`, dotaz nevrátil žádné záznamy a sady záznamů se neobsahují žádná data.

Související informace naleznete v tématu "Requery metodu" v nápovědě k DAO.

##  <a name="seek"></a>  CDaoRecordset::Seek

Voláním této členské funkce vyhledejte záznam v objektu sady záznamů indexovaný typ tabulky, která vyhovuje zadaným kritériím pro aktuální index a zkontrolujte, zda záznam aktuální záznam.

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>Parametry

*lpszComparison*<br/>
Jeden z těchto výrazů řetězce: "<","\<=", "=", "> =", nebo ">".

*pKey1*<br/>
Ukazatel [COleVariant](../../mfc/reference/colevariant-class.md) jejíž hodnota odpovídá na první pole v indexu. Povinný parametr.

*pKey2*<br/>
Ukazatel `COleVariant` jejíž hodnota odpovídá druhé pole v indexu, pokud existuje. Výchozí hodnota je NULL.

*pKey3*<br/>
Ukazatel `COleVariant` jejíž hodnota odpovídá třetí pole v indexu, pokud existuje. Výchozí hodnota je NULL.

*pKeyArray*<br/>
Ukazatel na pole variant. Velikost pole odpovídá počet polí v indexu.

*nKeys*<br/>
Celé číslo odpovídající velikost pole, což je počet polí v indexu.

> [!NOTE]
>  Nezadávejte zástupné znaky v klíčích. Způsobí, že zástupné znaky `Seek` vrátit žádné odpovídající záznamy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud najde odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Použijte druhý (pole) verzi `Seek` zpracování indexy polí čtyři nebo více.

`Seek` Umožňuje vysoce výkonné index vyhledávání u sady záznamů, typ tabulky. Je nutné nastavit index aktuálního volání `SetCurrentIndex` před voláním `Seek`. Pokud index identifikuje duplicitní klíče pole nebo polí, `Seek` vyhledá první záznam, který splňuje kritéria. Pokud není nastavený indexu, je vyvolána výjimka.

Všimněte si, že pokud nejsou vytvoření sady záznamů ve formátu UNICODE, `COleVariant` objekty musí být explicitně deklarovány ANSI. To můžete udělat pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formu konstruktor s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na `VT_BSTRT`.

Při volání `Seek`, předejte jeden nebo více klíčových hodnot a operátor porovnání ("<","\<=", "=", "> =", nebo ">"). `Seek` vyhledává zadaná pole klíčů a vyhledá první záznam, který splňuje kritéria stanovená ve *lpszComparison* a *pKey1*. Jednou nalezen `Seek` vrátí nenulovou hodnotu a díky tomuto záznamu aktuální. Pokud `Seek` nepodaří najít shodu, `Seek` vrátí nulu a aktuální záznam není definován. Při použití rozhraní DAO přímo, musíte explicitně zkontrolovala NoMatch vlastnost.

Pokud `lpszComparison` je "=", "> =", nebo ">", `Seek` začne na začátku indexu. Pokud *lpszComparison* je "<" nebo "< =", `Seek` spustí na konci indexu a hledá zpětně, pokud existují duplicitní index položky na konci. V takovém případě `Seek` začíná na libovolný záznam mezi položkami duplicitní index na konci indexu.

Existuje nemusí být aktuální záznam, když použijete `Seek`.

Vyhledejte záznam v typu dynamická sada nebo sada záznamů typu snímek, který splňuje určité podmínky, pomocí operace Find. Operace přesunu zahrnout všechny záznamy, nejen ty, které splňují určité podmínky, můžete využít k přesunout ze záznamu.

Nejde volat `Seek` na připojené tabulky libovolného typu, protože připojené tabulky musí být otevřen jako dynamická sada typ nebo typ snímku sady záznamů. Ale při volání `CDaoDatabase::Open` přímo otevřete Instalovatelné databázi ISAM, můžete volat `Seek` u tabulek v databázi, i když výkon může být pomalé.

Související informace naleznete v tématu "Vyhledat metodu" v nápovědě k DAO.

##  <a name="setabsoluteposition"></a>  CDaoRecordset::SetAbsolutePosition

Nastaví relativní číslo záznamu aktuální objekt sady záznamů.

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parametry

*lPosition*<br/>
Odpovídá pořadí aktuální záznam v sadě záznamů.

### <a name="remarks"></a>Poznámky

Volání `SetAbsolutePosition` umožňuje umístit aktuální záznam ukazatel na konkrétní záznam podle jeho pořadové číslo pozice v dynamických sad typ nebo typ snímku, záznamů. Můžete také určit aktuální číslo záznamu voláním [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
>  Tato členská funkce je platná pouze pro dynamické sady a sady záznamů typ snímku.

Je založený na nule; hodnota vlastnosti AbsolutePosition základního objektu rozhraní DAO nastavení 0 znamená první záznam v sadě záznamů. Nastavení hodnoty větší než počet způsobí, že mají údaj vyplněný záznamy knihovny MFC k vyvolání výjimky. Můžete určit počet naplněných záznamy v sadě záznamů voláním `GetRecordCount` členskou funkci.

Pokud je aktuální záznam odstranit, není definována hodnota vlastnosti AbsolutePosition a MFC vyvolá výjimku, pokud se na ni odkazuje. Nové záznamy se přidají na konci sekvence.

> [!NOTE]
>  Tato vlastnost není určena pro použití jako číslo náhradní záznam. Záložky jsou stále doporučený způsob uchování a vrácení k dané pozici a jediný způsob, jak umístit aktuální záznam napříč všemi typy objektů sady záznamů, které podporují záložky. Konkrétně se změny pozice daného záznamu při odstranění záznamů před. K dispozici je také žádnou záruku, že daný záznam budou mít stejné absolutní pozici, pokud sada záznamů se znovu vytvoří znovu vzhledem k tomu, že pokud není vytvořené pomocí příkazu SQL není zaručeno, že pořadí jednotlivých záznamů v rámci sady záznamů  **Řadit podle** klauzuli.

Související informace naleznete v tématu "AbsolutePosition vlastnost" v nápovědě k DAO.

##  <a name="setbookmark"></a>  CDaoRecordset::SetBookmark

Zavolejte tuto členskou funkci na pozici sady záznamů na záznam obsahující zadanou záložkou.

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) objekt, který obsahuje hodnotu záložku pro konkrétní záznam.

### <a name="remarks"></a>Poznámky

Při vytvoření nebo otevření objekt sady záznamů jednotlivých záznamů jeho už má jedinečný záložku. Záložka pro požadovaný aktuální záznam můžete načíst pomocí volání `GetBookmark` a ukládá hodnota, která má `COleVariant` objektu. Později mohli vrátit k tomuto záznamu voláním `SetBookmark` pomocí hodnoty uloženou záložku.

> [!NOTE]
>  Volání [Requery](#requery) změní DAO záložky.

Všimněte si, že pokud nejsou vytvoření sady záznamů ve formátu UNICODE, `COleVariant` objekt musí být explicitně deklarováno jako ANSI. To můžete udělat pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formu konstruktor s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na `VT_BSTRT`.

Související informace naleznete v tématech "Záložku Vlastnosti" a Bookmarkable"v nápovědě k DAO.

##  <a name="setcachesize"></a>  CDaoRecordset::SetCacheSize

Voláním této členské funkce, chcete-li nastavit počet záznamů do mezipaměti.

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parametry

*lSize*<br/>
Určuje počet záznamů. Typická hodnota je 100. Hodnota 0 vypne ukládání do mezipaměti. Nastavení musí být mezi 5 a 1 200 záznamů. Mezipaměť může použít značné množství paměti.

### <a name="remarks"></a>Poznámky

Mezipaměť je mezera v místní paměti, která obsahuje data naposled načetli ze serveru, v případě, že data požádat znovu, když je spuštěná aplikace. Ukládání dat zlepšuje výkon aplikace, která načte data ze vzdáleného serveru prostřednictvím objektů dynamické sady záznamů. Pokud se požaduje data, databázový stroj Microsoft Jet mezipaměti požadovaných dat nejprve zkontroluje místo načítání ze serveru, který trvá déle. Data, která nepochází ze zdroje dat ODBC není uložená v mezipaměti.

Všechny zdroje dat ODBC, jako je například připojené tabulky, můžete mít místní mezipaměti. Pokud chcete vytvořit mezipaměť, otevřete objekt sady záznamů ze zdroje vzdáleným datům, volání `SetCacheSize` a `SetCacheStart` členské funkce a poté zavolejte `FillCache` členská funkce nebo krokovat na záznamy pomocí jedné z operací přesunutí. *LSize* parametr `SetCacheSize` členská funkce může být založen na počet záznamů, které aplikace můžou najednou pracovat. Například pokud používáte sadu záznamů jako zdroj dat zobrazený na obrazovce, můžete předat `SetCacheSize` *lSize* parametr jako 20 až 20 záznamů najednou zobrazit.

Související informace naleznete v tématu "CacheSize CacheStart vlastnosti" v nápovědě k DAO.

##  <a name="setcachestart"></a>  CDaoRecordset::SetCacheStart

Voláním této členské funkce k určení záložku první záznam v sadě záznamů ukládat do mezipaměti.

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
A [COleVariant](../../mfc/reference/colevariant-class.md) záložku první záznam, který určuje v sadě záznamů ukládat do mezipaměti.

### <a name="remarks"></a>Poznámky

Můžete použít hodnotu záložku u všech záznamů pro *varBookmark* parametr `SetCacheStart` členskou funkci. Vytvořit záznam, který chcete spustit mezipaměti s aktuálním záznamem, vytvořit záložku pro tento záznam pomocí [SetBookmark](#setbookmark)a předat jako parametr pro hodnotu záložku `SetCacheStart` členskou funkci.

Databázový stroj Microsoft Jet vyžádá záznamy rozsahu mezipaměti z mezipaměti a vyžádá záznamů mimo rozsah mezipaměti ze serveru.

Záznamy načíst z mezipaměti neodrážejí změny provedené současně na zdroj dat jinými uživateli.

Chcete-li vynutit aktualizaci všech dat uložených v mezipaměti, předejte *lSize* parametr `SetCacheSize` jako 0, volání `SetCacheSize` znovu s velikostí mezipaměti jste původně požadovali a poté zavolejte `FillCache` členskou funkci.

Všimněte si, že pokud nejsou vytvoření sady záznamů ve formátu UNICODE, `COleVariant` objekt musí být explicitně deklarováno jako ANSI. To můžete udělat pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formu konstruktor s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na `VT_BSTRT`.

Související informace naleznete v tématu CacheSize, CacheStart vlastnosti"v nápovědě k DAO.

##  <a name="setcurrentindex"></a>  CDaoRecordset::SetCurrentIndex

Voláním této členské funkce nastavit v sadě záznamů typ tabulky indexu.

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ukazatel obsahující název indexu, která se má nastavit.

### <a name="remarks"></a>Poznámky

Záznamy v základní tabulky nejsou uložené v libovolném pořadí. Index nastavení změní pořadí záznamů vrácených z databáze, ale nemá vliv na pořadí, ve kterém se záznamy ukládají. Zadaný index musí již být definován. Pokud se pokusíte použít objekt index, který ještě neexistuje, nebo index není nastavená, pokud zavoláte [Seek](#seek), vyvolá výjimku, knihovny MFC.

Můžete vytvořit nový index pro tabulku voláním [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) a připojení nového indexu kolekce indexů základní tabledef voláním [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append), a pak znovu otevřít sadu záznamů.

Určená jenom pro indexy, které jsou definovány pro základní tabledef lze provést řazení záznamů vrácených ze sady záznamů typ tabulky. Záznamy v nějaké jiné pořadí řazení, můžete otevřít typ dynamická sada nebo sada záznamů typu snímek pomocí SQL **ORDERBY** klauzule uložené v [CDaoRecordset::m_strSort](#m_strsort).

Související informace naleznete v tématu "Objekt indexu" a definice "aktuální index" v nápovědě rozhraní DAO.

##  <a name="setfielddirty"></a>  CDaoRecordset::SetFieldDirty

Voláním této členské funkce označit, že pole datového člena sady záznamů jako změněné nebo jako beze změny.

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Obsahuje adresu pole datového člena v sadě záznamů nebo hodnota NULL. Pokud má hodnotu NULL, se označí všechny datové členy v sadě záznamů. (C++ NULL není stejná jako hodnota Null v, řečeno terminologií databáze, což znamená, že "s žádnou hodnotu.")

*bDirty*<br/>
TRUE, pokud je datový člen pole bude označen jako "nesprávné" (změněné). V opačném případě hodnotu FALSE, pokud je datový člen pole bude označen jako "clean" (beze změny).

### <a name="remarks"></a>Poznámky

Označení polí jako beze změny zajistí, že neaktualizuje pole.

Značky framework změnit pole datové členy zajistit, že se budou zapisovat do záznamu ve zdroji dat exchange (DFX) mechanismem DAO pole záznamu. Změna hodnoty pole obecně nastaví pole změny automaticky, tedy zřídka bude nutné zavolat `SetFieldDirty` sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to, jaká hodnota je v datech pole člen. DFX mechanismus využívá i použití PSEUDONULL. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud mechanismus dvojité ukládání do vyrovnávací paměti není používáno, pak změníte hodnotu pole nenastaví automaticky pole označeni jako neaktualizovaní. V takovém případě bude nutné explicitně nastavit pole jako neaktualizovaní. Příznak součástí [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tuto kontrolu automatického pole.

> [!NOTE]
>  Voláním této členské funkce, až po jste volali [upravit](#edit) nebo [AddNew](#addnew).

Použití hodnoty NULL pro první argument funkce platit pro všechny funkce `outputColumn` pole, nikoli **param** pole v `CDaoFieldExchange`. Například volání

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

Nastaví pouze `outputColumn` pole na hodnotu NULL; **param** pole zůstanou beze změn.

Pro práci na **param**, je nutné zadat skutečnou adresu jednotlivých **param** chcete pracovat, jako například:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

To znamená, že nemůžete nastavit všechny **param** pole na hodnotu NULL, jako u `outputColumn` pole.

`SetFieldDirty` se implementuje pomocí `DoFieldExchange`.

##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull

Voláním této členské funkce označit, že pole datového člena sady záznamů jako Null (konkrétně s žádná hodnota) nebo jinou hodnotu než Null.

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
Obsahuje adresu pole datového člena v sadě záznamů nebo hodnota NULL. Pokud má hodnotu NULL, se označí všechny datové členy v sadě záznamů. (C++ NULL není stejná jako hodnota Null v, řečeno terminologií databáze, což znamená, že "s žádnou hodnotu.")

*bNull*<br/>
Nenulové, pokud je datový člen pole bude označen jako s žádné hodnoty (Null). Jinak 0, pokud je datový člen pole bude označen jako jinou hodnotu než Null.

### <a name="remarks"></a>Poznámky

`SetFieldNull` se používá pro pole v vázaný `DoFieldExchange` mechanismus.

Při přidání nového záznamu do sady záznamů, všechny datové členy jsou zpočátku nastaven na hodnotu Null a označen jako "nesprávné" (změněné). Při načítání záznam ze zdroje dat, její sloupce již mají hodnoty nebo hodnotu Null. Pokud není vhodné vytvořit pole hodnotu Null, [cdaoexception –](../../mfc/reference/cdaoexception-class.md) je vyvolána výjimka.

Pokud použijete mechanismus dvojité ukládání do vyrovnávací paměti, například pokud budete chtít konkrétně určit pole z aktuální záznam tak, že hodnoty, volejte nemusí `SetFieldNull` s *bNull* nastavena na hodnotu TRUE, označit ji jako hodnotu Null. Pokud byla dříve označená pole hodnotu Null a teď chcete jí hodnotu, jednoduše nastavte jej na novou hodnotu. Nemáte, můžete odebrat příznak Null s `SetFieldNull`. Chcete-li zjistit, jestli pole může mít hodnotu Null, zavolejte [IsFieldNullable](#isfieldnullable).

Pokud nepoužíváte mechanismus dvojité ukládání do vyrovnávací paměti, pak změníte hodnotu pole nenastaví automaticky pole jako změny a jinou hodnotu než Null. Konkrétně je nutné nastavit pole změny a jinou hodnotu než Null. Příznak součástí [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tuto kontrolu automatického pole.

DFX mechanismus využívá užívání PSEUDONULL. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
>  Voláním této členské funkce, až po jste volali [upravit](#edit) nebo [AddNew](#addnew).

Použití NULL pro první argument funkce se vztahují pouze k funkci `outputColumn` pole, nikoli **param** pole v `CDaoFieldExchange`. Například volání

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

Nastaví pouze `outputColumn` pole na hodnotu NULL; **param** pole zůstanou beze změn.

##  <a name="setfieldvalue"></a>  CDaoRecordset::SetFieldValue

Voláním této členské funkce, chcete-li nastavit hodnotu pole, pořadí nebo můžete změnit hodnotu řetězce.

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec obsahující název pole.

*varValue*<br/>
Odkaz na [COleVariant](../../mfc/reference/colevariant-class.md) objekt obsahující hodnoty v polích.

*nIndex*<br/>
Celé číslo představující pořadí pole v kolekci polí sady záznamů (počítáno od nuly).

*lpszValue*<br/>
Ukazatel na řetězec obsahující hodnoty v polích.

### <a name="remarks"></a>Poznámky

Použití `SetFieldValue` a [getfieldvalue –](#getfieldvalue) dynamicky vytvořit vazbu pole v době běhu místo staticky vazeb sloupců pomocí [DoFieldExchange](#dofieldexchange) mechanismus.

Všimněte si, že pokud nejsou vytvoření sady záznamů ve formátu UNICODE, je nutné použít určitou formu `SetFieldValue` , který neobsahuje `COleVariant` parametr, nebo `COleVariant` objekt musí být explicitně deklarováno jako ANSI. To můžete udělat pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formu konstruktor s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na `VT_BSTRT`.

Související informace naleznete v tématech "Pole objektu" a "Hodnota vlastnosti" v nápovědě k DAO.

##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull

Voláním této členské funkce má být nastavena na hodnotu Null.

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index pole v sadě záznamů pro vyhledávání podle index založený na nule.

*lpszName*<br/>
Název pole v sadě záznamů pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

C++ NULL není stejná jako hodnota Null, tzn., v, řečeno terminologií databáze, "s žádnou hodnotu."

Související informace naleznete v tématech "Pole objektu" a "Hodnota vlastnosti" v nápovědě k DAO.

##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode

Voláním této členské funkce nastavte typ uzamčení záznamů.

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parametry

*bPessimistic*<br/>
Příznak, který označuje typ uzamčení.

### <a name="remarks"></a>Poznámky

Když pesimistické zamykání v důsledku toho stránka 2K obsahující záznam, který upravujete je uzamčeno ihned poté, co zavoláte `Edit` členskou funkci. Na stránce se odemkne při volání `Update` nebo `Close` členská funkce nebo kteroukoli z operací přesunutí nebo najít.

Při optimistického zamykání je v platnosti, stránka 2K obsahující záznam je uzamčen, pouze když probíhá aktualizace záznamu `Update` členskou funkci.

Pokud stránka je uzamčen, žádný jiný uživatel může upravovat záznamy na stejné stránce. Při volání `SetLockingMode` a předejte nenulovou hodnotu a jiný uživatel již má stránka uzamčen, dojde k výjimce při volání `Edit`. Ostatní uživatelé mohou číst data z uzamčených stránek.

Při volání `SetLockingMode` s nulovou hodnotou a pozdější volání `Update` uzamčeném stránce jiným uživatelem, dojde k výjimce. Chcete-li zobrazit změny provedené jinými uživateli k záznamu (a ztratit změny), zavolejte `SetBookmark` členskou funkci s hodnotou záložku aktuální záznam.

Při práci se zdroji dat rozhraní ODBC, je vždy optimistické režim uzamčení.

##  <a name="setparamvalue"></a>  CDaoRecordset::SetParamValue

Voláním této členské funkce pro nastavení hodnoty parametru v sadě záznamů v době běhu.

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Číselné pozice parametru v kolekci parametrů querydef.

*var*<br/>
Hodnota pro nastavení; viz poznámky.

*lpszName*<br/>
Název parametru, jehož hodnota, kterou chcete nastavit.

### <a name="remarks"></a>Poznámky

Parametr musí již byly vytvořeny jako součást řetězce SQL sady záznamů. Tento parametr můžete přistupovat pomocí názvu nebo podle jeho index pozice v kolekci.

Zadejte hodnotu pro nastavení jako `COleVariant` objektu. Informace o nastavení požadovanou hodnotu a typ v vaše `COleVariant` objektu, naleznete v tématu třídy [COleVariant](../../mfc/reference/colevariant-class.md). Všimněte si, že pokud nejsou vytvoření sady záznamů ve formátu UNICODE, `COleVariant` objekt musí být explicitně deklarováno jako ANSI. To můžete udělat pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)**  formu konstruktor s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na `VT_BSTRT`.

##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull

Voláním této členské funkce nastavit parametr na hodnotu Null.

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index pole v sadě záznamů pro vyhledávání podle index založený na nule.

*lpszName*<br/>
Název pole v sadě záznamů pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

C++ NULL není stejná jako hodnota Null, tzn., v, řečeno terminologií databáze, "s žádnou hodnotu."

##  <a name="setpercentposition"></a>  CDaoRecordset::SetPercentPosition

Voláním této členské funkce, chcete-li nastavit hodnotu, která změní Přibližná poloha aktuální záznam v objektu sady záznamů podle procentuální podíl záznamů v sadě záznamů.

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parametry

*fPosition*<br/>
Číslo mezi 0 a 100.

### <a name="remarks"></a>Poznámky

Při práci s typem dynamická sada nebo sada záznamů typu snímek, přechodem na poslední záznam před voláním nejprve naplnit sady záznamů `SetPercentPosition`. Při volání `SetPercentPosition` před plně naplnění sady záznamů, množství přesun je relativní vzhledem k počtu záznamů získat přístup, jak je uvedeno hodnotou [getrecordcount –](#getrecordcount). Můžete přesunout na poslední záznam volání `MoveLast`.

Jakmile zavoláte `SetPercentPosition`, stane aktuální záznam přibližné pozici odpovídající této hodnotě.

> [!NOTE]
>  Volání `SetPercentPosition` přesunout aktuální záznam konkrétní záznam v sadě záznamů se nedoporučuje. Volání [SetBookmark](#setbookmark) členské funkce místo.

Související informace naleznete v tématu "PercentPosition vlastnost" v nápovědě k DAO.

##  <a name="update"></a>  CDaoRecordset::Update

Voláním této členské funkce po volání `AddNew` nebo `Edit` členskou funkci.

```
virtual void Update();
```

### <a name="remarks"></a>Poznámky

Toto volání je vyžadované k dokončení `AddNew` nebo `Edit` operace.

Obě `AddNew` a `Edit` připravit vyrovnávací paměť úprav ve kterém je umístí údaje přidané nebo upravené pro ukládání do zdroje dat. `Update` uloží data. Jsou aktualizovány pouze pole označeno nebo zjistil jako změnit.

Pokud je zdroj dat podporuje transakce, lze provádět `Update` volání (a odpovídající `AddNew` nebo `Edit` volání) součástí transakce.

> [!CAUTION]
> Při volání `Update` bez předchozího volání `AddNew` nebo `Edit`, `Update` vyvolá `CDaoException`. Při volání `AddNew` nebo `Edit`, je nutné volat `Update` před voláním [MoveNext](#movenext) nebo zavřete připojení ke zdroji dat nebo sady záznamů. Jinak vaše změny se ztratí bez oznámení.

Pokud objekt sady záznamů je uzamčené pessimistically v prostředí, zůstane uzamčen od okamžiku záznamu `Edit` slouží, až do dokončení aktualizace. Pokud sada záznamů optimisticky je uzamčen, záznam je uzamčen a ve srovnání s předem upravený záznam těsně před plánovaným je aktualizována v databázi. Pokud záznam byl změněn, protože jste volali `Edit`, `Update` vyvolá výjimku, operace se nezdaří a knihovny MFC. Můžete změnit režim uzamčení s `SetLockingMode`.

> [!NOTE]
> Se používá optimistické uzamykání vždy o formátech externí databáze, jako je například rozhraní ODBC a jazyku Instalovatelné ISAM.

Související informace naleznete v tématech "Metodu AddNew", "CancelUpdate metoda", "Metodu Delete", "LastModified vlastnost", "Metodu aktualizace" a "EditMode vlastnost" v nápovědě k DAO.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
