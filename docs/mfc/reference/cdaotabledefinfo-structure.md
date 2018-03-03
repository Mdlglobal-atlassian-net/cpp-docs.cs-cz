---
title: "Cdaotabledefinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e949cb0348cb55fcee5a940b5753a5a8197e600b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo – struktura
`CDaoTableDefInfo` Struktura obsahuje informace o objekt tabledef definované pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoTableDefInfo  
{  
    CString m_strName;               // Primary  
    BOOL m_bUpdatable;               // Primary  
    long m_lAttributes;              // Primary  
    COleDateTime m_dateCreated;      // Secondary  
    COleDateTime m_dateLastUpdated;  // Secondary  
    CString m_strSrcTableName;       // Secondary  
    CString m_strConnect;            // Secondary  
    CString m_strValidationRule;     // All  
    CString m_strValidationText;     // All  
    long m_lRecordCount;             // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Objekt tabledef jedinečné názvy. K načtení hodnoty této vlastnosti přímo, volání objektu tabledef [GetName](../../mfc/reference/cdaotabledef-class.md#getname) – členská funkce. Další informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_bUpdatable`  
 Určuje, zda v tabulce můžete provedeny změny. Rychlým způsobem k určení, zda tabulka je v aktualizovatelné je otevřít `CDaoTableDef` objektu pro tabulku a volání objektu [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) – členská funkce. `CanUpdate`vždycky vrátí nenulovou hodnotu (**TRUE**) pro nově vytvořený objekt tabledef objekt a 0 (**FALSE**) připojené tabledef objektu. Nový objekt tabledef lze připojit pouze k databázi, pro kterou má aktuální uživatel oprávnění k zápisu. Pokud tabulka obsahuje pouze pole nonupdatable `CanUpdate` vrátí hodnotu 0. Pokud jeden nebo víc polích je možné aktualizovat, `CanUpdate` vrátí nenulovou hodnotu. Můžete upravit pouze aktualizovat pole. Další informace naleznete v tématu "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
 `m_lAttributes`  
 Určuje vlastnosti reprezentované objektem tabledef tabulky. Chcete-li získat aktuální atributy tabledef, volejte jeho [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) – členská funkce. Hodnota vrácená může být kombinací těchto dlouho konstanty (pomocí bitové operace OR (**&#124;**) operátor):  
  
- **dbAttachExclusive** pro databáze, které používají databázový stroj Microsoft Jet, určuje, v tabulce je otevřen pro výhradní použití připojené tabulka.  
  
- **dbAttachSavePWD** pro databáze, které používají databázový stroj Microsoft Jet, označuje, že ID uživatele a heslo pro připojené tabulku jsou uložit s informacemi o připojení.  
  
- **dbSystemObject** označuje v tabulce je systémová tabulka poskytuje databázový stroj Microsoft Jet. (Jen pro čtení.)  
  
- **dbHiddenObject** označuje v tabulce je skrytý tabulka poskytuje databázový stroj Microsoft Jet (pro dočasné použití). (Jen pro čtení.)  
  
- **dbAttachedTable** označuje připojené tabulky z databáze rozhraní ODBC, jako je například databázový stroj je v tabulce.  
  
- **dbAttachedODBC** označuje připojené tabulky z databáze ODBC, jako je Microsoft SQL Server je v tabulce.  
  
 `m_dateCreated`  
 Datum a čas, kdy byl vytvořen v tabulce. Chcete-li přímo získat datum vytvoření tabulky, volejte [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) členské funkce `CDaoTableDef` objekt přidružený k tabulce. Další informace naleznete v tématu komentáře níže. Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
 `m_dateLastUpdated`  
 Datum a čas poslední změny provedené v návrhu tabulky. Chcete-li načíst přímo datum poslední aktualizace v tabulce, volejte [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) členské funkce `CDaoTableDef` objekt přidružený k tabulce. Další informace naleznete v tématu komentáře níže. Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
 *m_strSrcTableName*  
 Určuje název připojené tabulky, pokud existuje. Chcete-li načíst přímo názvu zdrojové tabulky, volejte [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) členské funkce `CDaoTableDef` objekt přidružený k tabulce.  
  
 `m_strConnect`  
 Poskytuje informace o zdroji otevřenou databázi. Tuto vlastnost můžete zkontrolovat pomocí volání [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) členské funkce vaší `CDaoTableDef` objektu. Další informace o připojení řetězce naleznete v tématu `GetConnect`.  
  
 `m_strValidationRule`  
 Hodnota, která ověří data v tabledef pole, jako jsou změnit nebo přidat do tabulky. Ověření je podporováno pouze u databází, které používají databázový stroj Microsoft Jet. Chcete-li načíst přímo ověřovací pravidlo, volejte [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) členské funkce `CDaoTableDef` objekt přidružený k tabulce. Související informace naleznete v tématu "Vlastnosti Ověřovací pravidlo" v nápovědě rozhraní DAO.  
  
 `m_strValidationText`  
 Hodnota, která určuje text zprávy, který vaše aplikace by měl zobrazit, pokud není splněna ověřovací pravidlo určeného vlastností Ověřovací pravidlo. Související informace naleznete v tématu "Vlastnost Ověřovací text" v nápovědě rozhraní DAO.  
  
 *m_lRecordCount*  
 Počet záznamů v objektu tabledef získat přístup. Nastavení této vlastnosti je jen pro čtení. Chcete-li načíst přímo počet záznamů, volejte [getrecordcount –](../../mfc/reference/cdaotabledef-class.md#getrecordcount) členské funkce `CDaoTableDef` objektu. V dokumentaci k `GetRecordCount` popisuje další počet záznamů. Všimněte si, že načítání tento počet může být časově náročná operace Pokud tabulka obsahuje mnoho záznamů.  
  
## <a name="remarks"></a>Poznámky  
 Je třída objektu objekt tabledef [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Odkazy na primární, sekundární a všechny výše označuje, jak je vrácené informace [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) členské funkce ve třídě `CDaoDatabase`.  
  
 Načte informace [CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) – členská funkce je uložen v `CDaoTableDefInfo` struktura. Volání `GetTableDefInfo` členské funkce `CDaoDatabase` objektu, v jehož tabledefs – kolekce tabledef objekt se uloží. `CDaoTableDefInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoTableDefInfo` objektu.  
  
 Nastavení data a času jsou odvozené z počítače, na kterém byl vytvořen nebo naposledy aktualizován na základní tabulku. V prostředí musí uživatelé získávají těchto nastavení přímo ze souborového serveru, aby se zabránilo nesrovnalostí v DateCreated a LastUpdated nastavení vlastností.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
