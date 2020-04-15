---
title: CDaoQueryDefInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368936"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo – struktura

Struktura `CDaoQueryDefInfo` obsahuje informace o querydef objekt udefinovaný pro objekty přístupu k datům (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Jedinečně pojmenuje querydef objektu. Další informace naleznete v tématu "Name Property" v nápovědě dao. Volání [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) načíst tuto vlastnost přímo.

*m_nType*<br/>
Hodnota, která označuje provozní typ querydef objektu. Může jít o následující hodnoty:

- `dbQSelect`Vybrat – dotaz vybere záznamy.

- `dbQAction`Akce – dotaz přesune nebo změní data, ale nevrátí záznamy.

- `dbQCrosstab`Křížová tabule – dotaz vrátí data ve formátu podobném tabulce.

- `dbQDelete`Odstranit – dotaz odstraní sadu zadaných řádků.

- `dbQUpdate`Aktualizace – dotaz změní sadu záznamů.

- `dbQAppend`Připojit – dotaz přidá nové záznamy na konec tabulky nebo dotazu.

- `dbQMakeTable`Vytvořit tabulku – dotaz vytvoří novou tabulku ze sady záznamů.

- `dbQDDL`Definice dat – dotaz ovlivňuje strukturu tabulek nebo jejich částí.

- `dbQSQLPassThrough`Předávací – příkaz SQL je předán přímo do back-endu databáze bez zprostředkujícího zpracování.

- `dbQSetOperation`Sjednocení – dotaz vytvoří objekt sady záznamů typu snímek obsahující data ze všech zadaných záznamů ve dvou nebo více tabulkách s odebráním duplicitních záznamů. Chcete-li zahrnout duplikáty, přidejte klíčové slovo **ALL** v příkazu SQL querydef.

- `dbQSPTBulk`Používá `dbQSQLPassThrough` se k určení dotazu, který nevrací záznamy.

> [!NOTE]
> Chcete-li vytvořit předávací dotaz `dbQSQLPassThrough` SQL, nenastavíte konstantu. To je nastavena automaticky databázový stroj Microsoft Jet při vytváření querydef objektu a nastavení Connect vlastnost.

Další informace naleznete v tématu "Type Property" v nápovědě dao.

*m_dateCreated*<br/>
Datum a čas querydef byl vytvořen. Chcete-li přímo načíst datum, kdy byla querydef vytvořena, zavolejte člennou funkci [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) objektu `CDaoTableDef` přidruženého k tabulce. Další informace naleznete v komentářích níže. Podívejte se také na téma "DateCreated, LastUpdated Properties" v nápovědě DAO.

*m_dateLastUpdated*<br/>
Datum a čas poslední změny provedené querydef. Chcete-li přímo načíst datum poslední aktualizace tabulky, zavolejte člennou funkci [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) v hodnotě querydef. Další informace naleznete v komentářích níže. A podívejte se na téma "DateCreated, LastUpdated Vlastnosti" v DAO nápovědy.

*m_bUpdatable*<br/>
Označuje, zda lze provést změny querydef objektu. Pokud je tato vlastnost TRUE, querydef je aktualizovatelný; v opačném případě tomu tak není. Aktualizovatelné znamená, že definice dotazu objektu querydef může být změněna. Aktualizovatelná vlastnost objektu querydef je nastavena na hodnotu TRUE, pokud lze aktualizovat definici dotazu, i když výsledná sada záznamů není aktualizovatelná. Chcete-li načíst tuto vlastnost přímo, volejte querydef [je CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) člennou funkci. Další informace naleznete v tématu "Aktualizovatelná vlastnost" v nápovědě dao.

*m_bReturnsRecords*<br/>
Označuje, zda předávací dotaz SQL do externí databáze vrací záznamy. Pokud je tato vlastnost TRUE, dotaz vrátí záznamy. Chcete-li přímo načíst tuto vlastnost, zavolejte [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Ne všechny předávací dotazy SQL do externích databází vrátí záznamy. Například příkaz SQL **UPDATE** aktualizuje záznamy bez vrácení záznamů, zatímco příkaz SQL **SELECT** vrací záznamy. Další informace naleznete v tématu "ReturnsRecords Property" v nápovědě dao.

*m_strSQL*<br/>
Příkaz SQL, který definuje dotaz spuštěný objektem querydef. Vlastnost SQL obsahuje příkaz SQL, který určuje, jak jsou záznamy při spuštění dotazu vybírány, seskupeny a uspořádány. Dotaz můžete použít k výběru záznamů, které mají být zahrnuty do objektu sady záznamů typu dynaset nebo snímek. Můžete také definovat hromadné dotazy pro úpravu dat bez vrácení záznamů. Hodnotu této vlastnosti můžete načíst přímo voláním členské funkce [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) querydef.

*m_strConnect*<br/>
Obsahuje informace o zdroji databáze použité v předávacídotaz. Tyto informace mají podobu připojovacího řetězce. Další informace o řetězcích připojení a informace o načtení hodnoty této vlastnosti přímo naleznete v členské funkci [CDaoDatabase::GetConnect.](../../mfc/reference/cdaodatabase-class.md#getconnect)

*m_nODBCTimeout*<br/>
Počet sekund, po které databázový stroj Microsoft Jet čeká, než dojde k chybě vypršení časového limitu při spuštění dotazu v databázi ODBC. Pokud používáte databázi ODBC, například Microsoft SQL Server, může dojít ke zpoždění z důvodu síťového provozu nebo vysoké využití serveru ODBC. Spíše než čekání na dobu neurčitou, můžete určit, jak dlouho motor Microsoft Jet čeká před vyvolá chybu. Výchozí hodnota časového limitu je 60 sekund. Hodnotu této vlastnosti můžete načíst přímo voláním členské funkce [Querydef GetODBCTimeout.](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) Další informace naleznete v tématu "VLASTNOST ODBCTimeout" v nápovědě dao.

## <a name="remarks"></a>Poznámky

Querydef je objekt třídy [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Odkazy na primární, sekundární a všechny výše označují, jak jsou informace vráceny členskou funkcí [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) ve třídě `CDaoDatabase`.

Informace načtené členovou funkcí [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) `CDaoQueryDefInfo` jsou uloženy ve struktuře. Volání `GetQueryDefInfo` databázového objektu, ve jehož kolekci QueryDefs je uložen objekt querydef. `CDaoQueryDefInfo`také definuje `Dump` členská funkce v sestavení ladění. Můžete použít `Dump` k výpisu `CDaoQueryDefInfo` obsahu objektu. Class `CDaoDatabase` také poskytuje členské funkce pro přímý přístup ke `CDaoQueryDefInfo` všem vlastnostem vráceným v `GetQueryDefInfo`objektu, takže pravděpodobně budete muset volat jen zřídka .

Při připojení nové pole nebo parametr objekt u polí nebo parametry kolekce querydef objektu, je vyvolána výjimka, pokud podkladová databáze nepodporuje datový typ zadaný pro nový objekt.

Nastavení data a času jsou odvozeny z počítače, ve kterém querydef byl vytvořen nebo poslední aktualizace. Ve víceuživatelském prostředí by uživatelé měli získat tato nastavení přímo ze souborového serveru pomocí příkazu **net time,** aby se zabránilo nesrovnalostem v nastavení vlastností DateCreated a LastUpdated.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
