---
title: Cdaoquerydefinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDefInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 930626a2c28009f8f0174069a88a59a12c9059af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418538"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo – struktura

`CDaoQueryDefInfo` Struktura obsahuje informace o objektu querydef definovány pro datový přístup k objektům (DAO).

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
Objekt querydef jedinečné názvy. Další informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO. Volání [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) přímo načíst tuto vlastnost.

*m_nType*<br/>
Hodnota, která určuje typ provozní querydef objektu. Hodnota může být jeden z následujících akcí:

- `dbQSelect` Vyberte – výběru záznamů.

- `dbQAction` Akce – dotaz se přesune nebo změní data ale nevrací záznamy.

- `dbQCrosstab` Křížové – dotaz vrací data v tabulkovém formátu.

- `dbQDelete` Delete – dotaz odstraní sadu zadaných řádků.

- `dbQUpdate` Aktualizace – dotaz se změní sadu záznamů.

- `dbQAppend` Append – dotazu přidá nové záznamy na konec tabulky nebo dotazu.

- `dbQMakeTable` Vytvořit tabulku – dotaz vytvoří novou tabulku ze sady záznamů.

- `dbQDDL` Definice dat – dotaz ovlivní strukturu tabulek nebo jejich části.

- `dbQSQLPassThrough` Předávací – přímo na back-end databáze, bez pokročilého zpracování je předán příkazu jazyka SQL.

- `dbQSetOperation` Union – dotaz vytvoří objekt typ snímku, záznamů obsahující data z všechny zadané záznamy ve dvou nebo více tabulek s duplicitní záznamy, které odebrána. Aby byly tyto duplikáty, přidejte klíčové slovo **všechny** v příkazu SQL querydef.

- `dbQSPTBulk` Použít s `dbQSQLPassThrough` zadat dotaz, který nevrací záznamy.

> [!NOTE]
>  K vytvoření předávací dotaz SQL, nenastavíte `dbQSQLPassThrough` konstantní. To je nastavena automaticky v databázovém stroji Microsoft Jet při vytváření objektu querydef a nastavte vlastnost připojení.

Další informace naleznete v tématu "Vlastnost typu" v nápovědě k DAO.

*m_dateCreated*<br/>
Datum a čas, kdy byl vytvořen querydef. Chcete-li přímo načíst datum vytvoření querydef, zavolejte [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) členskou funkci `CDaoTableDef` objekt přidružený k tabulce. Další informace naleznete v tématu komentáře níže. Také naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

*m_dateLastUpdated*<br/>
Datum a čas poslední změny provedené querydef. Chcete-li načíst přímo datum poslední aktualizace v tabulce, zavolejte [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) členskou funkci querydef. Další informace naleznete v tématu komentáře níže. A najdete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

*m_bUpdatable*<br/>
Určuje, zda můžete provést změny k objektu querydef. Pokud je tato vlastnost hodnotu TRUE, querydef aktualizovatelný; v opačném případě není. Hodnoty znamená, že definice dotazu querydef objektu můžete změnit. Aktualizovat vlastnost objektu querydef je nastavena na hodnotu TRUE Pokud definice dotazu je možné aktualizovat, i v případě, že není výslednou sadu záznamů aktualizovat. Chcete-li tuto vlastnost načíst přímo, zavolejte querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) členskou funkci. Další informace naleznete v tématu "Aktualizovat vlastnost" v nápovědě k DAO.

*m_bReturnsRecords*<br/>
Určuje, zda předávací dotaz SQL k externí databázi vrátí záznamy. Pokud je tato vlastnost hodnotu TRUE, dotaz vrátí záznamy. Chcete-li tuto vlastnost načíst přímo, zavolejte [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Ne všechny předávacích dotazů SQL k externím databázím vrací záznamy. Například SQL **aktualizace** příkaz aktualizuje záznamy bez vrácení záznamy při SQL **vyberte** příkaz vrátí záznamy. Další informace naleznete v tématu "Vrací záznamy vlastnost" v nápovědě k DAO.

*m_strSQL*<br/>
Příkaz SQL, který definuje dotaz proveden querydef objektu. Vlastnost SQL obsahuje příkaz SQL, která určuje, jak jsou vybrány záznamy, seskupených a seřazených při spuštění dotazu. Dotaz můžete použít pro výběr záznamů, které mají být zahrnuty objekt sady záznamů typu dynamická sada nebo snímek. Můžete také definovat dotazy hromadně upravovat data bez vrácení záznamy. Hodnota této vlastnosti můžete načíst přímo pomocí volání querydef [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) členskou funkci.

*m_strConnect*<br/>
Poskytuje informace o zdrojové databáze používaná v předávací dotaz. Tyto informace má formu připojovací řetězec. Další informace o připojení řetězce a informace o načtení hodnoty této vlastnosti přímo, najdete v článku [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) členskou funkci.

*m_nODBCTimeout*<br/>
Počet sekund, po které databázový stroj Microsoft Jet počká, než vypršení časového limitu vyvolá se při spuštění dotazu na databázi rozhraní ODBC. Pokud používáte databázi aplikace rozhraní ODBC, jako je například Microsoft SQL Server, zpožděním může docházet kvůli provoz nebo velmi náročné využití sítě serveru ODBC. Namísto čekání po neomezeně dlouhou, můžete zadat, jak dlouho stroji Microsoft Jet čeká předtím, než dojde k chybě. Výchozí hodnota časového limitu je 60 sekund. Hodnota této vlastnosti můžete načíst přímo pomocí volání querydef [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) členskou funkci. Další informace naleznete v tématu "Odezvy vlastnost" v nápovědě k DAO.

## <a name="remarks"></a>Poznámky

Objekt třídy je querydef [cdaoquerydef –](../../mfc/reference/cdaoquerydef-class.md). Odkazy na primární, sekundární a všechny výše určit, jak vrácené informace [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) členské funkce ve třídě `CDaoDatabase`.

Načte informace [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) členská funkce je uložen v `CDaoQueryDefInfo` struktury. Volání `GetQueryDefInfo` pro databázový objekt, v jehož querydefs – kolekce querydef objekt se uloží. `CDaoQueryDefInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoQueryDefInfo` objektu. Třída `CDaoDatabase` také poskytuje členské funkce pro přímý přístup k všechny vlastnosti vrácené v `CDaoQueryDefInfo` objektu, tedy zřídka pravděpodobně bude nutné zavolat `GetQueryDefInfo`.

Po připojení nové pole nebo objekt parametr do pole nebo parametry kolekce querydef objektu, je vyvolána výjimka, pokud databáze nepodporuje datový typ zadaný pro nový objekt.

Nastavení data a času jsou odvozeny z počítače, na kterém querydef byl vytvořen nebo poslední aktualizace. V prostředí, uživatelé získají nastavení přímo ze souborového serveru pomocí **net čas** příkaz, aby nedostatky v DateCreated a LastUpdated nastavení vlastnosti.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
