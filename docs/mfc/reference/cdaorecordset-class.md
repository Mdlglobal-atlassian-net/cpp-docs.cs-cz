---
title: CDaoRecordset – třída
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
ms.openlocfilehash: 6a1475d1b0bc083cfd180ea5a211e752c973e2f8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754677"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset – třída

Představuje sadu záznamů vybraných ze zdroje dat.

## <a name="syntax"></a>Syntaxe

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Sada záznamů CDao::CDaoRecordset](#cdaorecordset)|Vytvoří `CDaoRecordset` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Sada záznamů CDao:AddNew](#addnew)|Připravuje se na přidání nového záznamu. [Chcete-li](#update) dokončit přidání, dokončete aktualizaci.|
|[Sada cdaorekordů::CanAppend](#canappend)|Vrátí nenulovou, pokud lze nové záznamy přidat do sady záznamů pomocí členské funkce [AddNew.](#addnew)|
|[Sada cdaorekordů::CanBookmark](#canbookmark)|Vrátí nenulovou hodnotu, pokud sada záznamů podporuje záložky.|
|[Sada záznamů CDao::Zrušit aktualizaci](#cancelupdate)|Zruší všechny čekající aktualizace z důvodu [operace Upravit](#edit) nebo [PřidatNový.](#addnew)|
|[Sada záznamů CDao::CanRestart](#canrestart)|Vrátí nenulovou, pokud lze [dotaz requery](#requery) znovu spustit a znovu spustit dotaz sady záznamů.|
|[Sada rekordů CDao::CanScroll](#canscroll)|Vrátí nenulovou hodnotu, pokud můžete procházet záznamy.|
|[Sada záznamů CDao:CanTransact](#cantransact)|Vrátí nenulovou, pokud zdroj dat podporuje transakce.|
|[Sada záznamů CDao::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud lze sadu záznamů aktualizovat (můžete přidávat, aktualizovat nebo odstraňovat záznamy).|
|[Sada záznamů CDao::Zavřít](#close)|Zavře sadu záznamů.|
|[CDaoRecordset::Delete](#delete)|Odstraní aktuální záznam ze sady záznamů. Po odstranění je nutné explicitně přejít na jiný záznam.|
|[Sada záznamů CDao::DoFieldExchange](#dofieldexchange)|Nazývá se výměna dat (v obou směrech) mezi datovými členy pole sady záznamů a odpovídajícím záznamem ve zdroji dat. Implementuje výměnu pole záznamu DAO (DFX).|
|[Sada záznamů CDao::Upravit](#edit)|Připraví změny aktuálního záznamu. Volání `Update` k dokončení úpravy.|
|[Sada záznamů CDao:FillCache](#fillcache)|Vyplní celou místní mezipaměť nebo její část pro objekt sady záznamů, který obsahuje data ze zdroje dat ODBC.|
|[Sada záznamů CDao::Najít](#find)|Vyhledá první, další, předchozí nebo poslední umístění určitého řetězce v sadě záznamů typu dynaset, která splňuje zadaná kritéria a umožňuje zaznamenat aktuální záznam.|
|[Sada záznamů CDao::FindFirst](#findfirst)|Vyhledá první záznam v sadě záznamů typu dynaset nebo snímek, který splňuje zadaná kritéria a způsobí, že tento záznam zaznamená aktuální záznam.|
|[Sada rekordů CDao::FindLast](#findlast)|Vyhledá poslední záznam v sadě záznamů typu dynaset nebo snímek, který splňuje zadaná kritéria a způsobí, že tento záznam zaznamená aktuální záznam.|
|[Sada záznamů CDao::FindNext](#findnext)|Vyhledá další záznam v sadě záznamů typu dynaset nebo snímek, která splňuje zadaná kritéria a způsobí, že tento záznam zaznamená aktuální záznam.|
|[Sada záznamů CDao:FindPrev](#findprev)|Vyhledá předchozí záznam v sadě záznamů typu dynaset nebo snímek, která splňuje zadaná kritéria a způsobí, že tento záznam zaznamená aktuální záznam.|
|[Sada záznamů CDao::GetAbsolutePosition](#getabsoluteposition)|Vrátí číslo záznamu aktuálního záznamu objektu sady záznamů.|
|[Sada záznamů CDao::GetBookmark](#getbookmark)|Vrátí hodnotu, která představuje záložku v záznamu.|
|[Sada záznamů CDao::GetCacheSize](#getcachesize)|Vrátí hodnotu, která určuje počet záznamů v sadě záznamů typu dynaset obsahující data, která mají být místně uložena do mezipaměti ze zdroje dat ODBC.|
|[Sada záznamů CDao::GetCacheStart](#getcachestart)|Vrátí hodnotu, která určuje záložku prvního záznamu v sadě záznamů, který má být uložen do mezipaměti.|
|[Sada záznamů CDao::GetCurrentIndex](#getcurrentindex)|Vrátí `CString` hodnotu obsahující název indexu naposledy použitý na indexovaném `CDaoRecordset`typu tabulky .|
|[Sada záznamů CDao::GetDateCreated](#getdatecreated)|Vrátí datum a čas vytvoření `CDaoRecordset` základní tabulky, která je podkladem objektu.|
|[Sada záznamů CDao::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny provedené v návrhu základní `CDaoRecordset` tabulky, která je základem objektu.|
|[Sada záznamů CDao::GetDefaultDBName](#getdefaultdbname)|Vrátí název výchozího zdroje dat.|
|[Sada záznamů CDao::GetDefaultSQL](#getdefaultsql)|Volána k získání výchozího řetězce SQL ke spuštění.|
|[Sada záznamů CDao::GetEditMode](#geteditmode)|Vrátí hodnotu, která označuje stav úprav pro aktuální záznam.|
|[Sada záznamů CDao::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v sadě záznamů.|
|[Sada záznamů CDao::GetFieldInfo](#getfieldinfo)|Vrátí určité druhy informací o polích v sadě záznamů.|
|[Sada záznamů CDao::Hodnota GetFieldValue](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|
|[Sada záznamů CDao::GetIndexCount](#getindexcount)|Načte počet indexů v tabulce, která je základem sady záznamů.|
|[Sada záznamů CDao::GetIndexInfo](#getindexinfo)|Vrátí různé druhy informací o indexu.|
|[Sada záznamů CDao::GetLastModifiedBookmark](#getlastmodifiedbookmark)|Slouží k určení naposledy přidaného nebo aktualizovaného záznamu.|
|[Sada záznamů CDao::GetLockingMode](#getlockingmode)|Vrátí hodnotu, která označuje typ uzamčení, který je v platnosti během úprav.|
|[Sada záznamů CDao::GetName](#getname)|Vrátí `CString` název sady záznamů.|
|[Sada záznamů CDao::GetParamValue](#getparamvalue)|Načte aktuální hodnotu zadaného parametru uloženého v podkladovém objektu DAOParameter.|
|[Sada záznamů CDao::GetPercentPosition](#getpercentposition)|Vrátí pozici aktuálního záznamu jako procento z celkového počtu záznamů.|
|[Sada záznamů CDao::GetRecordCount](#getrecordcount)|Vrátí počet záznamů, ke nini přistupuje v objektu sady záznamů.|
|[Sada záznamů CDao::GetSQL](#getsql)|Získá řetězec SQL slouží k výběru záznamů pro sadu záznamů.|
|[Sada záznamů CDao::GetType](#gettype)|Nazývá se určit typ sady záznamů: typ tabulky, dynaset typu nebo snímek typu.|
|[Sada záznamů CDao::Pravidlo ověření pravosti](#getvalidationrule)|Vrátí `CString` hodnotu obsahující, která ověřuje data při zadávání do pole.|
|[Sada záznamů CDao::GetValidationText](#getvalidationtext)|Načte text, který se zobrazí, pokud není splněno ověřovací pravidlo.|
|[Sada záznamů CDao::IsBOF](#isbof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna před prvním záznamem. Neexistuje žádný aktuální záznam.|
|[Sada záznamů CDao:IsDeleted](#isdeleted)|Vrátí nenulovou hodnotu, pokud je sada záznamů umístěna na odstraněný záznam.|
|[Sada záznamů CDao:IsEOF](#iseof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna za posledním záznamem. Neexistuje žádný aktuální záznam.|
|[Sada záznamů CDao::IsFieldDirty](#isfielddirty)|Vrátí nenulovou hodnotu, pokud bylo změněno zadané pole v aktuálním záznamu.|
|[Sada záznamů CDao::Hodnota IsFieldNull](#isfieldnull)|Vrátí nenulovou hodnotu, pokud je zadané pole v aktuálním záznamu Null (bez hodnoty).|
|[Sada záznamů CDao::Hodnotitelné hodnotu Hodnotitelné hodnotou](#isfieldnullable)|Vrátí nenulovou hodnotu, pokud lze zadané pole v aktuálním záznamu nastavit na hodnotu Null (bez hodnoty).|
|[Sada rekordů CDao::IsOpen](#isopen)|Vrátí nenulovou, pokud byla dříve volána [otevřená.](#open)|
|[Sada rekordů CDao::Přesunout](#move)|Umístí sadu záznamů na zadaný počet záznamů z aktuálního záznamu v obou směrech.|
|[Sada rekordů CDao::MoveFirst](#movefirst)|Umístí aktuální záznam na první záznam v sadě záznamů.|
|[Sada rekordů CDao::MoveLast](#movelast)|Umístí aktuální záznam na poslední záznam v sadě záznamů.|
|[Sada rekordů CDao::MoveNext](#movenext)|Umístí aktuální záznam na další záznam v sadě záznamů .|
|[Sada rekordů CDao:MovePrev](#moveprev)|Umístí aktuální záznam na předchozí záznam v sadě záznamů.|
|[Sada záznamů CDao::Otevřít](#open)|Vytvoří novou sadu záznamů z tabulky, sady dynasenebo snímku.|
|[Sada záznamů CDao::Redotaz](#requery)|Znovu spustí dotaz sady záznamů a aktualizuje vybrané záznamy.|
|[Sada rekordů CDao::Hledat](#seek)|Vyhledá záznam v objektu sady záznamů typu indexované tabulky, který splňuje zadaná kritéria pro aktuální index a způsobí, že tento záznam bude mít aktuální záznam.|
|[Sada rekordů CDao::Nastavitabsolutní pozici](#setabsoluteposition)|Nastaví číslo záznamu aktuálního záznamu objektu sady záznamů.|
|[Sada záznamů CDao:SetBookmark](#setbookmark)|Umístí sadu záznamů na záznam obsahující zadanou záložku.|
|[Sada záznamů CDao:SetSet](#setcachesize)|Nastaví hodnotu, která určuje počet záznamů v sadě záznamů typu dynaset obsahující data, která mají být místně uložena do mezipaměti ze zdroje dat ODBC.|
|[Sada záznamů CDao:SetSet](#setcachestart)|Nastaví hodnotu, která určuje záložku prvního záznamu v sadě záznamů, který má být uložen do mezipaměti.|
|[Sada záznamů CDao:SetCurrentIndex](#setcurrentindex)|Nazývá nastavit index na sadu záznamů typu tabulky.|
|[Sada rekordů CDao:SetFieldDirty](#setfielddirty)|Označí zadané pole v aktuálním záznamu jako změněné.|
|[Sada záznamů CDao:SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuálním záznamu na Hodnotu Null (bez hodnoty).|
|[Sada záznamů CDao::SetFieldValue](#setfieldvalue)|Nastaví hodnotu pole v sadě záznamů.|
|[Sada záznamů CDao::SetFieldValueNull](#setfieldvaluenull)|Nastaví hodnotu pole v sadě záznamů na Hodnotu Null. (bez hodnoty).|
|[Sada záznamů CDao:SetLockingMode](#setlockingmode)|Nastaví hodnotu, která označuje typ zamykání, který se má projevit během úprav.|
|[Sada záznamů CDao::SetParamValue](#setparamvalue)|Nastaví aktuální hodnotu zadaného parametru uloženého v podkladovém objektu DAOParameter.|
|[Sada záznamů CDao::SetParamValueNull](#setparamvaluenull)|Nastaví aktuální hodnotu zadaného parametru na Hodnotu Null (bez hodnoty).|
|[Sada záznamů CDao:SetPercentPosition](#setpercentposition)|Nastaví pozici aktuálního záznamu na umístění odpovídající procentu celkového počtu záznamů v sadě záznamů.|
|[Sada záznamů CDao::Aktualizovat](#update)|Dokončí operaci `AddNew` `Edit` nebo operaci uložením nových nebo upravených dat do zdroje dat.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[Sada záznamů CDao::m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Obsahuje příznak označující, zda jsou pole automaticky označena jako změněná.|
|[Sada záznamů CDao::m_nFields](#m_nfields)|Obsahuje počet datových členů pole ve třídě sady záznamů a počet sloupců vybraných sadou záznamů ze zdroje dat.|
|[Sada záznamů CDao::m_nParams](#m_nparams)|Obsahuje počet datových členů parametrů ve třídě sady záznamů – počet parametrů předaných s dotazem sady záznamů.|
|[Sada záznamů CDao::m_pDAORecordset](#m_pdaorecordset)|Ukazatel na rozhraní DAO, které je základem objektu sady záznamů.|
|[Sada záznamů CDao::m_pDatabase](#m_pdatabase)|Zdrojová databáze pro tuto sadu výsledků. Obsahuje ukazatel na objekt [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)|
|[Sada záznamů CDao::m_strFilter](#m_strfilter)|Obsahuje řetězec používaný k vytvoření příkazu SQL **WHERE.**|
|[Sada záznamů CDao::m_strSort](#m_strsort)|Obsahuje řetězec používaný k vytvoření příkazu POŘADÍ SQL **BY.**|

## <a name="remarks"></a>Poznámky

Objekty označované `CDaoRecordset` jako "sady záznamů" jsou k dispozici v následujících třech formulářích:

- Sady záznamů typu tabulka představují základní tabulku, kterou můžete použít ke kontrole, přidání, změně nebo odstranění záznamů z jedné databázové tabulky.

- Sady záznamů typu Dynaset jsou výsledkem dotazu, který může mít aktualizovatelné záznamy. Tyto sady záznamů jsou sadou záznamů, které můžete použít ke kontrole, přidání, změně nebo odstranění záznamů z podkladové databázové tabulky nebo tabulek. Sady záznamů typu Dynaset mohou obsahovat pole z jedné nebo více tabulek v databázi.

- Sady záznamů typu snímek jsou statickou kopií sady záznamů, které lze použít k vyhledání dat nebo generování sestav. Tyto sady záznamů mohou obsahovat pole z jedné nebo více tabulek v databázi, ale nelze je aktualizovat.

Každý formulář sady záznamů představuje sadu záznamů opravených v době otevření sady záznamů. Při přechodu na záznam v sadě záznamů typu tabulka nebo sady záznamů typu dynaset odráží změny provedené v záznamu po otevření sady záznamů, a to buď jinými uživateli, nebo jinými sadami záznamů v aplikaci. (Sadu záznamů typu snímek nelze aktualizovat.) Můžete použít `CDaoRecordset` přímo nebo odvodit třídu sady záznamů specifické pro aplikaci z `CDaoRecordset`aplikace . Pak můžete:

- Procházejte záznamy.

- Nastavte index a rychle vyhledejte záznamy pomocí [seek](#seek) (pouze sady záznamů typu tabulka).

- Najít záznamy na základě porovnání řetězců:\<"<", " =", "=", ">=" nebo ">" (sady záznamů typu dynaset a snímek).

- Aktualizujte záznamy a zadejte režim uzamčení (s výjimkou sad záznamů typu snímek).

- Filtrujte sadu záznamů, abyste omezili, které záznamy vybere z těch, které jsou k dispozici ve zdroji dat.

- Seřaďte sadu záznamů.

- Parametrizujte sadu záznamů pro přizpůsobení jejího výběru informacemi, které nejsou známy až do spuštění.

Třída `CDaoRecordset` dodává rozhraní podobné jako `CRecordset`třídy . Hlavní rozdíl je, `CDaoRecordset` že třída přistupuje k datům prostřednictvím objektu přístupu k datům (DAO) na základě OLE. Třída `CRecordset` přistupuje k systému DBMS prostřednictvím připojení otevřené databáze (ODBC) a ovladači ODBC pro tento systém DBMS.

> [!NOTE]
> Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Stále můžete přistupovat ke zdrojům dat ODBC pomocí tříd DAO; Třídy DAO obecně nabízejí vynikající funkce, protože jsou specifické pro databázový stroj Microsoft Jet.

Můžete použít `CDaoRecordset` přímo nebo odvodit třídu z `CDaoRecordset`. Chcete-li použít třídu sady záznamů v obou případech, otevřete databázi a `CDaoDatabase` vytvořte objekt sady záznamů a předejte konstruktoru ukazatel objektu. Můžete také vytvořit `CDaoRecordset` objekt a nechat knihovnu MFC vytvořit dočasný `CDaoDatabase` objekt za vás. Potom zavolejte člennou funkci [Open](#open) sady záznamů a určete, zda se jedná o sadu záznamů typu tabulka, sadu záznamů typu dynaset nebo sadu záznamů typu snímek. Volání `Open` vybere data z databáze a načte první záznam.

Pomocí členských funkcí objektu a datových členů můžete procházet záznamy a pracovat s nimi. Dostupné operace závisí na tom, zda se jedná o sadu záznamů typu tabulka, sadu záznamů typu dynaset nebo sadu záznamů typu snímek a zda je aktualizovatelná nebo jen pro čtení – to závisí na schopnostech databáze nebo zdroje dat připojení k otevřené databázi (ODBC). Chcete-li aktualizovat záznamy, které mohly být od `Open` volání změněny nebo přidány, zavolejte člennou funkci [Requery objektu.](#requery) Volání `Close` členské funkce objektu a zničit objekt po dokončení s ním.

`CDaoRecordset`používá výměnu pole záznamů DAO (DFX) k podpoře čtení a aktualizace polí `CDaoRecordset` záznamů `CDaoRecordset`prostřednictvím členů c++ typu bezpečné nebo odvozené třídy. Můžete také implementovat dynamickou vazbu sloupců v databázi bez použití mechanismu DFX pomocí [GetFieldValue](#getfieldvalue) a [SetFieldValue](#setfieldvalue).

Související informace naleznete v tématu "Recordset Object" v nápovědě dao.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>Sada záznamů CDao:AddNew

Volánítéto členské funkce chcete přidat nový záznam do sady záznamů typu tabulka nebo dynaset.

```
virtual void AddNew();
```

### <a name="remarks"></a>Poznámky

Pole záznamu jsou zpočátku Null. (V terminologii databáze null znamená "bez hodnoty" a není stejný jako NULL v jazyce C++.) Chcete-li operaci dokončit, musíte zavolat člennou funkci [Aktualizace.](#update) `Update`uloží změny do zdroje dat.

> [!CAUTION]
> Pokud upravíte záznam a potom přejdete na jiný záznam bez volání `Update`, změny budou bez upozornění ztraceny.

Pokud přidáte záznam do sady záznamů typu dynaset voláním [AddNew](#addnew), záznam je viditelný v sadě záznamů a `CDaoRecordset` zahrnut do podkladové tabulky, kde se stane viditelným pro všechny nové objekty.

Pozice nového záznamu závisí na typu sady záznamů:

- V sadě záznamů typu dynaset, kde je vložen nový záznam není zaručena. Toto chování se změnilo s Microsoft Jet 3.0 z důvodu výkonu a souběžnosti. Pokud je vaším cílem, aby nově přidaný záznam zaznamenal aktuální záznam, získejte záložku posledního upraveného záznamu a přesuňte se na tuto záložku:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- V sadě záznamů typu tabulky, pro kterou byl zadán index, jsou záznamy vráceny na správné místo v pořadí řazení. Pokud nebyl zadán žádný index, jsou na konci sady záznamů vráceny nové záznamy.

Záznam, který byl aktuální `AddNew` před použitím, zůstává aktuální. Pokud chcete, aby byl nový záznam aktuální a sada záznamů podporuje záložky, zavolejte [SetBookmark](#setbookmark) na záložku určenou nastavením vlastnosti LastModified podkladového objektu sady záznamů DAO. To je užitečné pro určení hodnoty polí čítače (automatického přírůstek) v přidaném záznamu. Další informace naleznete v tématu [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Pokud databáze podporuje transakce, můžete `AddNew` volání součástí transakce. Další informace o transakcích naleznete v tématu třída [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Všimněte si, že byste měli zavolat [CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) před voláním `AddNew`.

Je nezákonné volat `AddNew` sadu záznamů, jejíž [otevřená](#open) členská funkce nebyla volána. A `CDaoException` je vyvolána, `AddNew` pokud voláte sadu záznamů, které nelze připojit. Můžete určit, zda je sada záznamů aktualizovatelná voláním [CanAppend](#canappend).

Rámcové značky změnily datové členy pole, aby bylo zajištěno, že budou zapsány do záznamu na zdroji dat mechanismem výměny pole záznamů DAO (DFX). Změna hodnoty pole obecně nastaví pole dirty automaticky, takže budete zřídka muset volat [SetFieldDirty](#setfielddirty) sami, ale někdy můžete chtít zajistit, že sloupce budou explicitně aktualizovány nebo vloženy bez ohledu na to, jaká hodnota je v datovém členu pole. Mechanismus DFX také využívá použití **PSEUDO NULL**. Další informace naleznete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud mechanismus dvojité vyrovnávací paměti není používán, pak změna hodnoty pole automaticky nenastaví pole jako dirty. V takovém případě bude nutné explicitně nastavit pole dirty. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

> [!NOTE]
> Pokud jsou záznamy s dvojitou vyrovnávací pamětí (to znamená, že je povoleno automatické kontrolu polí), volání `CancelUpdate` obnoví členské proměnné na hodnoty, které měly před `AddNew` nebo `Edit` byly volány.

Související informace naleznete v tématech "AddNew Method", "CancelUpdate Method", "LastModified Property" a "EditMode Property" v nápovědě DAO.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>Sada cdaorekordů::CanAppend

Volání této členské funkce k určení, zda dříve otevřená sada záznamů umožňuje přidat nové záznamy voláním [addnew](#addnew) členské funkce.

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů umožňuje přidávání nových záznamů; jinak 0. `CanAppend`vrátí hodnotu 0, pokud jste sadu záznamů otevřeli jen pro čtení.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Append Method" v nápovědě DAO.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>Sada cdaorekordů::CanBookmark

Volání této členské funkce k určení, zda dříve otevřená sada záznamů umožňuje jednotlivě označit záznamy pomocí záložek.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů podporuje záložky, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud používáte sady záznamů založené výhradně na tabulkách databázového stroje Microsoft Jet, lze záložky použít s výjimkou sad záznamů typu snímek označených jako sady záznamů pouze pro předávání. Ostatní databázové produkty (externí zdroje dat ODBC) nemusí podporovat záložky.

Související informace naleznete v tématu "Bookmarkable Property" v nápovědě DAO.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>Sada záznamů CDao::Zrušit aktualizaci

Členská `CancelUpdate` funkce zruší všechny čekající aktualizace z důvodu [operace Upravit](#edit) nebo [PřidatNový.](#addnew)

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Poznámky

Například pokud aplikace volá `Edit` `AddNew` nebo členské funkce a `CancelUpdate` nevolal [Update](#update), `Edit` `AddNew` zruší všechny změny provedené po nebo byla volána.

> [!NOTE]
> Pokud jsou záznamy s dvojitou vyrovnávací pamětí (to znamená, že je povoleno automatické kontrolu polí), volání `CancelUpdate` obnoví členské proměnné na hodnoty, které měly před `AddNew` nebo `Edit` byly volány.

Pokud neexistuje `Edit` žádná `AddNew` nebo `CancelUpdate` operace čekající na vyřízení, způsobí, že knihovna MFC vyvolat výjimku. Volání [GetEditMode](#geteditmode) členské funkce k určení, zda je čekající operace, která může být zrušena.

Související informace naleznete v tématu "CancelUpdate Method" v nápovědě DAO.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>Sada záznamů CDao::CanRestart

Volání této členské funkce k určení, zda sada záznamů umožňuje restartování jeho `Requery` dotazu (aktualizovat jeho záznamy) voláním členské funkce.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud `Requery` lze volat znovu spustit dotaz sady záznamů, jinak 0.

### <a name="remarks"></a>Poznámky

Sady záznamů typu tabulky `Requery`nepodporují .

Pokud `Requery` není podporována, volejte [Zavřít](#close) a [pak Otevřít](#open) aktualizovat data. Můžete volat `Requery` aktualizaci základního parametrizačního dotazu objektu sady záznamů po změně hodnot parametrů.

Související informace naleznete v tématu "Restartovatelná vlastnost" v nápovědě dao.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>Sada rekordů CDao::CanScroll

Volání této členské funkce k určení, zda sada záznamů umožňuje posouvání.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud můžete procházet záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud voláte `dbForwardOnly` [Otevřít](#open) pomocí , může se sada záznamů posouvat pouze vpřed.

Související informace naleznete v tématu "Umístění ukazatele aktuálního záznamu s dao" v nápovědě DAO.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>Sada záznamů CDao:CanTransact

Volání této členské funkce k určení, zda sada záznamů umožňuje transakce.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud základní zdroj dat podporuje transakce, jinak 0.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Vlastnost transakcí" v nápovědě dao.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>Sada záznamů CDao::CanUpdate

Volání této členské funkce k určení, zda lze aktualizovat sadu záznamů.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze sadu záznamů aktualizovat (přidávat, aktualizovat a odstraňovat záznamy), jinak 0.

### <a name="remarks"></a>Poznámky

Sada záznamů může být jen pro čtení, pokud je základní `dbReadOnly` zdroj dat jen pro čtení nebo pokud jste zadali *pro nOptions* při volání [Open](#open) pro sadu záznamů.

Související informace naleznete v tématech "AddNew Method", "Edit Method", "Delete Method", "Update Method" a "Aktualizovatelná vlastnost" v nápovědě DAO.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>Sada záznamů CDao::CDaoRecordset

Vytvoří `CDaoRecordset` objekt.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabáze*<br/>
Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) nebo hodnotu NULL. Pokud není null `CDaoDatabase` a `Open` členská funkce objektu nebyla volána pro připojení ke zdroji dat, sada záznamů se pokusí otevřít za vás během vlastního volání [Open.](#open) Pokud předáte `CDaoDatabase` hodnotu NULL, objekt je vytvořen a připojen za vás pomocí informací `CDaoRecordset`o zdroji dat, které jste zadali, pokud jste odvodili třídu sady záznamů z aplikace .

### <a name="remarks"></a>Poznámky

Můžete použít `CDaoRecordset` přímo nebo odvodit `CDaoRecordset`třídu specifickou pro aplikaci z aplikace . Pomocí Průvodce classwizard můžete odvodit třídy sady záznamů.

> [!NOTE]
> Pokud odvodíte třídu, `CDaoRecordset` vaše odvozená třída musí zadat vlastní konstruktor. V konstruktoru odvozené třídy, volání `CDaoRecordset::CDaoRecordset`konstruktoru , předávání příslušné parametry spolu s ním.

Předejte null konstruktoru sady `CDaoDatabase` záznamů, aby byl objekt automaticky vytvořen a připojen. Toto je užitečná zkratka, která nevyžaduje `CDaoDatabase` vytvoření a připojení objektu před sestavením sady záznamů. Pokud `CDaoDatabase` objekt není otevřen, objekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) bude také vytvořen pro vás, který používá výchozí pracovní prostor. Další informace naleznete v [tématu CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

## <a name="cdaorecordsetclose"></a><a name="close"></a>Sada záznamů CDao::Zavřít

Zavřením `CDaoRecordset` objektu jej odeberete z kolekce otevřených sad záznamů v přidružené databázi.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Protože `Close` nezničí `CDaoRecordset` objekt, můžete objekt znovu použít `Open` voláním na stejném zdroji dat nebo jiném zdroji dat.

Všechny čekající [příkazy AddNew](#addnew) nebo [Edit](#edit) jsou zrušeny a všechny čekající transakce jsou vráceny zpět. Pokud chcete zachovat čekající dodatky nebo [Update](#update) úpravy, `Close` volejte Update před voláním pro každou sadu záznamů.

Po volání `Open` `Close`můžete volat znovu . To umožňuje znovu použít objekt sady záznamů. Lepší alternativou je zavolat [Requery](#requery), pokud je to možné.

Související informace naleznete v tématu "Close Method" v nápovědě dao.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDaoRecordset::Delete

Voláním této členské funkce odstraňte aktuální záznam v otevřeném objektu sady záznamů typu dynaset nebo table.

```
virtual void Delete();
```

### <a name="remarks"></a>Poznámky

Po úspěšném odstranění jsou datové členy sady záznamů nastaveny na hodnotu Null a chcete-li přesunout odstraněný záznam, musíte explicitně volat jednu z navigačních funkcí sady záznamů [(Přesunout](#move), [Hledat](#seek), [SetBookmark](#setbookmark)a tak dále). Při odstraňování záznamů ze sady záznamů musí být před voláním `Delete`v sadě záznamů aktuální záznam ; v opačném případě knihovna MFC vyvolá výjimku.

`Delete`odebere aktuální záznam a znepřístupní jej. Přestože odstraněný záznam nelze upravit ani použít, zůstane aktuální. Jakmile však přejdete na jiný záznam, nelze odstraněný záznam znovu otečn.

> [!CAUTION]
> Sada záznamů musí být aktualizovatelná a při volání `Delete`musí být v sadě záznamů platný aktuální záznam . Pokud například odstraníte záznam, ale před dalším voláním `Delete` se `Delete` neposunete na nový záznam, vyvolá výjimku [CDaoException](../../mfc/reference/cdaoexception-class.md).

Pokud používáte transakce a voláte členská funkce [CDaoWorkspace::Rollback,](../../mfc/reference/cdaoworkspace-class.md#rollback) můžete zrušit odstranění záznamu. Pokud je základní tabulka primární tabulkou v relaci kaskádového odstranění, odstranění aktuálního záznamu může také odstranit jeden nebo více záznamů v cizí tabulce. Další informace naleznete v definici "kaskádové odstranění" v nápovědě dao.

Na `AddNew` `Edit`rozdíl od `Delete` a volání není následuje `Update`volání .

Související informace naleznete v tématech "AddNew Method", "Edit Method", "Delete Method", "Update Method" a "Aktualizovatelná vlastnost" v nápovědě DAO.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>Sada záznamů CDao::DoFieldExchange

Rozhraní Framework volá tuto členská funkci k automatické výměně dat mezi datovými členy pole objektu sady záznamů a odpovídajícími sloupci aktuálního záznamu ve zdroji dat.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*Pfx*<br/>
Obsahuje ukazatel na `CDaoFieldExchange` objekt. Rámec již nastavil tento objekt k určení kontextu pro operaci výměny v terénu.

### <a name="remarks"></a>Poznámky

Také váže členy dat parametru, pokud existuje, na zástupné symboly parametrů v řetězci příkazu SQL pro výběr sady záznamů. Výměna dat pole, nazývaná DAO záznam oválná výměna polí (DFX), funguje v obou směrech: od datových členů pole sady záznamů až po pole záznamu ve zdroji dat a ze záznamu ve zdroji dat k objektu sady záznamů. Pokud vázajete sloupce dynamicky, `DoFieldExchange`není nutné implementovat .

Jedinou akcí, kterou je `DoFieldExchange` třeba normálně provést k implementaci pro odvozenou třídu sady záznamů, je vytvoření třídy pomocí Průvodce třídou a určení názvů a datových typů datových členů pole. Můžete také přidat kód, co ClassWizard zapíše k určení členů dat parametru. Pokud mají být všechna pole dynamicky vázána, bude tato funkce neaktivní, pokud nezadáte datové členy parametru.

Když deklarujete třídu odvozené sady záznamů pomocí `DoFieldExchange` Průvodce třídou, průvodce za píše přepsání za vás, které se podobá následujícímu příkladu:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>Sada záznamů CDao::Upravit

Volání této členské funkce povolit změny aktuálního záznamu.

```
virtual void Edit();
```

### <a name="remarks"></a>Poznámky

Po volání `Edit` členské funkce se změny provedené v polích aktuálního záznamu zkopírují do vyrovnávací paměti kopírování. Po provedeném požadovaných změnách `Update` záznamu voláním uložte změny. `Edit`uloží hodnoty datových členů sady záznamů. Pokud zavoláte `Edit`, provedete `Edit` změny a pak zavoláte znovu, hodnoty záznamu `Edit` se obnoví na hodnoty, které byly před prvním voláním.

> [!CAUTION]
> Pokud upravíte záznam a potom provedete jakoukoli operaci, která se přesune na jiný záznam bez předchozího volání `Update`, budou změny bez upozornění ztraceny. Pokud navíc zavřete sadu záznamů nebo nadřazenou databázi, bude upravený záznam bez upozornění zahozen.

V některých případech můžete chtít aktualizovat sloupec tím, že je Null (obsahující žádná data). Chcete-li tak `SetFieldNull` učinit, volání s parametrem TRUE označit pole Null; To také způsobí, že sloupec aktualizovat. Pokud chcete, aby bylo pole zapsáno do zdroje dat, `SetFieldDirty` i když se jeho hodnota nezměnila, volání s parametrem TRUE. To funguje i v případě, že pole mělo hodnotu Null.

Rámcové značky změnily datové členy pole, aby bylo zajištěno, že budou zapsány do záznamu na zdroji dat mechanismem výměny pole záznamů DAO (DFX). Změna hodnoty pole obecně nastaví pole dirty automaticky, takže budete zřídka muset volat [SetFieldDirty](#setfielddirty) sami, ale někdy můžete chtít zajistit, že sloupce budou explicitně aktualizovány nebo vloženy bez ohledu na to, jaká hodnota je v datovém členu pole. Mechanismus DFX také využívá použití **PSEUDO NULL**. Další informace naleznete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud mechanismus dvojité vyrovnávací paměti není používán, pak změna hodnoty pole automaticky nenastaví pole jako dirty. V takovém případě bude nutné explicitně nastavit pole dirty. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

Pokud je objekt sady záznamů pesimisticky uzamčen ve víceuživatelském `Edit` prostředí, zůstane záznam uzamčen od doby, kdy se použije, dokud nebude aktualizace dokončena. Pokud je sada záznamů optimisticky uzamčena, záznam je uzamčen a porovnán s předem upraveným záznamem těsně před aktualizací v databázi. Pokud se záznam od `Edit`volání `Update` změnil , operace se nezdaří a knihovna MFC vyvolá výjimku. Režim zamykání `SetLockingMode`můžete změnit pomocí .

> [!NOTE]
> Optimistické zamykání se vždy používá ve formátech externí databáze, jako je například ROZHRANÍ ODBC a instalovatelný ISAM.

Aktuální záznam zůstane aktuální `Edit`i po volání . Chcete-li volat `Edit`, musí existovat aktuální záznam. Pokud neexistuje žádný aktuální záznam nebo pokud sada záznamů neodkazuje na objekt sady záznamů typu open table nebo dynaset, dojde k výjimce. Volání `Edit` způsobí, že `CDaoException` vyvolá za následujících podmínek:

- Neexistuje žádný aktuální záznam.

- Databáze nebo sada záznamů je jen pro čtení.

- Žádná pole v záznamu nejsou aktualizovatelná.

- Databáze nebo sada záznamů byla otevřena pro výhradní použití jiným uživatelem.

- Jiný uživatel uzamkl stránku obsahující váš záznam.

Pokud zdroj dat podporuje transakce, můžete `Edit` volat část transakce. Všimněte si, `CDaoWorkspace::BeginTrans` že `Edit` byste měli zavolat před voláním a po otevření sady záznamů. Všimněte si `CDaoWorkspace::CommitTrans` také, že `Update` volání není `Edit` náhradou za volání k dokončení operace. Další informace o transakcích `CDaoWorkspace`naleznete v tématu class .

Související informace naleznete v tématech "AddNew Method", "Edit Method", "Delete Method", "Update Method" a "Aktualizovatelná vlastnost" v nápovědě DAO.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>Sada záznamů CDao:FillCache

Volání této členské funkce do mezipaměti zadaný počet záznamů ze sady záznamů.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parametry

*pVelikost*<br/>
Určuje počet řádků, které mají být vyplníny v mezipaměti. Pokud tento parametr vynechete, hodnota je určena nastavením vlastnosti CacheSize základního objektu DAO.

*pZnačka*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) určující záložku. Mezipaměť je vyplněna od záznamu označeného touto záložkou. Pokud tento parametr vynechete, bude mezipaměť vyplněna počínaje záznamem označeným vlastností CacheStart podkladového objektu DAO.

### <a name="remarks"></a>Poznámky

Ukládání do mezipaměti zlepšuje výkon aplikace, která načítá nebo načítá data ze vzdáleného serveru. Mezipaměť je místo v místní paměti, které obsahuje data naposledy načtená ze serveru za předpokladu, že data budou pravděpodobně požadována znovu, když je aplikace spuštěna. Pokud jsou požadována data, databázový stroj Microsoft Jet nejprve zkontroluje mezipaměť pro data, nikoli je načítá ze serveru, což trvá déle. Použití ukládání dat do mezipaměti na jiných zdrojích dat od odbc nemá žádný vliv, protože data nejsou uložena v mezipaměti.

Místo čekání na cache, které mají být vyplněny záznamy, jak jsou načteny, `FillCache` můžete explicitně vyplnit mezipaměť kdykoli voláním členské funkce. Jedná se o rychlejší způsob, `FillCache` jak vyplnit mezipaměť, protože načte několik záznamů najednou namísto jednoho najednou. Například při zobrazení každé obrazovky záznamů, můžete mít volání `FillCache` aplikace načíst další screenful záznamů.

Každá databáze ROZHRANÍ ODBC, ke které bude přistupováno pomocí objektů sady záznamů, může mít místní mezipaměť. Chcete-li vytvořit mezipaměť, otevřete objekt sady záznamů ze `SetCacheSize` `SetCacheStart` vzdáleného zdroje dat a potom zavolejte členské funkce sady záznamů. Pokud *lSize* a *lBookmark* vytvoří oblast, která je `SetCacheSize` částečně `SetCacheStart`nebo zcela mimo rozsah určený písmenem a ), část sady záznamů mimo tento rozsah je ignorována a není načtena do mezipaměti. Pokud `FillCache` požaduje více záznamů, než zůstávají ve vzdáleném zdroji dat, jsou načteny pouze zbývající záznamy a není vyvolána žádná výjimka.

Záznamy načtené z mezipaměti neodrážejí změny provedené současně se zdrojovými daty jinými uživateli.

`FillCache`načte pouze záznamy, které ještě nebyly uloženy do mezipaměti. Chcete-li vynutit aktualizaci všech `SetCacheSize` dat uložených v mezipaměti, zavolejte členní funkci s parametrem *lSize* rovným 0, znovu volat `SetCacheSize` s parametrem *lSize* rovnajícímu se velikosti mezipaměti, kterou jste původně požadovali, a potom volat `FillCache`.

Související informace naleznete v tématu "Metoda FillCache" v nápovědě DAO.

## <a name="cdaorecordsetfind"></a><a name="find"></a>Sada záznamů CDao::Najít

Volání této členské funkce vyhledejte konkrétní řetězec v sadě záznamů typu dynaset nebo snímek pomocí operátoru porovnání.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lFindType*<br/>
Hodnota označující typ požadovanou operaci Hledání. Možné hodnoty jsou:

- AFX_DAO_NEXT Najít další umístění odpovídajícího řetězce.

- AFX_DAO_PREV Najít předchozí umístění odpovídajícího řetězce.

- AFX_DAO_FIRST Najděte první umístění odpovídajícího řetězce.

- AFX_DAO_LAST Najít poslední umístění odpovídajícího řetězce.

*lpszFiltr*<br/>
Řetězec výraz (jako **klauzule WHERE** v příkazu SQL bez slova **WHERE**) slouží k vyhledání záznamu. Příklad:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou nalezeny odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Můžete najít první, další, předchozí nebo poslední instance řetězce. `Find`je virtuální funkce, takže ji můžete přepsat a přidat vlastní implementaci. Členské `FindFirst` `FindLast`funkce `FindNext`, `FindPrev` a členské `Find` funkce volají členská `Find` funkce, takže můžete použít k řízení chování všech operací hledání.

Chcete-li vyhledat záznam v sadě záznamů typu tabulka, zavolejte člennou funkci [Seek.](#seek)

> [!TIP]
> Čím menší je sada záznamů, která `Find` máte, tím účinnější bude. Obecně, a zejména s daty ODBC, je lepší vytvořit nový dotaz, který načte pouze požadované záznamy.

Související informace naleznete v tématu "FindFirst, FindLast, FindNext, FindPrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>Sada záznamů CDao::FindFirst

Volání této členské funkce najít první záznam, který odpovídá zadané podmínce.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFiltr*<br/>
Řetězec výraz (jako **klauzule WHERE** v příkazu SQL bez slova **WHERE**) slouží k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou nalezeny odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská `FindFirst` funkce zahájí hledání od začátku sady záznamů a vyhledá na konec sady záznamů.

Pokud chcete zahrnout všechny záznamy do hledání (nejen ty, které splňují určitou podmínku), použijte jednu z operací Přesunout k přechodu ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů `Seek` typu tabulky, zavolejte člennou funkci.

Pokud není nalezen záznam odpovídající kritériím, aktuální ukazatel záznamu `FindFirst` není určen a vrátí nulu. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje `FindFirst` `FindNext` kritéria, vyhledá první výskyt, vyhledá další výskyt a tak dále.

> [!CAUTION]
> Pokud upravujete aktuální záznam, nezapomeňte změny uložit `Update` voláním členské funkce před přesunutím na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny budou ztraceny bez upozornění.

Členské `Find` funkce prohledávají umístění a ve směru určeném v následující tabulce:

|Najít operace|Začátek|Směr hledání|
|---------------------|-----------|----------------------|
|`FindFirst`|Začátek sady záznamů|Konec sady záznamů|
|`FindLast`|Konec sady záznamů|Začátek sady záznamů|
|`FindNext`|Aktuální záznam|Konec sady záznamů|
|`FindPrevious`|Aktuální záznam|Začátek sady záznamů|

> [!NOTE]
> Při volání `FindLast`databázový stroj Microsoft Jet plně naplní sadu záznamů před zahájením hledání, pokud to ještě nebylo provedeno. První hledání může trvat déle než následné hledání.

Použití jedné z operací Hledání není `MoveFirst` stejné `MoveNext`jako volání nebo , které však jednoduše provede první nebo následující záznam aktuální bez zadání podmínky. Operaci Hledání můžete sledovat pomocí operace Přesunout.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit aktuální ukazatel záznamu zpět na platný záznam.

- Operaci Hledání nelze použít se sadou záznamů typu posouvání pouze dopředu.

- Při hledání polí obsahujících data byste měli použít formát data v USA (měsíc-den-rok), a to i v případě, že nepoužíváte americkou verzi databázového stroje Microsoft Jet. v opačném případě nemusí být nalezeny odpovídající záznamy.

- Při práci s databázemi ODBC a velkými dynasadami můžete zjistit, že použití operací hledání je pomalé, zejména při práci s velkými sadami záznamů. Můžete zlepšit výkon pomocí dotazů SQL s vlastní **ORDERBY** nebo **WHERE** `CDaoQuerydef` klauzule, parametrdotazy nebo objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v tématu "FindFirst, FindLast, FindNext, FindPrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>Sada rekordů CDao::FindLast

Volání této členské funkce najít poslední záznam, který odpovídá zadané podmínce.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFiltr*<br/>
Řetězec výraz (jako **klauzule WHERE** v příkazu SQL bez slova **WHERE**) slouží k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou nalezeny odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská `FindLast` funkce zahájí hledání na konci sady záznamů a hledá zpět směrem k začátku sady záznamů.

Pokud chcete zahrnout všechny záznamy do hledání (nejen ty, které splňují určitou podmínku), použijte jednu z operací Přesunout k přechodu ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů `Seek` typu tabulky, zavolejte člennou funkci.

Pokud není nalezen záznam odpovídající kritériím, aktuální ukazatel záznamu `FindLast` není určen a vrátí nulu. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje `FindFirst` `FindNext` kritéria, vyhledá první výskyt, vyhledá další výskyt po prvním výskytu a tak dále.

> [!CAUTION]
> Pokud upravujete aktuální záznam, nezapomeňte změny uložit `Update` voláním členské funkce před přesunutím na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny budou ztraceny bez upozornění.

Použití jedné z operací Hledání není `MoveFirst` stejné `MoveNext`jako volání nebo , které však jednoduše provede první nebo následující záznam aktuální bez zadání podmínky. Operaci Hledání můžete sledovat pomocí operace Přesunout.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit aktuální ukazatel záznamu zpět na platný záznam.

- Operaci Hledání nelze použít se sadou záznamů typu posouvání pouze dopředu.

- Při hledání polí obsahujících data byste měli použít formát data v USA (měsíc-den-rok), a to i v případě, že nepoužíváte americkou verzi databázového stroje Microsoft Jet. v opačném případě nemusí být nalezeny odpovídající záznamy.

- Při práci s databázemi ODBC a velkými dynasadami můžete zjistit, že použití operací hledání je pomalé, zejména při práci s velkými sadami záznamů. Můžete zlepšit výkon pomocí dotazů SQL s vlastní **ORDERBY** nebo **WHERE** `CDaoQuerydef` klauzule, parametrdotazy nebo objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v tématu "FindFirst, FindLast, FindNext, FindPrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>Sada záznamů CDao::FindNext

Volání této členské funkce najít další záznam, který odpovídá zadané podmínce.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFiltr*<br/>
Řetězec výraz (jako **klauzule WHERE** v příkazu SQL bez slova **WHERE**) slouží k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou nalezeny odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská `FindNext` funkce zahájí hledání na aktuální mši a vyhledá na konec sady záznamů.

Pokud chcete zahrnout všechny záznamy do hledání (nejen ty, které splňují určitou podmínku), použijte jednu z operací Přesunout k přechodu ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů `Seek` typu tabulky, zavolejte člennou funkci.

Pokud není nalezen záznam odpovídající kritériím, aktuální ukazatel záznamu `FindNext` není určen a vrátí nulu. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje `FindFirst` `FindNext` kritéria, vyhledá první výskyt, vyhledá další výskyt a tak dále.

> [!CAUTION]
> Pokud upravujete aktuální záznam, nezapomeňte změny uložit `Update` voláním členské funkce před přesunutím na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny budou ztraceny bez upozornění.

Použití jedné z operací Hledání není `MoveFirst` stejné `MoveNext`jako volání nebo , které však jednoduše provede první nebo následující záznam aktuální bez zadání podmínky. Operaci Hledání můžete sledovat pomocí operace Přesunout.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit aktuální ukazatel záznamu zpět na platný záznam.

- Operaci Hledání nelze použít se sadou záznamů typu posouvání pouze dopředu.

- Při hledání polí obsahujících data byste měli použít formát data v USA (měsíc-den-rok), a to i v případě, že nepoužíváte americkou verzi databázového stroje Microsoft Jet. v opačném případě nemusí být nalezeny odpovídající záznamy.

- Při práci s databázemi ODBC a velkými dynasadami můžete zjistit, že použití operací hledání je pomalé, zejména při práci s velkými sadami záznamů. Můžete zlepšit výkon pomocí dotazů SQL s vlastní **ORDERBY** nebo **WHERE** `CDaoQuerydef` klauzule, parametrdotazy nebo objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v tématu "FindFirst, FindLast, FindNext, FindPrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>Sada záznamů CDao:FindPrev

Volání této členské funkce najít předchozí záznam, který odpovídá zadané podmínce.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFiltr*<br/>
Řetězec výraz (jako **klauzule WHERE** v příkazu SQL bez slova **WHERE**) slouží k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou nalezeny odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská `FindPrev` funkce zahájí hledání na aktuálním záznamu a hledá zpět směrem k začátku sady záznamů.

Pokud chcete zahrnout všechny záznamy do hledání (nejen ty, které splňují určitou podmínku), použijte jednu z operací Přesunout k přechodu ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů `Seek` typu tabulky, zavolejte člennou funkci.

Pokud není nalezen záznam odpovídající kritériím, aktuální ukazatel záznamu `FindPrev` není určen a vrátí nulu. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje `FindFirst` `FindNext` kritéria, vyhledá první výskyt, vyhledá další výskyt a tak dále.

> [!CAUTION]
> Pokud upravujete aktuální záznam, nezapomeňte změny uložit `Update` voláním členské funkce před přesunutím na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny budou ztraceny bez upozornění.

Použití jedné z operací Hledání není `MoveFirst` stejné `MoveNext`jako volání nebo , které však jednoduše provede první nebo následující záznam aktuální bez zadání podmínky. Operaci Hledání můžete sledovat pomocí operace Přesunout.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit aktuální ukazatel záznamu zpět na platný záznam.

- Operaci Hledání nelze použít se sadou záznamů typu posouvání pouze dopředu.

- Při hledání polí obsahujících data byste měli použít formát data v USA (měsíc-den-rok), a to i v případě, že nepoužíváte americkou verzi databázového stroje Microsoft Jet. v opačném případě nemusí být nalezeny odpovídající záznamy.

- Při práci s databázemi ODBC a velkými dynasadami můžete zjistit, že použití operací hledání je pomalé, zejména při práci s velkými sadami záznamů. Můžete zlepšit výkon pomocí dotazů SQL s vlastní **ORDERBY** nebo **WHERE** `CDaoQuerydef` klauzule, parametrdotazy nebo objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v tématu "FindFirst, FindLast, FindNext, FindPrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>Sada záznamů CDao::GetAbsolutePosition

Vrátí číslo záznamu aktuálního záznamu objektu sady záznamů.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo od 0 do počtu záznamů v sadě záznamů. Odpovídá pořadí aktuálního záznamu v sadě záznamů.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti AbsolutePosition podkladového objektu DAO je založena na nule; nastavení 0 odkazuje na první záznam v sadě záznamů. Počet naplněných záznamů v sadě záznamů můžete určit voláním [GetRecordCount](#getrecordcount). Volání `GetRecordCount` může nějakou dobu trvat, protože musí přistupovat ke všem záznamům k určení počtu.

Pokud neexistuje žádný aktuální záznam, jako když nejsou žádné záznamy v sadě záznamů, - 1 je vrácena. Pokud je aktuální záznam odstraněn, hodnota vlastnosti AbsolutePosition není definována a knihovna MFC vyvolá výjimku, pokud je odkazována. U sad záznamů typu dynaset jsou na konec sekvence přidány nové záznamy.

> [!NOTE]
> Tato vlastnost není určena k použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem, jak zachovat a vrátit se na danou pozici, a jsou jediným způsobem, jak umístit aktuální záznam mezi všechny typy objektů sady záznamů. Zejména pozice daného záznamu se změní, když jsou záznamy před ním odstraněny. Neexistuje také žádné ujištění, že daný záznam bude mít stejnou absolutní pozici, pokud je sada záznamů znovu vytvořena, protože pořadí jednotlivých záznamů v rámci sady záznamů není zaručeno, pokud není vytvořeno pomocí příkazu SQL pomocí klauzule **ORDERBY.**

> [!NOTE]
> Tato členská funkce je platná pouze pro sady záznamů typu dynaset a snímek.

Související informace naleznete v tématu "Vlastnost absoluteposition" v nápovědě DAO.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>Sada záznamů CDao::GetBookmark

Volání této členské funkce získat hodnotu záložky v určitém záznamu.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu představující záložku v aktuálním záznamu.

### <a name="remarks"></a>Poznámky

Při vytvoření nebo otevření objektu sady záznamů má každý z jeho záznamů již jedinečnou záložku, pokud je podporuje. Volání `CanBookmark` k určení, zda sada záznamů podporuje záložky.

Záložku pro aktuální záznam můžete uložit přiřazením hodnoty záložky `COleVariant` k objektu. Chcete-li se k tomuto záznamu kdykoli vrátit `SetBookmark` po přesunutí na jiný záznam, volání s parametrem odpovídajícím hodnotě tohoto `COleVariant` objektu.

> [!NOTE]
> Volání [Requery](#requery) změní záložky DAO.

Související informace naleznete v tématu "Vlastnost záložek" v nápovědě dao.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>Sada záznamů CDao::GetCacheSize

Volání této členské funkce získat počet záznamů do mezipaměti.

```
long GetCacheSize();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje počet záznamů v sadě záznamů typu dynaset obsahující data, která mají být místně uložena do mezipaměti ze zdroje dat ODBC.

### <a name="remarks"></a>Poznámky

Ukládání dat do mezipaměti zlepšuje výkon aplikace, která načítá data ze vzdáleného serveru prostřednictvím objektů sady záznamů typu dynaset. Mezipaměť je mezera v místní paměti, která obsahuje data naposledy načtená ze serveru v případě, že data budou požadována znovu v době, kdy je aplikace spuštěna. Pokud jsou požadována data, databázový stroj Microsoft Jet nejprve zkontroluje mezipaměť pro požadovaná data, nikoli načítat ze serveru, což trvá déle. Data, která nepocházejí ze zdroje dat ODBC, nejsou uložena v mezipaměti.

Jakýkoli zdroj dat ROZHRANÍ ODBC, například připojená tabulka, může mít místní mezipaměť.

Související informace naleznete v tématu CacheSize, CacheStart Properties v nápovědě dao.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>Sada záznamů CDao::GetCacheStart

Volání této členské funkce získat hodnotu záložky první záznam v sadě záznamů, které mají být uloženy do mezipaměti.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Návratová hodnota

A, `COleVariant` který určuje záložku prvního záznamu v sadě záznamů, který má být uložen do mezipaměti.

### <a name="remarks"></a>Poznámky

Databázový stroj Microsoft Jet požaduje záznamy v rozsahu mezipaměti z mezipaměti a požaduje záznamy mimo rozsah mezipaměti ze serveru.

> [!NOTE]
> Záznamy načtené z mezipaměti neodrážejí změny provedené současně se zdrojovými daty jinými uživateli.

Související informace naleznete v tématu CacheSize, CacheStart Properties v nápovědě dao.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>Sada záznamů CDao::GetCurrentIndex

Volání této členské funkce k určení indexu aktuálně používá v `CDaoRecordset` objektu typu indexované tabulky.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` obsahující název indexu aktuálně používán se sadou záznamů typu tabulka. Vrátí prázdný řetězec, pokud nebyl nastaven žádný index.

### <a name="remarks"></a>Poznámky

Tento index je základem pro řazení záznamů v sadě záznamů typu tabulky a používá se členská funkce [Hledat](#seek) k vyhledání záznamů.

Objekt `CDaoRecordset` může mít více než jeden index, ale může používat pouze jeden index najednou (i když [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) objekt může mít několik indexů definované na něm).

Související informace naleznete v tématu "Objekt indexu" a definici "aktuální index" v nápovědě DAO.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>Sada záznamů CDao::GetDateCreated

Volání této členské funkce načíst datum a čas základní tabulka byla vytvořena.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas základní tabulka byla vytvořena.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena od počítače, ve kterém byla vytvořena základní tabulka.

Související informace naleznete v tématu DateCreated, LastUpdated Properties v nápovědě dao.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>Sada záznamů CDao::GetDateLastUpdated

Volání této členské funkce načíst datum a čas, kdy bylo naposledy aktualizováno schéma.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující datum a čas základní tabulka struktura (schéma) byl naposledy aktualizován.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena od počítače, ve kterém byla naposledy aktualizována struktura základní tabulky (schéma).

Související informace naleznete v tématu DateCreated, LastUpdated Properties v nápovědě dao.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>Sada záznamů CDao::GetDefaultDBName

Volání této členské funkce k určení názvu databáze pro tuto sadu záznamů.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje cestu a název databáze, ze které je odvozen a sadou záznamů.

### <a name="remarks"></a>Poznámky

Pokud je sada záznamů vytvořena bez ukazatele na [databázi CDao ,](../../mfc/reference/cdaodatabase-class.md)použije tuto cestu sada záznamů k otevření výchozí databáze. Ve výchozím nastavení vrátí tato funkce prázdný řetězec. Když ClassWizard odvozuje novou `CDaoRecordset`sadu záznamů z aplikace , vytvoří tuto funkci za vás.

Následující příklad ilustruje použití dvojité zpětné lomítko (\\\\) v řetězci, jak je požadováno pro řetězec správně interpretovat.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>Sada záznamů CDao::GetDefaultSQL

Rozhraní Framework volá tuto členskou funkci, aby získalo výchozí příkaz SQL, na kterém je založena sada záznamů.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje výchozí příkaz SQL.

### <a name="remarks"></a>Poznámky

Může se jedná o název tabulky nebo příkaz SQL **SELECT.**

Nepřímo definujete výchozí příkaz SQL deklarováním třídy sady záznamů pomocí Průvodce řazením záznamů a ClassWizard provede tento úkol za vás.

Pokud předáte prázdný řetězec SQL [open](#open), bude tato funkce volána k určení názvu tabulky nebo SQL pro sadu záznamů.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>Sada záznamů CDao::GetEditMode

Volání této členské funkce k určení stavu úprav, což je jedna z následujících hodnot:

```
short GetEditMode();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která označuje stav úprav pro aktuální záznam.

### <a name="remarks"></a>Poznámky

|Hodnota|Popis|
|-----------|-----------------|
|`dbEditNone`|Neprobíhá žádná operace úprav.|
|`dbEditInProgress`|`Edit`byla povolána.|
|`dbEditAdd`|`AddNew`byla povolána.|

Související informace naleznete v tématu "Vlastnost EditMode" v nápovědě dao.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>Sada záznamů CDao::GetFieldCount

Volání této členské funkce načíst počet polí (sloupců) definované v sadě záznamů.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v sadě záznamů.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Count Property" v nápovědě dao.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>Sada záznamů CDao::GetFieldInfo

Volání této členské funkce získat informace o polích v sadě záznamů.

```cpp
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
Nulový index předdefinovaného pole v kolekci Polí sady záznamů pro vyhledávání podle indexu.

*Fieldinfo*<br/>
Odkaz na strukturu [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o sadě záznamů mají být načteny. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit. Chcete-li dosáhnout nejlepšího výkonu, načtěte pouze úroveň informací, které potřebujete:

- `AFX_DAO_PRIMARY_INFO`(Výchozí) Název, Typ, Velikost, Atributy

- `AFX_DAO_SECONDARY_INFO`Primární informace plus: Ordinální pozice, Povinné, Povolit nulovou délku, Řazení objednávky, Cizí jméno, Zdrojové pole, Zdrojová tabulka

- `AFX_DAO_ALL_INFO`Primární a sekundární informace plus: Výchozí hodnota, ověřovací pravidlo, ověřovací text

*název lpsz*<br/>
Název pole.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat pole podle indexu. Druhá verze umožňuje vyhledat pole podle názvu.

Popis vrácených informací naleznete ve struktuře [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Když požadujete informace na jedné úrovni, získáte také informace pro všechny předchozí úrovně.

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>Sada záznamů CDao::Hodnota GetFieldValue

Volání této členské funkce k načtení dat v sadě záznamů.

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

*název lpsz*<br/>
Ukazatel na řetězec, který obsahuje název pole.

*varValue*<br/>
Odkaz na `COleVariant` objekt, který bude ukládat hodnotu pole.

*nIndex*<br/>
Nulový index pole v kolekci Polí sady záznamů pro vyhledávání podle indexu.

### <a name="return-value"></a>Návratová hodnota

Dvě verze, `GetFieldValue` které vrátí hodnotu vrátit [COleVariant](../../mfc/reference/colevariant-class.md) objekt, který obsahuje hodnotu pole.

### <a name="remarks"></a>Poznámky

Pole můžete vyhledat podle názvu nebo podle ordinální polohy.

> [!NOTE]
> Je efektivnější volat jednu z verzí této členské funkce, která přebírá odkaz na `COleVariant` objekt jako `COleVariant` parametr, spíše než volání verze, která vrací objekt. Posledně uvedené verze této funkce jsou uchovávány pro zpětnou kompatibilitu.

Použití `GetFieldValue` a [SetFieldValue](#setfieldvalue) dynamicky vázat pole za běhu, nikoli staticky vazebné sloupce pomocí [doFieldExchange](#dofieldexchange) mechanismus.

`GetFieldValue`a `DoFieldExchange` mechanismus lze kombinovat za účelem zlepšení výkonnosti. Například slouží `GetFieldValue` k načtení hodnoty, kterou potřebujete pouze na vyžádání, a přiřaďte toto volání tlačítku "Další informace" v rozhraní.

Související informace naleznete v tématech "Objekt pole" a "Vlastnost hodnoty" v nápovědě dao.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>Sada záznamů CDao::GetIndexCount

Volání této členské funkce k určení počtu indexů, které jsou k dispozici v sadě záznamů typu tabulka.

```
short GetIndexCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet indexů v sadě záznamů typu tabulka.

### <a name="remarks"></a>Poznámky

`GetIndexCount`je užitečné pro opakování všech indexů v sadě záznamů. Pro tento účel `GetIndexCount` použijte ve spojení s [GetIndexInfo](#getindexinfo). Pokud voláte tuto člennou funkci na sadách záznamů typu dynaset nebo snímek, knihovna MFC vyvolá výjimku.

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>Sada záznamů CDao::GetIndexInfo

Volání této členské funkce získat různé druhy informací o indexu definované v základní tabulce základní sadu záznamů.

```cpp
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
Index založený na nule v kolekci indexů tabulky pro vyhledávání podle číselné pozice.

*informace o indexech*<br/>
Odkaz na strukturu [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o indexu načíst. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit. Chcete-li dosáhnout nejlepšího výkonu, načtěte pouze úroveň informací, které potřebujete:

- `AFX_DAO_PRIMARY_INFO`(Výchozí) Název, Informace o poli, Pole

- `AFX_DAO_SECONDARY_INFO`Primární informace plus: Primární, Jedinečný, Clustered, IgnoreNulls, Povinné, Cizí

- `AFX_DAO_ALL_INFO`Primární a sekundární informace plus: Odlišný počet

*název lpsz*<br/>
Ukazatel na název objektu indexu pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat index podle jeho umístění v kolekci. Druhá verze umožňuje vyhledat index podle názvu.

Popis vrácených informací naleznete ve struktuře [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md) Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Když požadujete informace na jedné úrovni, získáte také informace pro všechny předchozí úrovně.

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>Sada záznamů CDao::GetLastModifiedBookmark

Volání této členské funkce načíst záložku naposledy přidané nebo aktualizovaný záznam.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Návratová hodnota

A `COleVariant` obsahující záložku, která označuje naposledy přidaný nebo změněný záznam.

### <a name="remarks"></a>Poznámky

Při vytvoření nebo otevření objektu sady záznamů má každý z jeho záznamů již jedinečnou záložku, pokud je podporuje. Volání [GetBookmark](#getbookmark) k určení, zda sada záznamů podporuje záložky. Pokud sada záznamů nepodporuje záložky, `CDaoException` je vyvolána.

Když přidáte záznam, zobrazí se na konci sady záznamů a není aktuálním záznamem. Chcete-li, aby byl `GetLastModifiedBookmark` nový `SetBookmark` záznam aktuální, volání a následné volání pro návrat k nově přidanému záznamu.

Související informace naleznete v tématu "LastModified Property" v nápovědě DAO.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>Sada záznamů CDao::GetLockingMode

Volání této členské funkce k určení typu uzamčení v platnost i pro sadu záznamů.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je typ uzamčení pesimistický, jinak 0 pro optimistické zamykání záznamu.

### <a name="remarks"></a>Poznámky

Když je v platnosti pesimistické zamykání, datová stránka obsahující záznam, který upravujete, je uzamčena, jakmile zavoláte funkci [Upravit](#edit) člen. Stránka se odemkne, když zavoláte [členskou](#update) funkci Aktualizovat nebo [Zavřít](#close) nebo některou z operací Přesunout nebo Najít.

Při optimistické uzamčení je v platnosti, datová stránka obsahující záznam `Update` je uzamčen pouze v případě, že záznam je aktualizován s členskou funkcí.

Při práci se zdroji dat ODBC je režim uzamčení vždy optimistický.

Související informace naleznete v tématech "LockEdits Property" a "Locking Behavior in Multiuser Applications" v nápovědě DAO.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>Sada záznamů CDao::GetName

Volání této členské funkce načíst název sady záznamů.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` obsahující název sady záznamů.

### <a name="remarks"></a>Poznámky

Název sady záznamů musí začínat písmenem a může obsahovat maximálně 40 znaků. Může obsahovat čísla a znaky podtržítka, ale nemůže obsahovat interpunkci nebo mezery.

Související informace naleznete v tématu "Name Property" v nápovědě dao.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>Sada záznamů CDao::GetParamValue

Volání této členské funkce k načtení aktuální hodnoty zadaného parametru uloženého v podkladovém objektu DAOParameter.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Číselná poloha parametru v podkladovém objektu DAOParameter.

*název lpsz*<br/>
Název parametru, jehož hodnotu chcete.

### <a name="return-value"></a>Návratová hodnota

Objekt třídy [COleVariant,](../../mfc/reference/colevariant-class.md) který obsahuje hodnotu parametru.

### <a name="remarks"></a>Poznámky

K parametru můžete přistupovat buď podle názvu, nebo podle jeho číselné polohy v kolekci.

Související informace naleznete v tématu "Objekt parametru" v nápovědě DAO.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>Sada záznamů CDao::GetPercentPosition

Při práci s sadou záznamů typu dynaset nebo `GetPercentPosition` snímek, pokud zavoláte před úplné vyplnění sady záznamů, množství pohybu je relativní k počtu záznamů, ke kterým bylo přistupováno, jak je uvedeno voláním [GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Návratová hodnota

Číslo mezi 0 a 100, které označuje přibližné umístění aktuálního záznamu v objektu sady záznamů na základě procenta záznamů v sadě záznamů.

### <a name="remarks"></a>Poznámky

Můžete přesunout na poslední záznam voláním [MoveLast](#movelast) k dokončení plnění všech sad záznamů, ale to může trvat značné množství času.

Můžete volat `GetPercentPosition` na všechny tři typy objektů sady záznamů, včetně tabulek bez indexů. Však nelze `GetPercentPosition` volat na posunout pouze dopředu snímky nebo na sadu záznamů otevřené z předávacího dotazu proti externí databázi. Pokud neexistuje žádný aktuální záznam nebo byl odstraněn `CDaoException` aktuální záznam, je vyvolána.

Související informace naleznete v tématu "Vlastnost pozice percentposition" v nápovědě dao.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>Sada záznamů CDao::GetRecordCount

Voláním této členské funkce zjistěte, kolik záznamů v sadě záznamů bylo zpřístupněno.

```
long GetRecordCount();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet záznamů, ke nini přistupuje v objektu sady záznamů.

### <a name="remarks"></a>Poznámky

`GetRecordCount`neznamená, kolik záznamů je obsaženo v sadě záznamů typu dynaset nebo snímek, dokud nebudou přístupné všechny záznamy. Toto volání členské funkce může trvat značné množství času na dokončení.

Po přístupu k poslednímu záznamu udává vrácená hodnota celkový počet neodstraněných záznamů v sadě záznamů. Chcete-li vynutit přístup k `MoveLast` poslednímu záznamu, zavolejte nebo `FindLast` členovou funkci pro sadu záznamů. Můžete také použít sql count k určení přibližného počtu záznamů, které dotaz vrátí.

Jako aplikace odstraní záznamy v sadě záznamů typu dynaset, `GetRecordCount` vrácená hodnota snižuje. Záznamy odstraněné jinými uživateli se `GetRecordCount` však neprojeví, dokud není aktuální záznam umístěn do odstraněného záznamu. Pokud provedete transakci, která ovlivňuje počet záznamů a `GetRecordCount` následně vrátit zpět transakce, nebude odrážet skutečný počet zbývajících záznamů.

Hodnota ze `GetRecordCount` sady záznamů typu snímek není ovlivněna změnami v podkladových tabulkách.

Hodnota ze `GetRecordCount` sady záznamů typu tabulky odráží přibližný počet záznamů v tabulce a je ovlivněna okamžitě při přidávání a odstraňování záznamů tabulky.

Sada záznamů bez záznamů vrátí hodnotu 0. Při práci s připojenými tabulkami `GetRecordCount` nebo databázemi ODBC vždy vrátí - 1. Volání `Requery` členské funkce v sadě záznamů obnoví `GetRecordCount` hodnotu stejně, jako kdyby byl dotaz znovu proveden.

Související informace naleznete v tématu "RecordCount Property" v nápovědě DAO.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>Sada záznamů CDao::GetSQL

Volání této členské funkce získat příkaz SQL, který byl použit k výběru záznamů sady záznamů při jeho otevření.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje příkaz SQL.

### <a name="remarks"></a>Poznámky

To bude obecně sql **select** příkaz.

Řetězec vrácený `GetSQL` podle se obvykle liší od libovolného řetězce, který jste předali sadě záznamů v parametru *lpszSQL* členské funkci [Otevřít.](#open) Důvodem je, že sada záznamů vytvoří úplný příkaz `Open`SQL na základě toho, co jste předali , co jste zadali pomocí ClassWizard a co jste zadali v [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) datových členů.

> [!NOTE]
> Volání této členské funkce `Open`pouze po volání .

Související informace naleznete v tématu "Vlastnost SQL" v nápovědě DAO.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>Sada záznamů CDao::GetType

Volání této členské funkce po otevření sady záznamů k určení typu objektu sady záznamů.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot označující typ sady záznamů:

- `dbOpenTable`Sada záznamů typu tabulka

- `dbOpenDynaset`Sada záznamů typu Dynaset

- `dbOpenSnapshot`Sada záznamů typu snímek

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Type Property" v nápovědě dao.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>Sada záznamů CDao::Pravidlo ověření pravosti

Volání této členské funkce k určení pravidla používaného k ověření dat.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující hodnotu, která ověřuje data v záznamu při změně nebo přidání do tabulky.

### <a name="remarks"></a>Poznámky

Toto pravidlo je založeno na textu a použije se při každé změně podkladové tabulky. Pokud data není legální, knihovna MFC vyvolá výjimku. Vrácená chybová zpráva je text vlastnosti ValidationText podkladového objektu pole, pokud je zadán, nebo text výrazu určeného vlastností ValidationRule základního objektu pole. Můžete volat [GetValidationText](#getvalidationtext) získat text chybové zprávy.

Například pole v záznamu, které vyžaduje den v měsíci, může mít ověřovací pravidlo, například "DEN MEZI 1 a 31".

Související informace naleznete v tématu "ValidationRule Property" v nápovědě dao.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>Sada záznamů CDao::GetValidationText

Volání této členské funkce k načtení textu vlastnosti ValidationText základního objektu pole.

```
CString GetValidationText();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující text zprávy, která je zobrazena, pokud hodnota pole nesplňuje ověřovací pravidlo základního objektu pole.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "Vlastnost ValidationText" v nápovědě dao.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>Sada záznamů CDao::IsBOF

Před přechodem ze záznamu na záznam zavolejte tuto členovou funkci a zjistěte, zda jste před prvním záznamem sady záznamů odešli.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy nebo pokud jste před prvním záznamem posunuli zpět; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete také `IsBOF` volat `IsEOF` spolu s chcete-li zjistit, zda sada záznamů obsahuje nějaké záznamy nebo je prázdný. Ihned po `Open`volání vrátí sada záznamů `IsBOF` hodnotu nenulová. Když otevřete sadu záznamů, která má alespoň jeden záznam, `IsBOF` první záznam je aktuální záznam a vrátí hodnotu 0.

Pokud je první záznam aktuální mše a voláte `MovePrev`, `IsBOF` vrátí se následně nenulová. Pokud `IsBOF` vrátí nenulovou `MovePrev`a volání , je vyvolána výjimka. Pokud `IsBOF` vrátí nenulovou hodnotu, aktuální záznam není definován a jakákoli akce, která vyžaduje aktuální záznam, bude mít za následek výjimku.

Vliv konkrétních `IsBOF` metod `IsEOF` na a nastavení:

- Interní `Open*` volání vytvoří první záznam v sadě záznamů `MoveFirst`jako aktuální záznam voláním . Proto volání `Open` na prázdnou sadu `IsBOF` `IsEOF` záznamů příčiny a vrátit nenulovou. (Chování neúspěšného `MoveFirst` volání naleznete `MoveLast` v následující tabulce.)

- Všechny operace přesunutí, které úspěšně `IsBOF` vyhledejte záznam, způsobí, že `IsEOF` se vrátí 0.

- Volání `AddNew` následované `Update` voláním, které úspěšně vloží nový `IsBOF` záznam, způsobí vrácení `IsEOF` 0, ale pouze v případě, že je již nenulová. Stav `IsEOF` zůstane vždy beze změny. Jak je definováno databázovým strojem Microsoft Jet, aktuální ukazatel záznamu prázdné sady záznamů je na konci souboru, takže každý nový záznam je vložen za aktuální záznam.

- Žádné `Delete` volání, i když odebere jediný zbývající záznam ze sady záznamů, `IsBOF` `IsEOF`nezmění hodnotu nebo .

V této tabulce jsou uvedeny, které `IsBOF` /  `IsEOF`operace přesunu jsou povoleny s různými kombinacemi aplikace .

||MoveFirst, MoveLast|Moveprev<br /><br /> Přesunout < 0|Přesunout 0|Movenext<br /><br /> Přesunout > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`=nenulová,<br /><br /> `IsEOF`=0|Povoleno|Výjimka|Výjimka|Povoleno|
|`IsBOF`=0,<br /><br /> `IsEOF`=nenulová|Povoleno|Povoleno|Výjimka|Výjimka|
|Oba nenulové|Výjimka|Výjimka|Výjimka|Výjimka|
|Oba 0|Povoleno|Povoleno|Povoleno|Povoleno|

Povolení operace Přesunutí neznamená, že operace úspěšně vyhledá záznam. Pouze označuje, že pokus o provedení zadané operace move je povolen a nevytvoří výjimku. Hodnota `IsBOF` a `IsEOF` členské funkce se může změnit v důsledku pokusu o přesunutí.

Vliv operací přesunutí, které nevyhledávají záznam `IsBOF` na `IsEOF` hodnotu a nastavení, je uveden v následující tabulce.

||Isbof|Iseof|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nenulová|Nenulová|
|`Move`0|Beze změny|Beze změny|
|`MovePrev`, `Move` < 0|Nenulová|Beze změny|
|`MoveNext`, `Move` > 0|Beze změny|Nenulová|

Související informace naleznete v tématu "BOF, EOF Properties" v nápovědě DAO.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>Sada záznamů CDao:IsDeleted

Volání této členské funkce k určení, zda byl odstraněn aktuální záznam.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je sada záznamů umístěna na odstraněný záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud přejdete na `IsDeleted` záznam a vrátíte hodnotu TRUE (nenulová), musíte se před provedením jiných operací sady záznamů posunout na jiný záznam.

> [!NOTE]
> Odstraněný stav není nutné kontrolovat u záznamů ve snímku nebo sadě záznamů typu tabulka. Vzhledem k tomu, že záznamy nelze odstranit `IsDeleted`ze snímku, není nutné volat . U sad záznamů typu tabulka jsou odstraněné záznamy ze sady záznamů skutečně odebrány. Jakmile byl záznam odstraněn vámi, jiným uživatelem nebo v jiné sadě záznamů, nelze se k tomuto záznamu vrátit zpět. Proto není třeba volat `IsDeleted`.

Když odstraníte záznam z dynasady, je odebrán ze sady záznamů a nelze jej přejít zpět k tomuto záznamu. Pokud je však záznam v dynasetě odstraněn jiným uživatelem nebo v `IsDeleted` jiné sadě záznamů založené na stejné tabulce, vrátí hodnotu TRUE, když se později posunete k tomuto záznamu.

Související informace naleznete v tématech "Delete Method", "LastModified Property" a "EditMode Property" v nápovědě dao.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>Sada záznamů CDao:IsEOF

Volání této členské funkce při posouvání ze záznamu do záznamu zjistit, zda jste překročili poslední záznam sady záznamů.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy nebo pokud jste se posunuli za poslední záznam; jinak 0.

### <a name="remarks"></a>Poznámky

Můžete také `IsEOF` volat k určení, zda sada záznamů obsahuje nějaké záznamy nebo je prázdný. Ihned po `Open`volání vrátí sada záznamů `IsEOF` hodnotu nenulová. Když otevřete sadu záznamů, která má alespoň jeden záznam, `IsEOF` první záznam je aktuální záznam a vrátí hodnotu 0.

Pokud je poslední záznam aktuálním `MoveNext`záznamem při volání , `IsEOF` vrátí se následně nenulová. Pokud `IsEOF` vrátí nenulovou `MoveNext`a volání , je vyvolána výjimka. Pokud `IsEOF` vrátí nenulovou hodnotu, aktuální záznam není definován a jakákoli akce, která vyžaduje aktuální záznam, bude mít za následek výjimku.

Vliv konkrétních `IsBOF` metod `IsEOF` na a nastavení:

- Interní `Open` volání vytvoří první záznam v sadě záznamů `MoveFirst`jako aktuální záznam voláním . Proto volání `Open` na prázdnou sadu `IsBOF` `IsEOF` záznamů příčiny a vrátit nenulovou. (Chování neúspěšného `MoveFirst` volání naleznete v následující tabulce.)

- Všechny operace přesunutí, které úspěšně `IsBOF` vyhledejte záznam, způsobí, že `IsEOF` se vrátí 0.

- Volání `AddNew` následované `Update` voláním, které úspěšně vloží nový `IsBOF` záznam, způsobí vrácení `IsEOF` 0, ale pouze v případě, že je již nenulová. Stav `IsEOF` zůstane vždy beze změny. Jak je definováno databázovým strojem Microsoft Jet, aktuální ukazatel záznamu prázdné sady záznamů je na konci souboru, takže každý nový záznam je vložen za aktuální záznam.

- Žádné `Delete` volání, i když odebere jediný zbývající záznam ze sady záznamů, `IsBOF` `IsEOF`nezmění hodnotu nebo .

V této tabulce jsou uvedeny, které `IsBOF` /  `IsEOF`operace přesunu jsou povoleny s různými kombinacemi aplikace .

||MoveFirst, MoveLast|Moveprev<br /><br /> Přesunout < 0|Přesunout 0|Movenext<br /><br /> Přesunout > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`=nenulová,<br /><br /> `IsEOF`=0|Povoleno|Výjimka|Výjimka|Povoleno|
|`IsBOF`=0,<br /><br /> `IsEOF`=nenulová|Povoleno|Povoleno|Výjimka|Výjimka|
|Oba nenulové|Výjimka|Výjimka|Výjimka|Výjimka|
|Oba 0|Povoleno|Povoleno|Povoleno|Povoleno|

Povolení operace Přesunutí neznamená, že operace úspěšně vyhledá záznam. Pouze označuje, že pokus o provedení zadané operace move je povolen a nevytvoří výjimku. Hodnota `IsBOF` a `IsEOF` členské funkce se může změnit v důsledku pokusu Move.

Vliv operací přesunutí, které nevyhledávají záznam `IsBOF` na `IsEOF` hodnotu a nastavení, je uveden v následující tabulce.

||Isbof|Iseof|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nenulová|Nenulová|
|`Move`0|Beze změny|Beze změny|
|`MovePrev`, `Move` < 0|Nenulová|Beze změny|
|`MoveNext`, `Move` > 0|Beze změny|Nenulová|

Související informace naleznete v tématu "BOF, EOF Properties" v nápovědě DAO.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>Sada záznamů CDao::IsFieldDirty

Volání této členské funkce k určení, zda byl zadaný datový člen pole dynasetu označen jako "dirty" (změněn).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Ukazatel na člena dat pole, jehož stav chcete zkontrolovat, nebo NULL k určení, zda některé z polí jsou nečisté.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zadaný datový člen pole označen jako nečistý; jinak 0.

### <a name="remarks"></a>Poznámky

Data `Update` ve všech datových členech nefunkčních `CDaoRecordset` polí budou přenesena do záznamu ve zdroji dat při aktualizaci `Edit` aktuálního záznamu voláním členské funkce (po volání nebo `AddNew`). S těmito znalostmi můžete podniknout další kroky, například neoznačený datový člen pole označit sloupec tak, aby nebyl zapsán do zdroje dat.

`IsFieldDirty`je implementována prostřednictvím `DoFieldExchange`.

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>Sada záznamů CDao::Hodnota IsFieldNull

Volání této členské funkce k určení, zda byl zadaný datový člen pole sady záznamů označen jako null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Ukazatel na datového člena pole, jehož stav chcete zkontrolovat, nebo NULL k určení, zda některé z polí jsou Null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zadaný datový člen pole označen jako Null; jinak 0.

### <a name="remarks"></a>Poznámky

(V terminologii databáze null znamená "bez hodnoty" a není stejný jako NULL v jazyce C++.) Pokud je datový člen pole označen jako Null, je interpretován jako sloupec aktuálního záznamu, pro který neexistuje žádná hodnota.

> [!NOTE]
> V určitých `IsFieldNull` situacích může být použití neefektivní, jak ukazuje následující příklad kódu:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> Pokud používáte dynamickou vazbu záznamu, `CDaoRecordset`aniž byste z ní odvodili , nezapomeňte použít VT_NULL, jak je znázorněno v příkladu.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>Sada záznamů CDao::Hodnotitelné hodnotu Hodnotitelné hodnotou

Volání této členské funkce k určení, zda je zadaný člen dat pole "nullable" (lze nastavit na hodnotu Null; C++ NULL není stejný jako Null, což v terminologii databáze znamená "bez hodnoty").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Ukazatel na datového člena pole, jehož stav chcete zkontrolovat, nebo NULL k určení, zda některé z polí jsou Null.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze zadaný datový člen pole provést jako Null; jinak 0.

### <a name="remarks"></a>Poznámky

Pole, které nemůže být Null, musí mít hodnotu. Pokud se pokusíte nastavit takové pole na hodnotu Null při přidávání nebo aktualizaci záznamu, zdroj dat odmítne přidání nebo aktualizaci a `Update` vyvolá výjimku. K výjimce dochází `Update`při volání `SetFieldNull`, nikoli při volání .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>Sada rekordů CDao::IsOpen

Volání této členské funkce k určení, zda je otevřena sada záznamů.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla `Open` dříve `Requery` volána funkce objektu nebo člena sady záznamů a sada záznamů nebyla uzavřena; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>Sada záznamů CDao::m_bCheckCacheForDirtyFields

Obsahuje příznak označující, zda jsou pole uložená v mezipaměti automaticky označena jako neznečištěná (změněná) a null.

### <a name="remarks"></a>Poznámky

Příznak je výchozí hodnotou TRUE. Nastavení v tomto datovém členu řídí celý mechanismus dvojité ukládání do vyrovnávací paměti. Pokud nastavíte příznak na HODNOTU TRUE, můžete vypnout ukládání do mezipaměti na základě pole po poli pomocí mechanismu DFX. Pokud nastavíte příznak NA FALSE, musíte volat `SetFieldDirty` a `SetFieldNull` sami.

Před voláním `Open`nastavte tento datový člen . Tento mechanismus je určen především pro snadné použití. Výkon může být pomalejší z důvodu dvojité ukládání do vyrovnávací paměti polí při provádění změn.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>Sada záznamů CDao::m_nFields

Obsahuje počet datových členů pole ve třídě sady záznamů a počet sloupců vybraných sadou záznamů ze zdroje dat.

### <a name="remarks"></a>Poznámky

Konstruktor pro třídu sady záznamů `m_nFields` musí inicializovat se správným počtem staticky vázaných polí. ClassWizard zapíše tuto inicializaci za vás při použití deklarovat třídu sady záznamů. Můžete také napsat ručně.

Rozhraní Framework používá toto číslo ke správě interakce mezi datovými členy pole a odpovídajícími sloupci aktuálního záznamu ve zdroji dat.

> [!NOTE]
> Toto číslo musí odpovídat počtu `DoFieldExchange` výstupních sloupců registrovaných po volání `SetFieldType` s parametrem `CDaoFieldExchange::outputColumn`.

Sloupce můžete dynamicky svázat `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue`pomocí a . Pokud tak učiníte, není nutné zvýšení počtu `m_nFields` v tak, aby odrážely počet `DoFieldExchange` volání funkce DFX v členské funkci.

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>Sada záznamů CDao::m_nParams

Obsahuje počet datových členů parametrů ve třídě sady záznamů – počet parametrů předaných dotazem sady záznamů.

### <a name="remarks"></a>Poznámky

Pokud vaše třída sady záznamů má všechny datové členy parametru, konstruktor pro třídu musí inicializovat *m_nParams* se správným číslem. Hodnota *m_nParams* výchozí hodnota 0. Pokud přidáte datové členy parametrů , musíte také ručně přidat inicializaci v konstruktoru třídy tak, aby odrážela počet parametrů (které musí být alespoň tak velké jako počet zástupných symbolů ve *vašem m_strFilter* nebo *m_strSort* řetězce).

Rozhraní framework používá toto číslo při parametrizaci dotazu sady záznamů.

> [!NOTE]
> Toto číslo musí odpovídat počtu "params" registrovaných po `DoFieldExchange` volání `SetFieldType` s parametrem `CFieldExchange::param`.

Související informace naleznete v tématu "Objekt parametru" v nápovědě DAO.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>Sada záznamů CDao::m_pDAORecordset

Obsahuje ukazatel na rozhraní OLE pro objekt sady záznamů `CDaoRecordset` DAO, který je základem objektu.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte, pokud potřebujete přímý přístup k rozhraní DAO.

Související informace naleznete v tématu "Recordset Object" v nápovědě dao.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>Sada záznamů CDao::m_pDatabase

Obsahuje ukazatel na `CDaoDatabase` objekt, jehož prostřednictvím je sada záznamů připojena ke zdroji dat.

### <a name="remarks"></a>Poznámky

Tato proměnná je nastavena dvěma způsoby. Obvykle předáte ukazatel již otevřený `CDaoDatabase` objekt při vytváření objektu sady záznamů. Pokud místo toho `CDaoRecordset` předáte hodnotu NULL, vytvoří `CDaoDatabase` za vás objekt a otevře jej. V obou `CDaoRecordset` případech uloží ukazatel v této proměnné.

Za normálních okolností nebudete muset `m_pDatabase`přímo používat ukazatel uložený v aplikaci . Pokud však napíšete `CDaoRecordset`vlastní rozšíření do aplikace , bude pravděpodobně nutné použít ukazatel. Například můžete potřebovat ukazatel, pokud hodíte vlastní `CDaoException`(y).

Související informace naleznete v tématu "Databázový objekt" v nápovědě dao.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>Sada záznamů CDao::m_strFilter

Obsahuje řetězec, který se používá k vytvoření **where** klauzule příkazu SQL.

### <a name="remarks"></a>Poznámky

Neobsahuje vyhrazené slovo **KDE** filtrovat sadu záznamů. Použití tohoto datového člena se nevztahuje na sady záznamů typu tabulka. Použití `m_strFilter` nemá žádný vliv při otevírání `CDaoQueryDef` sady záznamů pomocí ukazatele.

Při filtrování polí obsahujících data použijte formát data v USA (měsíc-den-rok), a to i v případě, že nepoužíváte americkou verzi databázového stroje Microsoft Jet. v opačném případě nemusí být data filtrována podle očekávání.

Související informace naleznete v tématu "Vlastnost filtru" v nápovědě dao.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>Sada záznamů CDao::m_strSort

Obsahuje řetězec obsahující **ORDERBY** klauzule příkazu SQL bez vyhrazených slov **ORDERBY**.

### <a name="remarks"></a>Poznámky

Můžete řadit na objekty dynaset- a snímek typu recordset objekty.

Objekty sady záznamů typu tabulka nelze seřadit. Chcete-li určit pořadí řazení sady záznamů typu tabulka, volejte [SetCurrentIndex](#setcurrentindex).

Použití *m_strSort* nemá žádný vliv při otevírání `CDaoQueryDef` sady záznamů pomocí ukazatele.

Související informace naleznete v tématu "Sort Property" v nápovědě dao.

## <a name="cdaorecordsetmove"></a><a name="move"></a>Sada rekordů CDao::Přesunout

Volání této členské funkce umístit záznamlset *lRows* záznamy z aktuálního záznamu.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parametry

*lŘádky*<br/>
Počet záznamů, které mají být posunuty dopředu nebo dozadu. Kladné hodnoty se posouvají vpřed ke konci sady záznamů. Záporné hodnoty se pohybují dozadu směrem k začátku.

### <a name="remarks"></a>Poznámky

Můžete se pohybovat dopředu nebo dozadu. `Move( 1 )`je ekvivalentní `MoveNext`písmenu a) a je `Move( -1 )` ekvivalentní . `MovePrev`

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Obecně platí, `IsBOF` že `IsEOF` volání obou a před Move operace k určení, zda sada záznamů má nějaké záznamy. Po volání `Open` `Requery`nebo , `IsBOF` `IsEOF`volání buď nebo .

> [!NOTE]
> Pokud jste se posunuli za začátek nebo `IsBOF` `IsEOF` konec sady záznamů (nebo vrátí nenulovou hodnotu), volání `Move` vyvolá `CDaoException`.

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Při volání `Move` na posunout pouze dopředu *snímek, parametr lRows* musí být kladné celé číslo a záložky nejsou povoleny, takže můžete přesunout pouze vpřed.

Chcete-li vytvořit první, poslední, následující nebo předchozí záznam v `MoveFirst`sadě `MoveLast` `MoveNext`záznamů, `MovePrev` aktuální záznam, zavolejte na , , nebo člennou funkci.

Související informace naleznete v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>Sada rekordů CDao::MoveFirst

Volání této členské funkce, chcete-li, aby první záznam v sadě záznamů (pokud existuje) aktuální záznam.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>Poznámky

Není třeba volat `MoveFirst` ihned po otevření sady záznamů. V té době je první záznam (pokud existuje) automaticky aktuální záznam.

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Obecně platí, `IsBOF` že `IsEOF` volání obou a před Move operace k určení, zda sada záznamů má nějaké záznamy. Po volání `Open` `Requery`nebo , `IsBOF` `IsEOF`volání buď nebo .

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Pomocí `Move` funkcí můžete přejít ze záznamu na záznam bez použití podmínky. Operace hledání slouží k vyhledání záznamů v objektu sady záznamů typu dynaset nebo snímek, které splňují určitou podmínku. Chcete-li vyhledat záznam v objektu sady `Seek`záznamů typu tabulky, zavolejte .

Pokud sada záznamů odkazuje na sadu záznamů typu tabulky, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti Index podkladového objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Pokud voláte `MoveLast` objekt sady záznamů na základě dotazu SQL nebo querydef, dotaz je vynuceno dokončení a objekt sady záznamů je plně naplněn.

Nelze volat `MoveFirst` nebo `MovePrev` členské funkce s posunutím pouze dopředu.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů `Move`o určitý počet záznamů dopředu nebo dozadu, volejte .

Související informace naleznete v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>Sada rekordů CDao::MoveLast

Volání této členské funkce, chcete-li, aby poslední záznam (pokud existuje) v sadě záznamů aktuální záznam.

```cpp
void MoveLast();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Obecně platí, `IsBOF` že `IsEOF` volání obou a před Move operace k určení, zda sada záznamů má nějaké záznamy. Po volání `Open` `Requery`nebo , `IsBOF` `IsEOF`volání buď nebo .

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Pomocí `Move` funkcí můžete přejít ze záznamu na záznam bez použití podmínky. Operace hledání slouží k vyhledání záznamů v objektu sady záznamů typu dynaset nebo snímek, které splňují určitou podmínku. Chcete-li vyhledat záznam v objektu sady `Seek`záznamů typu tabulky, zavolejte .

Pokud sada záznamů odkazuje na sadu záznamů typu tabulky, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti Index podkladového objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Pokud voláte `MoveLast` objekt sady záznamů na základě dotazu SQL nebo querydef, dotaz je vynuceno dokončení a objekt sady záznamů je plně naplněn.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů `Move`o určitý počet záznamů dopředu nebo dozadu, volejte .

Související informace naleznete v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>Sada rekordů CDao::MoveNext

Volání této členské funkce, chcete-li, aby další záznam v sadě záznamů byl aktuálním záznamem.

```cpp
void MoveNext();
```

### <a name="remarks"></a>Poznámky

Doporučujeme zavolat `IsBOF` před pokusem o přechod na předchozí záznam. Volání `MovePrev` vyvolá `CDaoException` if `IsBOF` vrátí nenulovou, označující, že jste již posouvali před prvním záznamem nebo že sada záznamů nevybrala žádné záznamy.

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Obecně platí, `IsBOF` že `IsEOF` volání obou a před Move operace k určení, zda sada záznamů má nějaké záznamy. Po volání `Open` `Requery`nebo , `IsBOF` `IsEOF`volání buď nebo .

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Pomocí `Move` funkcí můžete přejít ze záznamu na záznam bez použití podmínky. Operace hledání slouží k vyhledání záznamů v objektu sady záznamů typu dynaset nebo snímek, které splňují určitou podmínku. Chcete-li vyhledat záznam v objektu sady `Seek`záznamů typu tabulky, zavolejte .

Pokud sada záznamů odkazuje na sadu záznamů typu tabulky, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti Index podkladového objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů `Move`o určitý počet záznamů dopředu nebo dozadu, volejte .

Související informace naleznete v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>Sada rekordů CDao:MovePrev

Volání této členské funkce, aby předchozí záznam v sadě záznamů byl aktuálním záznamem.

```cpp
void MovePrev();
```

### <a name="remarks"></a>Poznámky

Doporučujeme zavolat `IsBOF` před pokusem o přechod na předchozí záznam. Volání `MovePrev` vyvolá `CDaoException` if `IsBOF` vrátí nenulovou, označující, že jste již posouvali před prvním záznamem nebo že sada záznamů nevybrala žádné záznamy.

> [!CAUTION]
> Volání některé `Move` z funkcí vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Obecně platí, `IsBOF` že `IsEOF` volání obou a před Move operace k určení, zda sada záznamů má nějaké záznamy. Po volání `Open` `Requery`nebo , `IsBOF` `IsEOF`volání buď nebo .

> [!NOTE]
> Pokud zavoláte některou z funkcí během `Move` aktualizace nebo přidání aktuálního záznamu, aktualizace budou bez upozornění ztraceny.

Pomocí `Move` funkcí můžete přejít ze záznamu na záznam bez použití podmínky. Operace hledání slouží k vyhledání záznamů v objektu sady záznamů typu dynaset nebo snímek, které splňují určitou podmínku. Chcete-li vyhledat záznam v objektu sady `Seek`záznamů typu tabulky, zavolejte .

Pokud sada záznamů odkazuje na sadu záznamů typu tabulky, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti Index podkladového objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Nelze volat `MoveFirst` nebo `MovePrev` členské funkce s posunutím pouze dopředu.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů `Move`o určitý počet záznamů dopředu nebo dozadu, volejte .

Související informace naleznete v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods" v nápovědě DAO.

## <a name="cdaorecordsetopen"></a><a name="open"></a>Sada záznamů CDao::Otevřít

Chcete-li načíst záznamy sady záznamů, je nutné volat tuto členská funkci.

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
Jedna z následujících hodnot:

- `dbOpenDynaset`Sada záznamů typu dynaset s obousměrným posouváním. Toto nastavení je výchozí.

- `dbOpenTable`Sada záznamů typu tabulky s obousměrným posouváním.

- `dbOpenSnapshot`Sada záznamů typu snímek s obousměrným posouváním.

*Lpszsql*<br/>
Ukazatel řetězce obsahující jedno z následujících:

- Ukazatel NULL.

- Název jednoho nebo více tabledefs a/nebo querydefs (oddělené čárkami).

- Příkaz SQL **SELECT** (volitelně s klauzulí SQL **WHERE** nebo **ORDERBY).**

- Předávací dotaz.

*nMožnosti*<br/>
Jedna nebo více možností uvedených níže. Výchozí hodnota je 0. Možné hodnoty jsou následující:

- `dbAppendOnly`Můžete připojit pouze nové záznamy (pouze sadu záznamů typu dynaset). Tato možnost znamená doslova, že záznamy mohou být připojeny pouze. Třídy databáze Rozhraní MFC ODBC mají možnost pouze pro připojení, která umožňuje načtení a připojení záznamů.

- `dbForwardOnly`Sada záznamů je snímek posouvání pouze dopředu.

- `dbSeeChanges`Vygenerujte výjimku, pokud jiný uživatel mění data, která upravujete.

- `dbDenyWrite`Ostatní uživatelé nemohou upravovat ani přidávat záznamy.

- `dbDenyRead`Ostatní uživatelé nemohou zobrazit záznamy (pouze sada záznamů typu tabulka).

- `dbReadOnly`Můžete zobrazit pouze záznamy; ostatní uživatelé je mohou upravovat.

- `dbInconsistent`Nekonzistentní aktualizace jsou povoleny (pouze sada záznamů typu dynaset).

- `dbConsistent`Jsou povoleny pouze konzistentní aktualizace (pouze sada záznamů typu dynaset).

> [!NOTE]
> Konstanty `dbConsistent` a `dbInconsistent` vzájemně se vylučují. Můžete použít jeden nebo druhý, ale ne obojí `Open`v dané instanci .

*pTableDef*<br/>
Ukazatel na objekt [CDaoTableDef.](../../mfc/reference/cdaotabledef-class.md) Tato verze je platná pouze pro sady záznamů typu tabulka. Při použití této `CDaoDatabase` možnosti se `CDaoRecordset` nepoužije ukazatel použitý k vytvoření této možnosti; místo toho se používá databáze, ve kterém tabledef umístěn.

*pQueryDef*<br/>
Ukazatel na objekt [CDaoQueryDef.](../../mfc/reference/cdaoquerydef-class.md) Tato verze je platná pouze pro sady záznamů typu dynaset a snímek. Při použití této `CDaoDatabase` možnosti se `CDaoRecordset` nepoužije ukazatel použitý k vytvoření této možnosti; místo toho se používá databáze, ve kterém je umístěn querydef.

### <a name="remarks"></a>Poznámky

Před `Open`voláním je nutné vytvořit objekt sady záznamů. Existuje několik způsobů, jak to provést:

- Při vytváření objektu sady záznamů předejte `CDaoDatabase` ukazatel objektu, který je již otevřen.

- Při vytváření objektu sady záznamů předejte `CDaoDatabase` ukazatel objektu, který není otevřen. Sada záznamů otevře `CDaoDatabase` objekt, ale nezavře jej, když se objekt sady záznamů zavře.

- Při vytváření objektu sady záznamů předejte ukazatel NULL. Objekt sady záznamů `GetDefaultDBName` volá, aby získal název aplikace Microsoft Access . MDB soubor otevřít. Sada záznamů pak `CDaoDatabase` otevře objekt a ponechá jej otevřený tak dlouho, dokud je sada záznamů otevřená. Při volání `Close` sady záznamů je `CDaoDatabase` objekt také uzavřen.

    > [!NOTE]
    >  Když sada záznamů `CDaoDatabase` otevře objekt, otevře zdroj dat s nevýhradním přístupem.

Pro `Open` verzi, která používá parametr *lpszSQL,* jakmile je sada záznamů otevřena, můžete načíst záznamy jedním z několika způsobů. První možností je mít funkce DFX ve vašem `DoFieldExchange`. Druhou možností je použití dynamické vazby voláním `GetFieldValue` členské funkce. Tyto možnosti mohou být implementovány samostatně nebo v kombinaci. Pokud jsou kombinovány, budete muset předat příkaz SQL sami `Open`na volání .

Při použití `Open` druhé verze, kde předáte v objektu, `CDaoTableDef` výsledné sloupce budou `DoFieldExchange` k dispozici pro vazbu prostřednictvím a `GetFieldValue`DFX mechanismus a/nebo dynamicky vázat prostřednictvím .

> [!NOTE]
> Můžete volat `Open` pouze `CDaoTableDef` pomocí objektu pro sady záznamů typu tabulky.

Při použití `Open` třetí verze, kde předáte v objektu, `CDaoQueryDef` tento dotaz bude proveden a výsledné sloupce `DoFieldExchange` budou k dispozici pro vás svázat `GetFieldValue`prostřednictvím a dfx mechanismus a/nebo dynamicky vázat prostřednictvím .

> [!NOTE]
> Můžete volat `Open` pouze `CDaoQueryDef` pomocí objektu pro sady záznamů typu dynaset a snímek.

Pro první `Open` verzi, která `lpszSQL` používá parametr, jsou záznamy vybrány na základě kritérií uvedených v následující tabulce.

|Hodnota parametru `lpszSQL`|Zvolené záznamy jsou určeny|Příklad|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Řetězec vrácený funkcí `GetDefaultSQL`.||
|Seznam oddělených čárkami jednoho nebo více názvů tabledefs a/nebo querydef.|Všechny sloupce reprezentované v . `DoFieldExchange`|`"Customer"`|
|**VYBRAT** seznam sloupců **z** tabulky|Zadané sloupce ze zadaných tabledef (y) a/nebo querydef(s).|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Obvyklý postup je předat `Open`NULL do ; v takovém `Open` případě `GetDefaultSQL`volání , overridable členské funkce, které `CDaoRecordset`ClassWizard generuje při vytváření -derived třídy. Tato hodnota poskytuje tabledef(s) a/nebo querydef name(s), které jste zadali v ClassWizard. Místo toho můžete zadat další informace v *parametru lpszSQL.*

Bez ohledu `Open` na to, co předáte, vytvoří konečný řetězec SQL pro dotaz (řetězec může mít klauzule SQL **WHERE** a **ORDERBY** připojené k *řetězci lpszSQL,* který jste předali) a poté spustí dotaz. Můžete prozkoumat vytvořený řetězec `GetSQL` voláním `Open`po volání .

Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Chcete-li nastavit možnosti sady záznamů, například filtr `m_strSort` nebo `m_strFilter` řazení, nastavte nebo po vytvoření `Open`objektu sady záznamů, ale před voláním . Pokud chcete aktualizovat záznamy v sadě záznamů po otevření sady `Requery`záznamů, zavolejte .

Pokud voláte `Open` na sadu záznamů typu dynaset nebo snímek nebo pokud zdroj dat odkazuje na příkaz SQL nebo tabledef, který představuje připojenou tabulku, nelze použít `dbOpenTable` pro argument typu; Pokud tak učiníte, knihovna MFC vyvolá výjimku. Chcete-li zjistit, zda objekt tabledef představuje připojenou tabulku, vytvořte objekt [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) a zavolejte jeho člennou funkci [GetConnect.](../../mfc/reference/cdaotabledef-class.md#getconnect)

`dbSeeChanges` Příznak použijte, pokud chcete vytvořit soutisk změn provedených jiným uživatelem nebo jiným programem v počítači při úpravách nebo odstranění stejného záznamu. Pokud například dva uživatelé začnou upravovat stejný záznam, `Update` první uživatel, který zavolá členovou funkci, bude úspěšný. Když `Update` je volána druhý `CDaoException` uživatel, je vyvolána. Podobně pokud se druhý uživatel `Delete` pokusí volat k odstranění záznamu a již byl změněn `CDaoException` prvním uživatelem, dojde k.

Obvykle pokud uživatel získá `CDaoException` to při aktualizaci, váš kód by měl aktualizovat obsah polí a načíst nově upravené hodnoty. Pokud dojde k výjimce v procesu odstranění, váš kód může zobrazit data nového záznamu uživateli a zprávu oznamující, že data byla nedávno změněna. V tomto okamžiku může váš kód požádat o potvrzení, že uživatel stále chce záznam odstranit.

> [!TIP]
> Pomocí možnosti posouvání pouze`dbForwardOnly`dopředu ( ) můžete zvýšit výkon, když aplikace provede jeden průchod sadou záznamů otevřenou ze zdroje dat ROZHRANÍ ODBC.

Související informace naleznete v tématu "OpenRecordset Method" v nápovědě DAO.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>Sada záznamů CDao::Redotaz

Volání této členské funkce znovu sestavit (aktualizovat) sadu záznamů.

```
virtual void Requery();
```

### <a name="remarks"></a>Poznámky

Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Aby sada záznamů odrážela dodatky a odstranění, které vy nebo jiní uživatelé provádíte do `Requery`zdroje dat, je nutné znovu vytvořit sadu záznamů voláním . Pokud je sada záznamů dynaset, automaticky odráží aktualizace, které vy nebo jiní uživatelé provedete s existujícími záznamy (ale ne s dodatky). Pokud je sada záznamů snímek, `Requery` musíte volat tak, aby odrážely úpravy ostatních uživatelů a také doplňky a odstranění.

Pro dynaset nebo snímek, `Requery` volání kdykoli chcete znovu sestavit sadu záznamů pomocí hodnot parametrů. Před voláním `Requery`nastavte nový filtr nebo seřaďte [nastavením m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) . Před voláním `Requery`nastavte nové parametry přiřazením nových hodnot datovým členům parametrů .

Pokud se pokus o znovusestavení sady záznamů nezdaří, sada záznamů je uzavřena. Před voláním `Requery`můžete určit, zda lze sadu záznamů znovu dotazovat voláním členské funkce [CanRestart.](#canrestart) `CanRestart`nezaručuje, `Requery` že bude úspěšná.

> [!CAUTION]
> Zavolejte `Requery` až po `Open`zavolání .

> [!NOTE]
> Volání [Requery](#requery) změní záložky DAO.

Nelze volat `Requery` na dynaset typu nebo snímek typu recordset, pokud volání `CanRestart` vrátí 0, ani jej nelze použít na sadu záznamů typu tabulka.

Pokud `IsBOF` oba `IsEOF` a vrátit nenulovou po volání `Requery`, dotaz nevrátil žádné záznamy a sada záznamů bude obsahovat žádná data.

Související informace naleznete v tématu "Metoda opětovného dotazování" v nápovědě dao.

## <a name="cdaorecordsetseek"></a><a name="seek"></a>Sada rekordů CDao::Hledat

Volání této členské funkce vyhledejte záznam v objektu sady záznamů typu indexované tabulky, který splňuje zadaná kritéria pro aktuální index a provede tento záznam aktuálním záznamem.

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

*lpszSrovnání*<br/>
Jeden z následujících řetězcových výrazů:\<"<", " =", "=", ">=" nebo ">".

*pKlíč1*<br/>
Ukazatel na [COleVariant,](../../mfc/reference/colevariant-class.md) jehož hodnota odpovídá první pole v indexu. Povinná hodnota.

*pKlíč2*<br/>
Ukazatel na `COleVariant` jehož hodnota odpovídá druhému poli v indexu, pokud existuje. Výchozí hodnota je null.

*pKlíč3*<br/>
Ukazatel na `COleVariant` jehož hodnota odpovídá třetí pole v indexu, pokud existuje. Výchozí hodnota je null.

*pKeyArray*<br/>
Ukazatel na pole variant. Velikost pole odpovídá počtu polí v indexu.

*nKlávesy*<br/>
Celé číslo odpovídající velikosti pole, což je počet polí v indexu.

> [!NOTE]
> Nezadávejte zástupné znaky v klíčích. Zástupné znaky `Seek` způsobí vrácení žádné odpovídající záznamy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou nalezeny odpovídající záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Použijte druhou (maticovou) `Seek` verzi ke zpracování indexů čtyř nebo více polí.

`Seek`umožňuje vyhledávání vysoce výkonných indexů na sadách záznamů typu tabulka. Aktuální index je nutné `SetCurrentIndex` nastavit `Seek`voláním před voláním . Pokud index identifikuje nejedinečné klíčové pole `Seek` nebo pole, vyhledá první záznam, který splňuje kritéria. Pokud nenastavíte index, je vyvolána výjimka.

Všimněte si, že pokud nevytváříte `COleVariant` sadu záznamů UNICODE, musí být objekty explicitně deklarovány ANSI. To lze provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktoru s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `VT_BSTRT` *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na .

Při volání `Seek`předáte jednu nebo více klíčových hodnot a\<operátor porovnání ("<", " =", "=", ">=" nebo ">"). `Seek`Prohledá zadaná klíčová pole a vyhledá první záznam, který splňuje kritéria zadaná *parametry lpszComparison* a *pKey1*. Po nalezení `Seek` vrátí nenulovou hodnotu a tento záznam bude aktuální. Pokud `Seek` se nepodaří `Seek` najít shodu, vrátí nulu a aktuální záznam není definován. Při použití DAO přímo, musíte explicitně zkontrolovat NoMatch vlastnost.

Pokud `lpszComparison` je "=", ">=" nebo `Seek` ">", začíná na začátku indexu. Pokud *lpszComparison* je "<" nebo `Seek` "<=", začíná na konci indexu a hledá zpět, pokud nejsou duplicitní položky rejstříku na konci. V tomto `Seek` případě začíná na libovolnou položku mezi duplicitní položky rejstříku na konci indexu.

Při použití `Seek`nemusí být aktuální záznam .

Chcete-li vyhledat záznam v sadě záznamů typu dynaset nebo snímek, která splňuje určitou podmínku, použijte operace hledání. Chcete-li zahrnout všechny záznamy, nikoli pouze ty, které splňují určitou podmínku, použijte operace přesunu k přesunu ze záznamu na záznam.

Nelze volat `Seek` na připojené tabulky libovolného typu, protože připojené tabulky musí být otevřeny jako sady záznamů typu dynaset nebo snímek. Pokud však `CDaoDatabase::Open` voláte k přímému otevření instalovatelné databáze `Seek` ISAM, můžete volat tabulky v této databázi, i když výkon může být pomalý.

Související informace naleznete v tématu "Seek Method" v nápovědě DAO.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>Sada rekordů CDao::Nastavitabsolutní pozici

Nastaví relativní počet záznamů aktuálního záznamu objektu sady záznamů.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parametry

*lPozice*<br/>
Odpovídá pořadí aktuálního záznamu v sadě záznamů.

### <a name="remarks"></a>Poznámky

Volání `SetAbsolutePosition` umožňuje umístit aktuální ukazatel záznamu na konkrétní záznam na základě jeho ordinální pozice v sadě záznamů typu dynaset nebo snímek. Aktuální číslo záznamu můžete také určit voláním [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
> Tato členská funkce je platná pouze pro sady záznamů typu dynaset a snímek.

Hodnota vlastnosti AbsolutePosition podkladového objektu DAO je založena na nule; nastavení 0 odkazuje na první záznam v sadě záznamů. Nastavení hodnoty větší než počet naplněných záznamů způsobí, že knihovna MFC vyvolá výjimku. Počet naplněných záznamů v sadě záznamů můžete určit `GetRecordCount` voláním členské funkce.

Pokud je aktuální záznam odstraněn, hodnota vlastnosti AbsolutePosition není definována a knihovna MFC vyvolá výjimku, pokud je odkazována. Na konec sekvence jsou přidány nové záznamy.

> [!NOTE]
> Tato vlastnost není určena k použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem, jak zachovat a vrátit se na danou pozici, a jsou jediným způsobem, jak umístit aktuální záznam napříč všemi typy objektů sady záznamů, které podporují záložky. Zejména pozice daného záznamu se změní, když jsou záznamy před ním odstraněny. Neexistuje také žádné ujištění, že daný záznam bude mít stejnou absolutní pozici, pokud je sada záznamů znovu vytvořena, protože pořadí jednotlivých záznamů v rámci sady záznamů není zaručeno, pokud není vytvořeno pomocí příkazu SQL pomocí klauzule **ORDERBY.**

Související informace naleznete v tématu "Vlastnost absoluteposition" v nápovědě DAO.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>Sada záznamů CDao:SetBookmark

Volání této členské funkce umístit sadu záznamů na záznam obsahující zadanou záložku.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) objekt obsahující hodnotu záložky pro určitý záznam.

### <a name="remarks"></a>Poznámky

Při vytvoření nebo otevření objektu sady záznamů má každý z jeho záznamů již jedinečnou záložku. Záložku pro aktuální záznam můžete načíst voláním `GetBookmark` a `COleVariant` uložením hodnoty do objektu. K tomuto záznamu se `SetBookmark` později můžete vrátit voláním pomocí uložené hodnoty záložky.

> [!NOTE]
> Volání [Requery](#requery) změní záložky DAO.

Všimněte si, že pokud nevytváříte `COleVariant` sadu záznamů UNICODE, musí být objekt explicitně deklarován ANSI. To lze provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktoru s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `VT_BSTRT` *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na .

Související informace naleznete v tématech "Vlastnost záložky" a Bookmarkable Property v nápovědě DAO.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>Sada záznamů CDao:SetSet

Voláním této členské funkce nastavte počet záznamů, které mají být uloženy do mezipaměti.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parametry

*lVelikost*<br/>
Určuje počet záznamů. Typická hodnota je 100. Nastavení 0 vypne ukládání do mezipaměti. Nastavení musí být mezi 5 a 1200 záznamy. Mezipaměť může používat značné množství paměti.

### <a name="remarks"></a>Poznámky

Mezipaměť je mezera v místní paměti, která obsahuje data naposledy načtená ze serveru v případě, že data budou požadována znovu v době, kdy je aplikace spuštěna. Ukládání dat do mezipaměti zlepšuje výkon aplikace, která načítá data ze vzdáleného serveru prostřednictvím objektů sady záznamů typu dynaset. Pokud jsou požadována data, databázový stroj Microsoft Jet nejprve zkontroluje mezipaměť pro požadovaná data, nikoli načítat ze serveru, což trvá déle. Data, která nepocházejí ze zdroje dat ODBC, nejsou uložena v mezipaměti.

Jakýkoli zdroj dat ROZHRANÍ ODBC, například připojená tabulka, může mít místní mezipaměť. Chcete-li vytvořit mezipaměť, otevřete objekt sady záznamů `SetCacheSize` `SetCacheStart` ze vzdáleného zdroje `FillCache` dat, zavolejte členské funkce a potom volání množitelské funkce nebo krokování záznamů pomocí jedné z operací Move. Parametr *lSize* `SetCacheSize` členské funkce může být založen na počtu záznamů, se kterými může aplikace pracovat najednou. Pokud například používáte sadu záznamů jako zdroj dat, která mají být zobrazena `SetCacheSize` na obrazovce, můžete předat parametr *lSize* jako 20 a zobrazit 20 záznamů najednou.

Související informace naleznete v tématu CacheSize, CacheStart Properties v nápovědě dao.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>Sada záznamů CDao:SetSet

Volání této členské funkce určit záložku prvního záznamu v sadě záznamů, které mají být uloženy do mezipaměti.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
[COleVariant,](../../mfc/reference/colevariant-class.md) který určuje záložku prvního záznamu v sadě záznamů, který má být uložen do mezipaměti.

### <a name="remarks"></a>Poznámky

Můžete použít hodnotu záložky libovolného záznamu pro parametr `SetCacheStart` *varBookmark* členské funkce. Vytvořte záznam, který chcete spustit mezipaměť s aktuálním záznamem, vytvořte záložku pro tento záznam pomocí `SetCacheStart` [SetBookmark](#setbookmark)a předejte hodnotu záložky jako parametr pro člennou funkci.

Databázový stroj Microsoft Jet požaduje záznamy v rozsahu mezipaměti z mezipaměti a požaduje záznamy mimo rozsah mezipaměti ze serveru.

Záznamy načtené z mezipaměti neodrážejí změny provedené současně se zdrojovými daty jinými uživateli.

Chcete-li vynutit aktualizaci všech dat uložených `SetCacheSize` v mezipaměti, předejte parametr *lSize* jako 0, `FillCache` znovu zavolejte `SetCacheSize` s velikostí mezipaměti, kterou jste původně požadovali, a pak zavolejte člennou funkci.

Všimněte si, že pokud nevytváříte `COleVariant` sadu záznamů UNICODE, musí být objekt explicitně deklarován ANSI. To lze provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktoru s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `VT_BSTRT` *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na .

Související informace naleznete v tématu CacheSize, CacheStart Properties" v nápovědě dao.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>Sada záznamů CDao:SetCurrentIndex

Volání této členské funkce nastavit index na sadu záznamů typu tabulky.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ukazatel obsahující název indexu, který má být nastaven.

### <a name="remarks"></a>Poznámky

Záznamy v základních tabulkách nejsou uloženy v určitém pořadí. Nastavení indexu změní pořadí záznamů vrácených z databáze, ale nemá vliv na pořadí, ve kterém jsou uloženy záznamy. Zadaný index již musí být definován. Pokud se pokusíte použít objekt indexu, který neexistuje, nebo pokud index není nastaven při volání [Seek](#seek), knihovna MFC vyvolá výjimku.

Nový index pro tabulku můžete vytvořit voláním [CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) a připojením nového indexu do kolekce indexů podkladového tabledef voláním [CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)a opětovným otevřením sady záznamů.

Záznamy vrácené ze sady záznamů typu tabulky lze seřadit pouze podle indexů definovaných pro podkladovou tabulkovou def. Chcete-li seřadit záznamy v jiném pořadí, můžete otevřít sadu záznamů typu dynaset nebo snímek pomocí klauzule SQL **ORDERBY** uložené v [sadě CDaoRecordset::m_strSort](#m_strsort).

Související informace naleznete v tématu "Objekt indexu" a definici "aktuální index" v nápovědě DAO.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>Sada rekordů CDao:SetFieldDirty

Volání této členské funkce příznakem člena dat pole sady záznamů jako změněné nebo jako beze změny.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo null. Pokud null, jsou označeny všechny členy dat pole v sadě záznamů. (C++ NULL není stejný jako Null v databázi terminologie, což znamená "bez hodnoty.")

*bDirty*<br/>
PRAVDA, pokud má být datový člen pole označen jako "dirty" (změněn). Jinak FALSE, pokud člen dat pole má být označen jako "čistý" (beze změny).

### <a name="remarks"></a>Poznámky

Označení polí jako nezměněných zajistí, že pole nebude aktualizováno.

Rámcové značky změnily datové členy pole, aby bylo zajištěno, že budou zapsány do záznamu na zdroji dat mechanismem výměny pole záznamů DAO (DFX). Změna hodnoty pole obvykle nastaví pole dirty automaticky, takže `SetFieldDirty` budete zřídka muset volat sami sebe, ale někdy můžete chtít zajistit, že sloupce budou explicitně aktualizovány nebo vloženy bez ohledu na to, jaká hodnota je v datovém členu pole. Mechanismus DFX také využívá použití PSEUDONULL. Další informace naleznete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud mechanismus dvojité vyrovnávací paměti není používán, pak změna hodnoty pole automaticky nenastaví pole jako dirty. V takovém případě bude nutné explicitně nastavit pole jako dirty. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

> [!NOTE]
> Volání této členské funkce až po volání [Upravit](#edit) nebo [Přidatnový](#addnew).

Použití null pro první argument funkce bude používat `outputColumn` funkci pro všechna `CDaoFieldExchange`pole, nikoli **param** pole v . Například volání

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

nastaví `outputColumn` pouze pole na hodnotu NULL; **param** pole nebudou ovlivněna.

Chcete-li pracovat na **param**, musíte zadat skutečnou adresu jednotlivých **param,** na kterém chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

To znamená, že nelze nastavit všechna pole **param** na hodnotu NULL, stejně jako u `outputColumn` polí.

`SetFieldDirty`je implementována prostřednictvím `DoFieldExchange`.

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>Sada záznamů CDao:SetFieldNull

Volání této členské funkce příznak emitované ho člen dat pole sady záznamů jako Null (konkrétně bez hodnoty) nebo jako non-Null.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo null. Pokud null, jsou označeny všechny členy dat pole v sadě záznamů. (C++ NULL není stejný jako Null v databázi terminologie, což znamená "bez hodnoty.")

*bNull*<br/>
Nenulová, pokud má být datový člen pole označen jako neoznačený jako bez hodnoty (Null). V opačném případě 0, pokud má být datový člen pole označen jako nenulový.

### <a name="remarks"></a>Poznámky

`SetFieldNull`se používá pro pole `DoFieldExchange` vázaná v mechanismu.

Když přidáte nový záznam do sady záznamů, všechny datové členy pole jsou zpočátku nastaveny na hodnotu Null a označeny jako "dirty" (změněno). Při načtení záznamu ze zdroje dat jeho sloupce již mají hodnoty nebo jsou null. Pokud není vhodné, aby pole Null, [CDaoException je vyvolána.](../../mfc/reference/cdaoexception-class.md)

Pokud používáte mechanismus dvojité ukládání do vyrovnávací paměti, například pokud chcete konkrétně určit pole aktuálního záznamu jako neobsahující hodnotu, volání `SetFieldNull` s *hodnotou bNull* nastavenou na hodnotu TRUE, která jej označuje jako null. Pokud bylo pole dříve označeno jako null a nyní chcete mu přidělit hodnotu, jednoduše nastavte jeho novou hodnotu. Není třeba odebrat příznak Null `SetFieldNull`s . Chcete-li zjistit, zda je povoleno mít pole hodnotu Null, zavolejte [isfieldnullable](#isfieldnullable).

Pokud nepoužíváte mechanismus dvojité ukládání do vyrovnávací paměti, pak změna hodnoty pole automaticky nenastaví pole jako dirty a non-Null. Je nutné konkrétně nastavit pole dirty a non-Null. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

Mechanismus DFX využívá použití PSEUDONULL. Další informace naleznete v tématu [CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
> Volání této členské funkce až po volání [Upravit](#edit) nebo [Přidatnový](#addnew).

Použití null pro první argument funkce bude používat `outputColumn` funkci pouze pro `CDaoFieldExchange`pole, nikoli **param** pole v . Například volání

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

nastaví `outputColumn` pouze pole na hodnotu NULL; **param** pole nebudou ovlivněna.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>Sada záznamů CDao::SetFieldValue

Volání této členské funkce nastavit hodnotu pole, buď ordinální pozice nebo změnou hodnoty řetězce.

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

*název lpsz*<br/>
Ukazatel na řetězec obsahující název pole.

*varValue*<br/>
Odkaz na [cOleVariant](../../mfc/reference/colevariant-class.md) objekt obsahující hodnotu obsahu pole.

*nIndex*<br/>
Celé číslo, které představuje pořitou pozici pole v kolekci Polí sady záznamů (od nuly).

*lpszValue*<br/>
Ukazatel na řetězec obsahující hodnotu obsahu pole.

### <a name="remarks"></a>Poznámky

Použití `SetFieldValue` a [GetFieldValue](#getfieldvalue) dynamicky vázat pole za běhu, nikoli staticky vazebné sloupce pomocí [doFieldExchange](#dofieldexchange) mechanismus.

Všimněte si, že pokud nevytváříte sadu záznamů UNICODE, musíte buď použít `SetFieldValue` formulář, který neobsahuje `COleVariant` parametr, nebo `COleVariant` objekt musí být explicitně deklarován ANSI. To lze provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktoru s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `VT_BSTRT` *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na .

Související informace naleznete v tématech "Objekt pole" a "Vlastnost hodnoty" v nápovědě dao.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>Sada záznamů CDao::SetFieldValueNull

Volání této členské funkce nastavit pole na hodnotu Null.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index pole v sadě záznamů pro vyhledávání podle indexu založeného na nule.

*název lpsz*<br/>
Název pole v sadě záznamů pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

C++ NULL není stejný jako Null, což v terminologii databáze znamená "bez hodnoty."

Související informace naleznete v tématech "Objekt pole" a "Vlastnost hodnoty" v nápovědě dao.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>Sada záznamů CDao:SetLockingMode

Volání této členské funkce nastavit typ uzamčení pro sadu záznamů.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parametry

*bPesimistič*<br/>
Příznak, který označuje typ zamykání.

### <a name="remarks"></a>Poznámky

Když je v platnosti pesimistické zamykání, stránka 2K obsahující záznam, který upravujete, je uzamčena, jakmile zavoláte členskou `Edit` funkci. Stránka se odemkne, `Update` `Close` když zavoláte nebo členskou funkci nebo některou z operací Move nebo Find.

Při optimistické uzamčení je v platnosti, 2K stránka obsahující záznam je `Update` uzamčen pouze v případě, že záznam je aktualizován s členskou funkcí.

Pokud je stránka zamknutá, žádný jiný uživatel nemůže upravovat záznamy na stejné stránce. Pokud zavoláte `SetLockingMode` a předáte nenulovou hodnotu a jiný uživatel již `Edit`má stránku uzamčenou, je při volání vyvolána výjimka . Ostatní uživatelé mohou číst data z uzamčených stránek.

Pokud voláte `SetLockingMode` s nulovou `Update` hodnotou a později voláte, když je stránka uzamčena jiným uživatelem, dojde k výjimce. Chcete-li zobrazit změny provedené v záznamu jiným uživatelem `SetBookmark` (a ztratit změny), zavolejte členská funkce s hodnotou záložky aktuálního záznamu.

Při práci se zdroji dat ODBC je režim uzamčení vždy optimistický.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>Sada záznamů CDao::SetParamValue

Volání této členské funkce nastavit hodnotu parametru v sadě záznamů za běhu.

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
Číselná pozice parametru v kolekci Parameters querydef.

*var*<br/>
Hodnota, která má být nastavena; viz Poznámky.

*název lpsz*<br/>
Název parametru, jehož hodnotu chcete nastavit.

### <a name="remarks"></a>Poznámky

Parametr již musí být vytvořen jako součást řetězce SQL sady záznamů. K parametru můžete přistupovat podle názvu nebo podle jeho pozice indexu v kolekci.

Zadejte hodnotu, `COleVariant` kterou chcete nastavit jako objekt. Informace o nastavení požadované hodnoty a `COleVariant` zadejte do objektu naleznete v tématu [colevariant](../../mfc/reference/colevariant-class.md)třídy . Všimněte si, že pokud nevytváříte `COleVariant` sadu záznamů UNICODE, musí být objekt explicitně deklarován ANSI. To lze provést pomocí [COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** forma konstruktoru s *vtSrc* nastavena na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `VT_BSTRT` *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavena na .

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>Sada záznamů CDao::SetParamValueNull

Volání této členské funkce nastavit parametr na hodnotu Null.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index pole v sadě záznamů pro vyhledávání podle indexu založeného na nule.

*název lpsz*<br/>
Název pole v sadě záznamů pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

C++ NULL není stejný jako Null, což v terminologii databáze znamená "bez hodnoty."

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>Sada záznamů CDao:SetPercentPosition

Voláním této členské funkce nastavte hodnotu, která změní přibližné umístění aktuálního záznamu v objektu sady záznamů na základě procenta záznamů v sadě záznamů.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parametry

*fPozice*<br/>
Číslo mezi 0 a 100.

### <a name="remarks"></a>Poznámky

Při práci se sadou záznamů typu dynaset nebo snímek nejprve naplňte sadu `SetPercentPosition`záznamů přesunutím na poslední záznam před voláním . Pokud zavoláte `SetPercentPosition` před plně naplnění sady záznamů, množství pohybu je relativní k počtu záznamů přístupných, jak je uvedeno v hodnotě [GetRecordCount](#getrecordcount). Na poslední záznam můžete přejít voláním `MoveLast`.

Po volání `SetPercentPosition`se záznam na přibližné pozici odpovídající této hodnotě stane aktuálním.

> [!NOTE]
> Volání `SetPercentPosition` pro přesunutí aktuálního záznamu na určitý záznam v sadě záznamů se nedoporučuje. Místo toho zavolejte člennou funkci [SetBookmark.](#setbookmark)

Související informace naleznete v tématu "Vlastnost pozice percentposition" v nápovědě dao.

## <a name="cdaorecordsetupdate"></a><a name="update"></a>Sada záznamů CDao::Aktualizovat

Volání této členské funkce po `AddNew` `Edit` volání nebo členské funkce.

```
virtual void Update();
```

### <a name="remarks"></a>Poznámky

Toto volání je `AddNew` nutné `Edit` k dokončení operace nebo.

Obě `AddNew` `Edit` a připravit upravit vyrovnávací paměti, ve kterém jsou umístěny přidané nebo upravené data pro uložení do zdroje dat. `Update`uloží data. Aktualizována jsou pouze pole označená nebo zjištěná jako změněná.

Pokud zdroj dat podporuje transakce, můžete `Update` volání (a `AddNew` `Edit` jeho odpovídající nebo volání) součástí transakce.

> [!CAUTION]
> Pokud `Update` zavoláte bez `AddNew` předchozího volání buď nebo `Edit`, `Update` vyvolá . `CDaoException` Pokud `AddNew` zavoláte `Edit`nebo , `Update` musíte zavolat před voláním [MoveNext](#movenext) nebo zavřít sadu záznamů nebo připojení zdroje dat. V opačném případě budou změny ztraceny bez oznámení.

Pokud je objekt sady záznamů pesimisticky uzamčen ve víceuživatelském `Edit` prostředí, zůstane záznam uzamčen od doby, kdy se použije, dokud nebude aktualizace dokončena. Pokud je sada záznamů optimisticky uzamčena, záznam je uzamčen a porovnán s předem upraveným záznamem těsně před aktualizací v databázi. Pokud se záznam od `Edit`volání `Update` změnil , operace se nezdaří a knihovna MFC vyvolá výjimku. Režim zamykání `SetLockingMode`můžete změnit pomocí .

> [!NOTE]
> Optimistické zamykání se vždy používá ve formátech externí databáze, jako je například ROZHRANÍ ODBC a instalovatelný ISAM.

Související informace naleznete v tématech "AddNew Method", "CancelUpdate Method", "Delete Method", "LastModified Property", "Update Method" a "EditMode Property" v nápovědě DAO.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
