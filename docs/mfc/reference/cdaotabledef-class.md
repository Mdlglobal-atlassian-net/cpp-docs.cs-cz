---
title: CDaoTableDef – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883863"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef – třída

Představuje uloženou definici základní tabulky nebo připojené tabulky.

## <a name="syntax"></a>Syntaxe

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Vytvoří objekt `CDaoTableDef`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef:: Append](#append)|Přidá novou tabulku do databáze.|
|[CDaoTableDef:: CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud je možné tabulku aktualizovat (můžete upravit definici polí nebo vlastností tabulky).|
|[CDaoTableDef:: Close](#close)|Zavře otevřený tabledef.|
|[CDaoTableDef:: Create](#create)|Vytvoří tabulku, kterou lze přidat do databáze pomocí [Append](#append).|
|[CDaoTableDef::CreateField](#createfield)|Volá se, aby se vytvořilo pole pro tabulku.|
|[CDaoTableDef::CreateIndex](#createindex)|Volá se, aby se vytvořil index pro tabulku.|
|[CDaoTableDef::D eleteField](#deletefield)|Volá se, aby se odstranilo pole z tabulky.|
|[CDaoTableDef::D eleteIndex](#deleteindex)|Volá se, aby se odstranil index z tabulky.|
|[CDaoTableDef:: Get– atributy](#getattributes)|Vrací hodnotu, která označuje jednu nebo více vlastností objektu `CDaoTableDef`.|
|[CDaoTableDef:: GetConnect](#getconnect)|Vrátí hodnotu, která poskytuje informace o zdroji tabulky.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Vrátí datum a čas, kdy byla vytvořena základní tabulka s podkladovým objektem `CDaoTableDef`.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny provedené v návrhu základní tabulky.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v tabulce.|
|[CDaoTableDef:: GetFieldInfo](#getfieldinfo)|Vrátí konkrétní druhy informací o polích v tabulce.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Vrátí počet indexů pro tabulku.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Vrátí konkrétní druhy informací o indexech pro tabulku.|
|[CDaoTableDef:: GetName](#getname)|Vrátí uživatelsky definovaný název tabulky.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v tabulce.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Vrátí hodnotu, která určuje název připojené tabulky ve zdrojové databázi.|
|[CDaoTableDef:: getověřovací pravidlo](#getvalidationrule)|Vrátí hodnotu, která ověřuje data v poli, jak je změněno nebo přidáno do tabulky.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Vrátí hodnotu, která určuje text zprávy, kterou aplikace zobrazuje, pokud hodnota objektu Field nevyhovuje zadanému ověřovacímu pravidlu.|
|[CDaoTableDef:: Open](#isopen)|Vrátí nenulovou hodnotu, pokud je tabulka otevřená.|
|[CDaoTableDef:: Open](#open)|Otevře existující tabledef uložený v kolekci TableDef's databáze.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informace o připojení pro připojenou tabulku.|
|[CDaoTableDef:: SetAttributes](#setattributes)|Nastaví hodnotu, která označuje jednu nebo více vlastností objektu `CDaoTableDef`.|
|[CDaoTableDef::SetConnect](#setconnect)|Nastaví hodnotu, která poskytuje informace o zdroji tabulky.|
|[CDaoTableDef::SetName](#setname)|Nastaví název tabulky.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Nastaví hodnotu, která určuje název připojené tabulky ve zdrojové databázi.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Nastaví hodnotu, která ověří data v poli, jak je změněno nebo přidáno do tabulky.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Nastaví hodnotu, která určuje text zprávy, kterou aplikace zobrazuje, pokud hodnota objektu Field nevyhovuje zadanému ověřovacímu pravidlu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef:: m_pDAOTableDef](#m_pdaotabledef)|Ukazatel na rozhraní DAO podkladový objekt tabledef.|
|[CDaoTableDef:: m_pDatabase](#m_pdatabase)|Zdrojová databáze pro tuto tabulku|

## <a name="remarks"></a>Poznámky

Každý objekt databáze rozhraní DAO udržuje kolekci s názvem TableDefs, která obsahuje všechny uložené objekty DAO tabledef.

S definicí tabulky pracujete pomocí objektu `CDaoTableDef`. Můžete například provést následující věci:

- Prověřte strukturu polí a indexů jakékoli místní, připojené nebo externí tabulky v databázi.

- Pro připojené tabulky zavolejte členské funkce `SetConnect` a `SetSourceTableName` a pomocí členské funkce `RefreshLink` aktualizujte připojení k připojeným tabulkám.

- Zavolejte členskou funkci `CanUpdate`, abyste zjistili, jestli můžete upravovat definice polí v tabulce.

- Získat nebo nastavit podmínky ověřování pomocí `GetValidationRule` a `SetValidationRule`a členských funkcí `GetValidationText` a `SetValidationText`.

- Pomocí `Open` členské funkce můžete vytvořit objekt `CDaoRecordset` typu tabulka-, sada nebo snímek.

    > [!NOTE]
    >  Databázové třídy DAO se liší od databázových tříd knihovny MFC založených na rozhraní ODBC (Open Database Connectivity). Všechny názvy databázových tříd DAO mají předponu "CDao". Ke zdrojům dat rozhraní ODBC můžete přistupovat i s třídami DAO; třídy DAO obecně nabízejí nadřazené možnosti, protože jsou specifické pro databázový stroj Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Použití objektů tabledef pro práci s existující tabulkou nebo pro vytvoření nové tabulky

1. Ve všech případech nejprve Sestavte objekt `CDaoTableDef` a poskytněte ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) , ke kterému tabulka patří.

1. Pak proveďte následující postup v závislosti na tom, co chcete:

   - Chcete-li použít existující uloženou tabulku, zavolejte na [otevřené](#open) členské funkce objektu TableDef a zadejte název uložené tabulky.

   - Chcete-li vytvořit novou tabulku, zavolejte funkci [Create](#create) member objektu TableDef a zadejte název tabulky. Chcete-li přidat pole a indexy do tabulky, zavolejte [CreateField](#createfield) a [CreateIndex](#createindex) .

   - Voláním [Append](#append) uložte tabulku tím, že ji připojíte do kolekce TableDefs databáze. `Create` vloží tabledef do otevřeného stavu, takže po volání `Create` nebudete volat `Open`.

        > [!TIP]
        >  Nejjednodušší způsob, jak vytvořit uložené tabulky, je vytvořit je a uložit je do databáze pomocí Microsoft Accessu. Pak je můžete otevřít a použít ve svém kódu knihovny MFC.

Chcete-li použít objekt tabledef, který jste otevřeli nebo vytvořili, vytvořte a otevřete objekt `CDaoRecordset` a zadejte název tabledef s hodnotou `dbOpenTable` v parametru *nOpenType* .

Chcete-li použít objekt tabledef k vytvoření objektu `CDaoRecordset`, obvykle je třeba vytvořit nebo otevřít tabledef, jak je popsáno výše, potom sestavit objekt sady záznamů a předat ukazatel na objekt tabledef při volání [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef, který předáte, musí být v otevřeném stavu. Další informace najdete v tématu Třída [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Po dokončení použití objektu tabledef zavolejte jeho členskou funkci [Close](../../mfc/reference/cdaorecordset-class.md#close) ; pak zničí objekt tabledef.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="append"></a>CDaoTableDef:: Append

Tuto členskou funkci zavolejte po volání metody [Create](#create) k vytvoření nového objektu tabledef k uložení tabledef v databázi.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

Funkce připojí objekt k kolekci TableDefs databáze. Tabledef můžete použít jako dočasný objekt a současně ho definovat tak, že ho nepřipojíte, ale pokud ho chcete uložit a používat, musíte volat `Append`.

> [!NOTE]
>  Pokud se pokusíte připojit nepojmenovaný tabledef (obsahující null nebo prázdný řetězec), knihovna MFC vyvolá výjimku.

Související informace naleznete v tématu "připojit metodu" v nápovědě k rozhraní DAO.

##  <a name="canupdate"></a>CDaoTableDef:: CanUpdate

Voláním této členské funkce určíte, zda lze změnit definici tabulky podkladového objektu `CDaoTableDef`.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je možné upravit strukturu tabulky (schématu) (Přidat nebo odstranit pole a indexy), jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se dá aktualizovat nově vytvořená tabulka s podkladovým objektem `CDaoTableDef` a připojenou tabulkou, která je základem `CDaoTableDef` objektu, nejde aktualizovat. Objekt `CDaoTableDef` může být aktualizovatelný, a to i v případě, že výsledná sada záznamů není aktualizovatelná.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "Aktualizovatelná vlastnost".

##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Vytvoří objekt `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Poznámky

Po sestavení objektu je nutné zavolat členskou funkci [Create](#create) nebo [Open](#open) . Po dokončení objektu musíte zavolat jeho členskou funkci [Close](#close) a zničit objekt `CDaoTableDef`.

##  <a name="close"></a>CDaoTableDef:: Close

Chcete-li zavřít a uvolnit objekt tabledef, zavolejte tuto členskou funkci.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Obvykle po volání `Close`odstraníte objekt tabledef, pokud byl přidělen s **novým**.

Po volání `Close`můžete zavolat [otevřít](#open) znovu. To umožňuje znovu použít objekt tabledef.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "Close Method".

##  <a name="create"></a>CDaoTableDef:: Create

Chcete-li vytvořit novou uloženou tabulku, zavolejte tuto členskou funkci.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který obsahuje název tabulky.

*lAttributes*<br/>
Hodnota odpovídající charakteristikám tabulky reprezentované objektem tabledef. Můžete použít bitový operátor or ke kombinování libovolné z následujících konstant:

|Trvalé|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|U databází, které používají databázový stroj Microsoft Jet, je tabulka připojená tabulka otevřená pro výhradní použití.|
|`dbAttachSavePWD`|U databází, které používají databázový stroj Microsoft Jet, se zobrazí informace o tom, že ID uživatele a heslo pro připojenou tabulku jsou uloženy spolu s informacemi o připojení.|
|`dbSystemObject`|Určuje, že tabulka je systémová tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbHiddenObject`|Určuje, že tabulka je skrytá tabulka poskytovaná databázovým strojem Microsoft Jet.|

*lpszSrcTable*<br/>
Ukazatel na řetězec obsahující název zdrojové tabulky. Ve výchozím nastavení je tato hodnota inicializována jako NULL.

*lpszConnect*<br/>
Ukazatel na řetězec obsahující výchozí připojovací řetězec. Ve výchozím nastavení je tato hodnota inicializována jako NULL.

### <a name="remarks"></a>Poznámky

Jakmile budete mít název tabledef, můžete zavolat příkaz [Append](#append) a uložit tabledef v kolekci TableDefs databáze. Po volání `Append`je tabledef v otevřeném stavu a můžete ho použít k vytvoření objektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

Související informace naleznete v tématu "metoda CreateTableDef" v nápovědě k rozhraní DAO.

##  <a name="createfield"></a>CDaoTableDef::CreateField

Chcete-li přidat pole do tabulky, zavolejte tuto členskou funkci.

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězcový výraz určující název tohoto pole.

*Noznámení*<br/>
Hodnota, která určuje datový typ pole. Nastavení může být jedna z těchto hodnot:

|Typ|Velikost (bajty)|Popis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|LOGICK|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Měna ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Datum a čas ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objekt OLE), [CLongBinary –](../../mfc/reference/clongbinary-class.md) nebo [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Hodnota, která určuje maximální velikost (v bajtech) pole obsahujícího text nebo pevnou velikost pole, které obsahuje textové nebo číselné hodnoty. Parametr *lSize* je ignorován pro všechna pole kromě textu.

*lAttributes*<br/>
Hodnota odpovídající vlastnostem pole a kterou lze kombinovat pomocí bitového operátoru OR.

|Trvalé|Popis|
|--------------|-----------------|
|`dbFixedField`|Velikost pole je pevná (výchozí pro číselná pole).|
|`dbVariableField`|Velikost pole je proměnná (pouze textová pole).|
|`dbAutoIncrField`|Hodnota pole pro nové záznamy se automaticky zvýší na jedinečné dlouhé celé číslo, které nelze změnit. Podporováno pouze pro databázové tabulky Microsoft Jet.|
|`dbUpdatableField`|Hodnota pole může být změněna.|
|`dbDescending`|Pole je seřazeno sestupně (Z-A nebo 100-0) pořadí (platí pouze pro objekt pole v kolekci pole objektu index). Pokud tuto konstantu vynecháte, pole se seřadí ve vzestupném pořadí (A-Z nebo 0-100) (výchozí).|

*FieldInfo*<br/>
Odkaz na strukturu [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) .

### <a name="remarks"></a>Poznámky

Objekt `DAOField` (OLE) je vytvořen a připojen ke kolekci polí objektu `DAOTableDef` (OLE). Kromě jejího použití pro zkoumání vlastností objektu můžete také použít `CDaoFieldInfo` k vytvoření vstupního parametru pro vytváření nových polí v tabledef. První verze `CreateField` se jednodušší používat, ale pokud chcete přesnější řízení, můžete použít druhou verzi `CreateField`, která přebírá `CDaoFieldInfo` parametr.

Pokud používáte verzi `CreateField`, která přebírá `CDaoFieldInfo` parametr, musíte pečlivě nastavit všechny následující členy struktury `CDaoFieldInfo`:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Zbývající členové `CDaoFieldInfo` by měli být nastaveni na **hodnotu 0**, false nebo prázdný řetězec, jak je to vhodné pro člena, nebo k `CDaoException` může dojít.

Související informace naleznete v tématu "metoda CreateField" v nápovědě k rozhraní DAO.

##  <a name="createindex"></a>CDaoTableDef::CreateIndex

Voláním této funkce přidáte index do tabulky.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parametry

*indexinfo*<br/>
Odkaz na strukturu [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) .

### <a name="remarks"></a>Poznámky

Indexy určují pořadí záznamů, které jsou dostupné z databázových tabulek, a to, jestli se mají Povolit duplicitní záznamy. Indexy také poskytují efektivní přístup k datům.

Nemusíte vytvářet indexy pro tabulky, ale v rozsáhlých, neindexovaných tabulkách, přístup k určitému záznamu nebo vytvoření sady záznamů může trvat dlouhou dobu. Na druhé straně vytváření příliš velkého počtu indexů zpomaluje operace aktualizace, připojení a odstranění, protože se automaticky aktualizují všechny indexy. Při rozhodování o tom, které indexy se mají vytvořit, vezměte v úvahu tyto faktory.

Musí být nastaveni následující členové `CDaoIndexInfo` struktury:

- `m_strName` je třeba zadat název.

- `m_pFieldInfos` musí odkazovat na pole `CDaoIndexFieldInfo` struktury.

- `m_nFields` musí určovat počet polí v poli `CDaoFieldInfo` struktury.

Zbývající členové budou ignorováni, pokud je nastavena hodnota FALSE. Kromě toho je člen `m_lDistinctCount` ignorován během vytváření indexu.

##  <a name="deletefield"></a>CDaoTableDef::D eleteField

Chcete-li odebrat pole a nepřístupný, zavolejte tuto členskou funkci.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězcový výraz, který je název existujícího pole.

*nIndex*<br/>
Index pole v kolekci polí založených na nule pro vyhledávání podle indexu

### <a name="remarks"></a>Poznámky

Tuto členskou funkci můžete použít pro nový objekt, který nebyl přidán do databáze nebo když funkce [CanUpdate](#canupdate) vrátí nenulovou hodnotu.

Související informace naleznete v tématu "odstranění metody" v nápovědě rozhraní DAO.

##  <a name="deleteindex"></a>CDaoTableDef::D eleteIndex

Chcete-li odstranit index v podkladové tabulce, zavolejte tuto členskou funkci.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězcový výraz, který je názvem existujícího indexu.

*nIndex*<br/>
Index pole objektu index v kolekci TableDefs založené na nule pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci můžete použít na nový objekt, který se nepřipojil k databázi, nebo když funkce [CanUpdate](#canupdate) vrátí nenulovou hodnotu.

Související informace naleznete v tématu "odstranění metody" v nápovědě rozhraní DAO.

##  <a name="getattributes"></a>CDaoTableDef:: Get– atributy

V případě objektu `CDaoTableDef` vrátí návratová hodnota vlastnosti tabulky reprezentované objektem `CDaoTableDef` a může se jednat o součet těchto konstant:

```
long GetAttributes();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu, která označuje jednu nebo více vlastností objektu `CDaoTableDef`.

### <a name="remarks"></a>Poznámky

|Trvalé|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|U databází, které používají databázový stroj Microsoft Jet, je tabulka připojená tabulka otevřená pro výhradní použití.|
|`dbAttachSavePWD`|U databází, které používají databázový stroj Microsoft Jet, se zobrazí informace o tom, že ID uživatele a heslo pro připojenou tabulku jsou uloženy spolu s informacemi o připojení.|
|`dbSystemObject`|Určuje, že tabulka je systémová tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbHiddenObject`|Určuje, že tabulka je skrytá tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbAttachedTable`|Určuje, že tabulka je připojená tabulka z jiné databáze než ODBC, jako je například databáze Paradox.|
|`dbAttachedODBC`|Určuje, že tabulka je připojená tabulka z databáze rozhraní ODBC, například Microsoft SQL Server.|

Systémová tabulka je tabulka vytvořená databázovým strojem Microsoft Jet, která obsahuje různé interní informace.

Skrytá tabulka je tabulka vytvořená pro dočasné použití databázovým strojem Microsoft Jet.

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="getconnect"></a>CDaoTableDef:: GetConnect

Zavolejte tuto členskou funkci pro získání připojovacího řetězce pro zdroj dat.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující cestu a typ databáze pro tabulku.

### <a name="remarks"></a>Poznámky

Pro objekt `CDaoTableDef`, který představuje připojenou tabulku, se objekt `CString` skládá z jedné nebo dvou částí (specifikátor typu databáze a cesta k databázi).

Cesta uvedená v následující tabulce je úplná cesta pro adresář obsahující soubory databáze a před ní musí být uveden identifikátor "DATABASE =". V některých případech (stejně jako u databází Microsoft Jet a Microsoft Excel) je do argumentu cesta databáze zahrnut konkrétní název souboru.

Tabulka v [CDaoTableDef:: SetConnect](#setconnect) zobrazuje možné typy databází a jejich odpovídající specifikátory databáze a cesty:

Pro základní tabulky databáze Microsoft Jet je specifikátorem prázdný řetězec ("").

Pokud je vyžadováno heslo, ale není k dispozici, zobrazí se v ovladači ODBC dialogové okno přihlášení při prvním otevření tabulky a znovu v případě, že je připojení zavřeno a znovu otevřeno. Pokud má připojená tabulka atribut `dbAttachSavePWD`, výzva k zadání přihlašovacích údajů se nezobrazí při opětovném otevření tabulky.

Související informace najdete v nápovědě k rozhraní DAO v tématu "připojení vlastnosti".

##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

Voláním této funkce určíte datum a čas, kdy byla vytvořena tabulka podkladového objektu `CDaoTableDef`.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která obsahuje datum a čas vytvoření tabulky podkladového objektu `CDaoTableDef`.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena z počítače, ve kterém byla vytvořena nebo naposledy aktualizována základní tabulka. Ve víceuživatelském prostředí by uživatelé měli získat tato nastavení přímo ze souborového serveru, aby se předešlo nesrovnalostem. To znamená, že všichni klienti by měli použít "standardní" zdroj času, třeba z jednoho serveru.

Související informace naleznete v tématu "DateCreated, hodnota LastUpdated Properties" v nápovědě pro rozhraní DAO.

##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Voláním této funkce určíte datum a čas, kdy byla tabulka podkladového objektu `CDaoTableDef` naposledy aktualizována.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která obsahuje datum a čas, kdy byla naposledy aktualizována tabulka podkladového objektu `CDaoTableDef`.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena z počítače, ve kterém byla vytvořena nebo naposledy aktualizována základní tabulka. Ve víceuživatelském prostředí by uživatelé měli získat tato nastavení přímo ze souborového serveru, aby se předešlo nesrovnalostem. To znamená, že všichni klienti by měli použít "standardní" zdroj času, třeba z jednoho serveru.

Související informace naleznete v tématu "DateCreated, hodnota LastUpdated Properties" v nápovědě pro rozhraní DAO.

##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Zavolejte tuto členskou funkci pro načtení počtu polí definovaných v tabulce.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v tabulce

### <a name="remarks"></a>Poznámky

Pokud je jeho hodnota 0, v kolekci nejsou žádné objekty.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "vlastnost Count".

##  <a name="getfieldinfo"></a>CDaoTableDef:: GetFieldInfo

Volejte tuto členskou funkci pro získání různých druhů informací o poli definovaném v tabledef.

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
Index objektu pole v kolekci polí založených na nule pro vyhledávání podle indexu.

*FieldInfo*<br/>
Odkaz na strukturu [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) .

*dwInfoOptions*<br/>
Možnosti, které určují, které informace o poli se mají načíst. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí:

- `AFX_DAO_PRIMARY_INFO` (výchozí) název, typ, velikost, atributy. Tuto možnost použijte pro nejrychlejší výkon.

- `AFX_DAO_SECONDARY_INFO` primární informace, navíc: ordinální pozice, požadováno, povolení nulové délky, pořadí řazení, cizí název, zdrojové pole, zdrojová tabulka

- `AFX_DAO_ALL_INFO` primární a sekundární informace, navíc: ověřovací pravidlo, text ověření, výchozí hodnota

*lpszName*<br/>
Ukazatel na název objektu pole pro vyhledávání podle názvu. Název je řetězec s až 64 znaky, které pole jedinečně pojmenují.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat pole podle indexu. Druhá verze umožňuje vyhledat pole podle názvu.

Popis vrácených informací najdete v tématu struktura [CDaoFieldInfo –](../../mfc/reference/cdaofieldinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Když si vyžádáte informace na jedné úrovni, získáte informace také pro všechny předchozí úrovně.

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Voláním této členské funkce získáte počet indexů pro tabulku.

```
short GetIndexCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet indexů pro tabulku.

### <a name="remarks"></a>Poznámky

Pokud je jeho hodnota 0, v kolekci nejsou žádné indexy.

Související informace naleznete v nápovědě k rozhraní DAO v tématu "vlastnost Count".

##  <a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Volejte tuto členskou funkci pro získání různých druhů informací o indexu definovaném v tabledef.

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
Číselný index objektu indexu v kolekci indexů založených na nule pro vyhledávání podle pozice v kolekci.

*indexinfo*<br/>
Odkaz na strukturu [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) .

*dwInfoOptions*<br/>
Možnosti, které určují, které informace o indexu mají být načteny. Dostupné možnosti jsou uvedené tady spolu s tím, co způsobí, že funkce vrátí:

- `AFX_DAO_PRIMARY_INFO` název, pole informace o poli. Tuto možnost použijte pro nejrychlejší výkon.

- `AFX_DAO_SECONDARY_INFO` primární informace, navíc: primární, jedinečný, clusterovaný, ignorované hodnoty null, povinné, cizí

- `AFX_DAO_ALL_INFO` primární a sekundární informace a navíc: jedinečný počet

*lpszName*<br/>
Ukazatel na název objektu indexu pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat index podle jeho pozice v kolekci. Druhá verze umožňuje vyhledat index podle názvu.

Popis vrácených informací najdete v tématu struktura [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) . Tato struktura obsahuje členy, které odpovídají položkám, které jsou uvedeny výše v popisu *dwInfoOptions*. Když si vyžádáte informace na jedné úrovni, získáte informace také pro všechny předchozí úrovně.

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="getname"></a>CDaoTableDef:: GetName

Zavolejte tuto členskou funkci, aby získala uživatelsky definovaný název podkladové tabulky.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Uživatelsky definovaný název tabulky.

### <a name="remarks"></a>Poznámky

Tento název začíná písmenem a může obsahovat maximálně 64 znaků. Může obsahovat číslice a podtržítka, ale nemůže obsahovat interpunkční znaménka nebo mezery.

Související informace najdete v tématu "vlastnost Name" v nápovědě k rozhraní DAO.

##  <a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Voláním této členské funkce zjistíte, kolik záznamů je v objektu `CDaoTableDef`.

```
long GetRecordCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů, které jsou k dispozici v objektu tabledef.

### <a name="remarks"></a>Poznámky

Volání `GetRecordCount` pro objekt `CDaoTableDef` typu tabulka odráží přibližný počet záznamů v tabulce a je okamžitě ovlivněn při přidávání a odstraňování záznamů tabulky. Transakce vracené zpět se zobrazí jako součást počtu záznamů, dokud nebudete volat [CDaoWorkspace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Objekt `CDaoTableDef` bez záznamů má nastavení vlastnosti počet záznamů na hodnotu 0. Při práci s připojenými tabulkami nebo databázemi ODBC `GetRecordCount` vždy vrátí hodnotu-1.

Související informace najdete v tématu "vlastnost RecordCount" v nápovědě k rozhraní DAO.

##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Voláním této členské funkce načtěte název připojené tabulky ve zdrojové databázi.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString`, který určuje název zdroje připojené tabulky nebo prázdný řetězec, pokud je tabulka nativních dat.

### <a name="remarks"></a>Poznámky

Připojená tabulka je tabulka v jiné databázi propojené s databází Microsoft Jet. Data pro připojené tabulky zůstanou v externí databázi, kde se můžou manipulovat jinými aplikacemi.

Související informace najdete v tématu "Vlastnost SourceTableName" v nápovědě k rozhraní DAO.

##  <a name="getvalidationrule"></a>CDaoTableDef:: getověřovací pravidlo

Voláním této členské funkce načtěte ověřovací pravidlo pro tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString`, který ověřuje data v poli, jak je změněno nebo přidáno do tabulky.

### <a name="remarks"></a>Poznámky

Ověřovací pravidla se používají v souvislosti s operacemi aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, musí aktualizace tohoto tabledef odpovídat předem určeným kritériím, aby se data změnila. Pokud změna neodpovídá kritériím, je vyvolána výjimka obsahující hodnotu [GetValidationText](#getvalidationtext) . Pro objekt `CDaoTableDef` je tato `CString` jen pro čtení pro připojenou tabulku a pro čtení i zápis pro základní tabulku.

Související informace najdete v nápovědě k rozhraní DAO v tématu vlastnost "ověřovací pravidlo".

##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Voláním této funkce načtete řetězec, který se zobrazí, když uživatel zadá data, která se neshodují s ověřovacím pravidlem.

```
CString GetValidationText();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString`, který určuje text zobrazený v případě, že uživatel zadá data, která se neshodují s ověřovacím pravidlem.

### <a name="remarks"></a>Poznámky

Pro objekt `CDaoTableDef` je tato `CString` jen pro čtení pro připojenou tabulku a pro čtení i zápis pro základní tabulku.

Související informace najdete v nápovědě k rozhraní DAO v tématu "vlastnost ověřovacího hesla".

##  <a name="isopen"></a>CDaoTableDef:: Open

Voláním této členské funkce určíte, zda je objekt `CDaoTableDef` aktuálně otevřen.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je objekt `CDaoTableDef` otevřený; v opačném případě 0.

### <a name="remarks"></a>Poznámky

##  <a name="m_pdatabase"></a>CDaoTableDef:: m_pDatabase

Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) pro tuto tabulku.

### <a name="remarks"></a>Poznámky

##  <a name="m_pdaotabledef"></a>CDaoTableDef:: m_pDAOTableDef

Obsahuje ukazatel na rozhraní OLE pro objekt DAO tabledef podkladového objektu `CDaoTableDef`.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte v případě, že potřebujete získat přímý přístup k rozhraní DAO.

##  <a name="open"></a>CDaoTableDef:: Open

Voláním této členské funkce otevřete tabledef dříve uloženou v kolekci TableDef's databáze.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který určuje název tabulky.

### <a name="remarks"></a>Poznámky

##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink

Chcete-li aktualizovat informace o připojení pro připojenou tabulku, zavolejte tuto členskou funkci.

```
void RefreshLink();
```

### <a name="remarks"></a>Poznámky

Informace o připojení pro připojenou tabulku změníte voláním [SetConnect](#setconnect) na odpovídajícím objektu `CDaoTableDef` a následným použitím `RefreshLink` členské funkce k aktualizaci informací. Při volání `RefreshLink`se nezmění vlastnosti připojené tabulky.

Aby se projevily změněné informace o připojení, musí být všechny otevřené objekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) založené na tomto tabledef zavřeny.

Související informace naleznete v tématu "metoda RefreshLink" v nápovědě k rozhraní DAO.

##  <a name="setattributes"></a>CDaoTableDef:: SetAttributes

Nastaví hodnotu, která označuje jednu nebo více vlastností objektu `CDaoTableDef`.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parametry

*lAttributes*<br/>
Charakteristiky tabulky reprezentované objektem `CDaoTableDef` a mohou být součtem těchto konstant:

|Trvalé|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|U databází, které používají databázový stroj Microsoft Jet, je tabulka připojená tabulka otevřená pro výhradní použití.|
|`dbAttachSavePWD`|U databází, které používají databázový stroj Microsoft Jet, se zobrazí informace o tom, že ID uživatele a heslo pro připojenou tabulku jsou uloženy spolu s informacemi o připojení.|
|`dbSystemObject`|Určuje, že tabulka je systémová tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbHiddenObject`|Určuje, že tabulka je skrytá tabulka poskytovaná databázovým strojem Microsoft Jet.|

### <a name="remarks"></a>Poznámky

Při nastavování více atributů je lze kombinovat pomocí součtu příslušných konstant pomocí bitového operátoru OR. Nastavení `dbAttachExclusive` v nepřipojené tabulce vyvolá výjimku. Kombinování následujících hodnot také produkuje výjimku:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Související informace naleznete v tématu "vlastnost atributů" v nápovědě rozhraní DAO.

##  <a name="setconnect"></a>CDaoTableDef::SetConnect

Pro objekt `CDaoTableDef`, který představuje připojenou tabulku, se objekt String skládá z jedné nebo dvou částí (specifikátor typu databáze a cesta k databázi).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Ukazatel na řetězcový výraz, který určuje další parametry, které se mají předat rozhraní ODBC nebo instalovat ovladače ISAM.

### <a name="remarks"></a>Poznámky

Cesta uvedená v následující tabulce je úplná cesta pro adresář obsahující soubory databáze a před ní musí být uveden identifikátor "DATABASE =". V některých případech (stejně jako u databází Microsoft Jet a Microsoft Excel) je do argumentu cesta databáze zahrnut konkrétní název souboru.

> [!NOTE]
>  Nepoužívejte prázdné znaky kolem příkazů Path pro rovnítko ve formátu "DATABASE = Drive:\\\path". Výsledkem bude vyjímka výjimky a selhání připojení.

V následující tabulce jsou uvedeny možné typy databází a jejich odpovídající specifikátory a cesty databáze:

|Typ databáze|Specifikátor|Cesta|
|-------------------|---------------|----------|
|Databáze pomocí databázového stroje Jet|"[`database`];"|"`drive`:\\\ *cesta*\\\ *filename*. DATABÁZI|
|dBASE III|"dBASE III;"|"`drive`:\\\ *cesta*"|
|dBASE IV|"dBASE IV;"|"`drive`:\\\ *cesta*"|
|dBASE 5|"dBASE 5,0;"|"`drive`:\\\ *cesta*"|
|Paradox 3. x|"Paradox 3. x;"|"`drive`:\\\ *cesta*"|
|Paradox 4. x|"Paradox 4. x;"|"`drive`:\\\ *cesta*"|
|Paradox 5. x|"Paradox 5. x;"|"`drive`:\\\ *cesta*"|
|Excel 3,0|"Excel 3,0;"|"`drive`:\\\ *cesta*\\\ *filename*. NAPŘ|
|Excel 4,0|"Excel 4,0;"|"`drive`:\\\ *cesta*\\\ *filename*. NAPŘ|
|Excel 5,0 nebo Excel 95|"Excel 5,0;"|"`drive`:\\\ *cesta*\\\ *filename*. NAPŘ|
|Excel 97|"Excel 8,0;"|"`drive`:\\\ *cesta*\ *filename*. NAPŘ|
|Import HTML|"Import HTML;"|"`drive`:\\\ *cesta*\ *filename*|
|HTML Export|"Export HTML;"|"`drive`:\\\ *cesta*"|
|Text|"Text;"|"Drive:\\\path"|
|ODBC|ODBC DATABÁZE = `database`; UID = *uživatel*; PWD = *Password*; DSN = *zdroj dat;* LOGINTIMEOUT = *sekundy;* " (To nemusí být úplný připojovací řetězec pro všechny servery. je to jenom příklad. Je velmi důležité, aby mezi parametry nebyla mezera.)|Žádná|
|Exchange|Výměn<br /><br /> MAPILEVEL = *FolderPath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [PROFILe = *Profile*;]<br /><br /> [PWD = *Password*;]<br /><br /> [DATABASE = `database`;] "|*"Drive*:\\\ *cesta*\\\ *filename*. DATABÁZI|

> [!NOTE]
>  Btrieve již není podporován z hlediska rozhraní DAO 3,5.

V připojovacích řetězcích je nutné použít dvojité zpětné lomítko (\\\\). Pokud jste změnili vlastnosti stávajícího připojení pomocí `SetConnect`, musíte následně volat [RefreshLink](#refreshlink). Pokud inicializujete vlastnosti připojení pomocí `SetConnect`, nemusíte volat `RefreshLink`, ale pokud se k tomu rozhodnete, nejprve tabledef přidejte.

Pokud je vyžadováno heslo, ale není k dispozici, zobrazí se v ovladači ODBC dialogové okno přihlášení při prvním otevření tabulky a znovu v případě, že je připojení zavřeno a znovu otevřeno.

Můžete nastavit připojovací řetězec pro objekt `CDaoTableDef` zadáním zdrojového argumentu do členské funkce `Create`. Můžete kontrolovat nastavení pro určení typu, cesty, ID uživatele, hesla nebo zdroje dat ODBC databáze. Další informace najdete v dokumentaci ke konkrétnímu ovladači.

Související informace najdete v nápovědě k rozhraní DAO v tématu "připojení vlastnosti".

##  <a name="setname"></a>CDaoTableDef::SetName

Zavolejte tuto členskou funkci pro nastavení uživatelsky definovaného názvu tabulky.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězcový výraz, který určuje název tabulky.

### <a name="remarks"></a>Poznámky

Název musí začínat písmenem a může obsahovat maximálně 64 znaků. Může obsahovat číslice a podtržítka, ale nemůže obsahovat interpunkční znaménka nebo mezery.

Související informace najdete v tématu "vlastnost Name" v nápovědě k rozhraní DAO.

##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

Voláním této členské funkce určíte název připojené tabulky nebo název základní tabulky, na které je objekt `CDaoTableDef` založený, protože existuje v původním zdroji dat.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parametry

*lpszSrcTableName*<br/>
Ukazatel na řetězcový výraz, který určuje název tabulky v externí databázi. U základní tabulky je toto nastavení prázdný řetězec ("").

### <a name="remarks"></a>Poznámky

Pak musíte zavolat [RefreshLink](#refreshlink). Nastavení této vlastnosti je prázdné pro základní tabulku a pro čtení a zápis pro připojenou tabulku nebo objekt, který není připojen ke kolekci.

Související informace najdete v tématu "Vlastnost SourceTableName" v nápovědě k rozhraní DAO.

##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

Zavolejte tuto členskou funkci pro nastavení ověřovacího pravidla pro tabledef.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parametry

*lpszValidationRule*<br/>
Ukazatel na řetězcový výraz, který ověřuje operaci.

### <a name="remarks"></a>Poznámky

Ověřovací pravidla se používají v souvislosti s operacemi aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, musí aktualizace tohoto tabledef odpovídat předem určeným kritériím, aby se data změnila. Pokud změna neodpovídá kritériím, zobrazí se výjimka obsahující text [GetValidationText](#getvalidationtext) .

Ověřování je podporováno pouze pro databáze, které používají databázový stroj Microsoft Jet. Výraz nemůže odkazovat na uživatelsky definované funkce, agregační funkce domény, agregační funkce SQL nebo dotazy. Ověřovací pravidlo pro objekt `CDaoTableDef` může odkazovat na více polí v tomto objektu.

Například pro pole s názvem *hire_date* a *termination_date*může pravidlo ověřování:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Související informace najdete v nápovědě k rozhraní DAO v tématu vlastnost "ověřovací pravidlo".

##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Zavolejte tuto členskou funkci pro nastavení textu výjimky ověřovacího pravidla pro objekt `CDaoTableDef` se základní tabulkou podporovanou databázovým strojem Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parametry

*lpszValidationText*<br/>
Ukazatel na řetězcový výraz, který určuje text zobrazený v případě, že jsou zadaná data neplatná.

### <a name="remarks"></a>Poznámky

Nemůžete nastavit ověřovací text připojené tabulky.

Související informace najdete v nápovědě k rozhraní DAO v tématu "vlastnost ověřovacího hesla".

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
