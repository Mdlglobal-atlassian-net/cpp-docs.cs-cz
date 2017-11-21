---
title: "Třída CDaoTableDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
dev_langs: C++
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 51fad5e7890ce311e46c07c9505cb889bf252376
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdaotabledef-class"></a>CDaoTableDef – třída
Představuje definici uložené na základní tabulku nebo připojené tabulky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoTableDef : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Vytvoří **CDaoTableDef** objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoTableDef::Append](#append)|Přidá novou tabulku do databáze.|  
|[CDaoTableDef::CanUpdate](#canupdate)|Vrátí nenulové hodnoty, pokud lze aktualizovat v tabulce (můžete upravit definici polí a vlastností tabulky).|  
|[CDaoTableDef::Close](#close)|Zavře otevřený objekt tabledef.|  
|[CDaoTableDef::Create](#create)|Vytvoří tabulku, která mohou být přidány do databáze pomocí [připojení](#append).|  
|[CDaoTableDef::CreateField](#createfield)|Voláno k vytvoření polí pro tabulku.|  
|[CDaoTableDef::CreateIndex](#createindex)|Voláno k vytvoření indexu pro tabulku.|  
|[CDaoTableDef::DeleteField](#deletefield)|Voláno k odstranění pole z tabulky.|  
|[CDaoTableDef::DeleteIndex](#deleteindex)|Voláno k odstranění indexu z tabulky.|  
|[CDaoTableDef::GetAttributes](#getattributes)|Vrátí hodnotu, která určuje jeden nebo více vlastnosti `CDaoTableDef` objektu.|  
|[CDaoTableDef::GetConnect](#getconnect)|Vrátí hodnotu, která poskytuje informace o zdroji této tabulky.|  
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Vrátí datum a čas základní tabulce základní `CDaoTableDef` se objekt vytvořil.|  
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny provedené v návrhu na základní tabulku.|  
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v tabulce.|  
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Vrátí určité informace o pole v tabulce.|  
|[CDaoTableDef::GetIndexCount](#getindexcount)|Vrátí počet indexů pro tabulku.|  
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Vrátí určité informace o indexy pro tabulku.|  
|[CDaoTableDef::GetName](#getname)|Vrátí uživatelem definovaný název tabulky.|  
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v tabulce.|  
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Vrátí hodnotu, která určuje název připojené tabulky v databázi zdrojové.|  
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Vrátí hodnotu, která ověří data v poli, protože je změnit nebo přidat do tabulky.|  
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Vrátí hodnotu, která určuje text zprávy, která vaše aplikace zobrazí, pokud hodnota objektu pole nesplňuje zadané pravidlo ověřování.|  
|[CDaoTableDef::IsOpen](#isopen)|Vrátí nenulové hodnoty, pokud je tabulka otevřete.|  
|[CDaoTableDef::Open](#open)|Otevře existující tabledef uloženy v databázi je TableDef na kolekci.|  
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informace o připojení pro připojené tabulky.|  
|[CDaoTableDef::SetAttributes](#setattributes)|Nastaví hodnotu, která určuje jeden nebo více vlastnosti `CDaoTableDef` objektu.|  
|[CDaoTableDef::SetConnect](#setconnect)|Nastaví hodnotu, která poskytuje informace o zdroji této tabulky.|  
|[CDaoTableDef::SetName](#setname)|Nastaví název tabulky.|  
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Nastaví hodnotu, která určuje název připojené tabulky v databázi zdrojové.|  
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Nastaví hodnotu, která ověří data v poli, protože je změnit nebo přidat do tabulky.|  
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Nastaví hodnotu, která určuje text zprávy, která vaše aplikace zobrazí, pokud hodnota objektu pole nesplňuje zadané pravidlo ověřování.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Ukazatel rozhraní DAO tabledef objekt základní.|  
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Zdrojové databáze pro tuto tabulku.|  
  
## <a name="remarks"></a>Poznámky  
 Každý databázový objekt DAO udržuje kolekci volat tabledefs –, který obsahuje všechny objekty uložené DAO tabledef.  
  
 Můžete upravit pomocí definice tabulky `CDaoTableDef` objektu. Například můžete:  
  
-   Zkontrolujte pole a index struktura žádné místní, připojené nebo externí tabulky v databázi.  
  
-   Volání `SetConnect` a `SetSourceTableName` členské funkce pro připojené tabulky a použití `RefreshLink` – členská funkce aktualizace připojení k připojené tabulky.  
  
-   Volání `CanUpdate` – členská funkce k určení, pokud můžete upravit definice polí v tabulce.  
  
-   Získání nebo nastavení ověření podmínky pomocí `GetValidationRule` a `SetValidationRule`a `GetValidationText` a `SetValidationText` členské funkce.  
  
-   Použití **otevřete** členskou funkci pro vytvoření tabulky-, dynamická sada nebo typu snímek `CDaoRecordset` objektu.  
  
    > [!NOTE]
    >  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Můžete i nadále přístup ke zdrojům dat ODBC s třídy DAO; třídy DAO obecně nabízí vynikající funkcí, protože jsou specifické pro databázový stroj Microsoft Jet.  
  
### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Použití objektů tabledef pro práci s existující tabulky nebo vytvořit novou tabulku  
  
1.  Ve všech případech se nejprve vytvořit `CDaoTableDef` objekt, poskytuje odkazy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu, ke které patří v tabulce.  
  
2.  Proveďte následující kroky, v závislosti na tom, co chcete použít:  
  
    -   Chcete-li použít stávající uložený tabulky, volejte objekt tabledef [otevřete](#open) – členská funkce, poskytuje název uloženého tabulky.  
  
    -   Chcete-li vytvořit novou tabulku, volejte objekt tabledef [vytvořit](#create) – členská funkce, zadávání názvu tabulky. Volání [CreateField](#createfield) a [CreateIndex](#createindex) do tabulky přidat pole a indexy.  
  
    -   Volání [připojení](#append) k uložení tabulky jejich přidáním do databáze tabledefs – kolekce. **Vytvořit** umístí tabledef do otevřeném stavu, takže po volání **vytvořit** Nevolejte **otevřete**.  
  
        > [!TIP]
        >  Nejjednodušší způsob, jak vytvořit uložené tabulky je jejich vytvoření a uložit je do databáze pomocí aplikace Microsoft Access. Pak můžete otevřít a použít je v kódu MFC.  
  
 Chcete-li použít objekt tabledef vytvořených nebo otevřít, vytvořte a otevřete `CDaoRecordset` objekt, zadáním názvu tabledef s **dbOpenTable** hodnotu `nOpenType` parametr.  
  
 Použití tabledef objekt k vytvoření `CDaoRecordset` můžete obvykle vytvořit nebo otevřít tabledef, jak je popsáno výše, a potom vytvořit objekt sady záznamů předání ukazatel objektu tabledef při volání objektu [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef, kterou předáte musí být v otevřeném stavu. Další informace najdete v tématu třídy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Po dokončení pomocí objektu tabledef volat jeho [Zavřít](../../mfc/reference/cdaorecordset-class.md#close) členské funkce; pak odstraňte objekt tabledef.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="append"></a>CDaoTableDef::Append  
 Volání této funkce člen po zavolání metody [vytvořit](#create) vytvořit nový objekt tabledef uložit tabledef v databázi.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce připojí objekt do databáze tabledefs – kolekce. Při definování není připojením ho můžete použít tabledef jako dočasný objekt, ale pokud chcete ukládat a používat ji, musí volat **připojení**.  
  
> [!NOTE]
>  Pokud se pokusíte připojit nepojmenované tabledef (obsahující hodnotu null nebo prázdný řetězec), MFC vyvolá výjimku.  
  
 Související informace naleznete v tématu "Připojit způsob" v nápovědě rozhraní DAO.  
  
##  <a name="canupdate"></a>CDaoTableDef::CanUpdate  
 Volání této funkce člen můžete určit, zda definice základní tabulce `CDaoTableDef` objektu můžete změnit.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud struktura tabulky (schéma) mohou být změněny (Přidání nebo odstranění polí a indexy), jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení nově vytvořené tabulky základní `CDaoTableDef` objekt můžete aktualizovat a připojené tabulky základní `CDaoTableDef` objekt nelze aktualizovat. A `CDaoTableDef` objekt může být aktualizovat, i když není možné aktualizovat, výsledná sada záznamů.  
  
 Související informace naleznete v tématu "Aktualizovat vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef  
 Vytvoří **CDaoTableDef** objektu.  
  
```  
CDaoTableDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Poté, co vytvořen objekt, je třeba zavolat [vytvořit](#create) nebo [otevřete](#open) – členská funkce. Po dokončení s daným objektem, musí volat jeho [Zavřít](#close) členské funkce a zrušení `CDaoTableDef` objektu.  
  
##  <a name="close"></a>CDaoTableDef::Close  
 Volání této funkce člen zavřete a vydání tabledef objektu.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Obvykle po volání **Zavřít**, pokud byl přidělen s se odstranit objekt tabledef **nové**.  
  
 Můžete volat [otevřete](#open) znovu po volání **Zavřít**. Díky tomu můžete znovu použít objekt tabledef.  
  
 Související informace naleznete v tématu "Zavřít způsob" v nápovědě rozhraní DAO.  
  
##  <a name="create"></a>CDaoTableDef::Create  
 Volání této funkce člen vytvořit novou tabulku uložené.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    long lAttributes = 0,  
    LPCTSTR lpszSrcTable = NULL,  
    LPCTSTR lpszConnect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na řetězec, který obsahuje název tabulky.  
  
 `lAttributes`  
 Hodnota odpovídající vlastností objektu rozhraní tabledef tabulky. Bitový operátor OR můžete použít některý z následujících konstant kombinovat:  
  
|Konstanta|Popis|  
|--------------|-----------------|  
|**dbAttachExclusive**|Pro databáze, které používají databázový stroj Microsoft Jet znamená, že v tabulce je tabulkou aplikace připojené otevřen pro výhradní použití.|  
|**dbAttachSavePWD**|Pro databáze, které používají databázový stroj Microsoft Jet označuje, že jsou uložit ID uživatele a heslo pro připojené tabulku s informacemi o připojení.|  
|**dbSystemObject**|Označuje, že v tabulce je systémová tabulka poskytuje databázový stroj Microsoft Jet.|  
|**dbHiddenObject**|Označuje, že v tabulce je skrytý tabulka poskytuje databázový stroj Microsoft Jet.|  
  
 *lpszSrcTable*  
 Ukazatel na řetězec obsahující název zdrojové tabulky. Ve výchozím nastavení je tato hodnota inicializován jako **NULL**.  
  
 `lpszConnect`  
 Ukazatel na řetězec obsahující výchozí připojovací řetězec. Ve výchozím nastavení je tato hodnota inicializován jako **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Jakmile s názvem tabledef pak můžete volat [připojení](#append) uložení tabledef do databáze tabledefs – kolekce. Po volání **připojení**, je tabledef v otevřeném stavu a slouží k vytvoření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu.  
  
 Související informace naleznete v tématu "CreateTableDef způsob" v nápovědě rozhraní DAO.  
  
##  <a name="createfield"></a>CDaoTableDef::CreateField  
 Volání této funkce člen přidat pole do tabulky.  
  
```  
void CreateField(
    LPCTSTR lpszName,  
    short nType,  
    long lSize,  
    long lAttributes = 0);  
  
void CreateField(CDaoFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na výraz řetězec určující název tohoto pole.  
  
 `nType`  
 Hodnota označující datový typ pole. Toto nastavení může být jedna z těchto hodnot:  
  
|Typ|Velikost (bajty)|Popis|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 bajt|BOOL|  
|**dbByte**|1|BYTE|  
|**dbInteger**|2|int|  
|**dbLong**|4|long|  
|**dbCurrency**|8|Měna ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|float|  
|**dbDouble**|8|double|  
|**dbDate**|8|Datum a čas ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|Dlouhá binární (OLE Object), [CLongBinary](../../mfc/reference/clongbinary-class.md) nebo [CByteArray](../../mfc/reference/cbytearray-class.md)|  
|**dbMemo**|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|  
  
 `lSize`  
 Hodnota, která určuje maximální velikost v bajtech pole obsahující text, nebo pevnou velikost pole, které obsahuje textové nebo číselné hodnoty. `lSize` Parametr je ignorován u všech textových polí.  
  
 `lAttributes`  
 Hodnota vlastnosti pole a které odpovídající lze spojovat pomocí bitové operace OR.  
  
|Konstanta|Popis|  
|--------------|-----------------|  
|**dbFixedField**|Velikost pole vyřešen (výchozí nastavení pro číselné pole).|  
|**dbVariableField**|Velikost pole je proměnná (pouze textová pole).|  
|**dbAutoIncrField**|Hodnota pole pro nové záznamy se automaticky zvýší na jedinečný dlouhé celé číslo, kterou nelze změnit. Podporováno pouze pro Microsoft Jet databázových tabulek.|  
|**dbUpdatableField**|Hodnota pole lze změnit.|  
|**dbDescending**|Toto pole je seřazené v sestupném (Z - A, nebo 100-0) pořadí (platí pouze pro objekt pole v kolekci polí objektu indexu). Pokud vynecháte tento konstanta, pole je seřadit ve vzestupném (A - Z nebo 0 - 100) pořadí (výchozí).|  
  
 `fieldinfo`  
 Odkaz na [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura.  
  
### <a name="remarks"></a>Poznámky  
 A **DAOField** (OLE) objekt se vytvoří a připojí ke kolekci polí **DAOTableDef** objektu (OLE). Kromě toho pro zkoumání vlastnosti objektu jeho použití, můžete také použít `CDaoFieldInfo` vytvořit vstupní parametr k vytvoření nové pole v tabledef. První verze součásti `CreateField` je jednodušší použít, ale pokud chcete jemnějšího ovládání, můžete použít druhá verze `CreateField`, které trvá `CDaoFieldInfo` parametr.  
  
 Pokud používáte verzi `CreateField` , která má `CDaoFieldInfo` parametr, musíte pečlivě nastavit všechny následující členy `CDaoFieldInfo` strukturu:  
  
- **m_strName**  
  
- `m_nType`  
  
- **m_lSize**  
  
- **m_lAttributes**  
  
- **m_bAllowZeroLength**  
  
 Zbývající členy `CDaoFieldInfo` musí být nastavena na **0**, **FALSE**, nebo na prázdný řetězec, podle potřeby pro člena nebo `CDaoException` může dojít.  
  
 Související informace naleznete v tématu "CreateField způsob" v nápovědě rozhraní DAO.  
  
##  <a name="createindex"></a>CDaoTableDef::CreateIndex  
 Volání této funkce můžete přidat do tabulky indexu.  
  
```  
void CreateIndex(CDaoIndexInfo& indexinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `indexinfo`  
 Odkaz na [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktura.  
  
### <a name="remarks"></a>Poznámky  
 Indexy určují pořadí záznamy, které jsou k němu přistupovat z tabulek databáze a zda jsou přijaty duplicitní záznamy. Indexy také poskytnout efektivní přístup k datům.  
  
 Nemáte k vytvoření indexů pro tabulky, ale v tabulkách velký, neindexovaných přístupu konkrétním záznamu nebo vytvoření sady záznamů může trvat dlouhou dobu. Na druhé straně vytváření indexů příliš mnoho zpomaluje aktualizace, připojit a operace odstranění, jako jsou automaticky aktualizovány všechny indexy. Zvažte tyto faktory, jako je rozhodnout, které indexy vytvořit.  
  
 Následující členy `CDaoIndexInfo` musí být nastavena strukturu:  
  
- **m_strName** je nutné zadat název.  
  
- `m_pFieldInfos`Musí odkazovat na pole `CDaoIndexFieldInfo` struktury.  
  
- `m_nFields`Musíte zadat počet polí v poli `CDaoFieldInfo` struktury.  
  
 Zbývající členy je ignorováno Pokud možnost **FALSE**. Kromě toho **m_lDistinctCount** člen se ignoruje při vytváření indexu.  
  
##  <a name="deletefield"></a>CDaoTableDef::DeleteField  
 Volání této funkce člena odebrat pole a nastavit jej jako nedostupné.  
  
```  
void DeleteField(LPCTSTR lpszName);  
void DeleteField(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na řetězcového výrazu, který je název existujícího pole.  
  
 `nIndex`  
 Index v poli v tabulce počítaný od nuly kolekce polí, pro vyhledávání podle indexu.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkci můžete použít na nový objekt, který nebyl se připojí k databázi nebo když [CanUpdate](#canupdate) vrátí nenulovou hodnotu.  
  
 Související informace naleznete v tématu "Odstranit metodu" v nápovědě rozhraní DAO.  
  
##  <a name="deleteindex"></a>CDaoTableDef::DeleteIndex  
 Volání této funkce člen k odstranění indexu v podkladové tabulce.  
  
```  
void DeleteIndex(LPCTSTR lpszName);  
void DeleteIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na řetězcového výrazu, který je název existujícího indexu.  
  
 `nIndex`  
 Index pole objektu indexu v databáze nule tabledefs – kolekce, pro vyhledávání podle indexu.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkci můžete použít na nový objekt, který nebyl se připojí k databázi nebo když [CanUpdate](#canupdate) vrátí nenulovou hodnotu.  
  
 Související informace naleznete v tématu "Odstranit metodu" v nápovědě rozhraní DAO.  
  
##  <a name="getattributes"></a>CDaoTableDef::GetAttributes  
 Pro `CDaoTableDef` objekt, určuje návratovou hodnotu vlastností tabulky reprezentována `CDaoTableDef` objektu a může být součet těchto konstant:  
  
```  
long GetAttributes();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, která určuje jeden nebo více vlastnosti `CDaoTableDef` objektu.  
  
### <a name="remarks"></a>Poznámky  
  
|Konstanta|Popis|  
|--------------|-----------------|  
|**dbAttachExclusive**|Pro databáze, které používají databázový stroj Microsoft Jet znamená, že v tabulce je tabulkou aplikace připojené otevřen pro výhradní použití.|  
|**dbAttachSavePWD**|Pro databáze, které používají databázový stroj Microsoft Jet označuje, že jsou uložit ID uživatele a heslo pro připojené tabulku s informacemi o připojení.|  
|**dbSystemObject**|Označuje, že v tabulce je systémová tabulka poskytuje databázový stroj Microsoft Jet.|  
|**dbHiddenObject**|Označuje, že v tabulce je skrytý tabulka poskytuje databázový stroj Microsoft Jet.|  
|**dbAttachedTable**|Označuje, že v tabulce je připojené tabulky z databáze rozhraní ODBC, jako je například databázový stroj.|  
|**dbAttachedODBC**|Označuje, že v tabulce je připojené tabulky z databáze ODBC, jako je Microsoft SQL Server.|  
  
 Systémová tabulka je vytvořen pro databázový stroj Microsoft Jet obsahující informace o různých interní tabulku.  
  
 Skryté tabulky je tabulka vytvořený pro dočasné použití pro databázový stroj Microsoft Jet.  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="getconnect"></a>CDaoTableDef::GetConnect  
 Volání této funkce člen získat připojovací řetězec pro zdroj dat.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt obsahující typ cesty a databáze pro tabulku.  
  
### <a name="remarks"></a>Poznámky  
 Pro `CDaoTableDef` objekt, který reprezentuje připojené tabulky, `CString` objekt se skládá z jednoho nebo dvou částí (specifikátor typu databáze a cestu k databázi).  
  
 Cesta, jak je znázorněno v následující tabulce je úplná cesta k adresáři obsahující soubory databáze a musí předcházet identifikátor "databáze =". V některých případech (jak s Microsoft Jet a aplikaci Microsoft Excel databáze) konkrétní název souboru je zahrnuta v argumentu cesta databáze.  
  
 V tabulce v [CDaoTableDef::SetConnect](#setconnect) ukazuje typy možné databáze a jejich odpovídající specifikátory databáze a cesty:  
  
 Pro základní tabulky databáze Microsoft Jet specifikátor je prázdný řetězec ("").  
  
 Pokud heslo je vyžadována, ale není zadaný, ovladač ODBC zobrazí čas při prvním přihlášení dialogové okno přístupu tabulky a znovu Pokud připojení je zavřít a znovu otevřít. Pokud má připojené tabulky **dbAttachSavePWD** atribut řádku přihlášení se nezobrazí, když znovu otevřete v tabulce.  
  
 Související informace naleznete v tématu "Připojit vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated  
 Volání této funkce určete datum a čas základní tabulky `CDaoTableDef` se objekt vytvořil.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu obsahující datum a čas vytvoření základní tabulky `CDaoTableDef` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Nastavení data a času jsou odvozené z počítače, na kterém byl vytvořen nebo naposledy aktualizován na základní tabulku. V prostředí s více uživateli uživatelé získávají tato nastavení přímo ze souborového serveru, aby se zabránilo nesrovnalostí; To znamená, musí všichni klienti použít zdroj času "standard", případně z jednoho serveru.  
  
 Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated  
 Volání této funkce určete datum a čas základní tabulky **CDaoTableDef** objekt poslední aktualizace.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu, která obsahuje datum a čas základní tabulky **CDaoTableDef** objekt poslední aktualizace.  
  
### <a name="remarks"></a>Poznámky  
 Nastavení data a času jsou odvozené z počítače, na kterém byl vytvořen nebo naposledy aktualizován na základní tabulku. V prostředí s více uživateli uživatelé získávají tato nastavení přímo ze souborového serveru, aby se zabránilo nesrovnalostí; To znamená, musí všichni klienti použít zdroj času "standard", případně z jednoho serveru.  
  
 Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount  
 Volání této funkce člen načíst počet polí definovaných v tabulce.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet polí v tabulce.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je jeho hodnota 0, nejsou žádné objekty v kolekci.  
  
 Související informace naleznete v tématu "Počet vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo  
 Volání této funkce člen získat různých typů informací o pole definovaná v tabledef.  
  
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
 Index objektu pole ve v tabulce počítaný od nuly kolekce polí, pro vyhledávání podle indexu.  
  
 `fieldinfo`  
 Odkaz na [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o pole, které chcete načíst. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit:  
  
- `AFX_DAO_PRIMARY_INFO`(Výchozí) Název, typ, velikost, atributy. Tuto možnost použijte pro nejrychlejší výkonu.  
  
- `AFX_DAO_SECONDARY_INFO`Primární informace, plus: pořadí pozice, potřeby povolit nulové délky, pořadí řazení, cizí název pole zdroje, zdrojová tabulka  
  
- `AFX_DAO_ALL_INFO`Informace o primární a sekundární plus: ověřovací pravidlo, Text pro ověření, výchozí hodnota  
  
 `lpszName`  
 Ukazatel na název objektu pole pro vyhledávání podle názvu. Název je řetězec s až 64 znaků, který jedinečně názvy pole.  
  
### <a name="remarks"></a>Poznámky  
 Jedna verze funkce umožňuje vyhledat pole podle indexu. Na další verzi umožňuje vyhledat pole podle názvu.  
  
 Popis vrácené informace naleznete v tématu [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popisu `dwInfoOptions`. Pokud budete požadovat informace na jedné úrovni, získáte informace o všech předchozích úrovní.  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount  
 Volání této funkce člen získat počet indexů pro tabulku.  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet indexů pro tabulku.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je jeho hodnota 0, nejsou žádné indexy v kolekci.  
  
 Související informace naleznete v tématu "Počet vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo  
 Volání této funkce člen získat různých typů informací o indexu definované v tabledef.  
  
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
 Číselný index objektu indexu ve v tabulce počítaný od nuly kolekce indexů, pro vyhledávání podle svého umístění v kolekci.  
  
 `indexinfo`  
 Odkaz na [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktura.  
  
 `dwInfoOptions`  
 Možnosti, které určují, které informace o index pro načtení. Dostupné možnosti jsou zde uvedeny společně s co způsobí funkce se má vrátit:  
  
- `AFX_DAO_PRIMARY_INFO`Pole Název pole informace. Tuto možnost použijte pro nejrychlejší výkonu.  
  
- `AFX_DAO_SECONDARY_INFO`Primární informace, plus: primární, jedinečný, clusteru, Ignorovat hodnoty Null, vyžaduje, cizí  
  
- `AFX_DAO_ALL_INFO`Informace o primární a sekundární plus: jednoznačného počtu  
  
 `lpszName`  
 Ukazatel na název indexu objekt, pro vyhledávání podle názvu.  
  
### <a name="remarks"></a>Poznámky  
 Jedna verze funkce umožňuje vyhledat index podle svého umístění v kolekci. Na další verzi umožňuje vyhledat index podle názvu.  
  
 Popis vrácené informace naleznete v tématu [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktura. Tato struktura má členy, které odpovídají položkám informace uvedené výše v popisu `dwInfoOptions`. Pokud budete požadovat informace na jedné úrovni, získáte informace o všech předchozích úrovní.  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="getname"></a>CDaoTableDef::GetName  
 Volání této funkce člen získat název definovaný uživatelem, základní tabulky.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Uživatelem definovaný název pro tabulku.  
  
### <a name="remarks"></a>Poznámky  
 Tento název začíná písmenem a může obsahovat maximálně 64 znaků. Může obsahovat čísla a podtržítka znaků však nemůže obsahovat interpunkční znaménka nebo mezery.  
  
 Související informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="getrecordcount"></a>CDaoTableDef::GetRecordCount  
 Volání této funkce člen a zjistěte, kolik záznamy jsou v `CDaoTableDef` objektu.  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet záznamů v objektu tabledef získat přístup.  
  
### <a name="remarks"></a>Poznámky  
 Volání metody `GetRecordCount` pro typ tabulky `CDaoTableDef` objekt odráží přibližný počet záznamů v tabulce a má vliv okamžitě, jako jsou tabulky záznamů přidat a odstranit. Vrátí zpátky, transakce se zobrazí jako součást počet záznamů, dokud zavoláte [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). A `CDaoTableDef` objekt se žádné záznamy má vlastnost počet záznamů je nastavena na hodnotu 0. Při práci s připojené tabulek nebo databází ODBC `GetRecordCount` vždy vrátí hodnotu -1.  
  
 Související informace naleznete v tématu "%d{RecordCount/ vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName  
 Volání této funkce člen načíst název připojené tabulky ve zdrojové databáze.  
  
```  
CString GetSourceTableName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt, který určuje název zdroje připojené tabulky nebo prázdný řetězec, pokud tabulka nativní data.  
  
### <a name="remarks"></a>Poznámky  
 Připojené tabulky je tabulka v jiné databázi propojené s databází Microsoft Jet. Data pro připojené tabulky zůstávají v externí databáze, kde může být používán jinými aplikacemi.  
  
 Související informace naleznete v tématu "%{sourcetablename/ vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule  
 Volání této funkce člen k načtení ověřovacího pravidla pro tabledef.  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **CString** objekt, který ověří data v poli, protože je změnit nebo přidat do tabulky.  
  
### <a name="remarks"></a>Poznámky  
 Pravidla ověřování se používají ve spojení s operace aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, aktualizace pro tento objekt tabledef musí vyhovovat kritériím předem určený předtím, než se data změní. Pokud tato změna neodpovídá kritéria, výjimku, která obsahuje hodnotu [GetValidationText](#getvalidationtext) je vyvolána výjimka. Pro `CDaoTableDef` objektu, to `CString` připojené tabulky a čtení/zápisu pro základní tabulka jen pro čtení.  
  
 Související informace naleznete v tématu "Vlastnosti Ověřovací pravidlo" v nápovědě rozhraní DAO.  
  
##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText  
 Volání této funkce se načíst řetězec k zobrazení, když uživatel zadá data, která neodpovídá ověřovacího pravidla.  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt, který určuje text, který zobrazí, pokud uživatel zadá data, která neodpovídá ověřovacího pravidla.  
  
### <a name="remarks"></a>Poznámky  
 Pro `CDaoTableDef` objektu, to `CString` připojené tabulky a čtení/zápisu pro základní tabulka jen pro čtení.  
  
 Související informace naleznete v tématu "Vlastnost Ověřovací text" v nápovědě rozhraní DAO.  
  
##  <a name="isopen"></a>CDaoTableDef::IsOpen  
 Volání této funkce člen můžete určit, zda `CDaoTableDef` objektu je aktuálně otevřený.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CDaoTableDef` objekt je otevřené; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase  
 Obsahuje odkazy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu pro tuto tabulku.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef  
 Obsahuje ukazatel na rozhraní OLE pro základní objekt DAO tabledef `CDaoTableDef` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud potřebujete získat přímo přístup k rozhraní DAO, použijte tento ukazatel.  
  
##  <a name="open"></a>CDaoTableDef::Open  
 Volání této funkce člen otevřete tabledef dříve uložené v databázi je TableDef na kolekci.  
  
```  
virtual void Open(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na řetězec, který určuje název tabulky.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink  
 Volání této funkce člen aktualizovat informace o připojení pro připojené tabulku.  
  
```  
void RefreshLink();
```  
  
### <a name="remarks"></a>Poznámky  
 Změnit informace o připojení pro připojené tabulku voláním [SetConnect](#setconnect) na odpovídajícím `CDaoTableDef` objekt a potom pomocí `RefreshLink` – členská funkce Aktualizovat informace o. Při volání `RefreshLink`, vlastnosti připojené tabulky, nebudou změněny.  
  
 Chcete-li vynutit upravenou připojit informace, které začnou platit, všechny otevřené [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekty podle této tabledef musí být uzavřeny.  
  
 Související informace naleznete v tématu "RefreshLink způsob" v nápovědě rozhraní DAO.  
  
##  <a name="setattributes"></a>CDaoTableDef::SetAttributes  
 Nastaví hodnotu, která určuje jeden nebo více vlastnosti `CDaoTableDef` objektu.  
  
```  
void SetAttributes(long lAttributes);
```  
  
### <a name="parameters"></a>Parametry  
 `lAttributes`  
 Vlastností tabulky reprezentována `CDaoTableDef` objektu a může být součet těchto konstant:  
  
|Konstanta|Popis|  
|--------------|-----------------|  
|**dbAttachExclusive**|Pro databáze, které používají databázový stroj Microsoft Jet znamená, že v tabulce je tabulkou aplikace připojené otevřen pro výhradní použití.|  
|**dbAttachSavePWD**|Pro databáze, které používají databázový stroj Microsoft Jet označuje, že jsou uložit ID uživatele a heslo pro připojené tabulku s informacemi o připojení.|  
|**dbSystemObject**|Označuje, že v tabulce je systémová tabulka poskytuje databázový stroj Microsoft Jet.|  
|**dbHiddenObject**|Označuje, že v tabulce je skrytý tabulka poskytuje databázový stroj Microsoft Jet.|  
  
### <a name="remarks"></a>Poznámky  
 Při nastavování několik atributů, můžete je spojit jako součet odpovídající pomocí operátoru bitové operace OR konstanty. Nastavení **dbAttachExclusive** na samostatný tabulku vytváří výjimku. Kombinování následující hodnoty také produktu výjimku:  
  
- **dbAttachExclusive &#124; dbAttachedODBC**  
  
- **dbAttachSavePWD &#124; dbAttachedTable**  
  
 Související informace naleznete v tématu "Vlastnosti Attributes" v nápovědě rozhraní DAO.  
  
##  <a name="setconnect"></a>CDaoTableDef::SetConnect  
 Pro `CDaoTableDef` objekt, který reprezentuje připojené tabulky, objekt řetězce se skládá z jednoho nebo dvou částí (specifikátor typu databáze a cestu k databázi).  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszConnect`  
 Ukazatel na řetězec výraz, který určuje další parametry k předání do rozhraní ODBC nebo instalovat ovladače databází.  
  
### <a name="remarks"></a>Poznámky  
 Cesta, jak je znázorněno v následující tabulce je úplná cesta k adresáři obsahující soubory databáze a musí předcházet identifikátor "databáze =". V některých případech (jak s Microsoft Jet a aplikaci Microsoft Excel databáze) konkrétní název souboru je zahrnuta v argumentu cesta databáze.  
  
> [!NOTE]
>  Nesmí obsahovat prázdné znaky znaménku rovná cesta příkazy ve formě "databáze = jednotka:\\\path". To způsobí výjimku hlášeny a selhání připojení.  
  
 Následující tabulka uvádí typy možné databáze a jejich odpovídající specifikátory databáze a cesty:  
  
|Typ databáze|Specifikátor|Cesta|  
|-------------------|---------------|----------|  
|Databáze pomocí databázový stroj|"[ `database`];"|" `drive`:\\\ *cesta*\\\ *filename*. MDB"|  
|dBASE III|"dBASE III;"|" `drive`:\\\ *cesta*"|  
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *cesta*"|  
|dBASE 5|"dBASE 5.0;"|" `drive`:\\\ *cesta*"|  
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *cesta*"|  
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *cesta*"|  
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *cesta*"|  
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *cesta*\\\ *filename*. XLS"|  
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *cesta*\\\ *filename*. XLS"|  
|Excel 5.0 nebo Excel 95|"Excel 5.0;"|" `drive`:\\\ *cesta*\\\ *filename*. XLS"|  
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *cesta*\ *filename*. XLS"|  
|HTML Import|"HTML Import;"|" `drive`:\\\ *cesta*\ *filename*"|  
|HTML Export|"HTML Export;"|" `drive`:\\\ *cesta*"|  
|Text|"Text;"|"jednotka:\\\path"|  
|ODBC|"ODBC; DATABÁZE = `database`; UID = *uživatele*; PWD = *heslo*; DSN = *datasourcename;* LOGINTIMEOUT = *sekund;*" (To nemusí být úplný připojovací řetězec pro všechny servery, je jenom jako příklad. Je velmi důležité, že nemají mezery mezi parametry.)|Žádné|  
|Exchange|"Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [Profil = *profil*;]<br /><br /> [PWD = *heslo*;]<br /><br /> [DATABÁZI = `database`;] "|*"jednotka*:\\\ *cesta*\\\ *filename*. MDB"|  
  
> [!NOTE]
>  Btrieve již není podporována od DAO 3.5.  
  
 Je nutné použít dvojité zpětné lomítko (\\\\) v připojovacích řetězcích. Pokud jste změnili vlastnosti stávající připojení pomocí `SetConnect`, musíte následně volat [RefreshLink](#refreshlink). Pokud se inicializace vlastnosti připojení pomocí `SetConnect`, budete potřebovat není volání `RefreshLink`, ale měli rozhodnete tak učinit, nejdřív připojit tabledef.  
  
 Pokud heslo je vyžadována, ale není zadaný, ovladač ODBC zobrazí čas při prvním přihlášení dialogové okno přístupu tabulky a znovu Pokud připojení je zavřít a znovu otevřít.  
  
 Můžete nastavit připojovací řetězec pro `CDaoTableDef` tím, že poskytuje zdroj argument pro objekt **vytvořit** – členská funkce. Můžete zkontrolovat nastavení k určení typu, cesta, ID uživatele, heslo nebo zdroje dat ODBC databáze. Další informace naleznete v dokumentaci pro určitý ovladač.  
  
 Související informace naleznete v tématu "Připojit vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="setname"></a>CDaoTableDef::SetName  
 Volání této funkce člen nastavit uživatelem definovaný název pro tabulku.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na řetězec výraz, který určuje název tabulky.  
  
### <a name="remarks"></a>Poznámky  
 Název musí začínat písmenem a může obsahovat maximálně 64 znaků. Může obsahovat čísla a podtržítka znaků však nemůže obsahovat interpunkční znaménka nebo mezery.  
  
 Související informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName  
 Volání této funkce člen a zadejte název připojené tabulky nebo název základní tabulky, na kterém `CDaoTableDef` základě objektu, protože existuje ve původního zdroje dat.  
  
```  
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSrcTableName*  
 Ukazatel na řetězcového výrazu, který určuje název tabulky v externí databáze. Pro základní tabulku, nastavení je prázdný řetězec ("").  
  
### <a name="remarks"></a>Poznámky  
 Pak musí volat [RefreshLink](#refreshlink). Nastavení této vlastnosti je prázdná pro základní tabulky a čtení/zápisu pro připojené tabulku nebo objekt, který není připojen ke kolekci.  
  
 Související informace naleznete v tématu "%{sourcetablename/ vlastnost" v nápovědě rozhraní DAO.  
  
##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule  
 Volání této funkce člen nastavit ověřovací pravidlo pro tabledef.  
  
```  
void SetValidationRule(LPCTSTR lpszValidationRule);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszValidationRule*  
 Ukazatel na řetězcového výrazu, která ověřuje operace.  
  
### <a name="remarks"></a>Poznámky  
 Pravidla ověřování se používají ve spojení s operace aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, aktualizace pro tento objekt tabledef musí vyhovovat kritériím předem určený předtím, než se data změní. Pokud tato změna neodpovídá kritéria, výjimku obsahující text [GetValidationText](#getvalidationtext) se zobrazí.  
  
 Ověření je podporováno pouze u databází, které používají databázový stroj Microsoft Jet. Výraz nelze odkazovat na uživatelem definované funkce domény agregační funkce, agregačních funkcí SQL nebo dotazy. Ověřovací pravidlo pro `CDaoTableDef` objektu se může vztahovat k více polí v objektu.  
  
 Například pro pole s názvem `hire_date` a `termination_date`, může být ověřovací pravidlo:  
  
 [!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]  
  
 Související informace naleznete v tématu "Vlastnosti Ověřovací pravidlo" v nápovědě rozhraní DAO.  
  
##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText  
 Volání této funkce člen nastavit text výjimky pravidla pro ověření `CDaoTableDef` objekt s podkladové základní tabulky, která je podporována pro databázový stroj Microsoft Jet.  
  
```  
void SetValidationText(LPCTSTR lpszValidationText);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszValidationText*  
 Ukazatel na řetězcového výrazu, který určuje text, který zobrazí, pokud zadaná data je neplatný.  
  
### <a name="remarks"></a>Poznámky  
 Nelze nastavit text pro ověření připojené tabulky.  
  
 Související informace naleznete v tématu "Vlastnost Ověřovací text" v nápovědě rozhraní DAO.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
