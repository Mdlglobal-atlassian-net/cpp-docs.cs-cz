---
title: "Cdaoquerydefinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoQueryDefInfo
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e476fd8e95b48b59bbb3bae41d9ad84829ca8fa9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo – struktura
`CDaoQueryDefInfo` Struktura obsahuje informace o objektu querydef definované pro přístup k objektům dat (DAO).  
  
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
 `m_strName`  
 Objekt querydef jedinečné názvy. Další informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO. Volání [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) přímo načíst tuto vlastnost.  
  
 `m_nType`  
 Hodnota, která označuje provozní typ objektu querydef. Hodnota může být jeden z následujících akcí:  
  
- **dbQSelect** vyberte – výběru záznamů.  
  
- **dbQAction** akce – dotaz přesune nebo změny dat ale nevrací záznamy.  
  
- **dbQCrosstab** sestavě křížových tabulek – dotaz vrací data v tabulkovém formátu.  
  
- **dbQDelete** odstranit – dotaz odstraní sadu zadaných řádků.  
  
- **dbQUpdate** aktualizace – dotaz se změní sadu záznamů.  
  
- **dbQAppend** připojení – dotaz přidá nové záznamy na konec tabulky nebo dotazu.  
  
- **dbQMakeTable** vytvářecí – dotaz vytvoří novou tabulku ze sady záznamů.  
  
- **dbQDDL** definiční – struktura tabulky nebo jejich části ovlivňuje dotazu.  
  
- **dbQSQLPassThrough** průchozí – příkaz jazyka SQL je předán přímo na back-end databáze, bez zprostředkující zpracování.  
  
- **dbQSetOperation** Union – dotaz vytvoří sada záznamů typu snímek objekt obsahující data z všechny zadané záznamy v dva nebo více tabulek s duplicitní záznamy odebrat. Chcete-li zahrnout duplicitní hodnoty, přidejte klíčové slovo **všechny** v příkazu SQL querydef.  
  
- **dbQSPTBulk** použít s **dbQSQLPassThrough** zadat dotaz, který nevrací záznamy.  
  
> [!NOTE]
>  Pokud chcete vytvořit předávací dotaz SQL, kterou nenastavíte **dbQSQLPassThrough** konstantní. Je nastavena automaticky pro databázový stroj Microsoft Jet při vytváření objektu querydef a nastavte vlastnost připojení.  
  
 Další informace naleznete v tématu "Vlastnost typu" v nápovědě rozhraní DAO.  
  
 `m_dateCreated`  
 Datum a čas, kdy byl vytvořen querydef. Chcete-li načíst přímo datum, byl vytvořen querydef, volejte [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) členské funkce `CDaoTableDef` objekt přidružený k tabulce. Další informace naleznete v tématu komentáře níže. Také naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_dateLastUpdated`  
 Datum a čas poslední změny provedené querydef. Chcete-li načíst přímo datum poslední aktualizace v tabulce, volejte [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) – členská funkce querydef. Další informace naleznete v tématu komentáře níže. A naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_bUpdatable`  
 Určuje, zda objekt querydef můžete provedeny změny. Pokud je tato vlastnost **TRUE**querydef je aktualizovat; jinak, není. Možností aktualizace znamená, že objekt querydef definice dotazu lze změnit. Aktualizovatelné objektu querydef je nastavena na **TRUE** Pokud definice dotazu lze aktualizovat, i když není možné aktualizovat, výsledná sada záznamů. Tato vlastnost načíst přímo, volání querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) – členská funkce. Další informace naleznete v tématu "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
 *m_bReturnsRecords*  
 Určuje, zda předávací dotaz SQL na externí databáze vrátí záznamy. Pokud je tato vlastnost **TRUE**, dotaz vrátí záznamy. Chcete-li tuto vlastnost načíst přímo, volejte [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Ne všechny předávací dotazy SQL k externím databázím vracet záznamy. Například SQL **aktualizace** příkaz aktualizují záznamy bez vrácení záznamů při SQL **vyberte** příkaz vrátit záznamy. Další informace naleznete v tématu "Vlastnost vrací záznamy" v nápovědě rozhraní DAO.  
  
 *m_strSQL*  
 Příkaz jazyka SQL, který definuje dotaz provedený objektu querydef. Vlastnost SQL obsahuje příkaz jazyka SQL, která určuje, jak jsou vybrány záznamy, seskupené a seřazené při spuštění dotazu. Dotaz můžete použít k výběru záznamy mají být zahrnuty v objektu dynamické nebo snímku sady záznamů. Můžete také definovat dotazy hromadnou úpravou dat bez vrácení záznamů. Hodnota této vlastnosti můžete načíst přímo voláním querydef [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) – členská funkce.  
  
 `m_strConnect`  
 Poskytuje informace o zdroji této databáze používaná v předávací dotaz. Tyto informace má podobu tohoto řetězce. Další informace o připojení řetězce a informace o načtení hodnota této vlastnosti přímo najdete v tématu [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) – členská funkce.  
  
 *m_nODBCTimeout*  
 Počet sekund, databázového stroje Microsoft Jet čeká, než vypršení časového limitu nastane při spuštění dotazu v databázi ODBC. Pokud používáte databázi aplikace rozhraní ODBC, jako je Microsoft SQL Server, může být zpoždění kvůli komunikaci nebo nadměrnému využití sítě serveru ODBC. Místo čekání po neomezeně, můžete určit, jak dlouho stroje Microsoft Jet čeká, než vyvolá chybu. Výchozí hodnota časového limitu je 60 sekund. Hodnota této vlastnosti můžete načíst přímo voláním querydef [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) – členská funkce. Další informace naleznete v tématu "Odezvy vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="remarks"></a>Poznámky  
 Je třída objektu querydef [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Odkazy na primární, sekundární a všechny výše označuje, jak je vrácené informace [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) členské funkce ve třídě `CDaoDatabase`.  
  
 Načte informace [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) – členská funkce je uložen v `CDaoQueryDefInfo` struktura. Volání `GetQueryDefInfo` pro objekt databáze, v jehož querydefs – kolekce querydef objekt se uloží. `CDaoQueryDefInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoQueryDefInfo` objektu. Třída `CDaoDatabase` také poskytuje členské funkce pro přímý přístup k všechny vlastnosti, vrátí se v `CDaoQueryDefInfo` objektu, takže bude pravděpodobně málokdy potřeba volat `GetQueryDefInfo`.  
  
 Když přidáte nové pole nebo objekt parametr kolekci polí nebo parametry objektu querydef, je vyvolána výjimka, pokud základní databáze nepodporuje datový typ zadaný pro nový objekt.  
  
 Nastavení data a času jsou odvozené z počítače, na kterém querydef vytvořená nebo poslední aktualizace. V prostředí, musí uživatelé získají tato nastavení přímo ze souborového serveru pomocí **net čas** příkaz, aby se zabránilo nesrovnalostí v nastavení vlastností DateCreated a LastUpdated.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
