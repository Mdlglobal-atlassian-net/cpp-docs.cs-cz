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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418788"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset Class

Představuje sadu záznamů vybraných ze zdroje dat.

## <a name="syntax"></a>Syntaxe

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoRecordset:: CDaoRecordset](#cdaorecordset)|Vytvoří objekt `CDaoRecordset`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoRecordset:: AddNew](#addnew)|Připraví pro přidání nového záznamu. Dokončete přidání [aktualizací](#update) volání.|
|[CDaoRecordset:: CanAppend](#canappend)|Vrátí nenulovou hodnotu, pokud je možné přidat nové záznamy do sady záznamů prostřednictvím členské funkce [AddNew](#addnew) .|
|[CDaoRecordset:: CanBookmark](#canbookmark)|Vrátí nenulovou hodnotu, pokud sada záznamů podporuje záložky.|
|[CDaoRecordset:: CancelUpdate](#cancelupdate)|Zruší všechny probíhající aktualizace z důvodu operace [Edit](#edit) nebo [AddNew](#addnew) .|
|[CDaoRecordset:: CanRestart](#canrestart)|Vrátí nenulovou hodnotu, pokud lze volat [opakované](#requery) dotazování pro opětovné spuštění dotazu sady záznamů.|
|[CDaoRecordset:: CanScroll](#canscroll)|Vrátí nenulovou hodnotu, pokud můžete procházet záznamy.|
|[CDaoRecordset:: CanTransact](#cantransact)|Vrátí nenulovou hodnotu, pokud zdroj dat podporuje transakce.|
|[CDaoRecordset:: CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud může být sada záznamů aktualizována (můžete přidat, aktualizovat nebo odstranit záznamy).|
|[CDaoRecordset:: Close](#close)|Zavře sadu záznamů.|
|[CDaoRecordset::D dstranit](#delete)|Odstraní aktuální záznam ze sady záznamů. Po odstranění musíte explicitně přejít na jiný záznam.|
|[CDaoRecordset::D oFieldExchange](#dofieldexchange)|Volá se k výměně dat (v obou směrech) mezi datovými členy pole sady záznamů a odpovídajícím záznamem ve zdroji dat. Implementuje výměnu pole záznamu DAO (DFX).|
|[CDaoRecordset:: Edit](#edit)|Připraví změny aktuálního záznamu. Pro dokončení úpravy zavolejte `Update`.|
|[CDaoRecordset:: FillCache](#fillcache)|Vyplní všechny nebo část místní mezipaměti pro objekt sady záznamů, který obsahuje data ze zdroje dat ODBC.|
|[CDaoRecordset:: Find](#find)|Vyhledá první, další, předchozí nebo poslední umístění konkrétního řetězce v sadě záznamů typu dynamická sada, která vyhovuje zadaným kritériím a vytváří záznam aktuálního záznamu.|
|[CDaoRecordset:: FindFirst](#findfirst)|Vyhledá první záznam v sadě dat typu Dynamic-Type nebo Snapshot-Type, který splňuje zadaná kritéria, a vytvoří záznam aktuálního záznamu.|
|[CDaoRecordset:: FindLast](#findlast)|Vyhledá poslední záznam v dynamické sadě nebo sadě záznamů typu Snapshot, které splňují zadaná kritéria, a vytvoří záznam aktuálního záznamu.|
|[CDaoRecordset:: NajítDalší](#findnext)|Vyhledá další záznam v sadě dat typu Dynamic-Type nebo Snapshot-Type, který splňuje zadaná kritéria, a vytvoří záznam aktuálního záznamu.|
|[CDaoRecordset:: FindPrev](#findprev)|Vyhledá předchozí záznam v sadě typů nebo sadě záznamů typu Snapshot, které splňují zadaná kritéria, a vytvoří záznam aktuálního záznamu.|
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|Vrátí číslo záznamu aktuálního záznamu objektu sady záznamů.|
|[CDaoRecordset:: GetBookmark](#getbookmark)|Vrátí hodnotu, která představuje záložku na záznamu.|
|[CDaoRecordset:: GetCacheSize](#getcachesize)|Vrátí hodnotu, která určuje počet záznamů v sadě záznamů typu Dynamic-Type obsahující data, která mají být uložena do mezipaměti ze zdroje dat ODBC.|
|[CDaoRecordset:: GetCacheStart](#getcachestart)|Vrátí hodnotu, která určuje záložku prvního záznamu v sadě záznamů, která má být ukládána do mezipaměti.|
|[CDaoRecordset:: GetCurrentIndex](#getcurrentindex)|Vrátí `CString` obsahující název indexu, který byl naposledy použit pro indexovaný `CDaoRecordset`typu Table.|
|[CDaoRecordset:: GetDateCreated](#getdatecreated)|Vrátí datum a čas, kdy se vytvořil základní tabulka s podkladovým objektem `CDaoRecordset`.|
|[CDaoRecordset:: GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny provedené v návrhu základní tabulky podkladového objektu `CDaoRecordset`.|
|[CDaoRecordset:: GetDefaultDBName](#getdefaultdbname)|Vrátí název výchozího zdroje dat.|
|[CDaoRecordset:: GetDefaultSQL](#getdefaultsql)|Volá se, aby se získal výchozí řetězec SQL, který se má provést.|
|[CDaoRecordset:: GetEditMode](#geteditmode)|Vrátí hodnotu, která označuje stav úprav aktuálního záznamu.|
|[CDaoRecordset:: GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v sadě záznamů.|
|[CDaoRecordset:: GetFieldInfo](#getfieldinfo)|Vrátí konkrétní druhy informací o polích v sadě záznamů.|
|[CDaoRecordset:: GetFieldValue –](#getfieldvalue)|Vrátí hodnotu pole v sadě záznamů.|
|[CDaoRecordset:: GetIndexCount](#getindexcount)|Načte počet indexů v tabulce podkladové sady záznamů.|
|[CDaoRecordset:: GetIndexInfo](#getindexinfo)|Vrátí různé druhy informací o indexu.|
|[CDaoRecordset:: GetLastModifiedBookmark](#getlastmodifiedbookmark)|Slouží k určení naposledy přidané nebo aktualizovaného záznamu.|
|[CDaoRecordset:: GetLockingMode](#getlockingmode)|Vrátí hodnotu, která označuje typ zamykání, který je platný při úpravách.|
|[CDaoRecordset:: GetName](#getname)|Vrátí `CString` obsahující název sady záznamů.|
|[CDaoRecordset:: GetParamValue](#getparamvalue)|Načte aktuální hodnotu zadaného parametru uloženou v podkladovém objektu DAOParameter.|
|[CDaoRecordset:: GetPercentPosition](#getpercentposition)|Vrátí pozici aktuálního záznamu jako procento z celkového počtu záznamů.|
|[CDaoRecordset:: GetRecordCount](#getrecordcount)|Vrátí počet záznamů, které jsou k dispozici v objektu sady záznamů.|
|[CDaoRecordset:: GetSQL](#getsql)|Získá řetězec SQL, který slouží k výběru záznamů pro sadu záznamů.|
|[CDaoRecordset:: GetType](#gettype)|Volá se, aby se určil typ sady záznamů: typ tabulky, dynamická sada nebo typ snímku.|
|[CDaoRecordset:: getověřovací pravidlo](#getvalidationrule)|Vrátí `CString` obsahující hodnotu, která ověřuje data při jejich zadání do pole.|
|[CDaoRecordset:: GetValidationText](#getvalidationtext)|Načte text, který se zobrazí, když není splněno ověřovací pravidlo.|
|[CDaoRecordset:: IsBOF](#isbof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna před první záznam. Neexistuje aktuální záznam.|
|[CDaoRecordset:: IsDeleted](#isdeleted)|Vrátí nenulovou hodnotu, pokud je sada záznamů umístěna na odstraněný záznam.|
|[CDaoRecordset:: IsEOF](#iseof)|Vrátí nenulovou hodnotu, pokud byla sada záznamů umístěna za posledním záznamem. Neexistuje aktuální záznam.|
|[CDaoRecordset:: IsFieldDirty](#isfielddirty)|Vrátí nenulovou hodnotu, pokud je zadané pole v aktuálním záznamu změněno.|
|[CDaoRecordset:: IsFieldNull](#isfieldnull)|Vrátí nenulovou hodnotu, pokud je zadané pole v aktuálním záznamu null (bez hodnoty).|
|[CDaoRecordset:: IsFieldNullable](#isfieldnullable)|Vrátí nenulovou hodnotu, pokud zadané pole v aktuálním záznamu může být nastaveno na hodnotu null (bez hodnoty).|
|[CDaoRecordset:: Open](#isopen)|Vrátí nenulovou hodnotu, pokud byla dříve volána metoda [Open](#open) .|
|[CDaoRecordset:: Move](#move)|Umístí sadu záznamů na zadaný počet záznamů z aktuálního záznamu v obou směrech.|
|[CDaoRecordset:: MoveFirst](#movefirst)|Umístí aktuální záznam na první záznam v sadě záznamů.|
|[CDaoRecordset:: MoveLast](#movelast)|Umístí aktuální záznam na poslední záznam v sadě záznamů.|
|[CDaoRecordset:: MoveNext](#movenext)|Umístí aktuální záznam na další záznam v sadě záznamů.|
|[CDaoRecordset:: MovePrev](#moveprev)|Umístí aktuální záznam na předchozí záznam v sadě záznamů.|
|[CDaoRecordset:: Open](#open)|Vytvoří novou sadu záznamů z tabulky, dynamické sady nebo snímku.|
|[CDaoRecordset:: Requery](#requery)|Spustí znovu dotaz sady záznamů pro aktualizaci vybraných záznamů.|
|[CDaoRecordset:: Seek](#seek)|Vyhledá záznam v indexovaném objektu sady záznamů typu tabulka, který splňuje zadaná kritéria pro aktuální index a vytváří záznam aktuálního záznamu.|
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|Nastaví číslo záznamu aktuálního záznamu objektu sady záznamů.|
|[CDaoRecordset:: SetBookmark](#setbookmark)|Umístí sadu záznamů na záznam, který obsahuje zadanou záložku.|
|[CDaoRecordset:: SetCacheSize](#setcachesize)|Nastaví hodnotu, která určuje počet záznamů v sadě typů sady záznamů, které obsahují data, která budou uložena v mezipaměti ze zdroje dat ODBC.|
|[CDaoRecordset:: SetCacheStart](#setcachestart)|Nastaví hodnotu, která určuje záložku prvního záznamu v sadě záznamů, která má být uložena do mezipaměti.|
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|Volá se, aby se nastavil index pro sadu záznamů typu tabulka.|
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|Označí zadané pole v aktuálním záznamu jako změněné.|
|[CDaoRecordset:: SetFieldNull](#setfieldnull)|Nastaví hodnotu zadaného pole v aktuálním záznamu na hodnotu null (bez hodnoty).|
|[CDaoRecordset:: SetFieldValue](#setfieldvalue)|Nastaví hodnotu pole v sadě záznamů.|
|[CDaoRecordset:: SetFieldValueNull](#setfieldvaluenull)|Nastaví hodnotu pole v sadě záznamů na hodnotu null. (nemá žádnou hodnotu).|
|[CDaoRecordset:: SetLockingMode](#setlockingmode)|Nastaví hodnotu, která označuje typ uzamykání, který se má projevit při úpravách.|
|[CDaoRecordset:: SetParamValue](#setparamvalue)|Nastaví aktuální hodnotu zadaného parametru uloženého v podkladovém objektu DAOParameter.|
|[CDaoRecordset:: SetParamValueNull](#setparamvaluenull)|Nastaví aktuální hodnotu zadaného parametru na hodnotu null (nemá žádnou hodnotu).|
|[CDaoRecordset:: SetPercentPosition](#setpercentposition)|Nastaví pozici aktuálního záznamu na místo odpovídající procentu celkového počtu záznamů v sadě záznamů.|
|[CDaoRecordset:: Update](#update)|Dokončí operaci `AddNew` nebo `Edit` uložením nových nebo upravených dat ve zdroji dat.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoRecordset:: m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|Obsahuje příznak označující, zda jsou pole automaticky označena jako změněná.|
|[CDaoRecordset:: m_nFields](#m_nfields)|Obsahuje počet datových členů pole v třídě sady záznamů a počet sloupců, které sada záznamů vybere ze zdroje dat.|
|[CDaoRecordset:: m_nParams](#m_nparams)|Obsahuje počet datových členů parametrů v třídě sady záznamů – počet parametrů předaných s dotazem sady záznamů.|
|[CDaoRecordset:: m_pDAORecordset](#m_pdaorecordset)|Ukazatel na rozhraní DAO základní objekt sady záznamů.|
|[CDaoRecordset:: m_pDatabase](#m_pdatabase)|Zdrojová databáze pro tuto sadu výsledků. Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .|
|[CDaoRecordset:: m_strFilter](#m_strfilter)|Obsahuje řetězec, který slouží k vytvoření příkazu SQL **WHERE** .|
|[CDaoRecordset:: m_strSort](#m_strsort)|Obsahuje řetězec, který slouží k vytvoření příkazu SQL **ORDER by** .|

## <a name="remarks"></a>Poznámky

Známé jako "sady záznamů" `CDaoRecordset` objekty jsou k dispozici v následujících třech formulářích:

- Sady záznamů typu tabulka reprezentují základní tabulku, kterou můžete použít k prohlédnutí, přidávání, změnám nebo odstraňování záznamů z jedné databázové tabulky.

- Sady záznamů typu dynamická sada jsou výsledkem dotazu, který může obsahovat aktualizovatelné záznamy. Tyto sady záznamů jsou sadou záznamů, které můžete použít k prohlédnutí, přidávání, změnám nebo odstraňování záznamů z podkladové databázové tabulky nebo tabulek. Sada záznamů typu dynamická sada může obsahovat pole z jedné nebo více tabulek v databázi.

- Sady záznamů typu snímky jsou statickou kopií sady záznamů, kterou můžete použít k vyhledání dat nebo generování sestav. Tyto sady záznamů mohou obsahovat pole z jedné nebo více tabulek v databázi, ale nelze je aktualizovat.

Každá forma sady záznamů představuje sadu záznamů, které jsou opraveny v okamžiku otevření sady záznamů. Když přejdete na záznam v sadě záznamů typu tabulka nebo v sadě záznamů typu dynamická sada, odrážejí změny provedené v záznamu po otevření sady záznamů, a to buď jinými uživateli, nebo jinými sadami záznamů ve vaší aplikaci. (Sadu záznamů typu snímek nelze aktualizovat.) Můžete použít `CDaoRecordset` přímo nebo odvodit třídu sady záznamů specifickou pro aplikaci z `CDaoRecordset`. Pak můžete:

- Procházejte záznamy.

- Nastavte index a rychle vyhledejte záznamy pomocí [Seek](#seek) (jenom sady záznamů typu Table).

- Vyhledá záznamy na základě porovnání řetězců: "<", "\<=", "=", "> =" nebo ">" (sada záznamů typu sady a snímky).

- Aktualizujte záznamy a určete režim uzamykání (s výjimkou záznamů typu snímky).

- Filtrováním sady záznamů omezíte, které záznamy vybírají z těch, které jsou k dispozici ve zdroji dat.

- Seřaďte sadu záznamů.

- Parametrizovat sadu záznamů pro přizpůsobení jejího výběru s informacemi, které nejsou známy až do doby běhu.

Třída `CDaoRecordset` poskytuje rozhraní podobné tomu `CRecordset`třídy. Hlavním rozdílem je, že třída `CDaoRecordset` přistupuje k datům prostřednictvím objektu DAO (Data Access Object) založeného na technologii OLE. Třída `CRecordset` přistupuje k systému DBMS prostřednictvím rozhraní ODBC (Open Database Connectivity) a ovladače ODBC pro daný systém DBMS.

> [!NOTE]
> Databázové třídy DAO se liší od databázových tříd knihovny MFC založených na rozhraní ODBC (Open Database Connectivity). Všechny názvy databázových tříd DAO mají předponu "CDao". Ke zdrojům dat rozhraní ODBC můžete přistupovat i s třídami DAO; třídy DAO obecně nabízejí nadřazené možnosti, protože jsou specifické pro databázový stroj Microsoft Jet.

Můžete buď použít `CDaoRecordset` přímo nebo odvodit třídu z `CDaoRecordset`. Chcete-li použít třídu sady záznamů v obou případech, otevřete databázi a vytvořte objekt sady záznamů a předejte konstruktoru ukazatel na objekt `CDaoDatabase`. Můžete také vytvořit objekt `CDaoRecordset` a nechat MFC vytvořit dočasný objekt `CDaoDatabase`. Poté [Zavolejte členskou funkci](#open) sady záznamů a určete, zda je objekt sada záznamů typu tabulka, sada záznamů typu sada záznamů nebo sada záznamů typu snímek. Volání `Open` vybírá data z databáze a načítá první záznam.

Pomocí členských funkcí objektu a datových členů můžete procházet záznamy a pracovat s nimi. Operace, které jsou k dispozici, závisí na tom, zda je objekt sada záznamů typu tabulka, sada záznamů sady záznamů nebo sada záznamů typu snímek a zda je aktualizovatelný nebo jen pro čtení. to závisí na schopnostech databáze nebo připojení Open Database (ODBC). zdroj dat Chcete-li aktualizovat záznamy, které mohly být změněny nebo přidány od volání `Open`, zavolejte členskou funkci [ZnovuSpustitDotaz](#requery) objektu. Voláním členské funkce objektu `Close` a zničením objektu po jeho dokončení.

`CDaoRecordset` používá pro výměnu pole záznamu (DFX) rozhraní DAO k podpoře čtení a aktualizace polí záznamů prostřednictvím bezpečných C++ členů vaší `CDaoRecordset` nebo `CDaoRecordset`třídy odvozené od typu. Můžete také implementovat dynamickou vazbu sloupců v databázi bez použití mechanismu DFX pomocí [GetFieldValue –](#getfieldvalue) a [SetFieldValue](#setfieldvalue).

Související informace naleznete v tématu "objekt sady záznamů" v nápovědě pro rozhraní DAO.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="addnew"></a>CDaoRecordset:: AddNew

Zavolejte tuto členskou funkci pro přidání nového záznamu do typu tabulky nebo sady záznamů typu dynamická sada.

```
virtual void AddNew();
```

### <a name="remarks"></a>Poznámky

Pole záznamu mají počáteční hodnotu null. (V terminologii databáze hodnota null znamená "nemá žádnou hodnotu" a není shodná s hodnotou NULL v C++.) K dokončení této operace je nutné zavolat členskou funkci [Update](#update) . `Update` uloží změny do zdroje dat.

> [!CAUTION]
>  Pokud záznam upravíte a potom se posuňte na jiný záznam bez volání `Update`, změny se ztratí bez upozornění.

Pokud přidáte záznam do sady záznamů typu dynamická sada voláním metody [AddNew](#addnew), záznam je viditelný v sadě záznamů a obsažen v podkladové tabulce, kde je viditelný pro všechny nové `CDaoRecordset` objekty.

Pozice nového záznamu závisí na typu sady záznamů:

- V sadě záznamů typu dynamická sada, kde je nový záznam vložen, není zaručena. Toto chování se u Microsoft Jet 3,0 změnilo z důvodů výkonu a souběžnosti. Pokud je vaším cílem udělat nově přidaný záznam na aktuální záznam, získat záložku poslední změněné položky a přejít na tuto záložku:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- V sadě záznamů typu tabulka, pro kterou byl zadán index, jsou vráceny záznamy na správném místě v pořadí řazení. Pokud není zadán žádný index, jsou vráceny nové záznamy na konci sady záznamů.

Záznam, který byl aktuální před použitím `AddNew` zůstane aktuální. Pokud chcete nový záznam vytvořit jako aktuální a sada záznamů podporuje záložky, zavolejte [SetBookmark](#setbookmark) na záložku identifikovanou nastavením vlastnosti LastModified základního objektu sady záznamů DAO. To je užitečné při určování hodnoty pro pole čítače (automatické zvýšení) v přidaném záznamu. Další informace najdete v tématu [GetLastModifiedBookmark](#getlastmodifiedbookmark).

Pokud databáze podporuje transakce, můžete provést `AddNew` volání části transakce. Další informace o transakcích naleznete v tématu Třída [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Všimněte si, že před voláním `AddNew`byste měli zavolat [CDaoWorkspace:: BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) .

Je neplatné volat `AddNew` pro sadu záznamů, jejíž [otevřená](#open) členská funkce nebyla volána. `CDaoException` je vyvolána, pokud zavoláte `AddNew` pro sadu záznamů, kterou nelze připojit. Můžete určit, zda je možné sadu záznamů aktualizovat voláním [CanAppend](#canappend).

Rozhraní označuje změněné datové členy pole, aby se zajistilo jejich zápis do záznamu ve zdroji dat pomocí mechanismu výměny pole záznamu (DFX) DAO. Změna hodnoty pole obvykle automaticky nastaví pole jako chybné, takže nebudete muset volat [SetFieldDirty](#setfielddirty) sami, ale možná budete chtít zajistit, aby se sloupce explicitně aktualizovaly nebo vložily bez ohledu na to, jaká hodnota je v datovém členu pole. Mechanismus DFX používá také použití **pseudo null**. Další informace naleznete v tématu [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud se nepoužívá mechanismus dvojitého ukládání do vyrovnávací paměti, pak při změně hodnoty pole se pole automaticky nenastaví jako nečisté. V takovém případě bude nutné explicitně nastavit pole jako nečisté. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

> [!NOTE]
> Pokud jsou záznamy dvojité vyrovnávací paměti (to znamená, že je povolena automatická kontrola polí), volání `CancelUpdate` obnoví členské proměnné na hodnoty, které měly předtím, než se zavolaly `AddNew` nebo `Edit`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Metoda AddNew", "CancelUpdate Method", "vlastnost LastModified" a "EditMode Property".

##  <a name="canappend"></a>CDaoRecordset:: CanAppend

Zavolejte tuto členskou funkci pro zjištění, zda dříve otevřená sada záznamů umožňuje přidat nové záznamy voláním členské funkce [AddNew](#addnew) .

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů povoluje přidávání nových záznamů; v opačném případě 0. `CanAppend` vrátí 0, pokud jste sadu záznamů otevřeli jako jen pro čtení.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "připojit metodu" v nápovědě k rozhraní DAO.

##  <a name="canbookmark"></a>CDaoRecordset:: CanBookmark

Zavolejte tuto členskou funkci, abyste zjistili, jestli dříve otevřená sada záznamů umožňuje jednotlivě označit záznamy pomocí záložek.

```
BOOL CanBookmark();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud sada záznamů podporuje záložky, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud používáte sady záznamů založené výhradně na tabulkách databázového stroje Microsoft Jet, lze použít záložky s výjimkou sad záznamů typu snímek označených jako dopředné sady záznamů s posouváním. Jiné databázové produkty (externí zdroje dat ODBC) nemusí podporovat záložky.

Související informace najdete v nápovědě k rozhraní DAO v tématu "vlastnost s možnostmi záložky".

##  <a name="cancelupdate"></a>CDaoRecordset:: CancelUpdate

Členská funkce `CancelUpdate` zruší všechny probíhající aktualizace z důvodu operace [Edit](#edit) nebo [AddNew](#addnew) .

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>Poznámky

Například pokud aplikace volá členskou funkci `Edit` nebo `AddNew` a nevolala [aktualizaci](#update), `CancelUpdate` zruší všechny změny provedené po volání `Edit` nebo `AddNew`.

> [!NOTE]
>  Pokud jsou záznamy dvojité vyrovnávací paměti (to znamená, že je povolena automatická kontrola polí), volání `CancelUpdate` obnoví členské proměnné na hodnoty, které měly předtím, než se zavolaly `AddNew` nebo `Edit`.

Pokud není k dispozici žádná `Edit` nebo `AddNew` nevyřízená operace, `CancelUpdate` způsobí, že knihovna MFC vyvolá výjimku. Zavolejte členskou funkci [GetEditMode](#geteditmode) a určete, zda existuje operace, kterou lze zrušit.

Související informace naleznete v tématu "metoda CancelUpdate" v nápovědě k rozhraní DAO.

##  <a name="canrestart"></a>CDaoRecordset:: CanRestart

Voláním této členské funkce určíte, zda sada záznamů umožňuje restartování dotazu (pro aktualizaci svých záznamů) voláním členské funkce `Requery`.

```
BOOL CanRestart();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je možné volat `Requery` pro opětovné spuštění dotazu sady záznamů, jinak 0.

### <a name="remarks"></a>Poznámky

Sady záznamů typu tabulka nepodporují `Requery`.

Není-li `Requery` podporována, [je nutné volat](#open) příkaz [Zavřít](#close) a aktualizovat data. Můžete volat `Requery` a aktualizovat dotaz na podkladový parametr objektu sady záznamů poté, co byly hodnoty parametru změněny.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "restartovaná vlastnost".

##  <a name="canscroll"></a>CDaoRecordset:: CanScroll

Voláním této členské funkce určíte, zda sada záznamů umožňuje posouvání.

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud můžete procházet záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud zavoláte možnost [otevřít](#open) v `dbForwardOnly`, sada záznamů může přejít pouze na popředí.

Související informace najdete v tématu "umístění aktuálního ukazatele na záznam s rozhraním DAO" v nápovědě pro rozhraní DAO.

##  <a name="cantransact"></a>CDaoRecordset:: CanTransact

Voláním této členské funkce určíte, zda sada záznamů povoluje transakce.

```
BOOL CanTransact();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, Pokud podkladový zdroj dat podporuje transakce, jinak 0.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu "vlastnost transakcí" v nápovědě k rozhraní DAO.

##  <a name="canupdate"></a>CDaoRecordset:: CanUpdate

Zavolejte tuto členskou funkci, abyste zjistili, jestli se sada záznamů dá aktualizovat.

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze sadu záznamů aktualizovat (přidávat, aktualizovat a odstraňovat záznamy), jinak 0.

### <a name="remarks"></a>Poznámky

Sada záznamů může být jen pro čtení, pokud je podkladový zdroj dat určen jen pro čtení, nebo pokud jste zadali `dbReadOnly` pro *nOptions* , když jste volali [otevřít](#open) pro sadu záznamů.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Metoda AddNew", "Upravit metodu", "Delete Method", "metoda aktualizace" a "aktualizovatelné vlastnosti".

##  <a name="cdaorecordset"></a>CDaoRecordset:: CDaoRecordset

Vytvoří objekt `CDaoRecordset`.

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) nebo hodnota null. Pokud hodnota není NULL a členská funkce `CDaoDatabase`ho objektu `Open` nebyla volána pro jeho připojení ke zdroji dat, sada záznamů se ji pokusí otevřít za vás během vlastního [otevřeného](#open) volání. Pokud předáte hodnotu NULL, objekt `CDaoDatabase` je vytvořen a připojen pro vás pomocí informací o zdroji dat, které jste určili, pokud jste třídu sady záznamů odvozeni z `CDaoRecordset`.

### <a name="remarks"></a>Poznámky

Můžete buď použít `CDaoRecordset` přímo nebo odvodit třídu specifickou pro aplikaci z `CDaoRecordset`. Pomocí ClassWizard můžete odvodit vaše třídy sady záznamů.

> [!NOTE]
>  Pokud odvozujete třídu `CDaoRecordset`, vaše odvozená třída musí poskytovat svůj vlastní konstruktor. V konstruktoru odvozené třídy volejte `CDaoRecordset::CDaoRecordset`konstruktoru a předejte příslušné parametry spolu s ním.

Předat hodnotu NULL konstruktoru sady záznamů, aby měl objekt `CDaoDatabase` vytvořen a připojen automaticky. Toto je užitečnou klávesovou zkratku, která nevyžaduje vytvoření a připojení objektu `CDaoDatabase` před sestavením sady záznamů. Pokud objekt `CDaoDatabase` není otevřený, vytvoří se pro vás taky objekt [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) , který používá výchozí pracovní prostor. Další informace najdete v tématu [CDaoDatabase:: CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase).

##  <a name="close"></a>CDaoRecordset:: Close

Zavření objektu `CDaoRecordset` odebere z kolekce otevřených sad záznamů v přidružené databázi.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že `Close` nezničí objekt `CDaoRecordset`, lze objekt znovu použít voláním `Open` ve stejném zdroji dat nebo v jiném zdroji dat.

Všechny dokončené příkazy [AddNew](#addnew) a [Edit](#edit) jsou zrušeny a všechny probíhající transakce jsou vráceny zpět. Pokud chcete zachovat nedokončená přidání nebo úpravy, zavolejte [aktualizaci](#update) před voláním `Close` pro každou sadu záznamů.

Po volání `Close`můžete volat `Open` znovu. To umožňuje znovu použít objekt sady záznamů. Lepší alternativou je zavolat [dotaz](#requery), pokud je to možné.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "Close Method".

##  <a name="delete"></a>CDaoRecordset::D dstranit

Zavolejte tuto členskou funkci pro odstranění aktuálního záznamu v otevřené dynamické sadě nebo objektu Recordset typu tabulka.

```
virtual void Delete();
```

### <a name="remarks"></a>Poznámky

Po úspěšném odstranění jsou datové členy pole sady záznamů nastaveny na hodnotu null a je nutné explicitně volat jednu z navigačních funkcí členů sady záznamů ( [Move](#move), [Seek](#seek), [SetBookmark](#setbookmark)a tak dále), aby bylo možné přesunout odstraněný záznam. Při odstraňování záznamů ze sady záznamů musí být v sadě záznamů před voláním `Delete`. v opačném případě knihovna MFC vyvolá výjimku.

`Delete` Odebere aktuální záznam a zpřístupní ho. Odstraněný záznam se nedá upravit ani použít, zůstane aktuální. Až se přesunete na jiný záznam, nemůžete tento záznam znovu nastavit jako aktuální.

> [!CAUTION]
>  Sada záznamů musí být aktualizovatelná a při volání `Delete`musí být aktuální záznam v sadě záznamů platný. Pokud například odstraníte záznam, ale nebudete se posouvat k novému záznamu předtím, než `Delete` znovu zavoláte, `Delete` vyvolá výjimku [CDaoException](../../mfc/reference/cdaoexception-class.md).

Můžete zrušit odstranění záznamu, pokud použijete transakce a zavoláte členskou funkci [CDaoWorkspace:: Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) . Pokud je základní tabulka primární tabulkou relace odstranění v kaskádě, odstranění aktuálního záznamu může také odstranit jeden nebo více záznamů v cizí tabulce. Další informace najdete v nápovědě k rozhraní DAO definice "kaskádová odstranění".

Na rozdíl od `AddNew` a `Edit`, volání `Delete` není následováno voláním `Update`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Metoda AddNew", "Upravit metodu", "Delete Method", "metoda aktualizace" a "aktualizovatelné vlastnosti".

##  <a name="dofieldexchange"></a>CDaoRecordset::D oFieldExchange

Rozhraní volá tuto členskou funkci, aby automaticky vyměnila data mezi poli datových členů objektu Recordset a odpovídající sloupce aktuálního záznamu ve zdroji dat.

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>Parametry

*pFX*<br/>
Obsahuje ukazatel na objekt `CDaoFieldExchange`. Rozhraní již nastaví tento objekt pro určení kontextu operace výměny pole.

### <a name="remarks"></a>Poznámky

Také váže vaše datové členy parametrů, pokud existují, na zástupné symboly parametrů v řetězci příkazu SQL pro výběr sady záznamů. Výměna dat polí označovaná jako výměna pole záznamu (DFX) typu DAO (Record Field Exchange) funguje v obou směrech: z datových členů pole objektu sady záznamů do polí záznamu ve zdroji dat a ze záznamu ve zdroji dat do objektu Recordset. Pokud vytváříte sloupce vazbě dynamicky, nemusíte implementovat `DoFieldExchange`.

Jediná akce, kterou je třeba obvykle provést k implementaci `DoFieldExchange` pro odvozenou třídu sady záznamů, je vytvoření třídy pomocí ClassWizard a určení názvů a datových typů datových členů pole. Můžete také přidat kód, který ClassWizard zápisy pro určení parametrů datových členů. Pokud mají být všechna pole svázána dynamicky, tato funkce bude neaktivní, pokud nezadáte parametry datových členů.

Při deklaraci odvozené třídy sady záznamů pomocí ClassWizard průvodce zapíše přepsání `DoFieldExchange` pro vás, které se podobá následujícímu příkladu:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>CDaoRecordset:: Edit

Voláním této členské funkce povolíte změny aktuálního záznamu.

```
virtual void Edit();
```

### <a name="remarks"></a>Poznámky

Po volání členské funkce `Edit` se změny provedené v polích aktuálního záznamu zkopírují do vyrovnávací paměti pro kopírování. Až provedete požadované změny záznamu, zavolá `Update`, aby se změny uložily. `Edit` ukládá hodnoty datových členů sady záznamů. Pokud voláte `Edit`, proveďte změny a zavolejte `Edit` znovu, hodnoty záznamu budou obnoveny na to, co byly před prvním `Edit` volání.

> [!CAUTION]
>  Pokud záznam upravíte a pak provedete jakoukoli operaci, která se přesune na jiný záznam bez prvního volání `Update`, změny se ztratí bez upozornění. Kromě toho, pokud chcete sadu záznamů nebo nadřazenou databázi zavřít, Upravovaný záznam se zahodí bez upozornění.

V některých případech můžete chtít sloupec aktualizovat tak, že ho nastavíte na hodnotu null (neobsahuje žádná data). Chcete-li to provést, zavolejte `SetFieldNull` s parametrem TRUE k označení pole na hodnotu null; tím také dojde k aktualizaci sloupce. Chcete-li, aby pole bylo zapsáno do zdroje dat, i když se jeho hodnota nezměnila, zavolejte `SetFieldDirty` s parametrem TRUE. To funguje i v případě, že pole má hodnotu null.

Rozhraní označuje změněné datové členy pole, aby se zajistilo jejich zápis do záznamu ve zdroji dat pomocí mechanismu výměny pole záznamu (DFX) DAO. Změna hodnoty pole obvykle automaticky nastaví pole jako chybné, takže nebudete muset volat [SetFieldDirty](#setfielddirty) sami, ale možná budete chtít zajistit, aby se sloupce explicitně aktualizovaly nebo vložily bez ohledu na to, jaká hodnota je v datovém členu pole. Mechanismus DFX používá také použití **pseudo null**. Další informace naleznete v tématu [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud se nepoužívá mechanismus dvojitého ukládání do vyrovnávací paměti, pak při změně hodnoty pole se pole automaticky nenastaví jako nečisté. V takovém případě bude nutné explicitně nastavit pole jako nečisté. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

Když je objekt sady záznamů pessimistically uzamčen ve víceuživatelském prostředí, zůstane záznam uzamčený z času `Edit` bude použit až do dokončení aktualizace. Pokud je sada záznamů optimisticky uzamčena, záznam je uzamčen a porovnán s dříve upraveným záznamem těsně před jeho aktualizací v databázi. Pokud se záznam změnil od chvíle, kdy jste volali `Edit`, operace `Update` se nezdařila a MFC vyvolá výjimku. Můžete změnit režim uzamykání pomocí `SetLockingMode`.

> [!NOTE]
>  Optimistické zamykání se vždycky používá u externích formátů databáze, jako je ODBC a Instalovatelné ISAM.

Aktuální záznam zůstane po volání `Edit`aktuální. Chcete-li volat `Edit`, musí existovat aktuální záznam. Pokud neexistuje žádný aktuální záznam nebo pokud sada záznamů neodkazuje na otevřený objekt sady záznamů typu tabulka nebo dynamická sada záznamů, dojde k výjimce. Volání `Edit` způsobí, že `CDaoException` vyvolána za následujících podmínek:

- Neexistuje aktuální záznam.

- Databáze nebo sada záznamů je jen pro čtení.

- Žádná pole v záznamu nelze aktualizovat.

- Databáze nebo sada záznamů byla otevřena pro výhradní použití jiným uživatelem.

- Jiný uživatel uzamkl stránku obsahující váš záznam.

Pokud zdroj dat podporuje transakce, můžete provést `Edit` volání části transakce. Všimněte si, že byste měli volat `CDaoWorkspace::BeginTrans` před voláním `Edit` a po otevření sady záznamů. Všimněte si také, že volání `CDaoWorkspace::CommitTrans` není náhradou za volání `Update` k dokončení operace `Edit`. Další informace o transakcích naleznete v tématu Class `CDaoWorkspace`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Metoda AddNew", "Upravit metodu", "Delete Method", "metoda aktualizace" a "aktualizovatelné vlastnosti".

##  <a name="fillcache"></a>CDaoRecordset:: FillCache

Tuto členskou funkci volejte pro ukládání zadaného počtu záznamů ze sady záznamů do mezipaměti.

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>Parametry

*pSize*<br/>
Určuje počet řádků, které mají být do mezipaměti vyplněny. Pokud tento parametr vynecháte, hodnota je určena nastavením vlastnosti CacheSize základního objektu DAO.

*pBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) určující záložku Mezipaměť je vyplněná od záznamu označeného touto záložkou. Pokud tento parametr vynecháte, bude mezipaměť vyplněna z záznamu označeného vlastností CacheStart základního objektu DAO.

### <a name="remarks"></a>Poznámky

Ukládání do mezipaměti vylepšuje výkon aplikace, která načítá nebo načítá data ze vzdáleného serveru. Mezipaměť je místo v místní paměti obsahující data, která se nedávno načítají ze serveru na předpokladu, že se data budou pravděpodobně požadovat znovu při spuštění aplikace. Když se vyžadují data, databázový stroj Microsoft Jet nejprve zkontroluje mezipaměť pro data a nenačte je ze serveru, což trvá více času. Použití ukládání dat do mezipaměti v datových zdrojích bez rozhraní ODBC nemá žádný vliv, protože data nejsou uložena v mezipaměti.

Místo čekání na vyplňování mezipaměti záznamy při jejich načítání můžete mezipaměť explicitně vyplnit kdykoli voláním členské funkce `FillCache`. To je rychlejší způsob, jak mezipaměť vyplnit, protože `FillCache` načítá několik záznamů najednou místo jednoho. Například při zobrazení každé obrazovky záznamů můžete mít volání aplikace `FillCache` k načtení další obrazovky záznamů.

Všechny databáze rozhraní ODBC, ke kterým je možné přidružit objekty sady záznamů, mohou mít místní mezipaměť. Chcete-li vytvořit mezipaměť, otevřete objekt sady záznamů ze vzdáleného zdroje dat a poté zavolejte `SetCacheSize` a `SetCacheStart` členské funkce sady záznamů. Pokud *lSize* a *lBookmark* vytvoří rozsah, který je částečně nebo zcela mimo rozsah určený `SetCacheSize` a `SetCacheStart`, část sady záznamů mimo tento rozsah je ignorována a není načtena do mezipaměti. Pokud `FillCache` požaduje více záznamů, než zůstává ve vzdáleném zdroji dat, načítají se pouze zbývající záznamy a není vyvolána žádná výjimka.

Záznamy načtené z mezipaměti nereflektují změny provedené souběžně na zdrojová data jinými uživateli.

`FillCache` načte pouze záznamy, které již nejsou uloženy v mezipaměti. Chcete-li vynutit aktualizaci všech dat uložených v mezipaměti, zavolejte členskou funkci `SetCacheSize` s parametrem *lSize* , který se rovná 0, zavolejte `SetCacheSize` znovu s parametrem *lSize* , který se rovná velikosti mezipaměti, kterou jste původně požadovali, a potom zavolejte `FillCache`.

Související informace naleznete v tématu "metoda FillCache" v nápovědě k rozhraní DAO.

##  <a name="find"></a>CDaoRecordset:: Find

Zavolejte tuto členskou funkci pro vyhledání konkrétního řetězce v sadě předsady nebo sadě záznamů typu snímky pomocí operátoru porovnání.

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lFindType*<br/>
Hodnota, která označuje typ požadované operace Find. Možné hodnoty jsou:

- AFX_DAO_NEXT najít další umístění odpovídajícího řetězce.

- AFX_DAO_PREV najít předchozí umístění odpovídajícího řetězce.

- AFX_DAO_FIRST najít první umístění odpovídajícího řetězce.

- AFX_DAO_LAST najít poslední umístění odpovídajícího řetězce.

*lpszFilter*<br/>
Řetězcový výraz (jako klauzule **WHERE** v příkazu SQL bez slova **WHERE**), který se používá k vyhledání záznamu. Příklad:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou nalezeny vyhovující záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Můžete najít první, další, předchozí nebo poslední instanci řetězce. `Find` je virtuální funkce, takže ji můžete přepsat a přidat vlastní implementaci. Členské funkce `FindFirst`, `FindLast`, `FindNext`a `FindPrev` volají členskou funkci `Find`, takže můžete použít `Find` k řízení chování všech operací Find.

Chcete-li vyhledat záznam v sadě záznamů typu tabulka, zavolejte členskou funkci [hledání](#seek) .

> [!TIP]
>  Menší sada záznamů, kterou máte, bude efektivnější `Find`. Obecně platí, že v případě dat ODBC je lepší vytvořit nový dotaz, který načte jenom ty záznamy, které chcete.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "FindFirst, FindLast, NajítDalší, FindPrevious Methods".

##  <a name="findfirst"></a>CDaoRecordset:: FindFirst

Zavolejte tuto členskou funkci, abyste našli první záznam, který odpovídá zadané podmínce.

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Řetězcový výraz (jako klauzule **WHERE** v příkazu SQL bez slova **WHERE**), který se používá k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou nalezeny vyhovující záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská funkce `FindFirst` začne hledat od začátku sady záznamů a vyhledává na konci sady záznamů.

Chcete-li do hledání zahrnout všechny záznamy (ne pouze ty, které splňují určitou podmínku), použijte jednu z operací přesunutí pro přesun ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů typu tabulka, zavolejte členskou funkci `Seek`.

Pokud není nalezen záznam, který by odpovídal kritériím, není určen aktuální ukazatel záznamu a `FindFirst` vrátí hodnotu nula. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt, `FindNext` vyhledá další výskyt a tak dále.

> [!CAUTION]
>  Pokud upravíte aktuální záznam, nezapomeňte uložit změny voláním členské funkce `Update` předtím, než přejdete na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny se ztratí bez upozornění.

Členské funkce `Find` hledají umístění a ve směru uvedeném v následující tabulce:

|Operace hledání|Začít|Směr hledání|
|---------------------|-----------|----------------------|
|`FindFirst`|Začátek sady záznamů|Konec sady záznamů|
|`FindLast`|Konec sady záznamů|Začátek sady záznamů|
|`FindNext`|Aktuální záznam|Konec sady záznamů|
|`FindPrevious`|Aktuální záznam|Začátek sady záznamů|

> [!NOTE]
>  Když zavoláte `FindLast`, databázový stroj Microsoft Jet plně naplní sadu záznamů před zahájením hledání, pokud ještě nebyl proveden. První hledání může trvat déle než následné hledání.

Použití jedné z operací Find není stejné jako volání `MoveFirst` nebo `MoveNext`, ale jednoduše vytvoří první nebo další záznam aktuální bez zadání podmínky. Operaci hledání můžete provést s operací přesunutí.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit ukazatel aktuální položky zpátky na platný záznam.

- Nemůžete použít operaci Find s dopřednou sadou záznamů typu snímky s možností posouvání.

- Při hledání polí obsahujících data byste měli použít formát kalendářního data (měsíc-den-rok), a to i v případě, že nepoužíváte americké verze databázového stroje Microsoft Jet. v opačném případě se nemusí najít vyhovující záznamy.

- Při práci s databázemi rozhraní ODBC a velkými sadami dynamická sada můžete zjistit, že použití operací Find je pomalé, zejména při práci s velkými sadami záznamů. Můžete zvýšit výkon pomocí dotazů SQL s přizpůsobenými klauzulemi **OrderBy** nebo **WHERE** , dotazy na parametry nebo `CDaoQuerydef` objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "FindFirst, FindLast, NajítDalší, FindPrevious Methods".

##  <a name="findlast"></a>CDaoRecordset:: FindLast

Voláním této členské funkce zjistíte poslední záznam, který odpovídá zadané podmínce.

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Řetězcový výraz (jako klauzule **WHERE** v příkazu SQL bez slova **WHERE**), který se používá k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou nalezeny vyhovující záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská funkce `FindLast` zahájí hledání na konci sady záznamů a vyhledá zpět směrem k začátku sady záznamů.

Chcete-li do hledání zahrnout všechny záznamy (ne pouze ty, které splňují určitou podmínku), použijte jednu z operací přesunutí pro přesun ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů typu tabulka, zavolejte členskou funkci `Seek`.

Pokud není nalezen záznam, který by odpovídal kritériím, není určen aktuální ukazatel záznamu a `FindLast` vrátí hodnotu nula. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt, `FindNext` vyhledá další výskyt po prvním výskytu a tak dále.

> [!CAUTION]
>  Pokud upravíte aktuální záznam, nezapomeňte uložit změny voláním členské funkce `Update` předtím, než přejdete na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny se ztratí bez upozornění.

Použití jedné z operací Find není stejné jako volání `MoveFirst` nebo `MoveNext`, ale jednoduše vytvoří první nebo další záznam aktuální bez zadání podmínky. Operaci hledání můžete provést s operací přesunutí.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit ukazatel aktuální položky zpátky na platný záznam.

- Nemůžete použít operaci Find s dopřednou sadou záznamů typu snímky s možností posouvání.

- Při hledání polí obsahujících data byste měli použít formát kalendářního data (měsíc-den-rok), a to i v případě, že nepoužíváte americké verze databázového stroje Microsoft Jet. v opačném případě se nemusí najít vyhovující záznamy.

- Při práci s databázemi rozhraní ODBC a velkými sadami dynamická sada můžete zjistit, že použití operací Find je pomalé, zejména při práci s velkými sadami záznamů. Můžete zvýšit výkon pomocí dotazů SQL s přizpůsobenými klauzulemi **OrderBy** nebo **WHERE** , dotazy na parametry nebo `CDaoQuerydef` objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "FindFirst, FindLast, NajítDalší, FindPrevious Methods".

##  <a name="findnext"></a>CDaoRecordset:: NajítDalší

Voláním této členské funkce můžete najít další záznam, který odpovídá zadané podmínce.

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Řetězcový výraz (jako klauzule **WHERE** v příkazu SQL bez slova **WHERE**), který se používá k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou nalezeny vyhovující záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská funkce `FindNext` začne hledat v aktuálním záznamu a hledá na konci sady záznamů.

Chcete-li do hledání zahrnout všechny záznamy (ne pouze ty, které splňují určitou podmínku), použijte jednu z operací přesunutí pro přesun ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů typu tabulka, zavolejte členskou funkci `Seek`.

Pokud není nalezen záznam, který by odpovídal kritériím, není určen aktuální ukazatel záznamu a `FindNext` vrátí hodnotu nula. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt, `FindNext` vyhledá další výskyt a tak dále.

> [!CAUTION]
>  Pokud upravíte aktuální záznam, nezapomeňte uložit změny voláním členské funkce `Update` předtím, než přejdete na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny se ztratí bez upozornění.

Použití jedné z operací Find není stejné jako volání `MoveFirst` nebo `MoveNext`, ale jednoduše vytvoří první nebo další záznam aktuální bez zadání podmínky. Operaci hledání můžete provést s operací přesunutí.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit ukazatel aktuální položky zpátky na platný záznam.

- Nemůžete použít operaci Find s dopřednou sadou záznamů typu snímky s možností posouvání.

- Při hledání polí obsahujících data byste měli použít formát kalendářního data (měsíc-den-rok), a to i v případě, že nepoužíváte americké verze databázového stroje Microsoft Jet. v opačném případě se nemusí najít vyhovující záznamy.

- Při práci s databázemi rozhraní ODBC a velkými sadami dynamická sada můžete zjistit, že použití operací Find je pomalé, zejména při práci s velkými sadami záznamů. Můžete zvýšit výkon pomocí dotazů SQL s přizpůsobenými klauzulemi **OrderBy** nebo **WHERE** , dotazy na parametry nebo `CDaoQuerydef` objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "FindFirst, FindLast, NajítDalší, FindPrevious Methods".

##  <a name="findprev"></a>CDaoRecordset:: FindPrev

Zavolejte tuto členskou funkci pro vyhledání předchozího záznamu, který odpovídá zadané podmínce.

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>Parametry

*lpszFilter*<br/>
Řetězcový výraz (jako klauzule **WHERE** v příkazu SQL bez slova **WHERE**), který se používá k vyhledání záznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou nalezeny vyhovující záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Členská funkce `FindPrev` zahájí hledání v aktuálním záznamu a zpětně vyhledá začátek sady záznamů.

Chcete-li do hledání zahrnout všechny záznamy (ne pouze ty, které splňují určitou podmínku), použijte jednu z operací přesunutí pro přesun ze záznamu na záznam. Chcete-li vyhledat záznam v sadě záznamů typu tabulka, zavolejte členskou funkci `Seek`.

Pokud není nalezen záznam, který by odpovídal kritériím, není určen aktuální ukazatel záznamu a `FindPrev` vrátí hodnotu nula. Pokud sada záznamů obsahuje více než jeden záznam, který splňuje kritéria, `FindFirst` vyhledá první výskyt, `FindNext` vyhledá další výskyt a tak dále.

> [!CAUTION]
>  Pokud upravíte aktuální záznam, nezapomeňte uložit změny voláním členské funkce `Update` předtím, než přejdete na jiný záznam. Pokud přejdete na jiný záznam bez aktualizace, změny se ztratí bez upozornění.

Použití jedné z operací Find není stejné jako volání `MoveFirst` nebo `MoveNext`, ale jednoduše vytvoří první nebo další záznam aktuální bez zadání podmínky. Operaci hledání můžete provést s operací přesunutí.

Při použití operací hledání mějte na paměti následující:

- Pokud `Find` vrátí nenulovou hodnotu, aktuální záznam není definován. V takovém případě je nutné umístit ukazatel aktuální položky zpátky na platný záznam.

- Nemůžete použít operaci Find s dopřednou sadou záznamů typu snímky s možností posouvání.

- Při hledání polí obsahujících data byste měli použít formát kalendářního data (měsíc-den-rok), a to i v případě, že nepoužíváte americké verze databázového stroje Microsoft Jet. v opačném případě se nemusí najít vyhovující záznamy.

- Při práci s databázemi rozhraní ODBC a velkými sadami dynamická sada můžete zjistit, že použití operací Find je pomalé, zejména při práci s velkými sadami záznamů. Můžete zvýšit výkon pomocí dotazů SQL s přizpůsobenými klauzulemi **OrderBy** nebo **WHERE** , dotazy na parametry nebo `CDaoQuerydef` objekty, které načítají konkrétní indexované záznamy.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "FindFirst, FindLast, NajítDalší, FindPrevious Methods".

##  <a name="getabsoluteposition"></a>CDaoRecordset:: GetAbsolutePosition

Vrátí číslo záznamu aktuálního záznamu objektu sady záznamů.

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo od 0 do počtu záznamů v sadě záznamů. Odpovídá pořadové pozici aktuálního záznamu v sadě záznamů.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti AbsolutePosition základního objektu DAO je založena na nule; nastavení 0 odkazuje na první záznam v sadě záznamů. Počet vyplněných záznamů v sadě záznamů můžete určit voláním [GetRecordCount](#getrecordcount). Volání `GetRecordCount` může nějakou dobu trvat, protože musí přistupovat ke všem záznamům a určit počet.

Pokud není k dispozici žádný aktuální záznam, jako když v sadě záznamů nejsou žádné záznamy, je vrácena položka-1. Pokud je aktuální záznam odstraněn, hodnota vlastnosti AbsolutePosition není definována a MFC vyvolá výjimku, pokud je odkazováno. Pro sadu záznamů typu dynamická sada jsou nové záznamy přidány na konec sekvence.

> [!NOTE]
>  Tato vlastnost není určena k použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem zachování a návratu na danou pozici a jsou jediným způsobem, jak umístit aktuální záznam napříč všemi typy objektů sady záznamů. Konkrétně se poloha daného záznamu změní, když jsou záznamy před smazány. K dispozici není také žádná záruka, že daný záznam bude mít stejnou absolutní pozici, pokud je znovu znovu vytvořena sada záznamů, protože pořadí jednotlivých záznamů v rámci sady záznamů není zaručeno, pokud není vytvořeno pomocí příkazu jazyka SQL pomocí klauzule **OrderBy** .

> [!NOTE]
>  Tato členská funkce je platná pouze pro sady záznamů typu Dynamic-Type a Snapshot-Type.

Související informace najdete v tématu "vlastnost AbsolutePosition" v nápovědě k rozhraní DAO.

##  <a name="getbookmark"></a>CDaoRecordset:: GetBookmark

Zavolejte tuto členskou funkci, aby se získala hodnota záložky v konkrétním záznamu.

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu představující záložku aktuálního záznamu.

### <a name="remarks"></a>Poznámky

Když je vytvořen nebo otevřen objekt sady záznamů, každý z jeho záznamů již obsahuje jedinečnou záložku, pokud ji podporuje. Zavolejte `CanBookmark` k určení, zda sada záznamů podporuje záložky.

Záložku pro aktuální záznam můžete uložit přiřazením hodnoty Bookmark k objektu `COleVariant`. Chcete-li se rychle vrátit k tomuto záznamu po přesunu na jiný záznam, zavolejte `SetBookmark` s parametrem odpovídajícím hodnotě tohoto objektu `COleVariant`.

> [!NOTE]
>  Volání [ZnovuSpustitDotaz](#requery) změní záložky rozhraní DAO.

Související informace naleznete v tématu "vlastnost záložky" v nápovědě k rozhraní DAO.

##  <a name="getcachesize"></a>CDaoRecordset:: GetCacheSize

Zavolejte tuto členskou funkci pro získání počtu záznamů uložených v mezipaměti.

```
long GetCacheSize();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje počet záznamů v sadě typů sady záznamů obsahující data, která mají být uložena do mezipaměti ze zdroje dat ODBC.

### <a name="remarks"></a>Poznámky

Ukládání dat do mezipaměti vylepšuje výkon aplikace, která načítá data ze vzdáleného serveru prostřednictvím objektů sad záznamů sady záznamů. Mezipaměť je místo v místní paměti, ve kterém jsou uložena data, která byla naposledy načtena ze serveru aplikace v případě, že se data budou požadovat znovu při spuštění aplikace. Když se vyžadují data, databázový stroj Microsoft Jet nejprve zkontroluje mezipaměť pro požadovaná data a nenačte ho ze serveru, což trvá víc času. Data, která nepocházejí ze zdroje dat ODBC, se v mezipaměti neukládají.

Všechny zdroje dat ODBC, jako je například připojená tabulka, můžou mít místní mezipaměť.

Související informace naleznete v tématu "CacheSize, CacheStart Properties" v nápovědě pro rozhraní DAO.

##  <a name="getcachestart"></a>CDaoRecordset:: GetCacheStart

Zavolejte tuto členskou funkci, aby se získala hodnota záložky prvního záznamu v sadě záznamů, která se má ukládat do mezipaměti.

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>Návratová hodnota

`COleVariant`, která určuje záložku prvního záznamu v sadě záznamů, která má být ukládána do mezipaměti.

### <a name="remarks"></a>Poznámky

Databázový stroj Microsoft Jet požaduje záznamy v rámci rozsahu mezipaměti z mezipaměti a vyžádá si záznamy mimo rozsah mezipaměti ze serveru.

> [!NOTE]
>  Záznamy načtené z mezipaměti nereflektují změny provedené souběžně na zdrojová data jinými uživateli.

Související informace naleznete v tématu "CacheSize, CacheStart Properties" v nápovědě pro rozhraní DAO.

##  <a name="getcurrentindex"></a>CDaoRecordset:: GetCurrentIndex

Voláním této členské funkce určíte index, který se aktuálně používá v indexovaném objektu typu tabulka `CDaoRecordset`.

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>Návratová hodnota

`CString` obsahující název indexu, který se aktuálně používá se sadou záznamů typu tabulka. Vrátí prázdný řetězec, pokud není nastaven žádný index.

### <a name="remarks"></a>Poznámky

Tento index je základem pro řazení záznamů v sadě záznamů typu tabulka a je použita funkcí členu [hledání](#seek) k vyhledání záznamů.

Objekt `CDaoRecordset` může mít více než jeden index, ale může používat pouze jeden index v čase (i když je v objektu [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) pravděpodobně definováno několik indexů).

Související informace najdete v nápovědě k rozhraní DAO v tématu "objekt" a definice "aktuální index".

##  <a name="getdatecreated"></a>CDaoRecordset:: GetDateCreated

Voláním této členské funkce načtěte datum a čas vytvoření základní tabulky.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

Objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obsahující datum a čas vytvoření základní tabulky.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena z počítače, ve kterém byla vytvořena základní tabulka.

Související informace naleznete v tématu "DateCreated, hodnota LastUpdated Properties" v nápovědě pro rozhraní DAO.

##  <a name="getdatelastupdated"></a>CDaoRecordset:: GetDateLastUpdated

Chcete-li načíst datum a čas poslední aktualizace schématu, zavolejte tuto členskou funkci.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

Objekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obsahující datum a čas poslední aktualizace struktury základní tabulky (schématu).

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena z počítače, na kterém se poslední aktualizace struktury základní tabulky (schématu) aktualizovala.

Související informace naleznete v tématu "DateCreated, hodnota LastUpdated Properties" v nápovědě pro rozhraní DAO.

##  <a name="getdefaultdbname"></a>CDaoRecordset:: GetDefaultDBName

Zavolejte tuto členskou funkci pro určení názvu databáze pro tuto sadu záznamů.

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>Návratová hodnota

`CString` obsahující cestu a název databáze, ze které je tato sada záznamů odvozena.

### <a name="remarks"></a>Poznámky

Pokud je vytvořena sada záznamů bez ukazatele na [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md), pak je tato cesta používána sadou záznamů k otevření výchozí databáze. Ve výchozím nastavení tato funkce vrací prázdný řetězec. Když ClassWizard odvozuje novou sadu záznamů od `CDaoRecordset`, vytvoří tuto funkci za vás.

Následující příklad ilustruje použití dvojitého zpětného lomítka (\\\\) v řetězci, jak je vyžadováno, aby byl řetězec správně interpretován.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>CDaoRecordset:: GetDefaultSQL

Rozhraní volá tuto členskou funkci, aby získala výchozí příkaz SQL, na kterém je sada záznamů založena.

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>Návratová hodnota

`CString`, který obsahuje výchozí příkaz SQL.

### <a name="remarks"></a>Poznámky

Může se jednat o název tabulky nebo příkaz SQL **Select** .

Nebudete nepřímo definovat výchozí příkaz SQL deklarováním třídy sady záznamů pomocí ClassWizard a ClassWizard tuto úlohu provede za vás.

Pokud předáte prázdný řetězec SQL, který má být [otevřen](#open), je volána Tato funkce pro určení názvu tabulky nebo SQL pro sadu záznamů.

##  <a name="geteditmode"></a>CDaoRecordset:: GetEditMode

Voláním této členské funkce určíte stav úprav, což je jedna z následujících hodnot:

```
short GetEditMode();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která označuje stav úprav aktuálního záznamu.

### <a name="remarks"></a>Poznámky

|Hodnota|Popis|
|-----------|-----------------|
|`dbEditNone`|Neprobíhá žádná operace úprav.|
|`dbEditInProgress`|byla volána `Edit`.|
|`dbEditAdd`|byla volána `AddNew`.|

Související informace najdete v tématu "vlastnost EditMode" v nápovědě k rozhraní DAO.

##  <a name="getfieldcount"></a>CDaoRecordset:: GetFieldCount

Zavolejte tuto členskou funkci pro načtení počtu polí (sloupců) definovaných v sadě záznamů.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v sadě záznamů.

### <a name="remarks"></a>Poznámky

Související informace naleznete v nápovědě k rozhraní DAO v tématu "vlastnost Count".

##  <a name="getfieldinfo"></a>CDaoRecordset:: GetFieldInfo

Chcete-li získat informace o polích v sadě záznamů, zavolejte tuto členskou funkci.

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
Index založený na nule předdefinovaného pole v kolekci polí sady záznamů pro vyhledávání podle indexu.

*FieldInfo*<br/>
Odkaz na strukturu [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) .

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o sadě záznamů se mají načíst. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí. Nejlepšího výkonu dosáhnete, když načtete jenom potřebné úrovně informací:

- `AFX_DAO_PRIMARY_INFO` (výchozí) název, typ, velikost, atributy

- `AFX_DAO_SECONDARY_INFO` primární informace, navíc: ordinální pozice, požadováno, povolení nulové délky, pořadí řazení, cizí název, zdrojové pole, zdrojová tabulka

- `AFX_DAO_ALL_INFO` primární a sekundární informace a navíc: výchozí hodnota, ověřovací pravidlo, Ověřovací text

*lpszName*<br/>
Název pole

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat pole podle indexu. Druhá verze umožňuje vyhledat pole podle názvu.

Popis vrácených informací najdete v tématu struktura [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Když si vyžádáte informace na jedné úrovni, získáte informace také pro všechny předchozí úrovně.

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="getfieldvalue"></a>CDaoRecordset:: GetFieldValue –

Chcete-li načíst data v sadě záznamů, zavolejte tuto členskou funkci.

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
Odkaz na objekt `COleVariant`, který uloží hodnotu pole.

*nIndex*<br/>
Index založený na nule pole v kolekci polí sady záznamů pro vyhledávání podle indexu.

### <a name="return-value"></a>Návratová hodnota

Dvě verze `GetFieldValue`, které vrací hodnotu, vrátí objekt [COleVariant](../../mfc/reference/colevariant-class.md) , který obsahuje hodnotu pole.

### <a name="remarks"></a>Poznámky

Můžete vyhledat pole podle názvu nebo podle pořadového čísla.

> [!NOTE]
>  Je efektivnější volat jednu z verzí této členské funkce, která přebírá odkaz na objekt `COleVariant` jako parametr, namísto volání verze, která vrací objekt `COleVariant`. Druhé verze této funkce jsou uchovávány kvůli zpětné kompatibilitě.

Použijte `GetFieldValue` a [SetFieldValue](#setfieldvalue) k dynamickému vázání polí v době běhu namísto staticky propojeného sloupce pomocí mechanismu [DoFieldExchange](#dofieldexchange) .

`GetFieldValue` a mechanismus `DoFieldExchange` lze kombinovat pro zlepšení výkonu. Například použijte `GetFieldValue` k načtení hodnoty, kterou potřebujete pouze na vyžádání, a přiřazení tohoto volání k tlačítku "Další informace" v rozhraní.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "objekt pole" a "vlastnost hodnoty".

##  <a name="getindexcount"></a>CDaoRecordset:: GetIndexCount

Zavolejte tuto členskou funkci pro určení počtu indexů dostupných v sadě záznamů typu tabulka.

```
short GetIndexCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet indexů v sadě záznamů typu tabulka

### <a name="remarks"></a>Poznámky

`GetIndexCount` je užitečné pro procházení všemi indexy v sadě záznamů. Pro tento účel použijte `GetIndexCount` ve spojení s [GetIndexInfo](#getindexinfo). Pokud zavoláte tuto členskou funkci pro sady záznamů typu Dynamic-Type nebo Snapshot-Type, knihovna MFC vyvolá výjimku.

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="getindexinfo"></a>CDaoRecordset:: GetIndexInfo

Tuto členskou funkci volejte pro získání různých druhů informací o indexu definovaném v základní tabulce, která je podkladem sady záznamů.

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
Index založený na nule v kolekci indexů tabulky pro vyhledávání podle číselné pozice.

*indexinfo*<br/>
Odkaz na strukturu [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) .

*dwInfoOptions*<br/>
Možnosti, které určují, které informace o indexu mají být načteny. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí. Nejlepšího výkonu dosáhnete, když načtete jenom potřebné úrovně informací:

- `AFX_DAO_PRIMARY_INFO` (výchozí) název, informace o poli, pole

- `AFX_DAO_SECONDARY_INFO` primární informace, navíc: primární, jedinečný, clusterovaný, IgnoreNulls, povinný, cizí

- `AFX_DAO_ALL_INFO` primární a sekundární informace a navíc: jedinečný počet

*lpszName*<br/>
Ukazatel na název objektu indexu pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat index podle jeho pozice v kolekci. Druhá verze umožňuje vyhledat index podle názvu.

Popis vrácených informací najdete v tématu struktura [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Když si vyžádáte informace na jedné úrovni, získáte informace také pro všechny předchozí úrovně.

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="getlastmodifiedbookmark"></a>CDaoRecordset:: GetLastModifiedBookmark

Zavolejte tuto členskou funkci, aby se načetla záložka naposledy přidané nebo aktualizovaného záznamu.

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>Návratová hodnota

`COleVariant` obsahující záložku, která označuje naposledy přidaný nebo změněný záznam.

### <a name="remarks"></a>Poznámky

Když je vytvořen nebo otevřen objekt sady záznamů, každý z jeho záznamů již obsahuje jedinečnou záložku, pokud ji podporuje. Voláním metody [GetBookmark](#getbookmark) určíte, zda sada záznamů podporuje záložky. Pokud sada záznamů nepodporuje záložky, je vyvolána `CDaoException`.

Když přidáte záznam, zobrazí se na konci sady záznamů a není aktuálním záznamem. Chcete-li nový záznam vytvořit, zavolejte `GetLastModifiedBookmark` a potom zavolejte `SetBookmark` a vraťte se k nově přidanému záznamu.

Související informace naleznete v tématu "vlastnost LastModified" v nápovědě k rozhraní DAO.

##  <a name="getlockingmode"></a>CDaoRecordset:: GetLockingMode

Voláním této členské funkce určíte typ zamykání platný pro sadu záznamů.

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je typ zamykání pesimistické, jinak 0 pro uzamykání optimistického záznamu.

### <a name="remarks"></a>Poznámky

Pokud je v platnosti pesimistické zamykání, datová stránka obsahující Upravovaný záznam je uzamčena ihned po volání funkce [Upravit](#edit) členskou funkci. Stránka je odemčena při volání členské funkce [Update](#update) nebo [Close](#close) nebo kterékoli operace přesunutí nebo hledání.

Pokud je v platnosti optimistické zamykání, datová stránka obsahující záznam je uzamčena pouze v případě, že je záznam aktualizován pomocí členské funkce `Update`.

Při práci se zdroji dat ODBC je režim uzamykání vždycky optimistický.

Související informace najdete v nápovědě k rozhraní DAO v tématech "vlastnost LockEdits" a "chování při zamykání v aplikacích s více uživateli".

##  <a name="getname"></a>CDaoRecordset:: GetName

Chcete-li načíst název sady záznamů, zavolejte tuto členskou funkci.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

`CString` obsahující název sady záznamů.

### <a name="remarks"></a>Poznámky

Název sady záznamů musí začínat písmenem a může obsahovat maximálně 40 znaků. Může obsahovat číslice a podtržítka, ale nemůže obsahovat interpunkční znaménka nebo mezery.

Související informace najdete v tématu "vlastnost Name" v nápovědě k rozhraní DAO.

##  <a name="getparamvalue"></a>CDaoRecordset:: GetParamValue

Zavolejte tuto členskou funkci pro načtení aktuální hodnoty zadaného parametru uloženého v podkladovém objektu DAOParameter.

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Číselné umístění parametru v podkladovém objektu DAOParameter

*lpszName*<br/>
Název parametru, jehož hodnotu chcete.

### <a name="return-value"></a>Návratová hodnota

Objekt třídy [COleVariant](../../mfc/reference/colevariant-class.md) , který obsahuje hodnotu parametru.

### <a name="remarks"></a>Poznámky

K parametru můžete přistupovat buď podle názvu, nebo podle jeho číselné pozice v kolekci.

Související informace naleznete v tématu "objekt parametru" v nápovědě rozhraní DAO.

##  <a name="getpercentposition"></a>CDaoRecordset:: GetPercentPosition

Při práci s dynamickou sadou typu nebo sadou záznamů typu snímky, pokud zavoláte `GetPercentPosition` před úplným naplnění sady záznamů, je velikost pohybu relativní vzhledem k počtu záznamů, které jsou k dispozici, jak je uvedeno voláním metody [GetRecordCount](#getrecordcount).

```
float GetPercentPosition();
```

### <a name="return-value"></a>Návratová hodnota

Číslo mezi 0 a 100, které označuje přibližné umístění aktuálního záznamu v objektu sady záznamů na základě procenta záznamů v sadě záznamů.

### <a name="remarks"></a>Poznámky

Můžete přejít na poslední záznam voláním [MoveLast](#movelast) k dokončení populace všech sad záznamů, ale to může trvat poměrně dlouhou dobu.

Můžete volat `GetPercentPosition` pro všechny tři typy objektů sady záznamů, včetně tabulek bez indexů. Nemůžete však volat `GetPercentPosition` na snímky s posouváním pouze s doposíláním nebo v sadě záznamů otevřené z předávacího dotazu na externí databázi. Pokud není k dispozici žádný aktuální záznam nebo byl odstraněn aktuální záznam, je vyvolána `CDaoException`.

Související informace najdete v tématu "vlastnost PercentPosition" v nápovědě k rozhraní DAO.

##  <a name="getrecordcount"></a>CDaoRecordset:: GetRecordCount

Voláním této členské funkce zjistíte, kolik záznamů v sadě záznamů bylo k dispozici.

```
long GetRecordCount();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet záznamů, které jsou k dispozici v objektu sady záznamů.

### <a name="remarks"></a>Poznámky

`GetRecordCount` neurčuje, kolik záznamů je obsaženo v dynamické sadě typu nebo sadě záznamů typu snímky, dokud nebudou k dispozici všechny záznamy. Dokončení tohoto volání členské funkce může trvat poměrně dlouhou dobu.

Jakmile je k poslednímu záznamu přistupný, vrácená hodnota označuje celkový počet neodstraněných záznamů v sadě záznamů. Chcete-li vynutit, aby byl poslední záznam k dispozici, zavolejte funkci `MoveLast` nebo `FindLast` členské funkce pro sadu záznamů. K určení přibližného počtu záznamů vrácených dotazem se dá použít také počet SQL.

Jak vaše aplikace odstraňuje záznamy v sadě záznamů typu Dynamic-Type, návratová hodnota `GetRecordCount` se zkrátí. Záznamy odstraněné jinými uživateli se ale neprojeví `GetRecordCount`, dokud se aktuální záznam neumístí na odstraněný záznam. Pokud spustíte transakci, která má vliv na počet záznamů a následně vrátí zpět transakci, `GetRecordCount` neodráží skutečný počet zbývajících záznamů.

Hodnota `GetRecordCount` ze sady záznamů typu snímky není ovlivněna změnami v podkladových tabulkách.

Hodnota `GetRecordCount` ze sady záznamů typu tabulka odráží přibližný počet záznamů v tabulce a je okamžitě ovlivněna při přidávání a odstraňování záznamů tabulky.

Sada záznamů bez záznamů vrátí hodnotu 0. Při práci s připojenými tabulkami nebo databázemi ODBC `GetRecordCount` vždy vrátí hodnotu-1. Volání členské funkce `Requery` v sadě záznamů obnoví hodnotu `GetRecordCount` stejně, jako kdyby byl dotaz znovu proveden.

Související informace najdete v tématu "vlastnost RecordCount" v nápovědě k rozhraní DAO.

##  <a name="getsql"></a>CDaoRecordset:: GetSQL

Zavolejte tuto členskou funkci, aby se získal příkaz SQL, který se použil k výběru záznamů sady záznamů při jejím otevření.

```
CString GetSQL() const;
```

### <a name="return-value"></a>Návratová hodnota

`CString` obsahující příkaz SQL.

### <a name="remarks"></a>Poznámky

Obvykle se jedná o příkaz SQL **Select** .

Řetězec vrácený `GetSQL` se obvykle liší od libovolného řetězce, který jste mohli předat sadě záznamů v parametru *lpszSQL* pro [otevřenou](#open) členskou funkci. Důvodem je, že sada záznamů vytvoří úplný příkaz SQL na základě toho, co jste předali do `Open`, co jste zadali v ClassWizard a co jste mohli zadat v datových členech [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) .

> [!NOTE]
>  Tuto členskou funkci volejte až po volání `Open`.

Související informace naleznete v tématu "vlastnost SQL" v nápovědě k rozhraní DAO.

##  <a name="gettype"></a>CDaoRecordset:: GetType

Po otevření sady záznamů volejte tuto členskou funkci pro určení typu objektu sady záznamů.

```
short GetType();
```

### <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot, které určují typ sady záznamů:

- `dbOpenTable` sada záznamů typu tabulka

- `dbOpenDynaset` dynamická sada – typ sady záznamů

- `dbOpenSnapshot` záznamová sada záznamů typu snímek

### <a name="remarks"></a>Poznámky

Související informace naleznete v nápovědě k rozhraní DAO v tématu "vlastnost typu".

##  <a name="getvalidationrule"></a>CDaoRecordset:: getověřovací pravidlo

Voláním této členské funkce určíte pravidlo používané k ověřování dat.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString`, který obsahuje hodnotu, která ověřuje data v záznamu při změně nebo přidání do tabulky.

### <a name="remarks"></a>Poznámky

Toto pravidlo je založené na textu a používá se pokaždé, když se změní podkladová tabulka. Pokud nejsou data platná, knihovna MFC vyvolá výjimku. Vrácená chybová zpráva je text vlastnosti Ověřovací text podkladového objektu pole, je-li tento parametr zadán, nebo text výrazu určeného vlastností "ověřovací pravidlo" objektu podkladového pole. Můžete zavolat [GetValidationText](#getvalidationtext) a získat text chybové zprávy.

Například pole v záznamu, které vyžaduje den v měsíci, může mít pravidlo ověřování, například "den mezi 1 a 31".

Související informace najdete v nápovědě k rozhraní DAO v tématu vlastnost "ověřovací pravidlo".

##  <a name="getvalidationtext"></a>CDaoRecordset:: GetValidationText

Zavolejte tuto členskou funkci pro načtení textu vlastnosti Ověřovací text podkladového objektu pole.

```
CString GetValidationText();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující text zprávy, která se zobrazí, pokud hodnota pole nevyhovuje ověřovacímu pravidlu objektu podkladového pole.

### <a name="remarks"></a>Poznámky

Související informace najdete v nápovědě k rozhraní DAO v tématu "vlastnost ověřovacího hesla".

##  <a name="isbof"></a>CDaoRecordset:: IsBOF

Než začnete s prvním záznamem sady záznamů, zavoláte tuto členskou funkci před přechodem ze záznamu na záznam a zjistěte, zda jste prošli.

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy nebo pokud jste se přesunuli zpět před první záznam; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Můžete také volat `IsBOF` společně s `IsEOF` k určení, zda sada záznamů obsahuje nějaké záznamy nebo je prázdná. Ihned po volání `Open`, pokud sada záznamů neobsahuje žádné záznamy, `IsBOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, která má alespoň jeden záznam, je první záznam aktuálním záznamem a `IsBOF` vrátí hodnotu 0.

Pokud je první záznam aktuálním záznamem a zavoláte `MovePrev`, `IsBOF` pak vrátí nenulovou hodnotu. Pokud `IsBOF` vrátí nenulovou hodnotu a zavoláte `MovePrev`, je vyvolána výjimka. Pokud `IsBOF` vrátí nenulovou hodnotu, aktuální záznam není definován a všechny akce, které vyžadují aktuální záznam, budou mít za následek výjimku.

Účinek specifických metod na `IsBOF` a nastavení `IsEOF`:

- Volání `Open*` interně vytvoří první záznam v sadě záznamů pomocí volání `MoveFirst`. Proto volání `Open` na prázdné sadě záznamů způsobí, že `IsBOF` a `IsEOF` vrátí nenulovou hodnotu. (Další informace naleznete v následující tabulce pro chování selhání `MoveFirst` nebo volání `MoveLast`.)

- Všechny operace přesunutí, které úspěšně hledají záznam, způsobí, že `IsBOF` i `IsEOF` vrátí hodnotu 0.

- Volání `AddNew` následovaný voláním `Update`, které úspěšně vkládá nový záznam, způsobí, že `IsBOF` vrátí 0, ale pouze v případě, že `IsEOF` je již nenulová. Stav `IsEOF` zůstane vždy beze změny. Jak je definováno databázovým strojem Microsoft Jet, je aktuální ukazatel záznamu prázdné sady záznamů na konci souboru, takže všechny nové záznamy budou vloženy po aktuálním záznamu.

- Jakékoli volání `Delete`, a to i v případě, že odebere jediný zbývající záznam ze sady záznamů, nezmění hodnotu `IsBOF` nebo `IsEOF`.

Tato tabulka ukazuje, které operace přesunutí jsou povoleny s různými kombinacemi `IsBOF`/ `IsEOF`.

||MoveFirst, MoveLast|MovePrev<br /><br /> Přesunout < 0|Přesunout 0|Metoda<br /><br /> Přesunout > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= nenulová hodnota<br /><br /> `IsEOF`= 0|Povoleno|Výjimka|Výjimka|Povoleno|
|`IsBOF`= 0,<br /><br /> `IsEOF`= nenulová|Povoleno|Povoleno|Výjimka|Výjimka|
|Nenulové|Výjimka|Výjimka|Výjimka|Výjimka|
|0|Povoleno|Povoleno|Povoleno|Povoleno|

Povolení operace přesunu neznamená, že operace úspěšně najde záznam. Označuje pouze to, že pokus o provedení zadané operace přesunutí je povolen a nevygeneruje výjimku. Hodnota `IsBOF` a `IsEOF` členských funkcí se může změnit v důsledku pokusu o přesunutí.

V následující tabulce je uveden účinek operací přesunutí, které neobsahují záznam na hodnotě `IsBOF` a nastavení `IsEOF`.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nenulovou|Nenulovou|
|`Move` 0|Žádné změny|Žádné změny|
|`MovePrev``Move` < 0|Nenulovou|Žádné změny|
|`MoveNext``Move` > 0|Žádné změny|Nenulovou|

Související informace najdete v nápovědě k rozhraní DAO v tématu "BOF, vlastnosti EOF".

##  <a name="isdeleted"></a>CDaoRecordset:: IsDeleted

Voláním této členské funkce určíte, zda byl aktuální záznam odstraněn.

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je sada záznamů umístěna na odstraněný záznam; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud se posunete na záznam a `IsDeleted` vrátí hodnotu TRUE (nenulový), musíte se před provedením jakékoli jiné operace sady záznamů posunout na jiný záznam.

> [!NOTE]
>  Nemusíte kontrolovat stav odstraněno pro záznamy ve snímku nebo sadě záznamů typu tabulka. Vzhledem k tomu, že záznamy nelze odstranit ze snímku, není nutné volat `IsDeleted`. Pro sady záznamů typu tabulka jsou ve skutečnosti odebrány odstraněné záznamy ze sady záznamů. Po odstranění záznamu, a to buď vy, jiný uživatel, nebo v jiné sadě záznamů, se nedá přejít zpátky k tomuto záznamu. Proto není nutné volat `IsDeleted`.

Odstraníte-li záznam z dynamické sady, je odebrán ze sady záznamů a nelze se k tomuto záznamu vrátit. Pokud je však záznam v dynamické sadě odstraněn jiným uživatelem nebo v jiné sadě záznamů založené na stejné tabulce, `IsDeleted` vrátí hodnotu TRUE při pozdějším posunu na daný záznam.

Související informace naleznete v tématu témata "odstranění metody", "vlastnost LastModified" a "EditMode Property" v nápovědě k rozhraní DAO.

##  <a name="iseof"></a>CDaoRecordset:: IsEOF

Tuto členskou funkci zavolejte při posouvání záznamu záznamu na záznam, abyste zjistili, jestli jste prošli za posledním záznamem sady záznamů.

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud sada záznamů neobsahuje žádné záznamy, nebo pokud jste propřesunuli více než poslední záznam; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Můžete také volat `IsEOF` k určení, zda sada záznamů obsahuje nějaké záznamy nebo je prázdná. Ihned po volání `Open`, pokud sada záznamů neobsahuje žádné záznamy, `IsEOF` vrátí nenulovou hodnotu. Při otevření sady záznamů, která má alespoň jeden záznam, je první záznam aktuálním záznamem a `IsEOF` vrátí hodnotu 0.

Pokud je poslední záznam aktuálním záznamem při volání `MoveNext`, `IsEOF` následně vrátí nenulovou hodnotu. Pokud `IsEOF` vrátí nenulovou hodnotu a zavoláte `MoveNext`, je vyvolána výjimka. Pokud `IsEOF` vrátí nenulovou hodnotu, aktuální záznam není definován a všechny akce, které vyžadují aktuální záznam, budou mít za následek výjimku.

Účinek specifických metod na `IsBOF` a nastavení `IsEOF`:

- Volání `Open` interně vytvoří první záznam v sadě záznamů pomocí volání `MoveFirst`. Proto volání `Open` na prázdné sadě záznamů způsobí, že `IsBOF` a `IsEOF` vrátí nenulovou hodnotu. (Další informace naleznete v následující tabulce pro chování neúspěšného `MoveFirst` volání.)

- Všechny operace přesunutí, které úspěšně hledají záznam, způsobí, že `IsBOF` i `IsEOF` vrátí hodnotu 0.

- Volání `AddNew` následovaný voláním `Update`, které úspěšně vkládá nový záznam, způsobí, že `IsBOF` vrátí 0, ale pouze v případě, že `IsEOF` je již nenulová. Stav `IsEOF` zůstane vždy beze změny. Jak je definováno databázovým strojem Microsoft Jet, je aktuální ukazatel záznamu prázdné sady záznamů na konci souboru, takže všechny nové záznamy budou vloženy po aktuálním záznamu.

- Jakékoli volání `Delete`, a to i v případě, že odebere jediný zbývající záznam ze sady záznamů, nezmění hodnotu `IsBOF` nebo `IsEOF`.

Tato tabulka ukazuje, které operace přesunutí jsou povoleny s různými kombinacemi `IsBOF`/ `IsEOF`.

||MoveFirst, MoveLast|MovePrev<br /><br /> Přesunout < 0|Přesunout 0|Metoda<br /><br /> Přesunout > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= nenulová hodnota<br /><br /> `IsEOF`= 0|Povoleno|Výjimka|Výjimka|Povoleno|
|`IsBOF`= 0,<br /><br /> `IsEOF`= nenulová|Povoleno|Povoleno|Výjimka|Výjimka|
|Nenulové|Výjimka|Výjimka|Výjimka|Výjimka|
|0|Povoleno|Povoleno|Povoleno|Povoleno|

Povolení operace přesunu neznamená, že operace úspěšně najde záznam. Označuje pouze to, že pokus o provedení zadané operace přesunutí je povolen a nevygeneruje výjimku. Hodnota `IsBOF` a `IsEOF` členských funkcí se může změnit v důsledku pokusu o přesunutí.

V následující tabulce je uveden účinek operací přesunutí, které neobsahují záznam na hodnotě `IsBOF` a nastavení `IsEOF`.

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|Nenulovou|Nenulovou|
|`Move` 0|Žádné změny|Žádné změny|
|`MovePrev``Move` < 0|Nenulovou|Žádné změny|
|`MoveNext``Move` > 0|Žádné změny|Nenulovou|

Související informace najdete v nápovědě k rozhraní DAO v tématu "BOF, vlastnosti EOF".

##  <a name="isfielddirty"></a>CDaoRecordset:: IsFieldDirty

Zavolejte tuto členskou funkci, abyste zjistili, jestli je zadaný datový člen pro dynamickou sadu označený příznakem "dirty" (změněno).

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Ukazatel na datový člen pole, jehož stav chcete ověřit, nebo hodnotu NULL, chcete-li určit, zda jsou některá pole nečistá.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zadaný datový člen pole označen jako nečistý; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Data ve všech datových členech v poli undirty se přenesou do záznamu ve zdroji dat, když je aktuální záznam aktualizován voláním členské funkce `Update` `CDaoRecordset` (po volání `Edit` nebo `AddNew`). S tímto vědomím můžete provést další kroky, jako je například odznačení příznaku datového člena pole k označení sloupce tak, aby se nezapsal do zdroje dat.

`IsFieldDirty` je implementován prostřednictvím `DoFieldExchange`.

##  <a name="isfieldnull"></a>CDaoRecordset:: IsFieldNull

Zavolejte tuto členskou funkci, abyste zjistili, jestli je zadaný datový člen v sadě záznamů označený jako null.

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Ukazatel na datový člen pole, jehož stav chcete ověřit, nebo hodnotu NULL, chcete-li určit, zda jsou některá pole null.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je zadaný datový člen pole označen jako null; v opačném případě 0.

### <a name="remarks"></a>Poznámky

(V terminologii databáze hodnota null znamená "nemá žádnou hodnotu" a není shodná s hodnotou NULL v C++.) Pokud je datový člen pole označen jako null, je interpretován jako sloupec aktuálního záznamu, pro který neexistuje žádná hodnota.

> [!NOTE]
>  V některých situacích může použití `IsFieldNull` být neefektivní, jak ukazuje následující příklad kódu:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  Pokud používáte dynamickou vazbu záznamů, aniž byste museli odvozovat z `CDaoRecordset`, nezapomeňte použít VT_NULL, jak je znázorněno v příkladu.

##  <a name="isfieldnullable"></a>CDaoRecordset:: IsFieldNullable

Voláním této členské funkce určíte, zda je zadaný datový člen pole "Nullable" (lze nastavit na hodnotu null). C++ Hodnota null není shodná s hodnotou null, která v terminologii databáze znamená "nemá žádnou hodnotu").

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Ukazatel na datový člen pole, jehož stav chcete ověřit, nebo hodnotu NULL, chcete-li určit, zda jsou některá pole null.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je možné zadaný datový člen pole nastavit na hodnotu null; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pole, které nemůže mít hodnotu null, musí mít hodnotu. Pokud se pokusíte nastavit takové pole na hodnotu null při přidávání nebo aktualizaci záznamu, zdroj dat odmítne přidání nebo aktualizaci a `Update` vyvolá výjimku. K výjimce dojde při volání `Update`, ne při volání `SetFieldNull`.

##  <a name="isopen"></a>CDaoRecordset:: Open

Zavolejte tuto členskou funkci, abyste zjistili, jestli je sada záznamů otevřená.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud již byla volána členská funkce objektu sady záznamů `Open` nebo `Requery` a sada záznamů nebyla zavřena; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset:: m_bCheckCacheForDirtyFields

Obsahuje příznak označující, zda jsou pole v mezipaměti automaticky označena jako nečistá (změnila) a null.

### <a name="remarks"></a>Poznámky

Příznak Standard je nastaven na hodnotu TRUE. Nastavení v tomto datovém členu řídí celý mechanismus dvojího ukládání do vyrovnávací paměti. Pokud nastavíte příznak na hodnotu TRUE, můžete vypnout ukládání do mezipaměti pro pole po jednotlivých polích pomocí mechanismu DFX. Pokud nastavíte příznak na FALSE, musíte volat `SetFieldDirty` a `SetFieldNull` sami.

Před voláním `Open`nastavte tohoto datového člena. Tento mechanismus je primárně určen pro snadné použití. Výkon může být pomalejší z důvodu dvojího ukládání polí do vyrovnávací paměti, když jsou provedeny změny.

##  <a name="m_nfields"></a>CDaoRecordset:: m_nFields

Obsahuje počet datových členů pole v třídě sady záznamů a počet sloupců, které sada záznamů vybere ze zdroje dat.

### <a name="remarks"></a>Poznámky

Konstruktor třídy sady záznamů musí inicializovat `m_nFields` se správným počtem staticky vázaných polí. ClassWizard zapíše tuto inicializaci za vás, když ji použijete k deklaraci vaší třídy sady záznamů. Můžete ho také napsat ručně.

Rozhraní používá toto číslo ke správě interakce mezi datovými členy pole a odpovídající sloupce aktuálního záznamu ve zdroji dat.

> [!NOTE]
>  Toto číslo musí odpovídat počtu výstupních sloupců zaregistrovaných v `DoFieldExchange` po volání `SetFieldType` s parametrem `CDaoFieldExchange::outputColumn`.

Sloupce můžete dynamicky navazovat způsobem `CDaoRecordset::GetFieldValue` a `CDaoRecordset::SetFieldValue`. Pokud tak učiníte, nemusíte zvyšovat počet v `m_nFields` tak, aby odrážel počet volání funkce DFX ve vaší členské funkci `DoFieldExchange`.

##  <a name="m_nparams"></a>CDaoRecordset:: m_nParams

Obsahuje počet datových členů parametrů v třídě sady záznamů – počet parametrů předaných s dotazem sady záznamů.

### <a name="remarks"></a>Poznámky

Pokud vaše třída sady záznamů obsahuje nějaké datové členy parametru, konstruktor třídy musí inicializovat *m_nParams* se správným číslem. Hodnota *m_nParams* výchozí hodnota je 0. Pokud přidáte datové členy parametru, které je nutné provést ručně – je nutné také ručně přidat inicializaci v konstruktoru třídy, aby odrážely počet parametrů (který musí být alespoň tak velký, jako je počet ' ' zástupných symbolů v *m_strFilter* nebo řetězci *m_strSort* ).

Rozhraní používá toto číslo při parameterizes dotazu sady záznamů.

> [!NOTE]
>  Toto číslo musí odpovídat počtu "paraí" zaregistrovaným v `DoFieldExchange` po volání `SetFieldType` s parametrem `CFieldExchange::param`.

Související informace naleznete v tématu "objekt parametru" v nápovědě rozhraní DAO.

##  <a name="m_pdaorecordset"></a>CDaoRecordset:: m_pDAORecordset

Obsahuje ukazatel na rozhraní OLE pro objekt sady záznamů DAO, který je základem objektu `CDaoRecordset`.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte v případě, že potřebujete získat přímý přístup k rozhraní DAO.

Související informace naleznete v tématu "objekt sady záznamů" v nápovědě pro rozhraní DAO.

##  <a name="m_pdatabase"></a>CDaoRecordset:: m_pDatabase

Obsahuje ukazatel na objekt `CDaoDatabase`, pomocí kterého je sada záznamů připojena ke zdroji dat.

### <a name="remarks"></a>Poznámky

Tato proměnná se nastavuje dvěma způsoby. Obvykle při vytváření objektu Recordset předáte ukazatel na objekt již otevřený `CDaoDatabase`. Pokud místo toho předáte hodnotu NULL, `CDaoRecordset` pro vás vytvoří objekt `CDaoDatabase` a otevře se. V obou případech `CDaoRecordset` ukládá ukazatel do této proměnné.

Obvykle nebudete muset přímo používat ukazatel uložený v `m_pDatabase`. Pokud však píšete vlastní rozšíření pro `CDaoRecordset`, může být nutné použít ukazatel. Například je možné, že budete potřebovat ukazatel, pokud vyvoláte vlastní `CDaoException`(y).

Související informace naleznete v tématu "databázový objekt" v nápovědě pro rozhraní DAO.

##  <a name="m_strfilter"></a>CDaoRecordset:: m_strFilter

Obsahuje řetězec, který se používá k vytvoření klauzule **WHERE** příkazu jazyka SQL.

### <a name="remarks"></a>Poznámky

Neobsahuje rezervované slovo, **kde** má být sada záznamů filtrována. Použití tohoto datového člena nelze použít pro sady záznamů typu Table. Použití `m_strFilter` nemá žádný vliv při otevírání sady záznamů pomocí ukazatele `CDaoQueryDef`.

Použijte formát kalendářních dat (měsíc-den-rok), když filtrujete pole obsahující data, a to i v případě, že nepoužíváte americké verze databázového stroje Microsoft Jet. jinak se data nemusí filtrovat podle očekávání.

Související informace naleznete v tématu "vlastnost filtru" v nápovědě k rozhraní DAO.

##  <a name="m_strsort"></a>CDaoRecordset:: m_strSort

Obsahuje řetězec obsahující klauzuli **OrderBy** příkazu SQL bez vyhrazených slov **OrderBy**.

### <a name="remarks"></a>Poznámky

Můžete řadit podle typu dynamické sady a objektů sady záznamů sad snímků.

Nemůžete řadit objekty sady záznamů typu tabulka. Chcete-li určit pořadí řazení sady záznamů typu tabulka, zavolejte [SetCurrentIndex](#setcurrentindex).

Použití *m_strSort* nemá žádný vliv při otevírání sady záznamů pomocí ukazatele `CDaoQueryDef`.

Související informace najdete v nápovědě k rozhraní DAO v tématu "vlastnost řazení".

##  <a name="move"></a>CDaoRecordset:: Move

Zavolejte tuto členskou funkci pro umístění záznamů záznamů *lRows* z aktuálního záznamu.

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>Parametry

*lRows*<br/>
Počet záznamů, které se mají přesunout dopředu nebo dozadu Kladné hodnoty posunou vpřed ke konci sady záznamů. Záporné hodnoty se posunou zpět směrem k začátku.

### <a name="remarks"></a>Poznámky

Můžete přesunout vpřed nebo zpět. `Move( 1 )` je ekvivalentem `MoveNext`a `Move( -1 )` je ekvivalentem `MovePrev`.

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně volejte `IsBOF` i `IsEOF` před operaci přesunu, abyste zjistili, zda sada záznamů obsahuje nějaké záznamy. Po volání `Open` nebo `Requery`zavolejte buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud jste se přesunuli za začátek nebo konec sady záznamů (`IsBOF` nebo `IsEOF` vrátí nenulovou hodnotu), volání `Move` vyvolá `CDaoException`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Při volání `Move` na snímkovém posunu, který je jen pro posouvání, musí být parametr *lRows* kladné celé číslo a záložky nejsou povoleny, takže můžete přejít pouze vpřed.

Chcete-li provést první, poslední, další nebo předchozí záznam v sadě záznamů aktuálního záznamu, zavolejte `MoveFirst`, `MoveLast`, `MoveNext`nebo `MovePrev` členské funkce.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods".

##  <a name="movefirst"></a>CDaoRecordset:: MoveFirst

Zavolejte tuto členskou funkci pro vytvoření prvního záznamu v sadě záznamů (pokud existuje) aktuálního záznamu.

```
void MoveFirst();
```

### <a name="remarks"></a>Poznámky

Po otevření sady záznamů není nutné volat `MoveFirst` hned. V tuto chvíli je první záznam (pokud existuje) automaticky aktuální záznam.

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně volejte `IsBOF` i `IsEOF` před operaci přesunu, abyste zjistili, zda sada záznamů obsahuje nějaké záznamy. Po volání `Open` nebo `Requery`zavolejte buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Pomocí funkce `Move` se můžete přesunout ze záznamu na záznam bez použití podmínky. Použijte operace Find k vyhledání záznamů v dynamickém typu nebo objektu sady záznamů typu snímky, které odpovídají určité podmínce. Chcete-li vyhledat záznam v objektu sady záznamů typu tabulka, zavolejte `Seek`.

Pokud sada záznamů odkazuje na sadu záznamů typu tabulka, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti index základního objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Pokud voláte `MoveLast` v objektu sady záznamů založeném na dotazu SQL nebo querydef, je dotaz nuceně dokončen a objekt sady záznamů je plně vyplněn.

Nelze volat funkci `MoveFirst` nebo `MovePrev` členské funkce s posuvným snímkem, který je pouze pro posouvání.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů o určitý počet záznamů vpřed nebo zpět, zavolejte `Move`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods".

##  <a name="movelast"></a>CDaoRecordset:: MoveLast

Zavolejte tuto členskou funkci, aby byl poslední záznam (pokud existuje) v sadě záznamů aktuální záznam.

```
void MoveLast();
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně volejte `IsBOF` i `IsEOF` před operaci přesunu, abyste zjistili, zda sada záznamů obsahuje nějaké záznamy. Po volání `Open` nebo `Requery`zavolejte buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Pomocí funkce `Move` se můžete přesunout ze záznamu na záznam bez použití podmínky. Použijte operace Find k vyhledání záznamů v dynamickém typu nebo objektu sady záznamů typu snímky, které odpovídají určité podmínce. Chcete-li vyhledat záznam v objektu sady záznamů typu tabulka, zavolejte `Seek`.

Pokud sada záznamů odkazuje na sadu záznamů typu tabulka, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti index základního objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Pokud voláte `MoveLast` v objektu sady záznamů založeném na dotazu SQL nebo querydef, je dotaz nuceně dokončen a objekt sady záznamů je plně vyplněn.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů o určitý počet záznamů vpřed nebo zpět, zavolejte `Move`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods".

##  <a name="movenext"></a>CDaoRecordset:: MoveNext

Zavolejte tuto členskou funkci, aby se v sadě záznamů navedl další záznam s aktuálním záznamem.

```
void MoveNext();
```

### <a name="remarks"></a>Poznámky

Před pokusem o přesun na předchozí záznam se doporučuje volat `IsBOF`. Volání `MovePrev` vyvolá `CDaoException`, pokud `IsBOF` vrátí nenulovou hodnotu, což značí, že jste již přesunuli před první záznam nebo že žádné záznamy nebyly vybrány sadou záznamů.

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně volejte `IsBOF` i `IsEOF` před operaci přesunu, abyste zjistili, zda sada záznamů obsahuje nějaké záznamy. Po volání `Open` nebo `Requery`zavolejte buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Pomocí funkce `Move` se můžete přesunout ze záznamu na záznam bez použití podmínky. Použijte operace Find k vyhledání záznamů v dynamickém typu nebo objektu sady záznamů typu snímky, které odpovídají určité podmínce. Chcete-li vyhledat záznam v objektu sady záznamů typu tabulka, zavolejte `Seek`.

Pokud sada záznamů odkazuje na sadu záznamů typu tabulka, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti index základního objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů o určitý počet záznamů vpřed nebo zpět, zavolejte `Move`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods".

##  <a name="moveprev"></a>CDaoRecordset:: MovePrev

Zavolejte tuto členskou funkci, aby se navedl předchozí záznam v sadě záznamů v aktuálním záznamu.

```
void MovePrev();
```

### <a name="remarks"></a>Poznámky

Před pokusem o přesun na předchozí záznam se doporučuje volat `IsBOF`. Volání `MovePrev` vyvolá `CDaoException`, pokud `IsBOF` vrátí nenulovou hodnotu, což značí, že jste již přesunuli před první záznam nebo že žádné záznamy nebyly vybrány sadou záznamů.

> [!CAUTION]
>  Volání kterékoli z `Move` Functions vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Obecně volejte `IsBOF` i `IsEOF` před operaci přesunu, abyste zjistili, zda sada záznamů obsahuje nějaké záznamy. Po volání `Open` nebo `Requery`zavolejte buď `IsBOF` nebo `IsEOF`.

> [!NOTE]
>  Pokud voláte některou z funkcí `Move`, zatímco se aktualizuje nebo přidává aktuální záznam, aktualizace se ztratí bez upozornění.

Pomocí funkce `Move` se můžete přesunout ze záznamu na záznam bez použití podmínky. Použijte operace Find k vyhledání záznamů v dynamickém typu nebo objektu sady záznamů typu snímky, které odpovídají určité podmínce. Chcete-li vyhledat záznam v objektu sady záznamů typu tabulka, zavolejte `Seek`.

Pokud sada záznamů odkazuje na sadu záznamů typu tabulka, pohyb následuje za aktuálním indexem tabulky. Aktuální index můžete nastavit pomocí vlastnosti index základního objektu DAO. Pokud nenastavíte aktuální index, pořadí vrácených záznamů není definováno.

Nelze volat funkci `MoveFirst` nebo `MovePrev` členské funkce s posuvným snímkem, který je pouze pro posouvání.

Chcete-li přesunout pozici aktuálního záznamu v objektu sady záznamů o určitý počet záznamů vpřed nebo zpět, zavolejte `Move`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Move Method" a "MoveFirst, MoveLast, MoveNext, MovePrevious Methods".

##  <a name="open"></a>CDaoRecordset:: Open

Chcete-li načíst záznamy pro sadu záznamů, je nutné zavolat tuto členskou funkci.

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

- `dbOpenDynaset` sadu záznamů typu dynamická sada s obousměrným posouváním. Toto nastavení je výchozí.

- `dbOpenTable` sadu záznamů typu tabulka s obousměrným posouváním.

- `dbOpenSnapshot` sadu záznamů typu snímek s obousměrným posouváním.

*Ipszsql*<br/>
Ukazatel řetězce obsahující jedno z následujících:

- Ukazatel NULL.

- Název jednoho nebo více TableDefs a/nebo QueryDefs (oddělených čárkami).

- Příkaz jazyka SQL **Select** (volitelně s klauzulí **WHERE** nebo **OrderBy** SQL).

- Předávací dotaz.

*nOptions*<br/>
Jednu nebo více možností uvedených níže. Výchozí hodnota je 0. Možné hodnoty jsou následující:

- `dbAppendOnly` lze připojit pouze nové záznamy (pouze sada záznamů typu dynamická sada). Tato možnost znamená, že záznamy mohou být připojeny pouze. Databázové třídy knihovny MFC rozhraní ODBC mají možnost pouze připojit, která umožňuje načtení a připojení záznamů.

- `dbForwardOnly` sada záznamů je jen pro posouvání snímku.

- `dbSeeChanges` generovat výjimku, pokud jiný uživatel mění data, která upravujete.

- `dbDenyWrite` ostatní uživatelé nemůžou upravovat ani přidávat záznamy.

- `dbDenyRead` ostatní uživatelé nemohou zobrazit záznamy (pouze sada záznamů typu tabulka).

- `dbReadOnly` můžete pouze zobrazit záznamy; ostatní uživatelé je mohou upravit.

- `dbInconsistent` nekonzistentní aktualizace jsou povoleny (pouze sada záznamů typu dynamická sada).

- `dbConsistent` pouze konzistentní aktualizace jsou povoleny (pouze sada záznamů typu dynamická sada).

> [!NOTE]
>  Konstanty `dbConsistent` a `dbInconsistent` se vzájemně vylučují. Můžete použít jeden nebo druhý, ale ne oba v dané instanci `Open`.

*pTableDef*<br/>
Ukazatel na objekt [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) . Tato verze je platná pouze pro sady záznamů typu Table. Při použití této možnosti není použit ukazatel `CDaoDatabase` použitý k vytvoření `CDaoRecordset`; místo toho se použije databáze, ve které se tabledef nachází.

*pQueryDef*<br/>
Ukazatel na objekt [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) . Tato verze je platná pouze pro sady záznamů typu Dynamic-Type a Snapshot-Type. Při použití této možnosti není použit ukazatel `CDaoDatabase` použitý k vytvoření `CDaoRecordset`; místo toho se použije databáze, ve které se nachází querydef.

### <a name="remarks"></a>Poznámky

Před voláním `Open`musíte vytvořit objekt sady záznamů. To lze provést několika způsoby:

- Při vytváření objektu sady záznamů předejte ukazatel na objekt `CDaoDatabase`, který je již otevřen.

- Při vytváření objektu sady záznamů předejte ukazatel na objekt `CDaoDatabase`, který není otevřen. Sada záznamů otevře objekt `CDaoDatabase`, ale při zavření objektu sady záznamů jej nebude zavřen.

- Při vytváření objektu sady záznamů předejte ukazatel s hodnotou NULL. Objekt sady záznamů volá `GetDefaultDBName`, aby získal název Microsoft Accessu. Soubor MDB, který se má otevřít Sada záznamů pak otevře objekt `CDaoDatabase` a zůstane otevřený, dokud je sada záznamů otevřená. Při volání `Close` v sadě záznamů je objekt `CDaoDatabase` také uzavřen.

    > [!NOTE]
    >  Když sada záznamů otevře objekt `CDaoDatabase`, otevře se zdroj dat s nevýhradním přístupem.

Pro verzi `Open`, která používá parametr *lpszSQL* po otevření sady záznamů, lze záznamy načíst v jednom z několika způsobů. První možností je mít funkce DFX ve vašem `DoFieldExchange`. Druhou možností je použít dynamickou vazbu voláním členské funkce `GetFieldValue`. Tyto možnosti lze implementovat samostatně nebo v kombinaci. Pokud jsou kombinovány, budete muset předat příkaz SQL do tohoto volání `Open`.

Při použití druhé verze `Open`, kde předáte do `CDaoTableDef` objektu, budou výsledné sloupce k dispozici pro svázání přes `DoFieldExchange` a mechanismu DFX a dynamicky Bind prostřednictvím `GetFieldValue`.

> [!NOTE]
>  Můžete volat `Open` pouze pomocí objektu `CDaoTableDef` pro sady záznamů typu Table.

Použijete-li třetí verzi `Open`, na kterou předáte objekt `CDaoQueryDef`, bude tento dotaz proveden a výsledné sloupce budou k dispozici pro svázání prostřednictvím `DoFieldExchange` a mechanismu DFX nebo dynamicky Bind prostřednictvím `GetFieldValue`.

> [!NOTE]
>  Můžete volat `Open` pouze pomocí objektu `CDaoQueryDef` pro sady záznamů typu Dynamic-Type a Snapshot.

Pro první verzi `Open`, která používá parametr `lpszSQL`, se záznamy vyberou na základě kritérií uvedených v následující tabulce.

|Hodnota parametru `lpszSQL`|Zvolené záznamy jsou určeny|Příklad|
|--------------------------------------|----------------------------------------|-------------|
|NULL|Řetězec vrácený funkcí `GetDefaultSQL`.||
|Čárkami oddělený seznam jednoho nebo více názvů TableDefs a/nebo querydef.|Všechny sloupce reprezentované v `DoFieldExchange`.|`"Customer"`|
|**Vybrat** sloupec-seznam **ze** seznamu tabulek|Zadané sloupce z určených TableDef a/nebo querydef.|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

Obvyklým postupem je předání hodnoty NULL `Open`; v takovém případě `Open` volá `GetDefaultSQL`, přepisovatelný členská funkce, která ClassWizard generuje při vytváření třídy odvozené od `CDaoRecordset`. Tato hodnota poskytuje tabledef (y) nebo názvy querydef, které jste zadali v ClassWizard. Místo toho můžete zadat další informace v parametru *lpszSQL* .

Cokoli, co předáte, `Open` vytvoří konečný řetězec SQL pro dotaz (řetězec může obsahovat klauzule SQL **WHERE** a **OrderBy** připojené k řetězci *lpszSQL* , který jste předali) a následně spustí dotaz. Můžete prozkoumávat vytvořený řetězec voláním `GetSQL` po volání `Open`.

Datové členy polí třídy sady záznamů jsou svázány se sloupci zvolených dat. Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Pokud chcete nastavit možnosti pro sadu záznamů, jako je filtr nebo řazení, nastavte `m_strSort` nebo `m_strFilter` po sestavení objektu sady záznamů, ale před voláním `Open`. Chcete-li aktualizovat záznamy v sadě záznamů poté, co je sada záznamů již otevřena, zavolejte `Requery`.

Pokud zavoláte `Open` na dynamické sadě nebo sadě záznamů typu snímky, nebo pokud zdroj dat odkazuje na příkaz SQL nebo tabledef, který představuje připojenou tabulku, nemůžete pro argument typu použít `dbOpenTable`. Pokud tak učiníte, knihovna MFC vyvolá výjimku. Chcete-li zjistit, zda objekt tabledef představuje připojenou tabulku, vytvořte objekt [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) a zavolejte jeho členskou funkci [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) .

Příznak `dbSeeChanges` použijte v případě, že chcete zachytit změny provedené jiným uživatelem nebo jiným programem na vašem počítači, když upravujete nebo odstraníte stejný záznam. Například pokud dva uživatelé začínají upravovat stejný záznam, první uživatel, který volá `Update` členské funkce, je úspěšný. Když je `Update` volána druhým uživatelem, je vyvolána `CDaoException`. Podobně pokud se druhý uživatel pokusí zavolat `Delete`, aby záznam odstranil a byl již změněn prvním uživatelem, dojde k `CDaoException`.

Obvykle Pokud uživatel získá tuto `CDaoException` při aktualizaci, váš kód by měl aktualizovat obsah polí a načíst nově upravené hodnoty. Pokud dojde k výjimce při odstraňování, váš kód může zobrazit data nového záznamu pro uživatele a zprávu oznamující, že se data v nedávné době změnila. V tomto okamžiku váš kód může požádat o potvrzení, že uživatel bude chtít záznam ještě odstranit.

> [!TIP]
>  Možnost posouvání s pouze přesměrováním (`dbForwardOnly`) slouží ke zvýšení výkonu, když aplikace provede jeden průchod sadou záznamů otevřených ze zdroje dat ODBC.

Související informace naleznete v tématu "metoda OpenRecordset" v nápovědě k rozhraní DAO.

##  <a name="requery"></a>CDaoRecordset:: Requery

Zavolejte tuto členskou funkci pro opětovné sestavení (obnovení) sady záznamů.

```
virtual void Requery();
```

### <a name="remarks"></a>Poznámky

Jsou-li vráceny jakékoli záznamy, první záznam se stává aktuálním záznamem.

Aby sada záznamů odrážela přidávání a odstraňování, které jste vy nebo jiní uživatelé nastavili na zdroj dat, je nutné sadu záznamů znovu sestavit voláním `Requery`. Pokud sada záznamů je dynamická sada, automaticky odrážejí aktualizace, které vy nebo jiní uživatelé provedete, do svých stávajících záznamů (ale ne přidaných). Pokud je sada záznamů snímkem, je nutné volat `Requery`, aby odrážela úpravy provedené jinými uživateli, a také přidání a odstranění.

V případě dynamické sady nebo snímku volejte `Requery` kdykoli chcete znovu sestavit sadu záznamů pomocí hodnot parametrů. Před voláním `Requery`nastavte nový filtr nebo řazení nastavením [m_strFilter](#m_strfilter) a [m_strSort](#m_strsort) . Před voláním `Requery`nastavte nové parametry přiřazením nových hodnot datovým členům parametru.

Pokud se pokus o opětovné sestavení sady záznamů nezdaří, sada záznamů je zavřena. Před voláním `Requery`můžete určit, zda se sada záznamů může znovu dotazovat voláním členské funkce [CanRestart](#canrestart) . `CanRestart` nezaručuje, že `Requery` bude úspěšná.

> [!CAUTION]
>  Vyvolejte `Requery` až po volání `Open`.

> [!NOTE]
>  Volání [ZnovuSpustitDotaz](#requery) změní záložky rozhraní DAO.

Pokud volání `CanRestart` vrátí hodnotu 0, nemůžete volat `Requery` pro sadu typu sady nebo snímku typu snímky, ani je nelze použít pro sadu záznamů typu tabulka.

Pokud `IsBOF` a `IsEOF` vrátí nenulovou hodnotu po volání `Requery`, dotaz nevrátil žádné záznamy a sada záznamů nebude obsahovat žádná data.

Související informace naleznete v tématu "metoda Requery" v nápovědě k rozhraní DAO.

##  <a name="seek"></a>CDaoRecordset:: Seek

Zavolejte tuto členskou funkci pro vyhledání záznamu v indexovaném objektu sady záznamů typu tabulka, který splňuje zadaná kritéria pro aktuální index a zaznamená si aktuální záznam.

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
Jeden z následujících řetězcových výrazů: "<", "\<=", "=", "> =" nebo ">".

*pKey1*<br/>
Ukazatel na [COleVariant](../../mfc/reference/colevariant-class.md) , jehož hodnota odpovídá prvnímu poli v indexu. Povinná hodnota.

*pKey2*<br/>
Ukazatel na `COleVariant`, jehož hodnota odpovídá druhému poli v indexu, pokud existuje. Výchozí hodnota je NULL.

*pKey3*<br/>
Ukazatel na `COleVariant`, jehož hodnota odpovídá třetímu poli v indexu (pokud existuje). Výchozí hodnota je NULL.

*pKeyArray*<br/>
Ukazatel na pole variant. Velikost pole odpovídá počtu polí v indexu.

*nKeys*<br/>
Celé číslo odpovídající velikosti pole, což je počet polí v indexu.

> [!NOTE]
>  Nezadávejte v klíčích zástupné znaky. Zástupné znaky způsobí, že `Seek` nevrátí žádné vyhovující záznamy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou nalezeny vyhovující záznamy, jinak 0.

### <a name="remarks"></a>Poznámky

Použijte druhou (Array) verzi `Seek` pro zpracování indexů čtyř polí nebo více.

`Seek` povoluje vysoce výkonné prohledávání indexu pro sady záznamů typu tabulka. Je nutné nastavit aktuální index voláním `SetCurrentIndex` před voláním `Seek`. Pokud index identifikuje pole nebo pole bez jedinečného klíče, `Seek` vyhledá první záznam, který splňuje kritéria. Pokud nenastavíte index, je vyvolána výjimka.

Všimněte si, že pokud nevytváříte sadu záznamů UNICODE, objekty `COleVariant` musí být explicitně deklarovány standardem ANSI. To lze provést pomocí formuláře [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **,** *vtSrc* **)** ve formě konstruktoru s *vtSrc* nastavenou na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavenou na `VT_BSTRT`.

Při volání `Seek`předáte jednu nebo více hodnot klíče a operátor porovnání ("<", "\<=", "=", "> =" nebo ">"). `Seek` prohledá zadaná klíčová pole a vyhledá první záznam, který splňuje kritéria zadaná v *lpszComparison* a *pKey1*. Po nalezení `Seek` vrátí nenulovou hodnotu a provede záznam aktuální. Pokud `Seek` nenalezne shodu, `Seek` vrátí hodnotu nula a aktuální záznam není definován. Pokud používáte rozhraní DAO přímo, musíte explicitně zaškrtnout vlastnost neshoda.

Pokud `lpszComparison` je "=", "> =" nebo ">", `Seek` začíná na začátku indexu. Pokud je *lpszComparison* "<" nebo "< =", `Seek` začíná na konci indexu a hledá zpět, pokud na konci nejsou žádné duplicitní položky indexu. V takovém případě `Seek` spustí libovolný záznam mezi duplicitními položkami indexu na konci indexu.

Když použijete `Seek`, nemusí se jednat o aktuální záznam.

Chcete-li najít záznam v sadě záznamů typu dynamická sada nebo typu snímky, který splňuje konkrétní podmínku, použijte operace Find. Chcete-li zahrnout všechny záznamy, nikoli pouze ty, které splní určitou podmínku, použijte operace přesunutí pro přesun ze záznamu na záznam.

Nelze volat `Seek` pro připojenou tabulku libovolného typu, protože připojené tabulky musí být otevřeny jako dynamické-typ nebo sady záznamů typu snímky. Nicméně pokud zavoláte `CDaoDatabase::Open` pro přímé otevření Instalovatelné databáze ISAM, můžete volat `Seek` v tabulkách v této databázi, i když výkon může být pomalý.

Související informace naleznete v tématu "Metoda hledání" v nápovědě k rozhraní DAO.

##  <a name="setabsoluteposition"></a>CDaoRecordset:: SetAbsolutePosition

Nastaví relativní číslo záznamu aktuálního záznamu objektu sady záznamů.

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>Parametry

*lPosition*<br/>
Odpovídá pořadové pozici aktuálního záznamu v sadě záznamů.

### <a name="remarks"></a>Poznámky

Volání `SetAbsolutePosition` umožňuje umístit ukazatel aktuálního záznamu na konkrétní záznam na základě jeho ordinální pozice v sadě dat typu Dynamic-Type nebo Snapshot. Aktuální číslo záznamu můžete určit také voláním [GetAbsolutePosition](#getabsoluteposition).

> [!NOTE]
>  Tato členská funkce je platná pouze pro sady záznamů typu Dynamic-Type a Snapshot-Type.

Hodnota vlastnosti AbsolutePosition základního objektu DAO je založena na nule; nastavení 0 odkazuje na první záznam v sadě záznamů. Nastavení hodnoty větší než počet vyplněných záznamů způsobí, že knihovna MFC vyvolá výjimku. Počet vyplněných záznamů v sadě záznamů můžete určit voláním členské funkce `GetRecordCount`.

Pokud je aktuální záznam odstraněn, hodnota vlastnosti AbsolutePosition není definována a MFC vyvolá výjimku, pokud je odkazováno. Nové záznamy jsou přidány na konec sekvence.

> [!NOTE]
>  Tato vlastnost není určena k použití jako náhradní číslo záznamu. Záložky jsou stále doporučeným způsobem zachování a návratu na danou pozici a jsou jediným způsobem, jak umístit aktuální záznam napříč všemi typy objektů sady záznamů, které podporují záložky. Konkrétně se poloha daného záznamu změní, když jsou záznamy před smazány. K dispozici není také žádná záruka, že daný záznam bude mít stejnou absolutní pozici, pokud je znovu znovu vytvořena sada záznamů, protože pořadí jednotlivých záznamů v rámci sady záznamů není zaručeno, pokud není vytvořeno pomocí příkazu jazyka SQL pomocí klauzule **OrderBy** .

Související informace najdete v tématu "vlastnost AbsolutePosition" v nápovědě k rozhraní DAO.

##  <a name="setbookmark"></a>CDaoRecordset:: SetBookmark

Zavolejte tuto členskou funkci pro umístění sady záznamů obsahující zadanou záložku.

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
Objekt [COleVariant](../../mfc/reference/colevariant-class.md) obsahující hodnotu záložky pro konkrétní záznam.

### <a name="remarks"></a>Poznámky

Když je vytvořen nebo otevřen objekt sady záznamů, každý z jeho záznamů již obsahuje jedinečnou záložku. Záložku pro aktuální záznam můžete načíst voláním `GetBookmark` a uložením hodnoty do objektu `COleVariant`. Později se můžete vrátit k tomuto záznamu voláním `SetBookmark` pomocí uložené hodnoty záložky.

> [!NOTE]
>  Volání [ZnovuSpustitDotaz](#requery) změní záložky rozhraní DAO.

Všimněte si, že pokud nevytváříte sadu záznamů UNICODE, objekt `COleVariant` musí být explicitně deklarován standardem ANSI. To lze provést pomocí formuláře [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **,** *vtSrc* **)** ve formě konstruktoru s *vtSrc* nastavenou na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavenou na `VT_BSTRT`.

Související informace naleznete v tématech "vlastnost záložky" a vlastnost Bookmark "v nápovědě k rozhraní DAO.

##  <a name="setcachesize"></a>CDaoRecordset:: SetCacheSize

Zavolejte tuto členskou funkci pro nastavení počtu záznamů, které mají být uloženy do mezipaměti.

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>Parametry

*lSize*<br/>
Určuje počet záznamů. Typická hodnota je 100. Nastavení 0 vypne ukládání do mezipaměti. Nastavení musí být v rozmezí 5 až 1200 záznamů. Mezipaměť může využívat značnou velikost paměti.

### <a name="remarks"></a>Poznámky

Mezipaměť je místo v místní paměti, ve kterém jsou uložena data, která byla naposledy načtena ze serveru aplikace v případě, že se data budou požadovat znovu při spuštění aplikace. Ukládání dat do mezipaměti vylepšuje výkon aplikace, která načítá data ze vzdáleného serveru prostřednictvím objektů sad záznamů sady záznamů. Když se vyžadují data, databázový stroj Microsoft Jet nejprve zkontroluje mezipaměť pro požadovaná data a nenačte ho ze serveru, což trvá víc času. Data, která nepocházejí ze zdroje dat ODBC, se v mezipaměti neukládají.

Všechny zdroje dat ODBC, jako je například připojená tabulka, můžou mít místní mezipaměť. Chcete-li vytvořit mezipaměť, otevřete objekt sady záznamů ze vzdáleného zdroje dat, zavolejte členské funkce `SetCacheSize` a `SetCacheStart` a potom zavolejte `FillCache` členské funkce nebo proveďte krok prostřednictvím záznamů pomocí jedné z operací přesunutí. Parametr *lSize* členské funkce `SetCacheSize` může být založen na počtu záznamů, se kterými může aplikace pracovat najednou. Pokud například používáte sadu záznamů jako zdroj dat, která se mají zobrazit na obrazovce, můžete předat parametr `SetCacheSize` *lSize* jako 20 a zobrazit 20 záznamů najednou.

Související informace naleznete v tématu "CacheSize, CacheStart Properties" v nápovědě pro rozhraní DAO.

##  <a name="setcachestart"></a>CDaoRecordset:: SetCacheStart

Zavolejte tuto členskou funkci pro určení záložky prvního záznamu v sadě záznamů, který má být ukládán do mezipaměti.

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>Parametry

*varBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) , který určuje záložku prvního záznamu v sadě záznamů, která má být uložena do mezipaměti.

### <a name="remarks"></a>Poznámky

Hodnotu záložky libovolného záznamu můžete použít pro parametr *varBookmark* členské funkce `SetCacheStart`. Proveďte záznam, který chcete spustit v mezipaměti s aktuálním záznamem, vytvořte záložku pro tento záznam pomocí [SetBookmark](#setbookmark)a předejte hodnotu záložky jako parametr pro členskou funkci `SetCacheStart`.

Databázový stroj Microsoft Jet požaduje záznamy v rámci rozsahu mezipaměti z mezipaměti a vyžádá si záznamy mimo rozsah mezipaměti ze serveru.

Záznamy načtené z mezipaměti nereflektují změny provedené souběžně na zdrojová data jinými uživateli.

Chcete-li vynutit aktualizaci všech dat uložených v mezipaměti, předejte parametr *lSize* `SetCacheSize` jako 0, zavolejte `SetCacheSize` znovu s velikostí mezipaměti, kterou jste původně požadovali, a potom zavolejte členskou funkci `FillCache`.

Všimněte si, že pokud nevytváříte sadu záznamů UNICODE, objekt `COleVariant` musí být explicitně deklarován standardem ANSI. To lze provést pomocí formuláře [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **,** *vtSrc* **)** ve formě konstruktoru s *vtSrc* nastavenou na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavenou na `VT_BSTRT`.

Související informace najdete v tématu CacheSize, CacheStart Properties "v nápovědě k rozhraní DAO.

##  <a name="setcurrentindex"></a>CDaoRecordset:: SetCurrentIndex

Zavolejte tuto členskou funkci pro nastavení indexu pro sadu záznamů typu tabulka.

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ukazatel obsahující název indexu, který má být nastaven.

### <a name="remarks"></a>Poznámky

Záznamy v základních tabulkách nejsou uloženy v žádném konkrétním pořadí. Nastavení indexu změní pořadí záznamů vrácených z databáze, ale nemá vliv na pořadí, ve kterém jsou záznamy uloženy. Zadaný index již musí být definován. Pokud se pokusíte použít objekt indexu, který neexistuje, nebo pokud není index nastaven při volání metody [Seek](#seek), knihovna MFC vyvolá výjimku.

Můžete vytvořit nový index pro tabulku voláním [CDaoTableDef:: CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) a připojením nového indexu k kolekci indexů podkladového tabledef voláním metody [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append)a následným otevřením sady záznamů.

Záznamy vrácené ze sady záznamů typu tabulka lze seřadit pouze pomocí indexů definovaných pro základní tabledef. Chcete-li seřadit záznamy v některém jiném pořadí, můžete otevřít sadu záznamů typu dynamická sada nebo snímky pomocí klauzule SQL **OrderBy** uložené v části [CDaoRecordset:: m_strSort](#m_strsort).

Související informace najdete v nápovědě k rozhraní DAO v tématu "objekt" a definice "aktuální index".

##  <a name="setfielddirty"></a>CDaoRecordset:: SetFieldDirty

Zavolejte tuto členskou funkci pro označení datového členu pole sady záznamů jako změněné nebo beze změny.

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo hodnotu NULL. Pokud je NULL, všechna pole datových členů v sadě záznamů jsou označena příznakem. (C++ Hodnota null není shodná s hodnotou null v terminologii databáze, což znamená "nemá žádnou hodnotu.")

*bDirty*<br/>
TRUE, pokud má datový člen pole označení "dirty" (změněno). Jinak FALSE, pokud datový člen pole musí být označen jako "vyčistit" (beze změny).

### <a name="remarks"></a>Poznámky

Označení polí jako nezměněné zajistí, že pole nebude aktualizováno.

Rozhraní označuje změněné datové členy pole, aby se zajistilo jejich zápis do záznamu ve zdroji dat pomocí mechanismu výměny pole záznamu (DFX) DAO. Změna hodnoty pole obvykle automaticky nastaví pole jako chybné, takže nebudete muset volat `SetFieldDirty` sami, ale někdy budete chtít zajistit, aby se sloupce explicitně aktualizovaly nebo vložily bez ohledu na to, jaká hodnota je v datovém členu pole. Mechanismus DFX používá také použití PSEUDONULL. Další informace naleznete v tématu [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

Pokud se nepoužívá mechanismus dvojitého ukládání do vyrovnávací paměti, pak při změně hodnoty pole se pole automaticky nenastaví jako nečisté. V takovém případě bude nutné explicitně nastavit pole jako nečisté. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

> [!NOTE]
>  Tuto členskou funkci volejte až poté, co jste volali [Edit](#edit) nebo [AddNew](#addnew).

Použití hodnoty NULL pro první argument funkce použije funkci na všechna `outputColumn` pole, nikoli na pole **param** v `CDaoFieldExchange`. Například volání

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

nastaví pouze `outputColumn` pole na hodnotu NULL; pole **param** nebudou nijak ovlivněna.

Chcete-li pracovat s **parametrem**, je nutné dodat skutečnou adresu jednotlivého **param** , na kterém chcete pracovat, například:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

To znamená, že nemůžete nastavit všechna pole **param** na hodnotu null, jak můžete používat pole `outputColumn`.

`SetFieldDirty` je implementován prostřednictvím `DoFieldExchange`.

##  <a name="setfieldnull"></a>CDaoRecordset:: SetFieldNull

Zavolejte tuto členskou funkci pro označení datového členu pole sady záznamů jako null (konkrétně bez hodnoty) nebo jako nenulového typu.

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
Obsahuje adresu datového člena pole v sadě záznamů nebo hodnotu NULL. Pokud je NULL, všechna pole datových členů v sadě záznamů jsou označena příznakem. (C++ Hodnota null není shodná s hodnotou null v terminologii databáze, což znamená "nemá žádnou hodnotu.")

*bNull*<br/>
Nenulová, pokud má datový člen pole označení bez hodnoty (null). V opačném případě 0, pokud má datový člen pole označení příznakem jako jiný než null.

### <a name="remarks"></a>Poznámky

`SetFieldNull` se používá pro pole vázaná v mechanismu `DoFieldExchange`.

Když přidáte nový záznam do sady záznamů, všechna pole datových členů jsou zpočátku nastavena na hodnotu null a označena jako "dirtá" (změna). Když načtete záznam ze zdroje dat, jeho sloupce buď již mají hodnoty, nebo mají hodnotu null. Pokud není vhodné vytvořit pole null, je vyvolána výjimka [CDaoException](../../mfc/reference/cdaoexception-class.md) .

Používáte-li mechanismus dvojího ukládání do vyrovnávací paměti, například pokud chcete určit pole aktuálního záznamu jako nehodnotu, zavolejte `SetFieldNull` s *bNull* nastavenou na hodnotu true, aby byl příznak označen jako null. Pokud pole již bylo označeno jako null a nyní chcete dát hodnotu, stačí nastavit novou hodnotu. Nemusíte odebírat příznak null s `SetFieldNull`. Chcete-li zjistit, zda je pole povoleno mít hodnotu null, zavolejte na [IsFieldNullable](#isfieldnullable).

Pokud nepoužíváte mechanismus dvojího ukládání do vyrovnávací paměti, pak při změně hodnoty pole není pole automaticky nastaveno na hodnotu undirty a jiná hodnota než null. Je nutné výslovně nastavit pole undirty a jinou než null. Příznak obsažený v [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) řídí tuto automatickou kontrolu polí.

Mechanismus DFX využívá použití PSEUDONULL. Další informace naleznete v tématu [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation).

> [!NOTE]
>  Tuto členskou funkci volejte až poté, co jste volali [Edit](#edit) nebo [AddNew](#addnew).

Použití hodnoty NULL pro první argument funkce použije funkci pouze pro `outputColumn` pole, nikoli pole **param** v `CDaoFieldExchange`. Například volání

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

nastaví pouze `outputColumn` pole na hodnotu NULL; pole **param** nebudou nijak ovlivněna.

##  <a name="setfieldvalue"></a>CDaoRecordset:: SetFieldValue

Zavolejte tuto členskou funkci pro nastavení hodnoty pole buď podle pořadového čísla, nebo změnou hodnoty řetězce.

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
Ukazatel na řetězec, který obsahuje název pole.

*varValue*<br/>
Odkaz na objekt [COleVariant](../../mfc/reference/colevariant-class.md) , který obsahuje hodnotu obsahu pole.

*nIndex*<br/>
Celé číslo představující pořadové místo pole v kolekci polí sady záznamů (založené na nule).

*lpszValue*<br/>
Ukazatel na řetězec obsahující hodnotu obsahu pole.

### <a name="remarks"></a>Poznámky

Použijte `SetFieldValue` a [GetFieldValue –](#getfieldvalue) k dynamickému vázání polí v době běhu namísto staticky propojeného sloupce pomocí mechanismu [DoFieldExchange](#dofieldexchange) .

Všimněte si, že pokud nevytváříte sadu záznamů UNICODE, je nutné buď použít formu `SetFieldValue`, která neobsahuje parametr `COleVariant`, nebo objekt `COleVariant` musí být explicitně deklarován standardem ANSI. To lze provést pomocí formuláře [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **,** *vtSrc* **)** ve formě konstruktoru s *vtSrc* nastavenou na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavenou na `VT_BSTRT`.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "objekt pole" a "vlastnost hodnoty".

##  <a name="setfieldvaluenull"></a>CDaoRecordset:: SetFieldValueNull

Zavolejte tuto členskou funkci pro nastavení pole na hodnotu null.

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index pole v sadě záznamů pro vyhledávání v indexu založeném na nule.

*lpszName*<br/>
Název pole v sadě záznamů pro vyhledávání podle názvu

### <a name="remarks"></a>Poznámky

C++Hodnota NULL není shodná s hodnotou null, která v terminologii databáze znamená, že "nemá žádnou hodnotu."

Související informace naleznete v nápovědě k rozhraní DAO v tématech "objekt pole" a "vlastnost hodnoty".

##  <a name="setlockingmode"></a>CDaoRecordset:: SetLockingMode

Zavolejte tuto členskou funkci pro nastavení typu uzamykání pro sadu záznamů.

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>Parametry

*bPessimistic*<br/>
Příznak, který označuje typ uzamykání.

### <a name="remarks"></a>Poznámky

Pokud je v platnosti pesimistické zamykání, stránka 2K obsahující Upravovaný záznam je uzamčena, Jakmile zavoláte členskou funkci `Edit`. Stránka je odemčena při volání `Update` nebo `Close` členské funkce nebo kterékoli operace přesunutí nebo hledání.

Pokud je v platnosti optimistické zamykání, stránka 2K obsahující záznam je uzamčena pouze v případě, že je záznam aktualizován pomocí členské funkce `Update`.

Pokud je stránka uzamčena, nikdo jiný uživatel nebude moci upravovat záznamy na stejné stránce. Pokud zavoláte `SetLockingMode` a předáte nenulovou hodnotu a jiný uživatel již stránku uzamkl, je vyvolána výjimka při volání `Edit`. Jiní uživatelé mohou číst data z uzamčených stránek.

Pokud zavoláte `SetLockingMode` s nulovou hodnotou a později volání `Update` Pokud je stránka uzamčena jiným uživatelem, dojde k výjimce. Chcete-li zobrazit změny provedené v záznamu jiným uživatelem (a ztratit změny), zavolejte členskou funkci `SetBookmark` s hodnotou záložky aktuálního záznamu.

Při práci se zdroji dat ODBC je režim uzamykání vždycky optimistický.

##  <a name="setparamvalue"></a>CDaoRecordset:: SetParamValue

Zavolejte tuto členskou funkci pro nastavení hodnoty parametru v sadě záznamů v době běhu.

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
Číselná pozice parametru v kolekci parametrů querydef.

*var*<br/>
Hodnota, která se má nastavit; viz poznámky.

*lpszName*<br/>
Název parametru, jehož hodnota má být nastavena.

### <a name="remarks"></a>Poznámky

Parametr již musí být vytvořen jako součást řetězce SQL sady záznamů. K parametru můžete přistupovat buď podle názvu, nebo podle jeho indexu na pozici v kolekci.

Zadejte hodnotu, která se má nastavit jako objekt `COleVariant`. Informace o nastavení požadované hodnoty a typu v objektu `COleVariant` naleznete v tématu Třída [COleVariant](../../mfc/reference/colevariant-class.md). Všimněte si, že pokud nevytváříte sadu záznamů UNICODE, objekt `COleVariant` musí být explicitně deklarován standardem ANSI. To lze provést pomocí formuláře [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **(** *lpszSrc* **,** *vtSrc* **)** ve formě konstruktoru s *vtSrc* nastavenou na `VT_BSTRT` (ANSI) nebo pomocí `COleVariant` funkce [SetString](../../mfc/reference/colevariant-class.md#setstring) **(** *lpszSrc* **,** *vtSrc* **)** s *vtSrc* nastavenou na `VT_BSTRT`.

##  <a name="setparamvaluenull"></a>CDaoRecordset:: SetParamValueNull

Chcete-li nastavit parametr na hodnotu null, zavolejte tuto členskou funkci.

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index pole v sadě záznamů pro vyhledávání v indexu založeném na nule.

*lpszName*<br/>
Název pole v sadě záznamů pro vyhledávání podle názvu

### <a name="remarks"></a>Poznámky

C++Hodnota NULL není shodná s hodnotou null, která v terminologii databáze znamená, že "nemá žádnou hodnotu."

##  <a name="setpercentposition"></a>CDaoRecordset:: SetPercentPosition

Zavolejte tuto členskou funkci pro nastavení hodnoty, která změní přibližné umístění aktuálního záznamu v objektu sady záznamů na základě procenta záznamů v sadě záznamů.

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>Parametry

*fPosition*<br/>
Číslo mezi 0 a 100.

### <a name="remarks"></a>Poznámky

Pokud pracujete s dynamickou sadou typu nebo sadou záznamů typu snímky, nejprve naplňte sadu záznamů přesunutím na poslední záznam před voláním `SetPercentPosition`. Pokud zavoláte `SetPercentPosition` před úplným vyplněním sady záznamů, je množství přesunu relativní k počtu záznamů, které jsou k dispozici, jak je uvedeno v hodnotě [GetRecordCount](#getrecordcount). Můžete přejít na poslední záznam voláním `MoveLast`.

Jakmile zavoláte `SetPercentPosition`, bude záznam na přibližné pozici odpovídající této hodnotě aktuální.

> [!NOTE]
>  Volání `SetPercentPosition` pro přesunutí aktuálního záznamu do konkrétního záznamu v sadě záznamů se nedoporučuje. Místo toho zavolejte členskou funkci [SetBookmark](#setbookmark) .

Související informace najdete v tématu "vlastnost PercentPosition" v nápovědě k rozhraní DAO.

##  <a name="update"></a>CDaoRecordset:: Update

Tuto členskou funkci volejte po volání `AddNew` nebo `Edit` členské funkce.

```
virtual void Update();
```

### <a name="remarks"></a>Poznámky

Toto volání je vyžadováno k dokončení operace `AddNew` nebo `Edit`.

`AddNew` i `Edit` připraví upravenou vyrovnávací paměť, ve které jsou přidaná nebo upravená data umístěna k uložení do zdroje dat. `Update` uloží data. Aktualizují se pouze pole označená nebo zjištěná jako změněná.

Pokud zdroj dat podporuje transakce, můžete uskutečnit `Update` volání (a odpovídající `AddNew` nebo volání `Edit`) část transakce.

> [!CAUTION]
> Pokud zavoláte `Update` bez prvního volání `AddNew` nebo `Edit`, `Update` vyvolá `CDaoException`. Pokud voláte `AddNew` nebo `Edit`, je nutné volat `Update` před voláním metody [MoveNext](#movenext) nebo zavřením buď sady záznamů, nebo připojení ke zdroji dat. V opačném případě se vaše změny ztratí bez oznámení.

Když je objekt sady záznamů pessimistically uzamčen ve víceuživatelském prostředí, zůstane záznam uzamčený z času `Edit` bude použit až do dokončení aktualizace. Pokud je sada záznamů optimisticky uzamčena, záznam je uzamčen a porovnán s dříve upraveným záznamem těsně před jeho aktualizací v databázi. Pokud se záznam změnil od chvíle, kdy jste volali `Edit`, operace `Update` se nezdařila a MFC vyvolá výjimku. Můžete změnit režim uzamykání pomocí `SetLockingMode`.

> [!NOTE]
> Optimistické zamykání se vždycky používá u externích formátů databáze, jako je ODBC a Instalovatelné ISAM.

Související informace naleznete v nápovědě k rozhraní DAO v tématech "Metoda AddNew", "CancelUpdate metoda", "Delete Method", "vlastnost LastModified", "metoda aktualizace" a "EditMode Property".

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
