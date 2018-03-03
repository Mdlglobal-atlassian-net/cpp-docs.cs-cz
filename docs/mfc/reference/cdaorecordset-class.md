---
title: "CDaoRecordset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e50e83a2d52567d30901cea33cfccec3e236fe67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaorecordset-class"></a>CDaoRecordset – třída
Představuje sadu záznamy ze zdroje dat vybraná.  
  
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
|[CDaoRecordset::AddNew](#addnew)|Připraví pro přidávání nového záznamu. Volání [aktualizace](#update) dokončit přidání.|  
|[CDaoRecordset::CanAppend](#canappend)|Vrátí nenulové hodnoty, pokud nové záznamy lze přidat do sady záznamů prostřednictvím [AddNew](#addnew) – členská funkce.|  
|[CDaoRecordset::CanBookmark](#canbookmark)|Vrátí nenulové hodnoty, pokud sada záznamu podporuje záložky.|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|Zruší všechny čekající aktualizace z důvodu [upravit](#edit) nebo [AddNew](#addnew) operaci.|  
|[CDaoRecordset::CanRestart](#canrestart)|Vrátí nenulovou Pokud [Requery](#requery) lze volat pro spusťte znovu dotaz sady záznamů.|  
|[CDaoRecordset::CanScroll](#canscroll)|Vrátí nenulové hodnoty, pokud lze procházet záznamů.|  
|[CDaoRecordset::CanTransact](#cantransact)|Vrátí nenulové hodnoty, pokud je zdroj dat podporuje transakce.|  
|[CDaoRecordset::CanUpdate](#canupdate)|Vrátí nenulové hodnoty, pokud lze aktualizovat sadu záznamů (můžete přidat, aktualizaci nebo odstranění záznamů).|  
|[CDaoRecordset::Close](#close)|Zavře sady záznamů.|  
|[CDaoRecordset::Delete](#delete)|Odstraní záznam na aktuální záznam ze sady záznamů. Po odstranění se musí explicitně přejít k jinému záznamu.|  
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|Volá se pro výměnu dat (v obou směrech) mezi pole datových členů sady záznamů a odpovídající záznam na datovém zdroji. Implementuje rozhraní DAO záznam pole exchange (DFX).|  
|[CDaoRecordset::Edit](#edit)|Připraví změny záznam na aktuální záznam. Volání **aktualizace** dokončete úpravu.|  
|[CDaoRecordset::FillCache](#fillcache)|Všechny výplněmi nebo součástí místní mezipaměti pro objekt sady záznamů, která obsahuje data ze zdroje dat ODBC.|  
|[CDaoRecordset::Find](#find)|Vyhledá první, další předchozí nebo poslední umístění konkrétní řetězec v dynamické sady záznamů, splňující zadaná kritéria a díky které záznam na aktuální záznam.|  
|[CDaoRecordset::FindFirst](#findfirst)|Vyhledá první záznam v dynamické sady nebo sadu záznamů typu snímek splňující zadaná kritéria a díky které záznam na aktuální záznam.|  
|[CDaoRecordset::FindLast](#findlast)|Vyhledá poslední záznam v dynamické sady nebo sadu záznamů typu snímek splňující zadaná kritéria a díky které záznam na aktuální záznam.|  
|[CDaoRecordset::FindNext](#findnext)|Vyhledat další záznam v dynamické sady nebo sadu záznamů typu snímek splňující zadaná kritéria a díky které záznam na aktuální záznam.|  
|[CDaoRecordset::FindPrev](#findprev)|Vyhledá předchozího záznamu v dynamické sady nebo sadu záznamů typu snímek splňující zadaná kritéria a díky které záznam na aktuální záznam.|  
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|Vrátí záznam počet aktuální záznam. objekt sady záznamů.|  
|[CDaoRecordset::GetBookmark](#getbookmark)|Vrátí hodnotu, která představuje záložku na záznam.|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|Vrátí hodnotu, která určuje počet záznamů v dynamické sady záznamů, který obsahuje data do místní mezipaměti ze zdroje dat ODBC.|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|Vrátí hodnotu, která určuje záložku na první záznam v sadě záznamů do mezipaměti.|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|Vrátí `CString` nedávno obsahující název indexu použít na indexované, typ tabulky `CDaoRecordset`.|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|Vrátí datum a čas základní tabulce základní `CDaoRecordset` objekt byl vytvořen|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny provedené v základní tabulce základní návrh `CDaoRecordset` objektu.|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|Vrací název zdroje dat výchozí.|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|Volá se získat výchozí řetězec SQL k provedení.|  
|[CDaoRecordset::GetEditMode](#geteditmode)|Vrátí hodnotu, která označuje stav úprav pro aktuální záznam.|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v sadě záznamů.|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|Vrátí určité informace o pole v sadě záznamů.|  
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|Načte počet indexů v tabulce základní sady záznamů.|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|Vrátí různé typy informací o indexu.|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Použít k určení nejvíc nedávno přidané nebo aktualizované záznamu.|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|Vrátí hodnotu, která určuje typ uzamčení, který je v platnosti během úprav.|  
|[CDaoRecordset::GetName](#getname)|Vrátí `CString` obsahující název sady záznamů.|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|Načte aktuální hodnotu zadaný parametr uložené v základní objekt DAOParameter.|  
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|Vrátí pozici na aktuální záznam v procentech celkový počet záznamů.|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|Vrátí počet záznamů, které jsou přístupné v objekt sady záznamů.|  
|[CDaoRecordset::GetSQL](#getsql)|Získá řetězec SQL, které jsou použity k výběru záznamy pro sady záznamů.|  
|[CDaoRecordset::GetType](#gettype)|Voláno k určení typu sady záznamů: typ tabulky, dynamické sady nebo typu snímek.|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|Vrátí `CString` obsahující hodnotu, která ověří data, protože je zadán do pole.|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|Načte text, který se zobrazí, pokud není splněna pravidla ověřování.|  
|[CDaoRecordset::IsBOF](#isbof)|Vrátí nenulové hodnoty, pokud sada záznamů obsahuje byl umístěn před první záznam. Neexistuje aktuální záznam.|  
|[CDaoRecordset::IsDeleted](#isdeleted)|Vrátí nenulové hodnoty, pokud sada záznamů umístěna na odstraněného záznamu.|  
|[CDaoRecordset::IsEOF](#iseof)|Vrátí nenulové hodnoty, pokud sada záznamů obsahuje byl umístěn za poslední záznam. Neexistuje aktuální záznam.|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|Vrátí nenulovou došlo ke změně v zadaném poli záznam na aktuální záznam.|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|Vrátí nenulové hodnoty, pokud v zadaném poli záznam na aktuální záznam má hodnotu Null (nutnosti žádná hodnota).|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|Vrátí nenulové hodnoty, pokud v zadaném poli záznam na aktuální záznam lze nastavit na hodnotu Null (nutnosti žádná hodnota).|  
|[CDaoRecordset::IsOpen](#isopen)|Vrátí nenulovou Pokud [otevřete](#open) byla volána dříve.|  
|[CDaoRecordset::Move](#move)|Umisťuje sadu záznamů na zadaný počet záznamů z aktuální záznam v obou směrech.|  
|[CDaoRecordset::MoveFirst](#movefirst)|Umisťuje záznam na aktuální záznam na první záznam v sadě záznamů.|  
|[CDaoRecordset::MoveLast](#movelast)|Umisťuje záznam na aktuální záznam na poslední záznam v sadě záznamů.|  
|[CDaoRecordset::MoveNext](#movenext)|Umisťuje záznam na aktuální záznam na další záznam v sadě záznamů.|  
|[CDaoRecordset::MovePrev](#moveprev)|Umisťuje záznam na aktuální záznam na předchozího záznamu v sadě záznamů.|  
|[CDaoRecordset::Open](#open)|Vytvoří nové sady záznamů z tabulek, dynamická sada nebo snímek.|  
|[CDaoRecordset::Requery](#requery)|Spustí dotaz sady záznamů znovu a aktualizujte vybrané záznamy.|  
|[CDaoRecordset::Seek](#seek)|Vyhledá záznam v objektu indexované typ tabulky záznamů splňující zadaná kritéria pro aktuální index a díky které záznam na aktuální záznam.|  
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|Nastaví počet záznam aktuální záznam. objekt sady záznamů.|  
|[CDaoRecordset::SetBookmark](#setbookmark)|Umisťuje sadu záznamů na záznam obsahující zadanou záložkou.|  
|[CDaoRecordset::SetCacheSize](#setcachesize)|Nastaví hodnotu, která určuje počet záznamů v dynamické sady záznamů, který obsahuje data do místní mezipaměti ze zdroje dat ODBC.|  
|[CDaoRecordset::SetCacheStart](#setcachestart)|Nastaví hodnotu, která určuje záložku na první záznam v sadě záznamů do mezipaměti.|  
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|Volá se nastavit indexu na sadu záznamů typu tabulky.|  
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|Označí aktuální záznam v zadaném poli jako změnit.|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuálním záznamu na hodnotu Null (nutnosti žádná hodnota).|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|Nastaví hodnotu pole v sadě záznamů.|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|Nastaví hodnotu pole v sadě záznamů na hodnotu Null. (žádná hodnota s).|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|Nastaví hodnotu, která určuje typ zámek k tomu během úprav.|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|Nastaví aktuální hodnotu zadaný parametr uložené v základní objekt DAOParameter|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|Nastaví aktuální hodnotu zadaného parametru na hodnotu Null (nutnosti žádná hodnota).|  
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|Nastavuje pozici na aktuální záznam do umístění odpovídající procento celkový počet záznamů v sadě záznamů.|  
|[CDaoRecordset::Update](#update)|Dokončení `AddNew` nebo **upravit** operaci uložením nových nebo upravených dat na datovém zdroji.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoRecordset::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Obsahuje příznak, který udává, zda pole jsou automaticky označeny jako změnit.|  
|[CDaoRecordset::m_nFields](#m_nfields)|Obsahuje počet pole datových členů ve třídě sady záznamů a počet sloupců vybraných funkcí sady záznamů z datového zdroje.|  
|[CDaoRecordset::m_nParams](#m_nparams)|Obsahuje počet parametry datových členů v třídě sady záznamů – počet parametrů předaných s dotaz sady záznamů|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|Ukazatel na základní objekt sady záznamů rozhraní DAO.|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|Nastavit zdrojové databáze pro tento výsledek. Obsahuje odkazy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.|  
|[CDaoRecordset::m_strFilter](#m_strfilter)|Obsahuje řetězec použitý k vytvoření SQL **kde** příkaz.|  
|[CDaoRecordset::m_strSort](#m_strsort)|Obsahuje řetězec použitý k vytvoření SQL **Order** příkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Označuje jako "sady záznamů," `CDaoRecordset` objekty jsou k dispozici v následujících tří podob:  
  
-   Sady záznamů typu tabulky představují základní tabulku, která vám pomůže zkontrolovat, přidat, změnit nebo odstranit záznamy z jedné tabulky databáze.  
  
-   Dynamické sady záznamů jsou výsledkem dotazu, který může mít aktualizovatelné záznamy. Tyto sady záznamů jsou sady záznamů, které vám pomůže zkontrolovat, přidat, změnit nebo odstranit záznamy ze základní databázové tabulky nebo tabulek. Dynamické sady záznamů můžou obsahovat pole z jedné nebo více tabulek v databázi.  
  
-   Sady záznamů typu snímek se statická kopie sady záznamů, které můžete použít k vyhledání dat nebo generování sestav. Tyto sady záznamů můžou obsahovat pole z jedné nebo více tabulek v databázi, ale nelze aktualizovat.  
  
 Každý formulář sada záznamů představuje sadu záznamů pevné v době, kdy je otevření sady záznamů. Pokud se posunete na záznam v sadě záznamů typu tabulky nebo sadě záznamů, odráží změny provedené v záznamu po otevření sady záznamů, pomocí jiných uživatelů nebo pomocí jiné sady záznamů ve vaší aplikaci. (Nelze aktualizovat sadu záznamů typu snímek.) Můžete použít `CDaoRecordset` přímo nebo odvodit třídu specifické pro aplikaci záznamů z `CDaoRecordset`. Pak můžete:  
  
-   Procházet záznamy.  
  
-   Nastavte indexu a rychle vyhledat záznamů pomocí [Seek](#seek) (pouze sady typ tabulky záznamů).  
  
-   Hledání záznamů na základě porovnání řetězce: "<","\<=", "=", "> =", nebo ">" (dynamické sady a sady záznamů typu snímek).  
  
-   Aktualizovat záznamy a určete režim uzamčení (s výjimkou sady záznamů typu snímek).  
  
-   Sada záznamů omezit záznamy, které vybere z dostupných ve zdroji dat filtrujte.  
  
-   Seřadí sadu záznamů.  
  
-   Parametrizace sady záznamů, chcete-li přizpůsobit svůj výběr s informacemi o není známý až při spuštění.  
  
 Třída `CDaoRecordset` poskytuje podobná třídy rozhraní `CRecordset`. Hlavní rozdíl je v této třídě `CDaoRecordset` získá přístup k datům prostřednictvím objekt DAO (Data Access) podle OLE. Třída `CRecordset` přistupuje databázového systému prostřednictvím připojení ODBC (Open Database) a ovladač ODBC pro tento databázového systému.  
  
> [!NOTE]
>  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Můžete i nadále přístup ke zdrojům dat ODBC s třídy DAO; třídy DAO obecně nabízí vynikající funkcí, protože jsou specifické pro databázový stroj Microsoft Jet.  
  
 Můžete buď používat `CDaoRecordset` přímo nebo odvození třídy z `CDaoRecordset`. Pokud chcete používat třídu sady záznamů v obou případech, otevřete databázi a vytvořte objekt sady záznamů, předávání konstruktoru ukazatel na vaše `CDaoDatabase` objektu. Můžete také vytvořit `CDaoRecordset` objektu a nechat MFC vytvoření dočasného `CDaoDatabase` objektu za vás. Potom zavolejte sady záznamů [otevřete](#open) – členská funkce, určující, zda je objekt na sadu záznamů typu tabulky, sadě záznamů nebo sadu záznamů typu snímek. Volání metody **otevřete** vybere data z databáze a načte na první záznam.  
  
 Pomocí objektu členských funkcí a data členy procházet záznamů a pracovat s nimi. K dispozici operace závisí na tom, jestli je objekt sadu záznamů typu tabulky, sadě záznamů nebo sadu záznamů typu snímek a zda je možné aktualizovat nebo jen pro čtení – to závisí na možnosti databáze nebo připojení ODBC (Open Database) zdroj dat. K aktualizaci záznamů, které může mít změnily nebo přibyly od **otevřete** volání, volání objektu [Requery –](#requery) – členská funkce. Volání objektu **Zavřít** členské funkce a odstraňte objekt po dokončení s ním.  
  
 `CDaoRecordset`používá rozhraní DAO výměna pole záznamu (DFX) k čtení a aktualizaci polí záznamů prostřednictvím bezpečnost typů C++ členy vaší `CDaoRecordset` nebo `CDaoRecordset`-odvozené třídy. Můžete taky implementovat dynamické vazby sloupců v databázi bez použití DFX mechanismus pomocí [GetFieldValue](#getfieldvalue) a [SetFieldValue](#setfieldvalue).  
  
 Související informace naleznete v tématu "Objekt sady záznamů" v nápovědě rozhraní DAO.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="addnew"></a>CDaoRecordset::AddNew  
 Volání této funkce člen přidat nový záznam na sadu záznamů typu tabulky nebo dynamické sady.  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>Poznámky  
 Pole záznamu jsou původně hodnotu Null. (V terminologii databáze Null znamená "nutnosti žádná hodnota" a není stejný jako **NULL** v jazyce C++.) Pokud chcete provést operaci, musí volat [aktualizace](#update) – členská funkce. **Aktualizace** uloží změny do zdroje dat.  
  
> [!CAUTION]
>  Pokud upravíte záznam a posuňte se k jinému záznamu bez volání **aktualizace**, změny budou ztraceny bez upozornění.  
  
 Pokud přidáte záznam pro dynamické sady záznamů voláním [AddNew](#addnew), záznamu je viditelná v sadě záznamů a zahrnuty v podkladové tabulce, kde bude viditelná pro žádného nové `CDaoRecordset` objekty.  
  
 Pozice nový záznam, závisí na typu sady záznamů:  
  
-   V dynamické sady záznamů, které je vložen nový záznam není zaručena. Toto chování změnit s Microsoft Jet 3.0 z důvodů výkonu a souběžnosti. Pokud je vaším cílem je nastavit nově přidaný záznam na aktuální záznam, získat záložky poslední změny záznamu a přesunout na tuto záložku:  
  
 [!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   V sadě záznamů typu tabulky, pro který bylo zadané index jsou vráceny záznamy jejich správné zavedené v pořadí řazení. Pokud byl zadán žádný index, vrátí se nové záznamy na konci sady záznamů.  
  
 Záznam, který byl předtím, než jste použili aktuální `AddNew` pořád aktuální. Pokud chcete vytvořit nový záznam na aktuální a podporuje sadu záznamů záložky, volání [SetBookmark](#setbookmark) na záložku identifikovaný změněno nastavení vlastnosti podkladového objektu sady záznamů rozhraní DAO. Díky tomu jsou užitečné pro určení hodnota pro čítač (automatického přírůstku) polí v záznamu o přidání. Další informace najdete v tématu [GetLastModifiedBookmark](#getlastmodifiedbookmark).  
  
 Pokud databáze podporuje transakce, můžete provést vaší `AddNew` volání součástí transakce. Další informace o transakcích, najdete v části třídy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Všimněte si, že by měly volat [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) před voláním `AddNew`.  
  
 Není povolen pro volání `AddNew` pro sadu záznamů jejichž [otevřete](#open) – členská funkce nebyla volána. A `CDaoException` je vyvolána při volání `AddNew` pro sady záznamů, který nelze přidat. Můžete určit, zda je záznamů aktualizovatelné voláním [CanAppend](#canappend).  
  
 Značky framework změnit pole datových členů zajistit, že se budou zapisovat do záznamu ve zdroji dat pomocí mechanismus výměna pole záznamu exchange (DFX). Změna hodnoty pole obecně nastaví pole změny automaticky, takže bude málokdy potřeba volat [SetFieldDirty](#setfielddirty) sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to jaké hodnoty se pole datového člena. DFX mechanismus využívá použití **PSEUDO NULL**. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Pokud není používán mechanismus dvojité ukládání do vyrovnávací paměti, změna pole nenastaví automaticky pole jako neaktualizovaní. V takovém případě bude nutné explicitně nastavit pole nekonzistence. Příznak obsažené v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tato kontrola automatické pole.  
  
> [!NOTE]
>  Pokud jsou záznamy dvojitou vyrovnávací pamětí (to znamená, automatické pole Kontrola povolena), volání `CancelUpdate` obnoví členské proměnné na hodnoty měly před `AddNew` nebo **upravit** byla volána.  
  
 Související informace najdete v tématech "AddNew – metoda", "CancelUpdate metodu", "Změněno vlastnost" a "EditMode vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="canappend"></a>CDaoRecordset::CanAppend  
 Volání této funkce člen k určení, zda dříve otevřen sada záznamů umožňuje přidat nové záznamy voláním [AddNew](#addnew) – členská funkce.  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě, že sada záznamů umožňuje přidání nové záznamy; jinak 0. `CanAppend`Vrátí 0, pokud jste otevřeli sada záznamů jen pro čtení.  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "Připojit způsob" v nápovědě rozhraní DAO.  
  
##  <a name="canbookmark"></a>CDaoRecordset::CanBookmark  
 Volání této funkce člen k určení, zda dříve otevřen sada záznamů umožňuje jednotlivě označit záznamů pomocí záložky.  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamu podporuje záložky, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte sady záznamů pouze na základě Microsoft Jet databázové stroje tabulky, lze s výjimkou záložky na sady záznamů typu snímek označení dopředné sady posouvání záznamů. Další produkty databáze (externí zdroje dat ODBC) nemusí podporovat záložky.  
  
 Související informace naleznete v tématu "Bookmarkable vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="cancelupdate"></a>CDaoRecordset::CancelUpdate  
 `CancelUpdate` – Členská funkce zruší všechny čekající aktualizace z důvodu [upravit](#edit) nebo [AddNew](#addnew) operaci.  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>Poznámky  
 Například pokud aplikace zavolá **upravit** nebo `AddNew` – členská funkce a nebyla volána [aktualizace](#update), `CancelUpdate` zruší veškeré změny provedené po **upravit**nebo `AddNew` byla volána.  
  
> [!NOTE]
>  Pokud jsou záznamy dvojitou vyrovnávací pamětí (to znamená, automatické pole Kontrola povolena), volání `CancelUpdate` obnoví členské proměnné na hodnoty měly před `AddNew` nebo **upravit** byla volána.  
  
 Pokud není žádná **upravit** nebo `AddNew` operace čeká na vyřízení, `CancelUpdate` způsobí, že MFC vyvolá výjimku. Volání [GetEditMode](#geteditmode) – členská funkce k určení, pokud existuje čekající operace, které se dají zrušit.  
  
 Související informace naleznete v tématu "CancelUpdate způsob" v nápovědě rozhraní DAO.  
  
##  <a name="canrestart"></a>CDaoRecordset::CanRestart  
 Volání této funkce člen k určení, zda sada záznamů umožňuje restartování jeho dotaz (Chcete-li obnovit svoje záznamy o) voláním **Requery –** – členská funkce.  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty **Requery** lze volat pro sady záznamů dotaz spustit znovu, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Sady záznamů typu tabulky nepodporují **Requery –**.  
  
 Pokud **Requery –** je nepodporuje volání [Zavřít](#close) pak [otevřete](#open) aktualizovat data. Můžete volat **Requery** aktualizovat objekt sady záznamů zdrojové parametr dotazu po došlo ke změně hodnoty parametru.  
  
 Související informace naleznete v tématu "Nabízet možnost restartování vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="canscroll"></a>CDaoRecordset::CanScroll  
 Volání této funkce člen k určení, zda sada záznamů umožňuje posouvání.  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud lze procházet záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Když zavoláte [otevřete](#open) s **dbForwardOnly**, sady záznamů lze posunout pouze dopředu.  
  
 Související informace naleznete v tématu "Umístění aktuální záznam ukazatel s DAO" v nápovědě rozhraní DAO.  
  
##  <a name="cantransact"></a>CDaoRecordset::CanTransact  
 Volání této funkce člen k určení, zda sada záznamů umožňuje transakce.  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud na podkladový zdroj dat podporuje transakce, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "Transakce vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="canupdate"></a>CDaoRecordset::CanUpdate  
 Volání této funkce člen k určení, zda lze aktualizovat sadu záznamů.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud lze aktualizovat sadu záznamů (přidat, aktualizovat a odstranit záznamy), jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Sady záznamů může být jen pro čtení, pokud příslušný zdroj dat je jen pro čtení, nebo pokud jste zadali **dbReadOnly** pro `nOptions` když jste volali metodu [otevřete](#open) sady záznamů.  
  
 Související informace najdete v tématech "AddNew – metoda", "Upravit způsob", "Odstranit metodu", "Metoda aktualizace" a "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset  
 Vytvoří `CDaoRecordset` objektu.  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Obsahuje odkazy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objekt nebo hodnota **NULL**. Není-li **NULL** a `CDaoDatabase` objektu **otevřete** – členská funkce nebyla zavolána pro připojení ke zdroji dat, sada záznamů pokusí otevřít pro vás během vlastní [otevřete ](#open) volání. Pokud předáte **NULL**, `CDaoDatabase` je objekt vytvořený a připojením pomocí informace o zdroji dat jste zadali, pokud je odvozená třídu sady záznamů z `CDaoRecordset`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete buď používat `CDaoRecordset` přímo nebo odvodit třídu specifické pro aplikaci z `CDaoRecordset`. ClassWizard můžete použít k odvození třídy sady záznamů.  
  
> [!NOTE]
>  Pokud odvozujete `CDaoRecordset` třídy, vaše odvozené třídy musí zadat svůj vlastní konstruktor. V konstruktoru odvozené třídy, volat konstruktor `CDaoRecordset::CDaoRecordset`, předáním příslušné parametry společně.  
  
 Předat **NULL** do sady záznamů konstruktoru tak, aby měl `CDaoDatabase` objekt vytvořený a připojení pro vás automaticky. To je užitečné zástupce, který nevyžaduje můžete vytvořit a připojit `CDaoDatabase` objekt před vytvořením sady záznamů. Pokud `CDaoDatabase` objekt není otevřený, [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) objektu bude vytvořen také pro vás, který používá výchozí pracovní prostor. Další informace najdete v tématu [CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).  
  
##  <a name="close"></a>CDaoRecordset::Close  
 Zavřením `CDaoRecordset` objekt odstraní ji z kolekce otevřete sad záznamů v přidružené databáze.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Protože **Zavřít** nezničí `CDaoRecordset` objekt, můžete opakovaně použít objekt voláním **otevřete** na stejném zdroji dat nebo jinému zdroji dat.  
  
 Všechna nevyřízená [AddNew](#addnew) nebo [upravit](#edit) došlo ke zrušení příkazů a všechny čekající transakce jsou vráceny zpět. Pokud chcete zachovat čekající na vyřízení dodatky nebo úpravy, zavolejte [aktualizace](#update) před voláním **Zavřít** pro každou sadu záznamů.  
  
 Můžete volat **otevřete** znovu po volání **Zavřít**. Díky tomu můžete znovu použít objekt sady záznamů. Lepší alternativou je volat [Requery –](#requery), pokud je to možné.  
  
 Související informace naleznete v tématu "Zavřít způsob" v nápovědě rozhraní DAO.  
  
##  <a name="delete"></a>CDaoRecordset::Delete  
 Volání této funkce člena odstranit záznam na aktuální záznam otevřený objekt sady záznamů dynamické sady nebo typ tabulky.  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>Poznámky  
 Po úspěšné odstranění sady záznamů pole datových členů nastaveny na hodnotu Null a musí explicitně volání jednoho z členské funkce navigační sady záznamů ( [přesunout](#move), [Seek](#seek), [ SetBookmark –](#setbookmark)a tak dále) opustit odstraněného záznamu. Při odstraňování záznamů z sady záznamů, musí existovat aktuální záznam v sadě záznamů před voláním **odstranit**, jinak hodnota MFC vyvolá výjimku.  
  
 **Odstranit** odstraní záznam na aktuální záznam a je nepřístupný. I když se nedají upravit ani používat odstraněného záznamu, se dá pořád aktuální. Po přechodu na jiný záznam, ale nemůžete odstraněného záznamu aktuální znovu.  
  
> [!CAUTION]
>  Musí být aktualizovat sadu záznamů a musí být platný záznam v sadě záznamů při volání **odstranit**. Například, pokud jste odstranit záznam, ale není přejděte na nový záznam před voláním **odstranit** znovu **odstranit** vyvolá [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Záznam můžete obnovit, pokud používáte transakce a zavoláte [CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) – členská funkce. Pokud základní tabulka je primární v cascade odstranit relaci, odstraňování záznam na aktuální záznam může také odstranit jeden nebo více záznamů v cizí tabulce. Další informace najdete v tématu v definici "kaskádové odstranění" v nápovědě rozhraní DAO.  
  
 Na rozdíl od `AddNew` a **upravit**, volání **odstranit** nenásleduje volání **aktualizace**.  
  
 Související informace najdete v tématech "AddNew – metoda", "Upravit způsob", "Odstranit metodu", "Metoda aktualizace" a "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange  
 Volá rámec této – členská funkce pro automaticky výměnu dat mezi pole datových členů z objektu sady záznamů a na odpovídající sloupce ve zdroji dat na aktuální záznam.  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>Parametry  
 `pFX`  
 Obsahuje odkazy `CDaoFieldExchange` objektu. Rozhraní bude již nastavili tento objekt určit kontext pro operaci exchange pole.  
  
### <a name="remarks"></a>Poznámky  
 Parametry datových členů, se také váže, pokud existuje, zástupných symbolů parametrů v příkaz SQL pro výběr sady záznamů. Výměna pole dat, nazývá výměna pole záznamu rozhraní DAO (DFX), funguje v obou směrech: objekt sady záznamů pole datových členů na pole záznamu ve zdroji dat a ze záznamu ve zdroji dat do objektu sady záznamů. Pokud jsou dynamické vazby sloupců, není nutné k implementaci `DoFieldExchange`.  
  
 Jedinou akcí, je obvykle nutné provést při implementaci `DoFieldExchange` pro odvozené sady záznamů třídy je vytvoření třídy s ClassWizard a zadejte názvy a datové typy pole datových členů. Kód může také přidat do ClassWizard zapisuje zadat parametry datových členů. Pokud všechna pole jsou vázat dynamicky, tato funkce bude neaktivní, pokud nezadáte parametry datových členů.  
  
 Po deklarování vaší třídy odvozené sady záznamů s ClassWizard zapisuje Průvodce přepsání `DoFieldExchange` , která se podobá následujícímu příkladu:  
  
 [!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="edit"></a>CDaoRecordset::Edit  
 Volání této funkce člen k povolení změn na aktuální záznam.  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>Poznámky  
 Jakmile zavoláte **upravit** – členská funkce, změny provedené na aktuální záznam pole se zkopírují do vyrovnávací paměti kopírování. Když provedete požadované změny k záznamu, volání **aktualizace** uložte provedené změny. **Upravit** uloží hodnoty datových členů sady záznamů. Když zavoláte **upravit**, provést změny, potom volat **upravit** znovu, obnoví hodnoty záznamu se nacházely před první **upravit** volání.  
  
> [!CAUTION]
>  Pokud záznam upravit a poté proveďte všechny operace přesune na jiný záznam bez první volání **aktualizace**, změny budou ztraceny bez upozornění. Kromě toho pokud zavřete databáze nadřazeného nebo sady záznamů, budou zahozeny upravený záznam bez upozornění.  
  
 V některých případech můžete chtít aktualizovat sloupec tím, že s hodnotou Null (obsahující žádná data). Chcete-li to provést, volejte `SetFieldNull` s parametrem **TRUE** označit pole hodnotu Null; to také způsobí, že sloupec aktualizovat. Pokud chcete, aby pole, které chcete být napsané ke zdroji dat i v případě, že její hodnota nezměnilo, volejte `SetFieldDirty` s parametrem **TRUE**. Tento postup funguje i v případě, že pole měl hodnotu Null.  
  
 Značky framework změnit pole datových členů zajistit, že se budou zapisovat do záznamu ve zdroji dat pomocí mechanismus výměna pole záznamu exchange (DFX). Změna hodnoty pole obecně nastaví pole změny automaticky, takže bude málokdy potřeba volat [SetFieldDirty](#setfielddirty) sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to jaké hodnoty se pole datového člena. DFX mechanismus využívá použití **PSEUDO NULL**. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Pokud není používán mechanismus dvojité ukládání do vyrovnávací paměti, změna pole nenastaví automaticky pole jako neaktualizovaní. V takovém případě bude nutné explicitně nastavit pole nekonzistence. Příznak obsažené v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tato kontrola automatické pole.  
  
 Když objekt sady záznamů pessimistically uzamčené v prostředí s více uživateli, zůstane uzamčen od okamžiku záznamu **upravit** se používá, dokud nebude aktualizaci. Pokud sada záznamů je ideálním případě uzamčené, záznamu je uzamčena a porovnání s předem upravený záznam těsně před je aktualizována v databázi. Pokud záznam došlo ke změně vzhledem k tomu, že jste volali metodu **upravit**, **aktualizace** operace selže a MFC vyvolá výjimku. Můžete změnit režim uzamčení s `SetLockingMode`.  
  
> [!NOTE]
>  Optimistické zamykání se vždy na externí databáze formáty, například rozhraní ODBC a instalovat ISAM používá.  
  
 Záznam na aktuální záznam zůstane aktuální po zavolání metody **upravit**. K volání **upravit**, musí být aktuální záznam. Pokud není žádný aktuální záznam nebo sadu záznamů neodkazuje na Otevřít tabulku type nebo dynamické sady objekt sady záznamů, dojde k výjimce. Volání metody **upravit** způsobí, že `CDaoException` vyvolání za následujících podmínek:  
  
-   Neexistuje aktuální záznam.  
  
-   Databáze nebo sada záznamů je jen pro čtení.  
  
-   Žádné pole v záznamu je možné aktualizovat.  
  
-   Databáze nebo sada záznamů byl pro výhradní použití otevřen jiným uživatelem.  
  
-   Stránka, která obsahuje vaše záznam uzamknul jiný uživatel.  
  
 Pokud zdroj dat podporuje transakce, můžete provést **upravit** volání součástí transakce. Všimněte si, že by měly volat `CDaoWorkspace::BeginTrans` před voláním **upravit** a po otevření sady záznamů. Všimněte si, že volání `CDaoWorkspace::CommitTrans` nenahrazuje pro volání **aktualizace** k dokončení **upravit** operaci. Další informace o transakcích, najdete v části třídy `CDaoWorkspace`.  
  
 Související informace najdete v tématech "AddNew – metoda", "Upravit způsob", "Odstranit metodu", "Metoda aktualizace" a "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="fillcache"></a>CDaoRecordset::FillCache  
 Volání této funkce člena pro ukládání do mezipaměti zadaný počet záznamů ze sady záznamů.  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pSize`  
 Určuje počet řádků k vyplnění v mezipaměti. Pokud tento parametr vynecháte, hodnota je určen podle nastavení vlastnosti velikost paměti podkladového objektu DAO.  
  
 `pBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) zadání záložky. Mezipaměť je vyplněno od záznam označený tuto záložku. Pokud tento parametr vynecháte, mezipaměti vyplněno od záznam označený vlastnost CacheStart základní objekt DAO.  
  
### <a name="remarks"></a>Poznámky  
 Ukládání do mezipaměti zvyšuje výkon aplikace, která získává, nebo načte data ze vzdáleného serveru. Mezipaměť je místo v místní paměti, která obsahuje data naposledy načtených ze serveru za předpokladu, že data bude pravděpodobně vyžádána znovu když aplikace běží. Pokud se požaduje data, databázový stroj Microsoft Jet nejprve hledá v mezipaměti pro data místo načítání ze serveru, což trvá déle. Pomocí dat do mezipaměti na zdroje dat jiný ODBC nemá žádný vliv, protože data se neukládají v mezipaměti.  
  
 Místo čekání mezipaměti, aby byla vyplněna se záznamy podle jejich načtení, můžete explicitně vyplnit mezipaměti kdykoli voláním `FillCache` – členská funkce. To je rychlejší způsob k vyplnění mezipaměti, protože `FillCache` načte několik záznamů najednou namísto postupně. Například když se zobrazí každý screenful záznamů, můžete mít volání aplikace `FillCache` načíst další screenful záznamů.  
  
 Všechny databáze ODBC přístup s objekty sady záznamů může mít místní mezipaměti. Chcete-li vytvořit mezipaměť, otevřete objekt sady záznamů z vzdálený zdroj dat a pak zavolají `SetCacheSize` a `SetCacheStart` členské funkce sady záznamů. Pokud `lSize` a *lBookmark* vytvoření rozsah, který je mimo rozsah určený částečně nebo zcela `SetCacheSize` a `SetCacheStart`, část sada záznamů mimo tento rozsah je ignorován a není načtena do mezipaměti. Pokud `FillCache` požadavky více záznamů, než zůstat v vzdálený zdroj dat, jsou vyvolány jenom zbývající záznamy a nedojde k výjimce.  
  
 Zaznamenává načítat z mezipaměti nereflektuje změny provedené současně ke zdrojovým datům jiných uživatelů.  
  
 `FillCache`načte pouze záznamy ještě není v mezipaměti. Chcete-li vynutit aktualizaci všech dat uložených v mezipaměti, volejte `SetCacheSize` – členská funkce s `lSize` parametr rovná 0, volání `SetCacheSize` znovu s `lSize` parametr rovná velikosti mezipaměti jste původně požádal a pak zavolají `FillCache`.  
  
 Související informace naleznete v tématu "FillCache způsob" v nápovědě rozhraní DAO.  
  
##  <a name="find"></a>CDaoRecordset::Find  
 Volání této funkce člen zjistit konkrétní řetězec v sadě záznamů typu dynamická sada nebo snímek pomocí operátoru porovnání.  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parametry  
 *lFindType*  
 Hodnota, která určuje typ operace hledání požadovaných. Možné hodnoty jsou:  
  
- **AFX_DAO_NEXT** vyhledat další umístění odpovídající řetězce.  
  
- **AFX_DAO_PREV** najít předchozí umístění odpovídající řetězec.  
  
- **AFX_DAO_FIRST** najít první umístění odpovídající řetězec.  
  
- **AFX_DAO_LAST** najít poslední umístění odpovídající řetězec.  
  
 `lpszFilter`  
 Řetězcového výrazu (jako **kde** klauzule v příkazu SQL bez slova **kde**) používaná k nalezení záznamu. Příklad:  
  
 [!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud najde odpovídající záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete najít na první, další, předchozí nebo poslední instance řetězce. **Najít** je virtuální funkce, takže můžete přepsat a přidat vlastní implementaci. `FindFirst`, `FindLast`, `FindNext`, A `FindPrev` členské funkce volání **najít** – členská funkce, abyste mohli používat **najít** můžete řídit chování všech operací najít .  
  
 Chcete-li vyhledat záznam v sadě záznamů typu tabulky, volejte [Seek](#seek) – členská funkce.  
  
> [!TIP]
>  Menší sadu záznamů, budete mít, účinnější **najít** bude. Obecně a hlavně s dat ODBC je lepší vytvořit nový dotaz, který načte právě požadované záznamy.  
  
 Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="findfirst"></a>CDaoRecordset::FindFirst  
 Volání této funkce člen najít na první záznam, který odpovídá zadanou podmínku.  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFilter`  
 Řetězcového výrazu (jako **kde** klauzule v příkazu SQL bez slova **kde**) používaná k nalezení záznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud najde odpovídající záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 `FindFirst` – Členská funkce začne jeho vyhledávání od začátku sady záznamů a hledání na konec sady záznamů.  
  
 Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky), použijte jednu z operace přesunutí pro přesun mezi záznamy. Chcete-li vyhledat záznam v sadě záznamů typu tabulky, volejte `Seek` – členská funkce.  
  
 Pokud záznam odpovídající kritériím není nachází, je aktuální záznam ukazatele neurčená, a `FindFirst` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá nejbližším výskytu a tak dále.  
  
> [!CAUTION]
>  Pokud chcete upravit záznam na aktuální záznam, je nutné uložit změny voláním **aktualizace** – členská funkce předtím, než přejdete k jinému záznamu. Pokud přesunete na jiný záznam bez aktualizace, vaše změny budou ztraceny bez upozornění.  
  
 **Najít** členské funkce vyhledávání z umístění a ve směru uvedené v následující tabulce:  
  
|Najít operací|Začátek|Směr vyhledávání|  
|---------------------|-----------|----------------------|  
|`FindFirst`|Začátek sady záznamů|Konec sady záznamů|  
|`FindLast`|Konec sady záznamů|Začátek sady záznamů|  
|`FindNext`|Aktuální záznam.|Konec sady záznamů|  
|**FindPrevious**|Aktuální záznam.|Začátek sady záznamů|  
  
> [!NOTE]
>  Při volání `FindLast`, databázový stroj Microsoft Jet plně naplní sady záznamů před zahájením vyhledávání, pokud to ještě neudělali. První hledání může trvat déle než následné hledání.  
  
 Pomocí některé z operací najít není stejný jako volání **MoveFirst** nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete provést operaci hledání v operaci přesunutí.  
  
 Mějte paměti následující při použití operací hledání:  
  
-   Pokud **najít** vrátí nenulový, není definován na aktuální záznam. V takovém případě musíte umístit ukazatel aktuálního záznamu zpět na platný záznam.  
  
-   Operace hledání nelze použít s posouvání dopředná sada záznamů typu snímek.  
  
-   Používejte formát data USA (měsíc den roku) při vyhledávání pro pole obsahující kalendářní data, i v případě, že nepoužíváte verzi USA databázového stroje Microsoft Jet; v opačném odpovídající záznamy asi se nenašla.  
  
-   Při práci s databázemi ODBC a dynamické velké sady, může se stát, že pomocí operací hledání je pomalý, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrických dotazů nebo **CDaoQuerydef** objekty, které načíst konkrétní indexované záznamy.  
  
 Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="findlast"></a>CDaoRecordset::FindLast  
 Volání této funkce člen najít poslední záznam, který odpovídá zadanou podmínku.  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFilter`  
 Řetězcového výrazu (jako **kde** klauzule v příkazu SQL bez slova **kde**) používaná k nalezení záznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud najde odpovídající záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 `FindLast` – Členská funkce začne vyhledávat na konci sady záznamů a hledání zpětné směrem začátek sady záznamů.  
  
 Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky), použijte jednu z operace přesunutí pro přesun mezi záznamy. Chcete-li vyhledat záznam v sadě záznamů typu tabulky, volejte `Seek` – členská funkce.  
  
 Pokud záznam odpovídající kritériím není nachází, je aktuální záznam ukazatele neurčená, a `FindLast` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá další výskyt po první výskyt a tak dále.  
  
> [!CAUTION]
>  Pokud chcete upravit záznam na aktuální záznam, ujistěte se, uložit změny voláním **aktualizace** – členská funkce předtím, než přejdete k jinému záznamu. Pokud přesunete na jiný záznam bez aktualizace, vaše změny budou ztraceny bez upozornění.  
  
 Pomocí některé z operací najít není stejný jako volání **MoveFirst** nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete provést operaci hledání v operaci přesunutí.  
  
 Mějte paměti následující při použití operací hledání:  
  
-   Pokud **najít** vrátí nenulový, není definován na aktuální záznam. V takovém případě musíte umístit ukazatel aktuálního záznamu zpět na platný záznam.  
  
-   Operace hledání nelze použít s posouvání dopředná sada záznamů typu snímek.  
  
-   Používejte formát data USA (měsíc den roku) při vyhledávání pro pole obsahující kalendářní data, i v případě, že nepoužíváte verzi USA databázového stroje Microsoft Jet; v opačném odpovídající záznamy asi se nenašla.  
  
-   Při práci s databázemi ODBC a dynamické velké sady, může se stát, že pomocí operací hledání je pomalý, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrických dotazů nebo **CDaoQuerydef** objekty, které načíst konkrétní indexované záznamy.  
  
 Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="findnext"></a>CDaoRecordset::FindNext  
 Volání této funkce člen najít další záznam, který odpovídá zadanou podmínku.  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFilter`  
 Řetězcového výrazu (jako **kde** klauzule v příkazu SQL bez slova **kde**) používaná k nalezení záznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud najde odpovídající záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 `FindNext` – Členská funkce začne vyhledávat na aktuální záznam a vyhledá na konec sady záznamů.  
  
 Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky), použijte jednu z operace přesunutí pro přesun mezi záznamy. Chcete-li vyhledat záznam v sadě záznamů typu tabulky, volejte `Seek` – členská funkce.  
  
 Pokud záznam odpovídající kritériím není nachází, je aktuální záznam ukazatele neurčená, a `FindNext` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá nejbližším výskytu a tak dále.  
  
> [!CAUTION]
>  Pokud chcete upravit záznam na aktuální záznam, ujistěte se, uložit změny voláním **aktualizace** – členská funkce předtím, než přejdete k jinému záznamu. Pokud přesunete na jiný záznam bez aktualizace, vaše změny budou ztraceny bez upozornění.  
  
 Pomocí některé z operací najít není stejný jako volání **MoveFirst** nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete provést operaci hledání v operaci přesunutí.  
  
 Mějte paměti následující při použití operací hledání:  
  
-   Pokud **najít** vrátí nenulový, není definován na aktuální záznam. V takovém případě musíte umístit ukazatel aktuálního záznamu zpět na platný záznam.  
  
-   Operace hledání nelze použít s posouvání dopředná sada záznamů typu snímek.  
  
-   Používejte formát data USA (měsíc den roku) při vyhledávání pro pole obsahující kalendářní data, i v případě, že nepoužíváte verzi USA databázového stroje Microsoft Jet; v opačném odpovídající záznamy asi se nenašla.  
  
-   Při práci s databázemi ODBC a dynamické velké sady, může se stát, že pomocí operací hledání je pomalý, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrických dotazů nebo **CDaoQuerydef** objekty, které načíst konkrétní indexované záznamy.  
  
 Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="findprev"></a>CDaoRecordset::FindPrev  
 Volání této funkce člen najít předchozí záznam, který odpovídá zadanou podmínku.  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFilter`  
 Řetězcového výrazu (jako **kde** klauzule v příkazu SQL bez slova **kde**) používaná k nalezení záznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud najde odpovídající záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 `FindPrev` – Členská funkce začne vyhledávat na aktuální záznam a hledá zpětně směrem začátek sady záznamů.  
  
 Pokud chcete zahrnout všechny záznamy v hledání (nikoli pouze ty, které splňují určité podmínky), použijte jednu z operace přesunutí pro přesun mezi záznamy. Chcete-li vyhledat záznam v sadě záznamů typu tabulky, volejte `Seek` – členská funkce.  
  
 Pokud záznam odpovídající kritériím není nachází, je aktuální záznam ukazatele neurčená, a `FindPrev` vrátí hodnotu 0. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt `FindNext` vyhledá nejbližším výskytu a tak dále.  
  
> [!CAUTION]
>  Pokud chcete upravit záznam na aktuální záznam, ujistěte se, uložit změny voláním **aktualizace** – členská funkce předtím, než přejdete k jinému záznamu. Pokud přesunete na jiný záznam bez aktualizace, vaše změny budou ztraceny bez upozornění.  
  
 Pomocí některé z operací najít není stejný jako volání **MoveFirst** nebo `MoveNext`, ale které jednoduše vytvoří na první nebo další záznam aktuální bez zadání podmínku. Můžete provést operaci hledání v operaci přesunutí.  
  
 Mějte paměti následující při použití operací hledání:  
  
-   Pokud **najít** vrátí nenulový, není definován na aktuální záznam. V takovém případě musíte umístit ukazatel aktuálního záznamu zpět na platný záznam.  
  
-   Operace hledání nelze použít s posouvání dopředná sada záznamů typu snímek.  
  
-   Používejte formát data USA (měsíc den roku) při vyhledávání pro pole obsahující kalendářní data, i v případě, že nepoužíváte verzi USA databázového stroje Microsoft Jet; v opačném odpovídající záznamy asi se nenašla.  
  
-   Při práci s databázemi ODBC a dynamické velké sady, může se stát, že pomocí operací hledání je pomalý, zejména při práci s velké sady záznamů. Výkon lze zvýšit pomocí dotazů SQL s přizpůsobit **ORDERBY** nebo **kde** klauzule, parametrických dotazů nebo **CDaoQuerydef** objekty, které načíst konkrétní indexované záznamy.  
  
 Související informace naleznete v tématu "FindFirst FindLast, FindNext FindPrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition  
 Vrátí záznam počet aktuální záznam. objekt sady záznamů.  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo od 0 do počet záznamů v sadě záznamů. Odpovídá pořadové číslo pozice na aktuální záznam v sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti AbsolutePosition podkladového objektu DAO je počítáno od nuly; Hodnota 0 odkazuje na první záznam v sadě záznamů. Můžete určit počet vyplněná záznamů v sadě záznamů voláním [getrecordcount –](#getrecordcount). Volání metody `GetRecordCount` vzhledem k tomu, že musí přístup všechny záznamy určit počet může chvíli trvat.  
  
 Pokud není žádný aktuální záznam, jako když neexistují žádné záznamy v sadě záznamů – vrátí hodnotu 1. Pokud se odstraní záznam na aktuální záznam, hodnota vlastnosti AbsolutePosition není definována a MFC vyvolá výjimku, pokud se odkazuje. Pro dynamické sady záznamů jsou nové záznamy přidány na konec pořadí.  
  
> [!NOTE]
>  Tato vlastnost není určena pro použití jako náhradní číslo záznamu. Záložky se stále doporučeným způsobem zachování a vrátilo se do dané pozici a jsou jediný způsob, jak umístit na aktuální záznam všech typů objektů sady záznamů. Na konkrétní pozici daného záznamu změní, když jsou záznamy předcházející ji odstranit. Je také žádné záruku, že daný záznam budou mít stejné absolutní umístění, pokud sada záznamů je znovu vytvořit znovu vzhledem k tomu, že není zaručena pořadí jednotlivých záznamů v rámci sady záznamů, pokud není vytvořená pomocí příkazu SQL  **ORDERBY** klauzule.  
  
> [!NOTE]
>  Tato funkce člen je platná pouze pro dynamické sady a sady záznamů typu snímek.  
  
 Související informace naleznete v tématu "AbsolutePosition vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getbookmark"></a>CDaoRecordset::GetBookmark  
 Volání této funkce člen k získání hodnoty záložku v určitém záznamu.  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu reprezentující záložek na aktuální záznam.  
  
### <a name="remarks"></a>Poznámky  
 Při vytvoření nebo otevřít objekt sady záznamů, každý z jeho záznamy jedinečný záložku již má, pokud je podporuje. Volání `CanBookmark` k určení, zda sady záznamů podporuje záložky.  
  
 Můžete uložit záložku na aktuální záznam přiřazením hodnoty záložku `COleVariant` objektu. Chcete-li rychle vrátit k kdykoli po přesunutí na jiný záznam, volejte `SetBookmark` s parametrem odpovídající hodnotě této `COleVariant` objektu.  
  
> [!NOTE]
>  Volání metody [Requery](#requery) změny DAO záložky.  
  
 Související informace naleznete v tématu "Záložku vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getcachesize"></a>CDaoRecordset::GetCacheSize  
 Volání této funkce člen získat počet záznamů v mezipaměti.  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která určuje počet záznamů v dynamické sady záznamů, který obsahuje data do místní mezipaměti ze zdroje dat ODBC.  
  
### <a name="remarks"></a>Poznámky  
 Ukládání dat zlepšuje výkon aplikace, která načte data ze vzdáleného serveru prostřednictvím objektů sady záznamů dynamické sady. Mezipaměť je místo v místní paměti, která obsahuje data naposledy načtená ze serveru, v případě, že data požádat znovu, když aplikace běží. Pokud se požaduje data, databázový stroj Microsoft Jet nejprve hledá v mezipaměti pro požadovaná data místo načítání ze serveru, který trvá déle. Data, která nepochází z zdroje dat ODBC není uložen v mezipaměti.  
  
 Všechny zdroje dat ODBC, jako je například připojené tabulky, může mít místní mezipaměti.  
  
 Související informace naleznete v tématu "Velikost paměti, vlastnosti CacheStart" v nápovědě rozhraní DAO.  
  
##  <a name="getcachestart"></a>CDaoRecordset::GetCacheStart  
 Volání této funkce člen získat hodnotu záložku na první záznam v sadě záznamů do mezipaměti.  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `COleVariant` určující záložku na první záznam v sadě záznamů do mezipaměti.  
  
### <a name="remarks"></a>Poznámky  
 Databázový stroj Microsoft Jet požadavky záznamů v mezipaměti rozsahu z mezipaměti a požaduje záznamy mimo rozsah mezipaměti ze serveru.  
  
> [!NOTE]
>  Záznamy načteny z mezipaměti nereflektuje změny provedené současně ke zdrojovým datům jiných uživatelů.  
  
 Související informace naleznete v tématu "Velikost paměti, vlastnosti CacheStart" v nápovědě rozhraní DAO.  
  
##  <a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex  
 Volání této funkce člen k určení index aktuálně nepoužívá v indexované typ tabulky `CDaoRecordset` objektu.  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující název indexu právě používá s sadu záznamů typu tabulky. Vrátí řetězec prázdný, pokud byl nastaven žádný index.  
  
### <a name="remarks"></a>Poznámky  
 Tento index je základem pro řazení záznamů v sadě záznamů typu tabulky a používá [Seek](#seek) – členská funkce vyhledání záznamů.  
  
 A `CDaoRecordset` objekt může mít více než jeden index, ale současně lze použít pouze jeden index (i když [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objekt může mít několik indexů definovanou).  
  
 Související informace najdete v tématu "Index objekt" a definice "aktuální index" v nápovědě rozhraní DAO.  
  
##  <a name="getdatecreated"></a>CDaoRecordset::GetDateCreated  
 Volání této funkce člen načíst datum a čas, kdy byl vytvořen na základní tabulku.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas vytvoření základní tabulky.  
  
### <a name="remarks"></a>Poznámky  
 Nastavení data a času jsou odvozené z počítače, v němž byla vytvořena na základní tabulku.  
  
 Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated  
 Volání této funkce člen načíst datum a čas poslední aktualizace schématu.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas poslední aktualizace struktury základní tabulky (schéma).  
  
### <a name="remarks"></a>Poznámky  
 Nastavení data a času jsou odvozeny od poslední aktualizace struktury základní tabulky (schéma) počítače.  
  
 Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName  
 Volání této funkce člen určit název databáze pro tuto sadu záznamů.  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující cestu a název databáze, z nichž je odvozen této sady záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud sadu záznamů je vytvořen bez ukazatel na [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), pak tuto cestu používá sada záznamů otevřete výchozí databáze. Ve výchozím nastavení vrátí tato funkce prázdný řetězec. Když ClassWizard odvozuje nové sady záznamů z `CDaoRecordset`, tato funkce se vytvoří pro vás.  
  
 Následující příklad ukazuje použití dvojité zpětné lomítko (\\\\) v řetězec, jako je potřebná pro řetězec, který má být správně interpretovat.  
  
 [!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL  
 Tato funkce člen získat příkaz výchozí SQL, na kterých je založena na sadu záznamů volá framework.  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující výchozí příkaz jazyka SQL.  
  
### <a name="remarks"></a>Poznámky  
 To může být název tabulky nebo SQL **vyberte** příkaz.  
  
 Nepřímo zadejte příkaz jazyka SQL výchozí deklarováním třídu sady záznamů s ClassWizard a ClassWizard tato úloha provede za vás.  
  
 Pokud předáte hodnotu null. řetězec SQL tak, aby [otevřete](#open), pak tato funkce je volána k určení názvu tabulky nebo SQL sady záznamů.  
  
##  <a name="geteditmode"></a>CDaoRecordset::GetEditMode  
 Volání této funkce člen k určení stavu úpravám, což je jedna z následujících hodnot:  
  
```  
short GetEditMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, která označuje stav úprav pro aktuální záznam.  
  
### <a name="remarks"></a>Poznámky  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**dbEditNone**|Probíhá operace bez úprav.|  
|**dbEditInProgress**|**Upravit** byla volána.|  
|**dbEditAdd**|`AddNew`byla volána.|  
  
 Související informace naleznete v tématu "EditMode vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getfieldcount"></a>CDaoRecordset::GetFieldCount  
 Volání této funkce člen načíst počet polí (sloupce) definované v sadě záznamů.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet polí v sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "Počet vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo  
 Volání této funkce člen ke získání informací o pole v sadě záznamů.  
  
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
 Index založený na nule předdefinované pole v kolekci polí sady záznamů, pro vyhledávání podle indexu.  
  
 `fieldinfo`  
 Odkaz na [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o sadě záznamů k načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit. Pro nejlepší výkon získat pouze úroveň informací, které budete potřebovat:  
  
- `AFX_DAO_PRIMARY_INFO`(Výchozí) Název, typ, velikost, atributy  
  
- `AFX_DAO_SECONDARY_INFO`Primární informace, plus: pořadí pozice, potřeby povolit nulové délky, pořadí řazení, cizí název pole zdroje, zdrojová tabulka  
  
- `AFX_DAO_ALL_INFO`Informace o primární a sekundární plus: Text pro ověření výchozí hodnotu ověřovacího pravidla  
  
 `lpszName`  
 Název pole.  
  
### <a name="remarks"></a>Poznámky  
 Jedna verze funkce umožňuje vyhledat pole podle indexu. Na další verzi umožňuje vyhledat pole podle názvu.  
  
 Popis vrácené informace naleznete v tématu [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popisu `dwInfoOptions`. Pokud budete požadovat informace na jedné úrovni, získáte informace o všech předchozích úrovní.  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="getfieldvalue"></a>CDaoRecordset::GetFieldValue  
 Volání této funkce člen k načtení dat v sadě záznamů.  
  
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
 `lpszName`  
 Ukazatel na řetězec, který obsahuje název pole.  
  
 `varValue`  
 Odkaz na `COleVariant` objekt, který se uloží hodnotu pole.  
  
 `nIndex`  
 Index počítaný od nuly pole v kolekci polí sady záznamů, pro vyhledávání podle indexu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Dvě verze `GetFieldValue` , vrátí hodnotu návratový [COleVariant](../../mfc/reference/colevariant-class.md) objekt, který obsahuje hodnotu pole.  
  
### <a name="remarks"></a>Poznámky  
 Pole můžete vyhledávat podle názvu nebo podle pořadí.  
  
> [!NOTE]
>  Pro volání jednu z verzí tento člen funkce, která přebírá je efektivnější `COleVariant` odkaz na objekt jako parametr místo volání na verzi, která vrátí `COleVariant` objektu. Pro zpětnou kompatibilitu jsou zachovány pozdější verze této funkce.  
  
 Použití `GetFieldValue` a [SetFieldValue](#setfieldvalue) dynamicky svázat pole v době běhu spíše než staticky vazba sloupce pomocí [DoFieldExchange](#dofieldexchange) mechanismus.  
  
 `GetFieldValue`a `DoFieldExchange` mechanismus mohou být kombinovány ke zlepšení výkonu. Například použít `GetFieldValue` načíst hodnotu, která budete potřebovat pouze na vyžádání a přiřazení této volání tlačítko "Další informace" v rozhraní.  
  
 Související informace najdete v tématech "Objekt pole" a "Hodnota vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getindexcount"></a>CDaoRecordset::GetIndexCount  
 Volání této funkce člen k určení počtu indexy, které jsou k dispozici v sadě záznamů typu tabulky.  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet indexů v sadě záznamů typu tabulky.  
  
### <a name="remarks"></a>Poznámky  
 `GetIndexCount`je užitečné pro ve smyčce přes všechny indexy v sadě záznamů. K tomuto účelu použít `GetIndexCount` ve spojení s [GetIndexInfo](#getindexinfo). Při volání této funkce člena na dynamické sady nebo sady záznamů typu snímek, MFC vyvolá výjimku.  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo  
 Volání této funkce člen získat různých typů informací o indexu definované v základní tabulce základní sady záznamů.  
  
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
 `nIndex`  
 Index založený na nule v kolekci indexy tabulky, pro vyhledávání číselné umístěním.  
  
 `indexinfo`  
 Odkaz na [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktura.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o index pro načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit. Pro nejlepší výkon získat pouze úroveň informací, které budete potřebovat:  
  
- `AFX_DAO_PRIMARY_INFO`(Výchozí) Název, informace o pole, pole  
  
- `AFX_DAO_SECONDARY_INFO`Primární informace, plus: primární, jedinečný, clusteru, Ignorovat hodnoty Null, vyžaduje, cizí  
  
- `AFX_DAO_ALL_INFO`Informace o primární a sekundární plus: jednoznačného počtu  
  
 `lpszName`  
 Ukazatel na název indexu objekt, pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 Jedna verze funkce umožňuje vyhledat index podle svého umístění v kolekci. Na další verzi umožňuje vyhledat index podle názvu.  
  
 Popis vrácené informace naleznete v tématu [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popisu `dwInfoOptions`. Pokud budete požadovat informace na jedné úrovni, získáte informace o všech předchozích úrovní.  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark  
 Volání této funkce člen k načtení záložky nejvíce nedávno přidané nebo aktualizované záznamu.  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `COleVariant` obsahující záložku, která určuje naposledy přidány nebo změněny záznamu.  
  
### <a name="remarks"></a>Poznámky  
 Při vytvoření nebo otevřít objekt sady záznamů, každý z jeho záznamy jedinečný záložku již má, pokud je podporuje. Volání [GetBookmark](#getbookmark) k určení, pokud sada záznamu podporuje záložky. Pokud sada záznamů nepodporuje záložky, `CDaoException` je vyvolána výjimka.  
  
 Když přidáte záznam, zobrazí se na konci sady záznamů a není na aktuální záznam. Chcete-li nový záznam aktuální, volání `GetLastModifiedBookmark` a pak zavolají `SetBookmark` se vraťte do nově přidaného záznamu.  
  
 Související informace naleznete v tématu "Změněno vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getlockingmode"></a>CDaoRecordset::GetLockingMode  
 Volání této funkce člen k určení typu uzamčení platit pro sadu záznamů.  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je typ zamykání pesimistické, jinak hodnota 0 pro optimistické zamykání.  
  
### <a name="remarks"></a>Poznámky  
 Kdy pesimistické zamykání je v platnosti, stránku dat obsahující záznam upravujete uzamčeno, jakmile zavoláte [upravit](#edit) – členská funkce. Stránka je odemčený při volání [aktualizace](#update) nebo [Zavřít](#close) – členská funkce nebo všechny operace přesunutí nebo najít.  
  
 Když optimistické zamykání je v platnosti stránku dat obsahující záznam uzamčeno pouze tehdy, když probíhá aktualizace záznamu **aktualizace** – členská funkce.  
  
 Při práci s zdroje dat ODBC, je vždy optimistické zamykání režimu.  
  
 Související informace najdete v tématech "LockEdits vlastnost" a "Uzamčení chování v s více uživateli aplikace" v nápovědě rozhraní DAO.  
  
##  <a name="getname"></a>CDaoRecordset::GetName  
 Volání této funkce člen načíst název sady záznamů.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující název sady záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Název sady záznamů musí začínat písmenem a může obsahovat nejvýše 40 znaků. Může obsahovat čísla a podtržítka znaků však nemůže obsahovat interpunkční znaménka nebo mezery.  
  
 Související informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getparamvalue"></a>CDaoRecordset::GetParamValue  
 Volání této funkce člen načíst aktuální hodnota zadaný parametr uložené v základní objekt DAOParameter.  
  
```  
virtual COleVariant GetParamValue(int nIndex);  
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Pozice číselné parametru základní objekt DAOParameter.  
  
 `lpszName`  
 Název parametru, jehož hodnotu chcete.  
  
### <a name="return-value"></a>Návratová hodnota  
 Třída objektu [COleVariant](../../mfc/reference/colevariant-class.md) obsahující hodnoty parametru.  
  
### <a name="remarks"></a>Poznámky  
 Parametr můžete přistupovat pomocí názvu nebo podle jeho číselné pozice v kolekci.  
  
 Související informace naleznete v tématu "Parametr objekt" v nápovědě rozhraní DAO.  
  
##  <a name="getpercentposition"></a>CDaoRecordset::GetPercentPosition  
 Při práci s dynamické sady nebo sadu záznamů typu snímek, když zavoláte `GetPercentPosition` před plně sestavování sady záznamů, množství přesun je relativní vzhledem k počtu záznamů získat přístup, které je uvedené voláním [getrecordcount –](#getrecordcount).  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo od 0 do 100 určující přibližnou umístění na aktuální záznam v objektu sady záznamů na základě procenta záznamy v sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Můžete přesunout na poslední záznam volání [MoveLast](#movelast) k dokončení naplnění všechny sady záznamů, ale to může trvat dlouhou dobu.  
  
 Můžete volat `GetPercentPosition` na všechny tři typy objektů sady záznamů, včetně tabulek bez indexy. Však nelze volat `GetPercentPosition` na dopředné posouvání snímky nebo v sadě záznamů otevřít z průchozí dotaz externí databáze. Pokud není žádný aktuální záznam nebo he aktuální záznam byl odstraněn, `CDaoException` je vyvolána výjimka.  
  
 Související informace naleznete v tématu "PercentPosition vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getrecordcount"></a>CDaoRecordset::GetRecordCount  
 Volání této funkce člen a zjistěte, kolik záznamy v sadě záznamů byl získat přístup.  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet záznamů, které jsou přístupné v objekt sady záznamů.  
  
### <a name="remarks"></a>Poznámky  
 `GetRecordCount`neindikuje počet záznamů, jsou obsažené v dynamické sady nebo sadu záznamů typu snímek, dokud všechny záznamy byla získat přístup. Toto volání funkce člen může trvat poměrně dlouhou dobu.  
  
 Jakmile přistupoval poslední záznam návratovou hodnotu Určuje celkový počet neodstraněných záznamů v sadě záznamů. Chcete-li vynutit poslední záznam nelze přistupovat, zavolejte `MoveLast` nebo `FindLast` – členská funkce sady záznamů. Počet SQL můžete použít také k určení přibližný počet záznamů, které vrátí dotaz.  
  
 Jak aplikace odstraňuje záznamy v sadě dynamické sady záznamů, vrátí hodnotu, která `GetRecordCount` snižuje. Však se neprojeví záznamy byly odstraněny jinými uživateli ve `GetRecordCount` dokud k záznamu odstraněného je umístěn na aktuální záznam. Je-li spustit transakci, která ovlivňuje počet záznamů a následně vrácení transakce, `GetRecordCount` nebude odráží skutečný počet zbývajících záznamů.  
  
 Hodnota `GetRecordCount` z sadu záznamů typu snímek nemá vliv změny v základní tabulky.  
  
 Hodnota `GetRecordCount` z typ tabulky záznamů odráží přibližný počet záznamů v tabulce a má vliv okamžitě, jako jsou tabulky záznamů přidat a odstranit.  
  
 Sady záznamů se žádné záznamy, vrátí hodnotu 0. Při práci s připojené tabulek nebo databází ODBC `GetRecordCount` vždy vrátí hodnotu - 1. Volání **Requery –** – členská funkce v sadě záznamů obnoví hodnotu `GetRecordCount` stejně, jako kdyby byly znovu spustit dotaz.  
  
 Související informace naleznete v tématu "%d{RecordCount/ vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getsql"></a>CDaoRecordset::GetSQL  
 Volání této funkce člen získat příkaz jazyka SQL, která byla použita k výběru sady záznamů záznamů, pokud byl otevřen.  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující příkaz jazyka SQL.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle to bude SQL **vyberte** příkaz.  
  
 Řetězec vrácený `GetSQL` se obvykle liší od libovolný řetězec, bylo předáno do sady záznamů v `lpszSQL` parametru [otevřete](#open) – členská funkce. Důvodem je, že vytváří sadu záznamů úplný příkaz SQL na předán na základě **otevřete**zadaným ClassWizard a co možná jste zadali v [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) datových členů.  
  
> [!NOTE]
>  Volání této funkce člen pouze po volání **otevřete**.  
  
 Související informace naleznete v tématu "Vlastnost SQL" v nápovědě rozhraní DAO.  
  
##  <a name="gettype"></a>CDaoRecordset::GetType  
 Volání této funkce člen po otevření sady záznamů se zjistit typ objektu sady záznamů.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z následujících hodnot, která určuje typ sady záznamů:  
  
- **dbOpenTable** sada záznamů typu tabulky  
  
- **dbOpenDynaset** dynamické sady  
  
- **dbOpenSnapshot** sada záznamů typu snímek  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "Vlastnost typu" v nápovědě rozhraní DAO.  
  
##  <a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule  
 Volání této funkce člen k určení pravidlo slouží k ověření data.  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt obsahující hodnotu, která ověří data v záznamu, protože je změnit nebo přidat do tabulky.  
  
### <a name="remarks"></a>Poznámky  
 Toto pravidlo je založený na textu a platí pokaždé, když se změní v základní tabulce. Pokud data není právní, MFC vyvolá výjimku. Vrácená chybová zpráva je vlastnost ověřovací text podkladového objektu pole, pokud zadaný text nebo text výrazu určeného vlastností ValidationRule podkladového objektu pole. Můžete volat [GetValidationText](#getvalidationtext) se získat text chybové zprávy.  
  
 Například pole v záznamu, který vyžaduje den v měsíci může mít ověřovacího pravidla jako "den BETWEEN 1 a 31."  
  
 Související informace naleznete v tématu "Vlastnosti Ověřovací pravidlo" v nápovědě rozhraní DAO.  
  
##  <a name="getvalidationtext"></a>CDaoRecordset::GetValidationText  
 Volání této funkce člen k získání textu vlastnost ověřovací text podkladového objektu pole.  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt obsahující text zprávy, který se zobrazí, pokud hodnota pole nesplňuje ověřovací pravidlo podkladového objektu pole.  
  
### <a name="remarks"></a>Poznámky  
 Související informace naleznete v tématu "Vlastnost Ověřovací text" v nápovědě rozhraní DAO.  
  
##  <a name="isbof"></a>CDaoRecordset::IsBOF  
 Volání této funkce člen před posunutí ze záznamu záznam se dozvíte, zda jste došli před na první záznam sady záznamů.  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přešli zpátky před první záznam; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete také volat `IsBOF` spolu s `IsEOF` k určení, zda sada záznamů obsahuje záznamy nebo je prázdný. Okamžitě po zavolání metody **otevřete**, pokud sada záznamů obsahuje žádné záznamy `IsBOF` vrátí nenulovou hodnotu. Když otevřete záznamů, která obsahuje alespoň jeden záznam, je na první záznam na aktuální záznam a `IsBOF` vrátí hodnotu 0.  
  
 Pokud na první záznam na aktuální záznam a volání `MovePrev`, `IsBOF` následně vrátí nenulové hodnoty. Pokud `IsBOF` vrátí nenulovou a volání `MovePrev`, je vyvolána výjimka. Pokud `IsBOF` vrátí nenulové hodnoty, není definován na aktuální záznam a jakoukoliv akci, která vyžaduje aktuální záznam způsobí výjimku.  
  
 Účinek konkrétní metody na `IsBOF` a `IsEOF` nastavení:  
  
-   Volání metody **otevřete** interně provede na první záznam v sadě záznamů na aktuální záznam voláním **MoveFirst**. Proto volání **otevřete** na prázdnou sadu záznamů příčiny `IsBOF` a `IsEOF` vrátit nenulové hodnoty. (Viz následující tabulka pro chování nezdařené **MoveFirst** nebo `MoveLast` volání.)  
  
-   Všechny operace přesunutí, které úspěšně najít záznam způsobit, že oba `IsBOF` a `IsEOF` vrátit 0.  
  
-   `AddNew` Následuje volání **aktualizace** způsobí, že volání, které úspěšně vloží nový záznam `IsBOF` vrátit 0, ale jenom v případě `IsEOF` je již nenulové hodnoty. Stav `IsEOF` vždy zůstanou nezměněna. Jak jsou definovány pro databázový stroj Microsoft Jet, je aktuální záznam ukazatel prázdnou sadu záznamů na konci souboru, takže všechny nový záznam vkládají záznam na aktuální záznam.  
  
-   Všechny **odstranit** volání, i když ho odebere jenom zbývající záznam ze sady záznamů, nedojde ke změně hodnotu `IsBOF` nebo `IsEOF`.  
  
 Tato tabulka ukazuje, které jsou povoleny přesunutí nabízela jinou kombinaci `IsBOF` /  `IsEOF`.  
  
||MoveFirst MoveLast|MovePrev –,<br /><br /> Přesunout < 0|Přesunout 0|MoveNext –,<br /><br /> Přesunout > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= nenulové hodnoty,<br /><br /> `IsEOF`=0|Povoleno|Výjimka|Výjimka|Povoleno|  
|`IsBOF`=0,<br /><br /> `IsEOF`= nenulové hodnoty|Povoleno|Povoleno|Výjimka|Výjimka|  
|Oba nenulové hodnoty|Výjimka|Výjimka|Výjimka|Výjimka|  
|Obě 0|Povoleno|Povoleno|Povoleno|Povoleno|  
  
 Umožňuje operace přesunu neznamená, že operace úspěšně najít záznam. Ho jenom označuje, že pokus o provést zadanou operaci přesunutí je povolen a nebude generovat výjimku. Hodnota `IsBOF` a `IsEOF` členské funkce může změnit v důsledku pokusu o přesun.  
  
 Účinek operace přesunutí, které Neumísťujte záznam na základě hodnoty `IsBOF` a `IsEOF` nastavení je uvedené v následující tabulce.  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst –**,`MoveLast`|Nenulové hodnoty|Nenulové hodnoty|  
|**Přesunout** 0|Žádná změna|Žádná změna|  
|`MovePrev`, **Přesunout** < 0|Nenulové hodnoty|Žádná změna|  
|`MoveNext`, **Přesunout** > 0|Žádná změna|Nenulové hodnoty|  
  
 Související informace naleznete v tématu "BOF, vlastnosti EOF" v nápovědě rozhraní DAO.  
  
##  <a name="isdeleted"></a>CDaoRecordset::IsDeleted  
 Volání této funkce člen k určení, zda byl odstraněn záznam na aktuální záznam.  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů umístěna na záznam odstraněného; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se posunete na záznam a `IsDeleted` vrátí **TRUE** (nenulové hodnoty), pak musí posunutí jiný záznam před provedením další operace sady záznamů.  
  
> [!NOTE]
>  Nemusíte zkontrolujte odstranila stav pro záznamy v sadě záznamů snímek nebo typ tabulky. Vzhledem k tomu, že záznamy nelze odstranit ze snímku, není nutné volat `IsDeleted`. Pro typ tabulky sady záznamů jsou ve skutečnosti odstraněné záznamy odebrané ze sady záznamů. Jakmile se záznam byl odstraněn, vy, jiným uživatelem, nebo v jiné sadě záznamů, nelze přejděte zpět na tento záznam. Proto není nutné volat `IsDeleted`.  
  
 Pokud odstraníte záznam z dynamická sada, bude odebrán ze sady záznamů a nemůže přejděte zpět na tento záznam. Pokud však záznam v dynamická sada je odstraněna jiným uživatelem nebo v jiné záznamů na základě ve stejné tabulce `IsDeleted` vrátí **TRUE** Pokud se později posunete na tento záznam.  
  
 Související informace najdete v tématech "Odstranit způsob", "Změněno vlastnost" a "EditMode vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="iseof"></a>CDaoRecordset::IsEOF  
 Volání této funkce člen při posunutí ze záznamu záznamu zjistěte, zda jste došli nad rámec poslední záznam sady záznamů.  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud sada záznamů obsahuje žádné záznamy nebo pokud jste přešli nad rámec poslední záznam; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete také volat `IsEOF` k určení, zda sada záznamů obsahuje záznamy nebo je prázdný. Okamžitě po zavolání metody **otevřete**, pokud sada záznamů obsahuje žádné záznamy `IsEOF` vrátí nenulovou hodnotu. Když otevřete záznamů, která obsahuje alespoň jeden záznam, je na první záznam na aktuální záznam a `IsEOF` vrátí hodnotu 0.  
  
 Pokud je poslední záznam na aktuální záznam při volání `MoveNext`, `IsEOF` následně vrátí nenulové hodnoty. Pokud `IsEOF` vrátí nenulovou a volání `MoveNext`, je vyvolána výjimka. Pokud `IsEOF` vrátí nenulové hodnoty, není definován na aktuální záznam a jakoukoliv akci, která vyžaduje aktuální záznam způsobí výjimku.  
  
 Účinek konkrétní metody na `IsBOF` a `IsEOF` nastavení:  
  
-   Volání metody **otevřete** interně provede na první záznam v sadě záznamů na aktuální záznam voláním **MoveFirst**. Proto volání **otevřete** na prázdnou sadu záznamů příčiny `IsBOF` a `IsEOF` vrátit nenulové hodnoty. (Viz následující tabulka pro chování nezdařené **MoveFirst** volání.)  
  
-   Všechny operace přesunutí, které úspěšně najít záznam způsobit, že oba `IsBOF` a `IsEOF` vrátit 0.  
  
-   `AddNew` Následuje volání **aktualizace** způsobí, že volání, které úspěšně vloží nový záznam `IsBOF` vrátit 0, ale jenom v případě `IsEOF` je již nenulové hodnoty. Stav `IsEOF` vždy zůstanou nezměněna. Jak jsou definovány pro databázový stroj Microsoft Jet, je aktuální záznam ukazatel prázdnou sadu záznamů na konci souboru, takže všechny nový záznam vkládají záznam na aktuální záznam.  
  
-   Všechny **odstranit** volání, i když ho odebere jenom zbývající záznam ze sady záznamů, nedojde ke změně hodnotu `IsBOF` nebo `IsEOF`.  
  
 Tato tabulka ukazuje, které jsou povoleny přesunutí nabízela jinou kombinaci `IsBOF` /  `IsEOF`.  
  
||MoveFirst MoveLast|MovePrev –,<br /><br /> Přesunout < 0|Přesunout 0|MoveNext –,<br /><br /> Přesunout > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= nenulové hodnoty,<br /><br /> `IsEOF`=0|Povoleno|Výjimka|Výjimka|Povoleno|  
|`IsBOF`=0,<br /><br /> `IsEOF`= nenulové hodnoty|Povoleno|Povoleno|Výjimka|Výjimka|  
|Oba nenulové hodnoty|Výjimka|Výjimka|Výjimka|Výjimka|  
|Obě 0|Povoleno|Povoleno|Povoleno|Povoleno|  
  
 Umožňuje operace přesunu neznamená, že operace úspěšně najít záznam. Ho jenom označuje, že pokus o provést zadanou operaci přesunutí je povolen a nebude generovat výjimku. Hodnota `IsBOF` a `IsEOF` členské funkce může změnit v důsledku pokusu o přesun.  
  
 Účinek operace přesunutí, které Neumísťujte záznam na základě hodnoty `IsBOF` a `IsEOF` nastavení je uvedené v následující tabulce.  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst –**,`MoveLast`|Nenulové hodnoty|Nenulové hodnoty|  
|**Přesunout** 0|Žádná změna|Žádná změna|  
|`MovePrev`, **Přesunout** < 0|Nenulové hodnoty|Žádná změna|  
|`MoveNext`, **Přesunout** > 0|Žádná změna|Nenulové hodnoty|  
  
 Související informace naleznete v tématu "BOF, vlastnosti EOF" v nápovědě rozhraní DAO.  
  
##  <a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty  
 Volání této funkce člen k určení, zda zadaná pole data členem dynamická sada má byla označena jako "Chybná" (změnit).  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Ukazatel na pole datového člena, jejichž stav chcete zkontrolovat, nebo **NULL** k určení, pokud žádná pole jsou chybná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadané pole datového člena je označena jako chybná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Data v všechny změny pole datových členů budou přeneseny na záznam ve zdroji dat při aktualizaci na aktuální záznam voláním **aktualizace** členské funkce `CDaoRecordset` (následující volání **upravit**nebo `AddNew`). Replikace, můžete provést další kroky, jako například unflagging pole datového člena k označení sloupce, takže ho nebude možné zapsat do zdroje dat.  
  
 `IsFieldDirty`se implementuje pomocí `DoFieldExchange`.  
  
##  <a name="isfieldnull"></a>CDaoRecordset::IsFieldNull  
 Volání této funkce člen k určení, zda zadaná pole datových členů sady záznamů byl označen příznakem jako hodnotu Null.  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Ukazatel na pole datového člena, jejichž stav chcete zkontrolovat, nebo **NULL** k určení, pokud je některý z pole hodnotu Null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadané pole datového člena označen příznakem jako hodnota Null. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 (V terminologii databáze Null znamená "nutnosti žádná hodnota" a není stejný jako **NULL** v jazyce C++.) Pokud pole datových členů je označena jako hodnota Null, je interpretován jako sloupec na aktuální záznam, pro kterou neexistuje žádná hodnota.  
  
> [!NOTE]
>  V některých situacích pomocí `IsFieldNull` může být neefektivní, jak ukazuje následující příklad kódu:  
  
 [!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  Pokud používáte dynamické vazby záznamů, bez odvozování z `CDaoRecordset`, je nutné používat **VT_NULL** jak je znázorněno v příkladu.  
  
##  <a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable  
 Volání této funkce člen k určení, zda je zadaná pole datového člena "null" (může být nastavena na hodnotu Null; C++ **NULL** není stejná jako hodnota Null, což v terminologii databáze znamená "s žádnou hodnotu").  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Ukazatel na pole datového člena, jejichž stav chcete zkontrolovat, nebo **NULL** k určení, pokud je některý z pole hodnotu Null.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zadané pole datového člena lze hodnotu Null; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pole, která nemůže mít hodnotu Null, musí mít hodnotu. Pokud se pokusíte toto pole nastavíte na hodnotu Null při přidávání nebo aktualizaci záznamu, zdroj dat odmítne přidání nebo aktualizace, a **aktualizace** vyvolá výjimku. Výjimka nastává při volání **aktualizace**, není při volání `SetFieldNull`.  
  
##  <a name="isopen"></a>CDaoRecordset::IsOpen  
 Volání této funkce člen k určení, pokud sada záznamů je otevřený.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě objekt sady záznamů **otevřete** nebo **Requery –** – členská funkce dříve byla volána a sady záznamů nebyla uzavřena; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset::m_bCheckCacheForDirtyFields  
 Obsahuje příznak, který udává, zda v mezipaměti pole jsou automaticky označeny jako nesprávné (změněné) a hodnotu Null.  
  
### <a name="remarks"></a>Poznámky  
 Použije se výchozí hodnota příznak **TRUE**. Nastavení v této – datový člen řídí celý mechanismus dvojité ukládání do vyrovnávací paměti. Pokud nastavíte příznak na **TRUE**, můžete vypnout ukládání do mezipaměti na základě pole pole pomocí mechanismu DFX. Pokud nastavíte příznak na **FALSE**, musí volat `SetFieldDirty` a `SetFieldNull` sami.  
  
 Tento člen data před voláním **otevřete**. Tento mechanismus je určen pro snadné použití. Výkon může být pomalejší kvůli ukládání polí, jakmile jsou změny.  
  
##  <a name="m_nfields"></a>CDaoRecordset::m_nFields  
 Obsahuje počet pole datových členů ve třídě sady záznamů a počet sloupců vybraných funkcí sady záznamů z datového zdroje.  
  
### <a name="remarks"></a>Poznámky  
 V konstruktoru pro třídy sady záznamů musí inicializovat `m_nFields` s správný počet staticky vázané pole. ClassWizard zapíše tento inicializace pro vás, pokud ji používáte deklarovat třídu sady záznamů. Je také možné zapsat ji ručně.  
  
 Rozhraní používá toto číslo ke správě interakce mezi pole datových členů a na odpovídající sloupce ve zdroji dat na aktuální záznam.  
  
> [!NOTE]
>  Toto číslo musí odpovídat počtu sloupců výstup registrované v `DoFieldExchange` po volání `SetFieldType` s parametrem **CDaoFieldExchange::outputColumn**.  
  
 Můžete vytvořit vazbu sloupců dynamicky ve své `CDaoRecordset::GetFieldValue` a `CDaoRecordset::SetFieldValue`. Pokud tak učiníte, není potřeba zvýšit počet v `m_nFields` tak, aby odrážela počet DFX funkce volání vaší `DoFieldExchange` – členská funkce.  
  
##  <a name="m_nparams"></a>CDaoRecordset::m_nParams  
 Obsahuje počet parametry datových členů v třídě sady záznamů – počet parametrů předaných s dotaz sady záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše sada záznamů třída má všechny parametry datových členů, musí inicializovat v konstruktoru pro třídu `m_nParams` s správné číslo. Hodnota `m_nParams` výchozí hodnota je 0. Pokud přidáte parametry datových členů – které je potřeba udělat ručně – musí také ručně přidat inicializaci v konstruktoru třídy tak, aby odrážela počet parametrů (která musí být alespoň tak velké, jaká počet '' zástupné symboly v vaší **m_strFilter**  nebo `m_strSort` řetězec).  
  
 Rozhraní používá toto číslo, když ho parameterizes dotaz sady záznamů.  
  
> [!NOTE]
>  Toto číslo musí odpovídat počtu "parametry" zaregistrovaný v `DoFieldExchange` po volání `SetFieldType` s parametrem **CFieldExchange::param**.  
  
 Související informace naleznete v tématu "Parametr objekt" v nápovědě rozhraní DAO.  
  
##  <a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset  
 Obsahuje ukazatel na rozhraní OLE pro základní objekt sady záznamů rozhraní DAO `CDaoRecordset` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud potřebujete získat přímo přístup k rozhraní DAO, použijte tento ukazatel.  
  
 Související informace naleznete v tématu "Objekt sady záznamů" v nápovědě rozhraní DAO.  
  
##  <a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase  
 Obsahuje odkazy `CDaoDatabase` objekt, pomocí kterého je sada záznamů připojený ke zdroji dat.  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná je nastavená dvěma způsoby. Obvykle můžete předat ukazatel již otevřete `CDaoDatabase` objektu při sestavení objektu záznamů. Pokud předáte **NULL** místo toho **CDaoRecordset** vytvoří `CDaoDatabase` objekt pro vás a otevře ji. V obou případech `CDaoRecordset` ukládá ukazatele v této proměnné.  
  
 Obvykle nebudete muset přímo pomocí ukazatele uložené v **m_pDatabase**. Pokud píšete vlastní rozšíření `CDaoRecordset`, ale budete muset použít ukazatele. Například může být nutné ukazatele Pokud jste throw vlastní `CDaoException`(s).  
  
 Související informace naleznete v tématu "Objekt databáze" v nápovědě rozhraní DAO.  
  
##  <a name="m_strfilter"></a>CDaoRecordset::m_strFilter  
 Obsahuje řetězec, který se používá pro konstrukci **kde** klauzuli příkazu SQL.  
  
### <a name="remarks"></a>Poznámky  
 Nezahrnuje vyhrazené slovo **kde** pro filtrování sady záznamů. Použití této – datový člen není použitelná pro sady záznamů typu tabulky. Použití **m_strFilter** nemá žádný vliv, při otevírání sada záznamů pomocí `CDaoQueryDef` ukazatel.  
  
 Použijte formát data USA (měsíc den roku) při filtrování pole obsahující kalendářní data, i v případě, že nepoužíváte verzi USA databázového stroje Microsoft Jet; data, jinak hodnota nemusí být filtrovány podle očekávání.  
  
 Související informace naleznete v tématu "Vlastnost filtru" v nápovědě rozhraní DAO.  
  
##  <a name="m_strsort"></a>CDaoRecordset::m_strSort  
 Obsahuje řetězec obsahující **ORDERBY** klauzuli příkazu SQL bez vyhrazených slov **ORDERBY**.  
  
### <a name="remarks"></a>Poznámky  
 Můžete řadit na objekty sada záznamů typu dynamická sada a snímek.  
  
 Nelze řadit objekty sady záznamů typu tabulky. Chcete-li určit pořadí řazení sady záznamů typu tabulky, volejte [SetCurrentIndex](#setcurrentindex).  
  
 Použití `m_strSort` nemá žádný vliv, při otevírání sada záznamů pomocí `CDaoQueryDef` ukazatel.  
  
 Související informace naleznete v tématu "Vlastnosti řazení" v nápovědě rozhraní DAO.  
  
##  <a name="move"></a>CDaoRecordset::Move  
 Volání této funkce člen na pozici sady záznamů `lRows` záznamy na aktuální záznam.  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>Parametry  
 `lRows`  
 Počet záznamů k přesunutí nebo předchozí. Kladné hodnoty. přesuňte směrem vpřed, na konci sady záznamů. Záporné hodnoty přesunout zpátky, zpět na začátek.  
  
### <a name="remarks"></a>Poznámky  
 Můžete přesunout nebo předchozí. `Move( 1 )`je ekvivalentní `MoveNext`, a `Move( -1 )` je ekvivalentní `MovePrev`.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Obecně platí, jak volat `IsBOF` a `IsEOF` předtím, než operace přesunutí k určení, zda má sada záznamů žádné záznamy. Po zavolání metody **otevřete** nebo **Requery –**, volání buď `IsBOF` nebo `IsEOF`.  
  
> [!NOTE]
>  Pokud jste přešli po začátku nebo konci sadu záznamů ( `IsBOF` nebo `IsEOF` vrátí nenulovou hodnotu), volání **přesunout** vyvolá `CDaoException`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Při volání **přesunout** dopředné posouvání snímku `lRows` parametr musí být kladné celé číslo a záložky nejsou povoleny, a přesunout předávat jenom.  
  
 Chcete-li první, poslední, další nebo předchozí záznam v sadě záznamů aktuálním záznamu, volání **MoveFirst**, `MoveLast`, `MoveNext`, nebo `MovePrev` – členská funkce.  
  
 Související informace najdete v tématech "Metoda přesunout" a "MoveFirst MoveLast, MoveNext MovePrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="movefirst"></a>CDaoRecordset::MoveFirst  
 Volání této funkce člen, aby na první záznam v sadě záznamů (pokud existuje) záznam na aktuální záznam.  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>Poznámky  
 Není nutné volat **MoveFirst** okamžitě po otevření sady záznamů. V ten moment se první záznam (pokud existuje) je automaticky záznam na aktuální záznam.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Obecně platí, jak volat `IsBOF` a `IsEOF` předtím, než operace přesunutí k určení, zda má sada záznamů žádné záznamy. Po zavolání metody **otevřete** nebo **Requery –**, volání buď `IsBOF` nebo `IsEOF`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Použití **přesunout** funkce pro přesun mezi záznamy bez použití podmínku. Pomocí operací hledání vyhledejte záznamy v dynamické sady nebo objekt sady záznamů typu snímek, která splňují určité podmínky. Chcete-li vyhledat záznam v objektu sada záznamů typu tabulky, volejte `Seek`.  
  
 Pokud sadu záznamů odkazuje na sadu záznamů typu tabulky, následuje pohyb aktuální index v tabulce. Aktuální index lze nastavit pomocí vlastnost Index základní objekt DAO. Pokud aktuální index není nastavena, pořadí vrácených záznamů není definován.  
  
 Když zavoláte `MoveLast` na objekt sady záznamů na základě dotazu SQL nebo querydef, dotaz musí k dokončení a je plně vyplní objekt sady záznamů.  
  
 Nelze volat **MoveFirst** nebo `MovePrev` – členská funkce s dopředné posouvání snímku.  
  
 Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů konkrétní počet záznamů vpřed nebo zpětné, volejte **přesunout**.  
  
 Související informace najdete v tématech "Metoda přesunout" a "MoveFirst MoveLast, MoveNext MovePrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="movelast"></a>CDaoRecordset::MoveLast  
 Volání této funkce člen, aby poslední záznam (pokud existuje) v sadě záznamů na aktuální záznam.  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Obecně platí, jak volat `IsBOF` a `IsEOF` předtím, než operace přesunutí k určení, zda má sada záznamů žádné záznamy. Po zavolání metody **otevřete** nebo **Requery –**, volání buď `IsBOF` nebo `IsEOF`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Použití **přesunout** funkce pro přesun mezi záznamy bez použití podmínku. Pomocí operací hledání vyhledejte záznamy v dynamické sady nebo objekt sady záznamů typu snímek, která splňují určité podmínky. Chcete-li vyhledat záznam v objektu sada záznamů typu tabulky, volejte `Seek`.  
  
 Pokud sadu záznamů odkazuje na sadu záznamů typu tabulky, následuje pohyb aktuální index v tabulce. Aktuální index lze nastavit pomocí vlastnost Index základní objekt DAO. Pokud aktuální index není nastavena, pořadí vrácených záznamů není definován.  
  
 Když zavoláte `MoveLast` na objekt sady záznamů na základě dotazu SQL nebo querydef, dotaz musí k dokončení a je plně vyplní objekt sady záznamů.  
  
 Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů konkrétní počet záznamů vpřed nebo zpětné, volejte **přesunout**.  
  
 Související informace najdete v tématech "Metoda přesunout" a "MoveFirst MoveLast, MoveNext MovePrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="movenext"></a>CDaoRecordset::MoveNext  
 Volání této funkce člen, aby se na další záznam v sadě záznamů na aktuální záznam.  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>Poznámky  
 Doporučuje se, že zavoláte `IsBOF` před dalším pokusem o přesun do předchozího záznamu. Volání `MovePrev` vyvolá výjimku `CDaoException` Pokud `IsBOF` vrátí nenulové hodnoty, která znamená, že jste již přešli před první záznam nebo, nebyly vybrány žádné záznamy pomocí sady záznamů.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Obecně platí, jak volat `IsBOF` a `IsEOF` předtím, než operace přesunutí k určení, zda má sada záznamů žádné záznamy. Po zavolání metody **otevřete** nebo **Requery –**, volání buď `IsBOF` nebo `IsEOF`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Použití **přesunout** funkce pro přesun mezi záznamy bez použití podmínku. Pomocí operací hledání vyhledejte záznamy v dynamické sady nebo objekt sady záznamů typu snímek, která splňují určité podmínky. Chcete-li vyhledat záznam v objektu sada záznamů typu tabulky, volejte `Seek`.  
  
 Pokud sadu záznamů odkazuje na sadu záznamů typu tabulky, následuje pohyb aktuální index v tabulce. Aktuální index lze nastavit pomocí vlastnost Index základní objekt DAO. Pokud aktuální index není nastavena, pořadí vrácených záznamů není definován.  
  
 Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů konkrétní počet záznamů vpřed nebo zpětné, volejte **přesunout**.  
  
 Související informace najdete v tématech "Metoda přesunout" a "MoveFirst MoveLast, MoveNext MovePrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="moveprev"></a>CDaoRecordset::MovePrev  
 Volání této funkce člen aby předchozího záznamu v sadě záznamů na aktuální záznam.  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>Poznámky  
 Doporučuje se, že zavoláte `IsBOF` před dalším pokusem o přesun do předchozího záznamu. Volání `MovePrev` vyvolá výjimku `CDaoException` Pokud `IsBOF` vrátí nenulové hodnoty, která znamená, že jste již přešli před první záznam nebo, nebyly vybrány žádné záznamy pomocí sady záznamů.  
  
> [!CAUTION]
>  Žádné z volání **přesunout** funkce vyvolá výjimku, pokud má sada záznamů žádné záznamy. Obecně platí, jak volat `IsBOF` a `IsEOF` předtím, než operace přesunutí k určení, zda má sada záznamů žádné záznamy. Po zavolání metody **otevřete** nebo **Requery –**, volání buď `IsBOF` nebo `IsEOF`.  
  
> [!NOTE]
>  Pokud žádné z volání **přesunout** funkce při záznam na aktuální záznam se aktualizovat nebo přidání, aktualizace se ztratí bez upozornění.  
  
 Použití **přesunout** funkce pro přesun mezi záznamy bez použití podmínku. Pomocí operací hledání vyhledejte záznamy v dynamické sady nebo objekt sady záznamů typu snímek, která splňují určité podmínky. Chcete-li vyhledat záznam v objektu sada záznamů typu tabulky, volejte `Seek`.  
  
 Pokud sadu záznamů odkazuje na sadu záznamů typu tabulky, následuje pohyb aktuální index v tabulce. Aktuální index lze nastavit pomocí vlastnost Index základní objekt DAO. Pokud aktuální index není nastavena, pořadí vrácených záznamů není definován.  
  
 Nelze volat **MoveFirst** nebo `MovePrev` – členská funkce s dopředné posouvání snímku.  
  
 Chcete-li přesunout umístění aktuální záznam v objektu sady záznamů konkrétní počet záznamů vpřed nebo zpětné, volejte **přesunout**.  
  
 Související informace najdete v tématech "Metoda přesunout" a "MoveFirst MoveLast, MoveNext MovePrevious metod" v nápovědě rozhraní DAO.  
  
##  <a name="open"></a>CDaoRecordset::Open  
 Tato funkce člen načíst záznamy pro sadu záznamů musí volat.  
  
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
 `nOpenType`  
 Jedna z následujících hodnot:  
  
- **dbOpenDynaset** dynamické sady záznamů s obousměrný posouvání. Toto nastavení je výchozí.  
  
- **dbOpenTable** sadu záznamů typu tabulky s obousměrný posouvání.  
  
- **dbOpenSnapshot** sadu záznamů typu snímek s obousměrný posouvání.  
  
 `lpszSQL`  
 Ukazatel řetězce obsahující jedno z následujících:  
  
-   A **NULL** ukazatel.  
  
-   Název jeden nebo více tabledefs – nebo querydefs – (oddělené čárkami).  
  
-   SQL **vyberte** – příkaz (volitelně i s SQL **kde** nebo **ORDERBY** klauzule).  
  
-   Předávací dotaz.  
  
 `nOptions`  
 Jeden nebo více z níže uvedených možností: Výchozí hodnota je 0. Možné hodnoty jsou následující:  
  
- **dbAppendOnly** pouze můžete přidat nové záznamy (pouze sada dynamické sady záznamů). Tato možnost oznámena znamená, že může pouze přidávat záznamy. Databázové třídy MFC rozhraní ODBC mít připojovacím možnost, která umožňuje záznamů, které mají být načteny a připojí.  
  
- **dbForwardOnly** je snímku dopředné posouvání záznamů.  
  
- **dbSeeChanges** generovat výjimku, pokud jiný uživatel se mění data upravujete.  
  
- **dbDenyWrite** jiných uživatelů nelze upravit, nebo přidejte záznamy.  
  
- **dbDenyRead** jiných uživatelů nelze zobrazit záznamy (pouze sada typ tabulky záznamů).  
  
- **dbReadOnly** můžete zobrazit jenom záznamy; jiných uživatelů můžete je upravit.  
  
- **dbInconsistent** nekonzistentní aktualizace jsou povoleny (pouze sada dynamické sady záznamů).  
  
- **dbConsistent** pouze konzistentní aktualizace jsou povolené (pouze sada dynamické sady záznamů).  
  
> [!NOTE]
>  Konstanty **dbConsistent** a **dbInconsistent** se vzájemně vylučují. Můžete použít jeden nebo druhý, ale ne obojí v dané instanci systému **otevřete**.  
  
 *pTableDef*  
 Ukazatel [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objektu. Tato verze je platná pouze pro sady záznamů typu tabulky. Při použití této možnosti `CDaoDatabase` použitý k vytvoření ukazatele `CDaoRecordset` nepoužívá; místo toho se používá databázi, ve kterém se nachází tabledef.  
  
 *pQueryDef*  
 Ukazatel [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) objektu. Tato verze je platná pouze pro dynamické sady a sady záznamů typu snímek. Při použití této možnosti `CDaoDatabase` použitý k vytvoření ukazatele `CDaoRecordset` nepoužívá; místo toho se používá databázi, ve kterém se nachází querydef.  
  
### <a name="remarks"></a>Poznámky  
 Před voláním **otevřete**, je nutné vytvořit objekt sady záznamů. Chcete-li to provést několika způsoby:  
  
-   Když vytvoříte objekt sady záznamů, můžete předat ukazatel `CDaoDatabase` objekt, který je již otevřeno.  
  
-   Když vytvoříte objekt sady záznamů, můžete předat ukazatel `CDaoDatabase` objekt, který není otevřený. Otevře sadu záznamů `CDaoDatabase` objektu, ale nebude zavřete ho po zavření objektu sady záznamů.  
  
-   Pokud vytvoříte objekt sady záznamů, předat **NULL** ukazatel. Volání objektu sady záznamů `GetDefaultDBName` získat název aplikace Microsoft Access. Otevření souboru MDB. Potom otevře sadu záznamů `CDaoDatabase` objekt a udržuje ho otevřete tak dlouho, dokud sada záznamů je otevřený. Při volání **Zavřít** v sadě záznamů, `CDaoDatabase` také objekt je zavřený.  
  
    > [!NOTE]
    >  Když se otevře sadu záznamů `CDaoDatabase` objektu, otevře se zdroji dat s níže přístup.  
  
 Pro verzi **otevřete** používající `lpszSQL` parametr, jakmile je sada záznamů otevřete můžete načíst záznamy v několika způsoby. První možností je tak, aby měl DFX – funkce vašem `DoFieldExchange`. Druhou možností je použití dynamické vazby voláním `GetFieldValue` – členská funkce. Tyto možnosti se dají implementovat samostatně nebo v kombinaci. Pokud jsou zkombinovány, je nutné předat v příkazu SQL sami na volání **otevřete**.  
  
 Při použití druhé verze **otevřete** kde předáte v `CDaoTableDef` objektu, výsledná sloupce, které bude k dispozici pro vázání prostřednictvím `DoFieldExchange` a DFX mechanismus, anebo vazby dynamicky prostřednictvím `GetFieldValue`.  
  
> [!NOTE]
>  Může volat pouze **otevřete** pomocí `CDaoTableDef` objekt pro sady záznamů typu tabulky.  
  
 Při použití třetí verzi **otevřete** kde předáte v `CDaoQueryDef` objektu, že dotaz bude proveden a výsledný sloupce, které bude k dispozici pro vázání prostřednictvím `DoFieldExchange` a DFX mechanismus, nebo dynamicky vazby prostřednictvím `GetFieldValue`.  
  
> [!NOTE]
>  Může volat pouze **otevřete** pomocí `CDaoQueryDef` objekt pro dynamické sady a sady záznamů typu snímek.  
  
 Pro první verze součásti **otevřete** používající `lpszSQL` parametr záznamy jsou vybrané na základě kritérií, které jsou uvedené v následující tabulce.  
  
|Hodnota `lpszSQL` parametr|Zvolené záznamy jsou určeny|Příklad|  
|--------------------------------------|----------------------------------------|-------------|  
|**HODNOTU NULL**|Řetězec vrácený funkcí `GetDefaultSQL`.||  
|Čárkami oddělený seznam tabledefs – jeden nebo více nebo querydef názvy.|Všechny sloupce znázorněná `DoFieldExchange`.|`"Customer"`|  
|**Vyberte** seznamu sloupců **FROM** seznam tabulek|Zadané sloupce ze zadaného tabledef(s) nebo querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 Součástí postupu je předat **NULL** k **otevřete**; v takovém případě **otevřete** volání `GetDefaultSQL`, přepisovatelné členské funkce, která ClassWizard generuje při vytváření `CDaoRecordset`– odvozené třídy. Tuto hodnotu poskytuje tabledef(s) nebo querydef názvy, které zadáte v ClassWizard. Místo toho lze zadat jiné informace v parametru `lpszSQL`.  
  
 Ať předáte **otevřete** vytvoří konečnou řetězec SQL pro dotaz (řetězec může mít SQL **kde** a **ORDERBY** klauzule připojenou k `lpszSQL` je řetězec Předaný) a potom provede daný dotaz. Můžete zkontrolovat vytvořený řetězec voláním `GetSQL` po volání **otevřete**.  
  
 Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.  
  
 Pokud chcete nastavit možnosti sady záznamů, jako je například filtrování nebo řazení, nastavte `m_strSort` nebo **m_strFilter** po sestavení objektu záznamů, ale před voláním **otevřete**. Pokud chcete aktualizovat záznamy v sadě záznamů po sada záznamů je už otevřený, volejte **Requery –**.  
  
 Když zavoláte **otevřete** na dynamické sady nebo sadu záznamů typu snímek, nebo pokud zdroj dat odkazuje na příkazu SQL nebo tabledef, představující připojené tabulky, nemůžete použít **dbOpenTable** pro typ argument; Pokud tak učiníte, MFC vyvolá výjimku. Chcete-li zjistit, zda objekt tabledef představuje připojené tabulky, vytvořte [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objekt a volání jeho [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) – členská funkce.  
  
 Použití **dbSeeChanges** příznak, pokud chcete změny provedené jiným uživatelem nebo v jiném programu na počítači při úpravě nebo odstranění stejný záznam pro depeše. Například, pokud dva uživatelé začít upravovat na stejné záznam, první uživatel k volání **aktualizace** – členská funkce úspěšné. Když **aktualizace** volá druhého uživatele, `CDaoException` je vyvolána výjimka. Podobně pokud se druhý uživatel se pokusí zavolat **odstranit** odstranit záznam ale již byla změněna první uživatel, `CDaoException` dojde.  
  
 Obvykle když uživatel získá to `CDaoException` při aktualizaci, váš kód by měl aktualizovat obsah pole a načíst nově upravené hodnoty. V případě výjimka Probíhá odstraňování kódu zobrazit nové údaje záznamů uživateli a zprávu s upozorněním, že data se nedávno změnila. Kód v tomto okamžiku můžete požádat o potvrzení, že stále chce uživatel odstranit záznam.  
  
> [!TIP]
>  Použijte možnost posouvání dopředné ( **dbForwardOnly**) ke zlepšení výkonu, pokud vaše aplikace provede jednom průchodu prostřednictvím sady záznamů otevřené ze zdroje dat ODBC.  
  
 Související informace naleznete v tématu "OpenRecordset způsob" v nápovědě rozhraní DAO.  
  
##  <a name="requery"></a>CDaoRecordset::Requery  
 Volání této funkce člena pro opětovné sestavení (Aktualizovat) sady záznamů.  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>Poznámky  
 Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.  
  
 V pořadí sady záznamů tak, aby odrážela přidání a odstranění, které vy nebo jiní uživatelé využívají ke zdroji dat, musíte znovu vytvořit sadu záznamů voláním **Requery –**. Pokud je dynamická sada záznamů, automaticky zobrazuje aktualizace, které vy nebo jiní uživatelé provést na existující záznamy (ale ne dodatky). Pokud je sada záznamů snímku, musí volat **Requery** tak, aby odrážela úpravy ostatní uživatelé a také přidání a odstranění.  
  
 Dynamická sada nebo snímek, volání **Requery** kdykoli chcete znovu vytvořit sadu záznamů pomocí hodnoty parametrů. Nastavte nový filtr nebo řazení nastavením [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) před voláním **Requery –**. Nastavit nové parametry přiřazením nové hodnoty pro parametry datových členů před voláním **Requery –**.  
  
 Pokud se nezdaří pokus o znovu vytvoření sady záznamů, sada záznamů je zavřený. Před voláním **Requery –**, můžete určit, zda může být sada záznamů fokusu voláním [CanRestart](#canrestart) – členská funkce. `CanRestart`není zaručeno, který **Requery** bude úspěšné.  
  
> [!CAUTION]
>  Volání **Requery –** až poté, co můžete volat **otevřete**.  
  
> [!NOTE]
>  Volání metody [Requery](#requery) změny DAO záložky.  
  
 Nelze volat **Requery –** na dynamické sady nebo sadu záznamů typu snímek Pokud volání `CanRestart` vrátí hodnotu 0, ani můžete můžete ji použít v sadě záznamů typu tabulky.  
  
 Pokud oba `IsBOF` a `IsEOF` vrátí nenulovou po zavolání metody **Requery –**, dotaz nevrátil žádné záznamů a záznamů bude obsahovat žádná data.  
  
 Související informace naleznete v tématu "Requery – metoda" v nápovědě rozhraní DAO.  
  
##  <a name="seek"></a>CDaoRecordset::Seek  
 Volání této funkce člen najít záznam v objektu indexované typ tabulky záznamů splňující zadaná kritéria pro aktuální index a že záznam na aktuální záznam.  
  
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
 `lpszComparison`  
 Jeden z výrazů následující řetězec: "<","\<=", "=", "> =", nebo ">".  
  
 `pKey1`  
 Ukazatel [COleVariant](../../mfc/reference/colevariant-class.md) jejíž hodnota odpovídá na první pole v indexu. Požadováno.  
  
 *pKey2*  
 Ukazatel na `COleVariant` jejíž hodnota odpovídá druhé pole v indexu, pokud existuje. Použije se výchozí hodnota **NULL**.  
  
 *pKey3*  
 Ukazatel na `COleVariant` jejíž hodnota odpovídá třetí pole v indexu, pokud existuje. Použije se výchozí hodnota **NULL**.  
  
 *pKeyArray*  
 Ukazatel na poli proměnných. Velikost pole odpovídá počet polí v indexu.  
  
 *nKeys*  
 Celé číslo odpovídající velikost pole, která je počet polí v indexu.  
  
> [!NOTE]
>  Nezadávejte zástupné znaky v klíče. Zástupné znaky způsobí `Seek` vrátit žádné odpovídající záznamy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud najde odpovídající záznamy, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Druhý (pole) verzi nástroje `Seek` pro zpracování indexy pole čtyři nebo více.  
  
 `Seek`Umožňuje vysoce výkonné indexu vyhledávání na sady záznamů typu tabulky. Je nutné nastavit aktuální index voláním `SetCurrentIndex` před voláním `Seek`. Pokud index identifikuje nejedinečný klíčové pole nebo polí `Seek` vyhledá na první záznam, který splňuje kritéria. Pokud nezadáte žádnou index, je vyvolána výjimka.  
  
 Všimněte si, že pokud nejsou vytvoření sady záznamů znakové sady UNICODE, `COleVariant` objekty musí být explicitně deklarován ANSI. To můžete provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formu – konstruktor s `vtSrc` nastavena na `VT_BSTRT` (ANSI) nebo pomocí **COleVariant** funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** s `vtSrc` nastavena na `VT_BSTRT`.  
  
 Při volání `Seek`, předáte jednu nebo více hodnot klíče a operátor porovnání ("<","\<=", "=", "> =", nebo ">"). `Seek`Vyhledá prostřednictvím zadaná pole klíče a vyhledá na první záznam, který splňuje kritériím `lpszComparison` a `pKey1`. Jednou najde, `Seek` vrátí nenulovou hodnotu a díky záznamů aktuální. Pokud `Seek` nepodaří najít shodu, `Seek` vrátí nula, a na aktuální záznam není definován. Pokud používáte rozhraní DAO přímo, je nutné zkontrolovat explicitně NoMatch vlastnost.  
  
 Pokud `lpszComparison` je "=", "> =", nebo ">", `Seek` spustí na začátku index. Pokud `lpszComparison` je "<" nebo "< =", `Seek` spustí na konci index a hledá zpětně, pokud existují duplicitní index položky na konci. V takovém případě `Seek` začíná na libovolného položku mezi duplicitní index položky na konci index.  
  
 Existuje nemusí být aktuální záznam, když používáte `Seek`.  
  
 Vyhledat záznam v dynamické sady nebo sada záznamů typu snímek, která splňuje určité podmínky, použijte operace hledání. Zahrnout všechny záznamy, nikoli pouze ty, které splňují určité podmínky, pomocí operace přesunutí přesouvat mezi záznamy.  
  
 Nelze volat `Seek` na připojené tabulky libovolného typu, protože připojené tabulky musí být otevřen jako dynamické sady nebo sady záznamů typu snímek. Ale při volání `CDaoDatabase::Open` Pokud chcete otevřít přímo instalovatelných ISAM databázi, můžete zavolat `Seek` pro tabulky v databázi, i když výkon může být pomalé.  
  
 Související informace naleznete v tématu "Hledat způsob" v nápovědě rozhraní DAO.  
  
##  <a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition  
 Nastaví počet relativní záznam aktuální záznam. objekt sady záznamů.  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>Parametry  
 *lPosition*  
 Odpovídá pořadové číslo pozice na aktuální záznam v sadě záznamů.  
  
### <a name="remarks"></a>Poznámky  
 Volání metody `SetAbsolutePosition` umožňuje umístit aktuální záznamů ukazatel na konkrétní záznam podle jeho pořadové číslo pozice v dynamické sady nebo sadu záznamů typu snímek. Aktuální počet záznamů můžete také určit voláním [GetAbsolutePosition](#getabsoluteposition).  
  
> [!NOTE]
>  Tato funkce člen je platná pouze pro dynamické sady a sady záznamů typu snímek.  
  
 Hodnota vlastnosti AbsolutePosition podkladového objektu DAO je počítáno od nuly; Hodnota 0 odkazuje na první záznam v sadě záznamů. Nastavení hodnoty vyšší než počet vyplněná záznamy příčiny MFC vyvolá výjimku. Můžete určit počet vyplněná záznamů v sadě záznamů voláním `GetRecordCount` – členská funkce.  
  
 Pokud se odstraní záznam na aktuální záznam, hodnota vlastnosti AbsolutePosition není definována a MFC vyvolá výjimku, pokud se odkazuje. Nové záznamy jsou přidány na konec pořadí.  
  
> [!NOTE]
>  Tato vlastnost není určena pro použití jako náhradní číslo záznamu. Záložky se stále doporučeným způsobem zachování a vrátilo se do dané pozici a jsou jediný způsob, jak umístit na aktuální záznam všech typů objektů sady záznamů, které podporují záložky. Na konkrétní pozici daného záznamu změní, když jsou záznamy předcházející ji odstranit. Je také žádné záruku, že daný záznam budou mít stejné absolutní umístění, pokud sada záznamů je znovu vytvořit znovu vzhledem k tomu, že není zaručena pořadí jednotlivých záznamů v rámci sady záznamů, pokud není vytvořená pomocí příkazu SQL  **ORDERBY** klauzule.  
  
 Související informace naleznete v tématu "AbsolutePosition vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="setbookmark"></a>CDaoRecordset::SetBookmark  
 Volání této funkce člen na pozici sadu záznamů na záznam obsahující zadanou záložkou.  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) objekt obsahující hodnotu záložku pro konkrétní záznam.  
  
### <a name="remarks"></a>Poznámky  
 Při vytvoření nebo otevřít objekt sady záznamů, každý z jeho záznamy již má jedinečný záložku. Záložky na aktuální záznam můžete načíst pomocí volání `GetBookmark` a ukládání hodnota, která má `COleVariant` objektu. Se později mohli vrátit na tento záznam voláním `SetBookmark` pomocí hodnoty uložené záložky.  
  
> [!NOTE]
>  Volání metody [Requery](#requery) změny DAO záložky.  
  
 Všimněte si, že pokud nejsou vytvoření sady záznamů znakové sady UNICODE, `COleVariant` objekt musí být explicitně deklarován ANSI. To můžete provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formu – konstruktor s `vtSrc` nastavena na `VT_BSTRT` (ANSI) nebo pomocí **COleVariant** funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** s `vtSrc` nastavena na `VT_BSTRT`.  
  
 Související informace najdete v tématech "Záložku vlastnost" a Bookmarkable vlastnost"v nápovědě rozhraní DAO.  
  
##  <a name="setcachesize"></a>CDaoRecordset::SetCacheSize  
 Volání této funkce člen nastavit počet záznamů v mezipaměti.  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>Parametry  
 `lSize`  
 Určuje počet záznamů. Typické hodnota je 100. Hodnota 0 vypne ukládání do mezipaměti. Nastavení musí být mezi 5 a 1200 záznamů. Mezipaměti může použít značné množství paměti.  
  
### <a name="remarks"></a>Poznámky  
 Mezipaměť je místo v místní paměti, která obsahuje data naposledy načtená ze serveru, v případě, že data požádat znovu, když aplikace běží. Ukládání dat zlepšuje výkon aplikace, která načte data ze vzdáleného serveru prostřednictvím objektů sady záznamů dynamické sady. Pokud se požaduje data, databázový stroj Microsoft Jet nejprve hledá v mezipaměti pro požadovaná data místo načítání ze serveru, který trvá déle. Data, která nepochází z zdroje dat ODBC není uložen v mezipaměti.  
  
 Všechny zdroje dat ODBC, jako je například připojené tabulky, může mít místní mezipaměti. Chcete-li vytvořit mezipaměť, otevřete objekt sady záznamů ve zdroji dat vzdáleného volání `SetCacheSize` a `SetCacheStart` členských funkcí a pak volání `FillCache` – členská funkce nebo krok prostřednictvím záznamy pomocí jedné z operace Move. `lSize` Parametr `SetCacheSize` – členská funkce může být založen na počet záznamů, vaše aplikace může spolupracovat s najednou. Například pokud používáte sadu záznamů jako zdroj dat, který se má zobrazit na obrazovce, můžete předat `SetCacheSize` `lSize` parametr jako 20 zobrazíte 20 záznamů najednou.  
  
 Související informace naleznete v tématu "Velikost paměti, vlastnosti CacheStart" v nápovědě rozhraní DAO.  
  
##  <a name="setcachestart"></a>CDaoRecordset::SetCacheStart  
 Volání této funkce člen k určení záložku na první záznam v sadě záznamů do mezipaměti.  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>Parametry  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) určující záložku na první záznam v sadě záznamů do mezipaměti.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít hodnotu záložku žádné záznamu `varBookmark` parametr `SetCacheStart` – členská funkce. Ujistěte se, záznam, který chcete spustit mezipaměti s aktuální záznam, vytvořit záložku pro tento záznam pomocí [SetBookmark –](#setbookmark)a předejte jako parametr pro hodnotu záložku `SetCacheStart` – členská funkce.  
  
 Databázový stroj Microsoft Jet požadavky záznamů v mezipaměti rozsahu z mezipaměti a požaduje záznamy mimo rozsah mezipaměti ze serveru.  
  
 Záznamy načteny z mezipaměti nereflektuje změny provedené současně ke zdrojovým datům jiných uživatelů.  
  
 Chcete-li vynutit aktualizaci všech dat uložených v mezipaměti, předat `lSize` parametr `SetCacheSize` jako 0, volání `SetCacheSize` znovu s velikostí mezipaměti jste původně požádal a pak zavolají `FillCache` – členská funkce.  
  
 Všimněte si, že pokud nejsou vytvoření sady záznamů znakové sady UNICODE, `COleVariant` objekt musí být explicitně deklarován ANSI. To můžete provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formu – konstruktor s `vtSrc` nastavena na `VT_BSTRT` (ANSI) nebo pomocí **COleVariant** funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** s `vtSrc` nastavena na `VT_BSTRT`.  
  
 Související informace naleznete v tématu velikost paměti, vlastnosti CacheStart"v nápovědě rozhraní DAO.  
  
##  <a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex  
 Volání této funkce člen nastavit indexu v sadě záznamů typu tabulky.  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 Ukazatel obsahující název indexu, který má být nastavena.  
  
### <a name="remarks"></a>Poznámky  
 Záznamy v základních tabulek nejsou uložené v libovolném pořadí. Nastavení indexu změny pořadí vrácených z databáze záznamů, ale nemá vliv na pořadí, ve kterém jsou uloženy záznamy. Zadaný index musí být již definován. Pokud se pokusíte použít objekt index, který neexistuje, nebo pokud index není nastaven při volání [Seek](#seek), MFC vyvolá výjimku.  
  
 Můžete vytvořit nový index pro tabulku voláním [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) a přidávání nového indexu do kolekce indexů základní tabledef voláním [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append), a znovu spustit sadu záznamů.  
  
 Pouze pomocí indexy definovaný pro základní tabledef lze provést řazení záznamů vrácených ze sady záznamů typu tabulky. Chcete-li záznamy v některé jiné pořadí řazení, můžete otevřít dynamické sady nebo sadu záznamů typu snímek pomocí SQL **ORDERBY** klauzule uložené v [CDaoRecordset::m_strSort](#m_strsort).  
  
 Související informace najdete v tématu "Index objekt" a definice "aktuální index" v nápovědě rozhraní DAO.  
  
##  <a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty  
 Volání této funkce člena na příznak pole datových členů sady záznamů jako změněné nebo jako beze změny.  
  
```  
void SetFieldDirty(
    void* pv,  
    BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Obsahuje pole datového člena v sadě záznamů adresu nebo **NULL**. Pokud **NULL**, jsou označeny všechna pole datových členů v sadě záznamů. (C++ **NULL** není stejná jako hodnota Null v terminologii databáze, což znamená "žádná hodnota s".)  
  
 `bDirty`  
 **Hodnota TRUE,** Pokud pole datového člena je označen jako "nesprávné" (změněné). V opačném případě **FALSE** Pokud pole datového člena je označen jako "čisté" (beze změny).  
  
### <a name="remarks"></a>Poznámky  
 Označení pole jako beze změny zajistí, že není aktualizovat pole.  
  
 Značky framework změnit pole datových členů zajistit, že se budou zapisovat do záznamu ve zdroji dat pomocí mechanismus výměna pole záznamu exchange (DFX). Změna hodnoty pole obecně nastaví pole změny automaticky, takže bude málokdy potřeba volat `SetFieldDirty` sami, ale můžete někdy chtít zajistit, že sloupce budou explicitně aktualizovat nebo vložit bez ohledu na to, jaké hodnota je v datech pole člen. DFX mechanismus využívá použití **PSEUDONULL**. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
 Pokud není používán mechanismus dvojité ukládání do vyrovnávací paměti, změna pole nenastaví automaticky pole jako neaktualizovaní. V takovém případě bude nutné explicitně nastavit pole jako neaktualizovaní. Příznak obsažené v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tato kontrola automatické pole.  
  
> [!NOTE]
>  Volání této funkce člen až poté, co můžete volat [upravit](#edit) nebo [AddNew](#addnew).  
  
 Pomocí **NULL** pro první argument funkce uplatňovat pro všechny funkce **outputColumn** polí není **param** polí v `CDaoFieldExchange`. Například volání  
  
 [!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 Nastaví pouze **outputColumn** polí k **NULL**; **param** pole, zůstanou beze změn.  
  
 Při práci **param**, musíte zadat adresu skutečného jednotlivých **param** chcete pracovat, jako například:  
  
 [!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 To znamená, že nelze nastavit všechny **param** polí k **NULL**, stejně jako **outputColumn** pole.  
  
 `SetFieldDirty`se implementuje pomocí `DoFieldExchange`.  
  
##  <a name="setfieldnull"></a>CDaoRecordset::SetFieldNull  
 Volání této funkce člena na příznak pole datových členů sady záznamů jako hodnotu Null (konkrétně nutnosti žádná hodnota) nebo jinou hodnotu než Null.  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 Obsahuje pole datového člena v sadě záznamů adresu nebo **NULL**. Pokud **NULL**, jsou označeny všechna pole datových členů v sadě záznamů. (C++ **NULL** není stejná jako hodnota Null v terminologii databáze, což znamená "žádná hodnota s".)  
  
 `bNull`  
 Nenulové hodnoty, pokud je pole data člen bude označen jako s žádnou hodnotu (Null). Jinak hodnota 0, pokud datový člen pole bude označen jako nesmí být nulová.  
  
### <a name="remarks"></a>Poznámky  
 `SetFieldNull`se používá pro pole hranice ve `DoFieldExchange` mechanismus.  
  
 Když přidáte nový záznam do sady záznamů, jsou všechny datové členy původně nastavená na hodnotu Null a označené jako "nesprávné" (změněné). Pokud načítáte záznam ze zdroje dat, její sloupce buď již mít hodnoty, nebo hodnotu Null. Pokud není vhodné vytvořit pole hodnotu Null, [CDaoException](../../mfc/reference/cdaoexception-class.md) je vyvolána výjimka.  
  
 Pokud používáte mechanismus dvojité ukládání do vyrovnávací paměti, například pokud chcete konkrétně určíte pole na aktuální záznam, který nemá hodnotu volání `SetFieldNull` s `bNull` nastavena na **TRUE** na příznak jako hodnotu Null. Pokud byl dříve označená pole hodnotu Null a teď chcete u ní hodnotu, jednoduše nastavte ho na novou hodnotu. Nemáte odeberte příznak Null s `SetFieldNull`. Chcete-li zjistit, zda pole může mít hodnotu Null, volejte [IsFieldNullable](#isfieldnullable).  
  
 Pokud nepoužíváte mechanismus dvojité ukládání do vyrovnávací paměti, změna pole nenastaví automaticky pole jako nekonzistentní a nesmí být nulová. Konkrétně je nutné nastavit pole nekonzistence a nesmí být nulová. Příznak obsažené v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) ovládací prvky tato kontrola automatické pole.  
  
 DFX mechanismus využívá použití **PSEUDONULL**. Další informace najdete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).  
  
> [!NOTE]
>  Volání této funkce člen až poté, co můžete volat [upravit](#edit) nebo [AddNew](#addnew).  
  
 Pomocí **NULL** pro první argument funkce se vztahují pouze k funkci **outputColumn** polí není **param** polí v `CDaoFieldExchange`. Například volání  
  
 [!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 Nastaví pouze **outputColumn** polí k **NULL**; **param** pole, zůstanou beze změn.  
  
##  <a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue  
 Volání této funkce člen, nastavit hodnotu pole, podle pořadí pozice nebo změnou hodnoty řetězce.  
  
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
 `lpszName`  
 Ukazatel na řetězec, který obsahuje název pole.  
  
 `varValue`  
 Odkaz na [COleVariant](../../mfc/reference/colevariant-class.md) objekt, který obsahuje hodnotu v polích.  
  
 `nIndex`  
 Celé číslo, které představuje pořadové číslo pozice pole v kolekci polí sady záznamů (počítáno od nuly).  
  
 `lpszValue`  
 Ukazatel na řetězec obsahující hodnotu v polích.  
  
### <a name="remarks"></a>Poznámky  
 Použití `SetFieldValue` a [GetFieldValue](#getfieldvalue) dynamicky svázat pole v době běhu spíše než staticky vazba sloupce pomocí [DoFieldExchange](#dofieldexchange) mechanismus.  
  
 Všimněte si, že pokud nejsou vytvoření sady záznamů znakové sady UNICODE, je nutné použít forma `SetFieldValue` , neobsahuje `COleVariant` parametr nebo `COleVariant` objekt musí být explicitně deklarován ANSI. To můžete provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formu – konstruktor s `vtSrc` nastavena na `VT_BSTRT` (ANSI) nebo pomocí **COleVariant** funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** s `vtSrc` nastavena na `VT_BSTRT`.  
  
 Související informace najdete v tématech "Objekt pole" a "Hodnota vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull  
 Volání této funkce člen má být nastavena na hodnotu Null.  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index pole v sadě záznamů, pro vyhledávání indexem.  
  
 `lpszName`  
 Název pole v sadě záznamů pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 C++ **NULL** není stejná jako hodnota Null, což v terminologii databáze znamená "s žádnou hodnotu."  
  
 Související informace najdete v tématech "Objekt pole" a "Hodnota vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="setlockingmode"></a>CDaoRecordset::SetLockingMode  
 Volání této funkce člen nastavení uzamčení pro sadu záznamů typu.  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>Parametry  
 *bPessimistic*  
 Příznak, který určuje typ uzamčení.  
  
### <a name="remarks"></a>Poznámky  
 Kdy pesimistické zamykání je v platnosti, stránka 2 kB, která obsahuje záznam upravujete uzamčeno, jakmile zavoláte **upravit** – členská funkce. Stránka je odemčený při volání **aktualizace** nebo **Zavřít** – členská funkce nebo všechny operace přesunutí nebo najít.  
  
 Když optimistické zamykání je v platnosti, stránka 2 kB, která obsahuje záznam uzamčeno pouze tehdy, když probíhá aktualizace záznamu **aktualizace** – členská funkce.  
  
 Pokud je uzamčené na stránce, můžete žádný uživatel upravit záznamy na stejné stránce. Když zavoláte `SetLockingMode` a předat nenulovou hodnotu a jiný uživatel již má stránce uzamčen, je vyvolána výjimka při volání **upravit**. Ostatní uživatelé mohou číst data z uzamčených stránek.  
  
 Když zavoláte `SetLockingMode` s hodnotou nula a novější volání **aktualizace** při stránky je uzamčen jiným uživatelem, dojde k výjimce. Chcete-li zobrazit změny k záznamu jiným uživatelem (a ztratit změny), zavolejte `SetBookmark` – členská funkce s hodnotou záložku na aktuální záznam.  
  
 Při práci s zdroje dat ODBC, je vždy optimistické zamykání režimu.  
  
##  <a name="setparamvalue"></a>CDaoRecordset::SetParamValue  
 Volání této funkce člen k nastavení hodnoty parametru v sadě záznamů v době běhu.  
  
```  
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Číselné pozice parametr v kolekci parametrů querydef.  
  
 `var`  
 Hodnota k nastavení; v části poznámky.  
  
 `lpszName`  
 Název parametru, jehož hodnota, kterou chcete nastavit.  
  
### <a name="remarks"></a>Poznámky  
 Parametr musí již byly vytvořeny jako součást řetězec SQL sady záznamů. Parametr můžete přistupovat pomocí názvu nebo pomocí pozici indexu v kolekci.  
  
 Zadejte hodnotu pro nastavení jako `COleVariant` objektu. Informace o nastavení požadovanou hodnotu a pak zadejte vaše `COleVariant` objektů najdete v tématu třídy [COleVariant](../../mfc/reference/colevariant-class.md). Všimněte si, že pokud nejsou vytvoření sady záznamů znakové sady UNICODE, `COleVariant` objekt musí být explicitně deklarován ANSI. To můžete provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **,** `vtSrc` **)** formu – konstruktor s `vtSrc` nastavena na `VT_BSTRT` (ANSI) nebo pomocí **COleVariant** funkce [SetString –](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **,** `vtSrc` **)** s `vtSrc` nastavena na `VT_BSTRT`.  
  
##  <a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull  
 Volání této funkce člen nastavit parametr na hodnotu Null.  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index pole v sadě záznamů, pro vyhledávání indexem.  
  
 `lpszName`  
 Název pole v sadě záznamů pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 C++ **NULL** není stejná jako hodnota Null, což v terminologii databáze znamená "s žádnou hodnotu."  
  
##  <a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition  
 Volání této funkce člen nastavit hodnotu, která změní přibližnou umístění na aktuální záznam v objektu sady záznamů na základě procenta záznamy v sadě záznamů.  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>Parametry  
 *fPosition*  
 Číslo od 0 do 100.  
  
### <a name="remarks"></a>Poznámky  
 Při práci s dynamické sady nebo sadu záznamů typu snímek, nejprve naplnit sadu záznamů přesunutím na poslední záznam před voláním `SetPercentPosition`. Když zavoláte `SetPercentPosition` před plně sestavování sady záznamů, množství přesun je relativní vzhledem k počtu záznamů získat přístup, které je uvedené hodnotou [getrecordcount –](#getrecordcount). Můžete přesunout na poslední záznam volání `MoveLast`.  
  
 Jakmile zavoláte `SetPercentPosition`, změní na aktuální záznam na přibližnou pozici odpovídající této hodnotě.  
  
> [!NOTE]
>  Volání metody `SetPercentPosition` přesunout na aktuální záznam na konkrétní záznam v sadě záznamů se nedoporučuje. Volání [SetBookmark](#setbookmark) členské funkce místo.  
  
 Související informace naleznete v tématu "PercentPosition vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="update"></a>CDaoRecordset::Update  
 Volání této funkce člen po volání `AddNew` nebo **upravit** – členská funkce.  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>Poznámky  
 Toto volání je nutné pro dokončení `AddNew` nebo **upravit** operaci.  
  
 Obě `AddNew` a **upravit** příprava ve kterém je umístěn přidané nebo upravených dat vyrovnávací paměti pro ukládání ke zdroji dat. **Aktualizace** uloží data. Jsou aktualizovány pouze pole označené nebo detekované jako změnit.  
  
 Pokud zdroj dat podporuje transakce, můžete provést **aktualizace** volání (a odpovídající `AddNew` nebo **upravit** volání) součástí transakce.  
  
> [!CAUTION]
>  Když zavoláte **aktualizace** bez předchozího volání `AddNew` nebo **upravit**, **aktualizace** vyvolá `CDaoException`. Když zavoláte `AddNew` nebo **upravit**, musí volat **aktualizace** před voláním [MoveNext](#movenext) nebo zavřete připojení ke zdroji dat nebo sady záznamů. Jinak vaše změny budou ztraceny bez oznámení.  
  
 Když objekt sady záznamů pessimistically uzamčené v prostředí s více uživateli, zůstane uzamčen od okamžiku záznamu **upravit** se používá, dokud nebude aktualizaci. Pokud sada záznamů je ideálním případě uzamčené, záznamu je uzamčena a porovnání s předem upravený záznam těsně před je aktualizována v databázi. Pokud záznam došlo ke změně vzhledem k tomu, že jste volali metodu **upravit**, **aktualizace** operace selže a MFC vyvolá výjimku. Můžete změnit režim uzamčení s `SetLockingMode`.  
  
> [!NOTE]
>  Optimistické zamykání se vždy na externí databáze formáty, například rozhraní ODBC a instalovat ISAM používá.  
  
 Související informace najdete v tématech "AddNew – metoda", "CancelUpdate metodu", "Odstranit způsob", "Změněno vlastnost", "Metoda aktualizace" a "EditMode vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)
