---
title: Cdaotabledefinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0563cf930d9722adf175a2b82c1e7788ea3d066a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415821"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo – struktura

`CDaoTableDefInfo` Struktura obsahuje informace o objektu tabledef definovány pro datový přístup k objektům (DAO).

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

*m_strName*<br/>
Objekt tabledef jedinečné názvy. K načtení hodnoty této vlastnosti přímo, volání objektu tabledef [GetName](../../mfc/reference/cdaotabledef-class.md#getname) členskou funkci. Další informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_bUpdatable*<br/>
Určuje, zda můžete provést změny k tabulce. Rychlý způsob, jak zjistit, jestli je aktualizovat tabulku je otevřít `CDaoTableDef` pro tabulku a následně zavolat objekt [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) členskou funkci. `CanUpdate` vždycky vrátí nenulovou hodnotu (TRUE) pro nově vytvořený tabledef objekt a pro objekt připojené tabledef 0 (FALSE). Nový objekt tabledef lze připojit pouze k databázi, pro kterou má aktuální uživatel oprávnění k zápisu. Pokud tabulka obsahuje pouze pole nonupdatable `CanUpdate` vrátí hodnotu 0. Pokud jeden nebo více polí je možné aktualizovat, `CanUpdate` vrátí nenulovou hodnotu. Můžete upravit pouze pole aktualizovat. Další informace naleznete v tématu "Aktualizovat vlastnost" v nápovědě k DAO.

*m_lAttributes*<br/>
Určuje vlastnosti tabulky tabledef objektem. Chcete-li načíst aktuální atributy tabledef, zavolejte jeho [GetAttributes –](../../mfc/reference/cdaotabledef-class.md#getattributes) členskou funkci. Vrácená hodnota může být kombinací těchto dlouhé konstanty (pomocí bitového operátoru OR (**&#124;**) – operátor):

- `dbAttachExclusive` U databází, které používají databázovém stroji Microsoft Jet značí, že v tabulce je otevřen pro výhradní použití připojené tabulky.

- `dbAttachSavePWD` U databází, které používají databázovém stroji Microsoft Jet označuje, že se uloží ID uživatele a heslo pro připojené tabulku s informacemi o připojení.

- `dbSystemObject` Označuje, že systémová tabulka poskytuje databázový stroj Microsoft Jet je tabulka. (Jen pro čtení.)

- `dbHiddenObject` Označuje, že tabulka se skryté tabulky, poskytovaných databázový stroj Microsoft Jet (pro dočasné použití). (Jen pro čtení.)

- `dbAttachedTable` Označuje, že je tabulka připojené tabulky z databáze rozhraní ODBC, jako je databázový stroj.

- `dbAttachedODBC` Označuje, že je tabulka připojené tabulky z databáze ODBC, jako je Microsoft SQL Server.

*m_dateCreated*<br/>
Datum a čas, který byl vytvořen v tabulce. Chcete-li načíst přímo datum vytvoření tabulky, zavolejte [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) členskou funkci `CDaoTableDef` objekt přidružený k tabulce. Další informace naleznete v tématu komentáře níže. Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

*m_dateLastUpdated*<br/>
Datum a čas poslední změny v návrhu v tabulce. Chcete-li načíst přímo datum poslední aktualizace v tabulce, zavolejte [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) členskou funkci `CDaoTableDef` objekt přidružený k tabulce. Další informace naleznete v tématu komentáře níže. Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

*m_strSrcTableName*<br/>
Určuje název připojené tabulky, pokud existuje. Chcete-li přímo načíst název zdrojové tabulky, zavolejte [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) členskou funkci `CDaoTableDef` objekt přidružený k tabulce.

*m_strConnect*<br/>
Poskytuje informace o zdroji otevřenou databázi. Tuto vlastnost můžete zkontrolovat, že volání [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) členskou funkci vaše `CDaoTableDef` objektu. Další informace o připojení řetězců naleznete v tématu `GetConnect`.

*m_strValidationRule*<br/>
Hodnota, která ověřuje data v polích tabledef, protože se změnily nebo přibyly tabulku. Ověření se podporuje jenom pro databáze, které používají databázový stroj Microsoft Jet. Chcete-li načíst přímo ověřovacího pravidla, zavolejte [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) členskou funkci `CDaoTableDef` objekt přidružený k tabulce. Související informace naleznete v tématu "Ověřovací pravidlo vlastnost" v nápovědě k DAO.

*m_strValidationText*<br/>
Hodnota, která určuje text zprávy, která vaše aplikace by měla zobrazí, pokud není splněná ověřovací pravidlo určené vlastností Ověřovací pravidlo. Související informace naleznete v tématu "Ověřovací vlastnost" v nápovědě k DAO.

*m_lRecordCount*<br/>
Počet záznamů v objektu tabledef získat přístup. Nastavení této vlastnosti je jen pro čtení. Přímo načíst počet záznamů, zavolejte [getrecordcount –](../../mfc/reference/cdaotabledef-class.md#getrecordcount) členskou funkci `CDaoTableDef` objektu. V dokumentaci k `GetRecordCount` popisuje dál počet záznamů. Všimněte si, že načítání tohoto počtu může být časově náročná operace. Pokud tabulka obsahuje mnoho záznamů.

## <a name="remarks"></a>Poznámky

Objekt třídy je tabledef [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md). Odkazy na primární, sekundární a všechny výše určit, jak vrácené informace [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) členské funkce ve třídě `CDaoDatabase`.

Načte informace [CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) členská funkce je uložen v `CDaoTableDefInfo` struktury. Volání `GetTableDefInfo` členskou funkci `CDaoDatabase` objekt, v jehož tabledefs – kolekce tabledef objekt se uloží. `CDaoTableDefInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoTableDefInfo` objektu.

Nastavení data a času jsou odvozeny z počítače, na kterém byla vytvořena nebo poslední aktualizace základní tabulka. V prostředí musí uživatelé získají tato nastavení přímo ze souborového serveru, aby nedostatky v DateCreated a nastavení vlastností LastUpdated.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)
