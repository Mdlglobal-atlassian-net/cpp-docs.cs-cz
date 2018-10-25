---
title: Cdaotabledef – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a943374731785ecadd13f89ee5c1b760acfb46d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064859"
---
# <a name="cdaotabledef-class"></a>Cdaotabledef – třída

Představuje uloženou definici základní tabulky nebo připojené tabulky.

## <a name="syntax"></a>Syntaxe

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Vytvoří `CDaoTableDef` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|Přidá novou tabulku do databáze.|
|[CDaoTableDef::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud je možné aktualizovat tabulky (můžete upravit definice polí a vlastností tabulky).|
|[CDaoTableDef::Close](#close)|Zavře otevřený tabledef.|
|[CDaoTableDef::Create](#create)|Vytvoří tabulku, která mohou být přidány do databáze pomocí [připojit](#append).|
|[CDaoTableDef::CreateField](#createfield)|Volá se, aby vytvořit pole tabulky.|
|[CDaoTableDef::CreateIndex](#createindex)|Volá se, k vytvoření indexu pro tabulku.|
|[CDaoTableDef::DeleteField](#deletefield)|Volá se, jak odstranit pole z tabulky.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Volá se, aby odstranění indexu z tabulky.|
|[CDaoTableDef::GetAttributes](#getattributes)|Vrátí hodnotu, která určuje jeden nebo více vlastností `CDaoTableDef` objektu.|
|[CDaoTableDef::GetConnect](#getconnect)|Vrátí hodnotu, která poskytuje informace o zdrojové tabulce.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Vrátí datum a čas v základní tabulce podkladových `CDaoTableDef` objekt byl vytvořen.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny v návrhu v základní tabulce.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v tabulce.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Vrátí určité druhy informací o polích v tabulce.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Vrátí počet indexů pro tabulku.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Vrátí určité druhy informací o indexování pro tabulku.|
|[CDaoTableDef::GetName](#getname)|Vrátí uživatelem definovaný název tabulky.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v tabulce.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Vrátí hodnotu, která určuje název připojené tabulky ve zdrojové databázi.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Vrátí hodnotu, která ověřuje data v poli jako ho se nezmění ani nepřidá do tabulky.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Vrátí hodnotu, která určuje text zprávy, která vaše aplikace zobrazí, pokud hodnotu objektu pole nevyhovuje zadané pravidlo ověřování.|
|[CDaoTableDef::IsOpen](#isopen)|Vrátí nenulovou hodnotu, pokud je tabulka otevřete.|
|[CDaoTableDef::Open](#open)|Otevře existující tabledef uložené v databázi vaší společnosti TableDef kolekce.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informace o připojení pro připojené tabulky.|
|[CDaoTableDef::SetAttributes](#setattributes)|Nastaví hodnotu, která určuje jeden nebo více vlastností `CDaoTableDef` objektu.|
|[CDaoTableDef::SetConnect](#setconnect)|Nastaví hodnotu, která poskytuje informace o zdrojové tabulce.|
|[CDaoTableDef::SetName](#setname)|Nastaví název tabulky.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Nastaví hodnotu, která určuje název připojené tabulky ve zdrojové databázi.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Nastaví hodnotu, která ověřuje data v poli jako ho se nezmění ani nepřidá do tabulky.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Nastaví hodnotu, která určuje text zprávy, která vaše aplikace zobrazí, pokud hodnotu objektu pole nevyhovuje zadané pravidlo ověřování.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Ukazatel na rozhraní DAO základního objektu tabledef.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Zdrojová databáze pro tuto tabulku.|

## <a name="remarks"></a>Poznámky

Každý databázový objekt DAO udržuje kolekci s názvem tabledefs –, který obsahuje všechny objekty uložené tabledef DAO.

Můžete pracovat s definici tabulky pomocí `CDaoTableDef` objektu. Například můžete:

- Zkontrolujte strukturu pole a indexu jakékoli místní, připojené nebo externí tabulky v databázi.

- Volání `SetConnect` a `SetSourceTableName` členské funkce pro připojené tabulky a použití `RefreshLink` členská funkce se aktualizovat připojení k připojené tabulky.

- Volání `CanUpdate` členskou funkci k určení, pokud můžete upravit definice polí v tabulce.

- Získání nebo nastavení ověření podmínky použití `GetValidationRule` a `SetValidationRule`a `GetValidationText` a `SetValidationText` členské funkce.

- Použití `Open` členskou funkci pro vytvoření tabulky-, dynamická sada nebo typ snímku `CDaoRecordset` objektu.

    > [!NOTE]
    >  Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Můžete si pořád přístup ke zdrojům dat ODBC s tříd DAO; třídy DAO obecně nabízejí vynikající možnosti, protože jsou specifické pro databázový stroj Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Použití objektů tabledef pro práci s existující tabulky nebo vytvořit novou tabulku

1. Ve všech případech, nejprve se vytvoří `CDaoTableDef` objekt, ukazatel na poskytnutí [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu, ke které patří tabulky.

1. Proveďte následující kroky, podle toho, co chcete:

   - Pokud chcete použít stávající uložený tabulky, volání objektu tabledef [otevřít](#open) členskou funkci, poskytnutí název uloženého tabulky.

   - Pokud chcete vytvořit novou tabulku, volání objektu tabledef [vytvořit](#create) členskou funkci, zadání názvu tabulky. Volání [CreateField](#createfield) a [CreateIndex](#createindex) přidání pole a indexů do tabulky.

   - Volání [připojit](#append) k uložení tabulky připojením k vaší databáze tabledefs – kolekce. `Create` Vloží tabledef v otevřeném stavu, takže po volání `Create` není volána `Open`.

        > [!TIP]
        >  Můžete je vytvořit a uložit je ve vaší databázi pomocí aplikace Microsoft Access je nejjednodušší způsob, jak vytvářet tabulky uložené. Pak můžete otevřít a použít je ve vašem kódu knihovny MFC.

Použití objektu tabledef jste otevřeli nebo vytvořili, vytvořte a otevřete `CDaoRecordset` objekt zadáním názvu tabledef s `dbOpenTable` hodnota v *nOpenType* parametru.

Použití objektu tabledef k vytvoření `CDaoRecordset` obvykle vytvoříte nebo otevřete tabledef výše popsaným způsobem a pak vytvořit objekt sady záznamů předání ukazatele do objektu tabledef při volání objektu [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef, které můžete předat musí být v otevřeném stavu. Další informace najdete v tématu třídy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Po dokončení práce tabledef objekt volat jeho [Zavřít](../../mfc/reference/cdaorecordset-class.md#close) členské funkci; poté zničit objekt tabledef.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="append"></a>  CDaoTableDef::Append

Voláním této členské funkce po zavolání [vytvořit](#create) k vytvoření nového objektu tabledef uložit tabledef v databázi.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

Funkce objekt připojí k vaší databáze tabledefs – kolekce. Můžete použít tabledef jako dočasný objekt při definování není připojením, ale pokud chcete uložit a použít, musíte zavolat `Append`.

> [!NOTE]
>  Pokud se pokusíte připojit nepojmenované tabledef (obsahuje hodnotu null nebo prázdný řetězec), knihovna MFC vyvolá výjimku.

Související informace naleznete v tématu "Metodu" v nápovědě k DAO.

##  <a name="canupdate"></a>  CDaoTableDef::CanUpdate

Voláním této členské funkce k určení, jestli definici základní tabulky `CDaoTableDef` objektu můžete změnit.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je možné upravit struktura tabulky (schéma) (Přidání nebo odstranění pole a indexy), jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení nově vytvořenou databázi základní `CDaoTableDef` objekt je možné aktualizovat a jako základ připojené tabulky `CDaoTableDef` objekt nelze aktualizovat. A `CDaoTableDef` objekt může být aktualizovat, i v případě, že není výslednou sadu záznamů aktualizovat.

Související informace naleznete v tématu "Aktualizovat vlastnost" v nápovědě k DAO.

##  <a name="cdaotabledef"></a>  CDaoTableDef::CDaoTableDef

Vytvoří `CDaoTableDef` objektu.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu.

### <a name="remarks"></a>Poznámky

Po vytvoření objektu, je třeba zavolat [vytvořit](#create) nebo [otevřít](#open) členskou funkci. Jakmile skončíte s objektem, je nutné volat jeho [Zavřít](#close) členské funkce a zničit `CDaoTableDef` objektu.

##  <a name="close"></a>  CDaoTableDef::Close

Voláním této členské funkce uvolnění objektu tabledef a zavřete.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Obvykle po volání `Close`, odstraňte objekt tabledef, pokud byla přidělena pomocí **nové**.

Můžete volat [otevřít](#open) znovu po volání `Close`. Díky tomu můžete znovu použít objekt tabledef.

Související informace naleznete v tématu "Metoda Close" v nápovědě k DAO.

##  <a name="create"></a>  CDaoTableDef::Create

Voláním této členské funkce, chcete-li vytvořit novou tabulku uložené.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec obsahující název tabulky.

*lAttributes*<br/>
Hodnota odpovídající vlastnosti tabulky tabledef objektem. Bitový operátor OR můžete kombinovat některý z následujících konstant:

|Konstanta|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|U databází, které používají databázovém stroji Microsoft Jet značí, že v tabulce je otevřen pro výhradní použití připojené tabulky.|
|`dbAttachSavePWD`|U databází, které používají databázovém stroji Microsoft Jet označuje, že se uloží ID uživatele a heslo pro připojené tabulku s informacemi o připojení.|
|`dbSystemObject`|Označuje, že systémová tabulka poskytuje databázový stroj Microsoft Jet je tabulka.|
|`dbHiddenObject`|Označuje, že tabulka se skryté tabulky, poskytovaných databázový stroj Microsoft Jet.|

*lpszSrcTable*<br/>
Ukazatel na řetězec obsahující název zdrojové tabulky. Ve výchozím nastavení je tato hodnota inicializován jako hodnota NULL.

*lpszConnect*<br/>
Ukazatel na řetězec obsahující výchozí připojovací řetězec. Ve výchozím nastavení je tato hodnota inicializován jako hodnota NULL.

### <a name="remarks"></a>Poznámky

Jakmile pojmenujete tabledef, pak můžete volat [připojit](#append) uložit tabledef databáze tabledefs – kolekce. Po volání `Append`tabledef je v otevřeném stavu a slouží k vytvoření [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu.

Související informace naleznete v tématu "CreateTableDef metodu" v nápovědě k DAO.

##  <a name="createfield"></a>  CDaoTableDef::CreateField

Voláním této členské funkce, chcete-li přidat pole do tabulky.

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

*nTyp*<br/>
Hodnota označující datový typ pole. Toto nastavení může být jedna z těchto hodnot:

|Typ|Velikost (bajty)|Popis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Měny ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Datum a čas ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Dlouhá binární soubor (objekt OLE) [CLongBinary](../../mfc/reference/clongbinary-class.md) nebo [CByteArray –](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Hodnota, která určuje maximální velikost v bajtech, pole, který obsahuje text, nebo pevné velikosti pole, která obsahuje textové nebo číselné hodnoty. *LSize* parametr je ignorován u všech textových polí.

*lAttributes*<br/>
Hodnota odpovídající vlastnosti pole a, který lze spojovat pomocí bitového operátoru OR.

|Konstanta|Popis|
|--------------|-----------------|
|`dbFixedField`|Velikost pole je pevně (výchozí nastavení pro číselné pole).|
|`dbVariableField`|Velikost pole je proměnná (pouze textové pole).|
|`dbAutoIncrField`|Hodnotu pole pro nové záznamy se automaticky zvýší na jedinečné long integer, která se nedá změnit. Podporováno pouze pro Microsoft Jet databázových tabulek.|
|`dbUpdatableField`|Můžete změnit hodnotu pole.|
|`dbDescending`|Pole je seřazen v sestupném (Z - A nebo 100-0) pořadí (platí pouze pro pole objektů v kolekci polí objektu indexu). Vynecháte-li tato konstanta, pole je seřazen vzestupně (A – Z nebo 0 – 100) pořadí (výchozí).|

*FieldInfo*<br/>
Odkaz na [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury.

### <a name="remarks"></a>Poznámky

A `DAOField` objekt (OLE) se vytvoří a připojí ke kolekci polí `DAOTableDef` objekt (OLE). Kromě jeho použití pro zkoumání vlastností objektu můžete také použít `CDaoFieldInfo` vytvořit vstupní parametr pro vytvoření nových polí v tabledef. První verze `CreateField` je jednodušší použít, ale pokud chcete lepší kontrolu, můžete použít druhou verzi `CreateField`, které přijímá `CDaoFieldInfo` parametr.

Pokud používáte verzi `CreateField` , která přijímá `CDaoFieldInfo` parametr, musíte pečlivě nastavit každý z následujících členů `CDaoFieldInfo` struktury:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Zbývající členy `CDaoFieldInfo` by mělo být nastavené **0**, FALSE nebo prázdný řetězec, podle potřeby pro člena nebo `CDaoException` může dojít.

Související informace naleznete v tématu "CreateField metodu" v nápovědě k DAO.

##  <a name="createindex"></a>  CDaoTableDef::CreateIndex

Voláním této funkce do tabulky přidat index.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parametry

*indexinfo*<br/>
Odkaz na [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktury.

### <a name="remarks"></a>Poznámky

Indexy určují pořadí záznamů, které jsou k němu přistupovat z databázové tabulky a určuje, jestli jsou přijaty duplicitní záznamy. Indexy také poskytují efektivní přístup k datům.

Není nutné k vytváření indexů pro tabulky, ale v tabulkách velké, neindexovaný přístup ke konkrétní záznam nebo vytvoření sady záznamů může trvat dlouhou dobu. Vytváření moc velký počet indexů na druhé straně může zpomalit aktualizace, přidat a odstranit operací, protože se automaticky aktualizují všechny indexy. Jak se můžete rozhodnout, které indexy vytvořit vezměte v úvahu tyto faktory.

Následující členové `CDaoIndexInfo` struktura musí být nastavena:

- `m_strName` Je nutné zadat název.

- `m_pFieldInfos` Musí odkazovat na pole `CDaoIndexFieldInfo` struktury.

- `m_nFields` Musíte zadat počet polí v poli `CDaoFieldInfo` struktury.

Zbývající členy se ignorované if nastaví na hodnotu FALSE. Kromě toho `m_lDistinctCount` členů se ignoruje při vytváření indexu.

##  <a name="deletefield"></a>  CDaoTableDef::DeleteField

Voláním této členské funkce pole odebrat a usnadnit nepřístupný.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec výraz, který je název existujícího pole.

*nIndex*<br/>
Index pole v tabulky založený na nule kolekce pole pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Tuto funkci člena můžete použít na nový objekt, který nebyl se připojí k databázi nebo když [CanUpdate](#canupdate) vrátí nenulovou hodnotu.

Související informace naleznete v tématu "Odstranit metodu" v nápovědě k DAO.

##  <a name="deleteindex"></a>  CDaoTableDef::DeleteIndex

Voláním této členské funkce pro odstranění indexu v základní tabulce.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na výraz řetězce, který je název existujícího indexu.

*nIndex*<br/>
Index pole objektu indexu ve vaší databáze od nuly tabledefs – kolekce, pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Tuto funkci člena můžete použít na nový objekt, který nebyl se připojí k databázi nebo když [CanUpdate](#canupdate) vrátí nenulovou hodnotu.

Související informace naleznete v tématu "Odstranit metodu" v nápovědě k DAO.

##  <a name="getattributes"></a>  CDaoTableDef::GetAttributes

Pro `CDaoTableDef` objekt, návratová hodnota určuje vlastností tabulky reprezentována `CDaoTableDef` objekt a může být součet těchto konstanty:

```
long GetAttributes();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která určuje jeden nebo více vlastností `CDaoTableDef` objektu.

### <a name="remarks"></a>Poznámky

|Konstanta|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|U databází, které používají databázovém stroji Microsoft Jet značí, že v tabulce je otevřen pro výhradní použití připojené tabulky.|
|`dbAttachSavePWD`|U databází, které používají databázovém stroji Microsoft Jet označuje, že se uloží ID uživatele a heslo pro připojené tabulku s informacemi o připojení.|
|`dbSystemObject`|Označuje, že systémová tabulka poskytuje databázový stroj Microsoft Jet je tabulka.|
|`dbHiddenObject`|Označuje, že tabulka se skryté tabulky, poskytovaných databázový stroj Microsoft Jet.|
|`dbAttachedTable`|Označuje, že je tabulka připojené tabulky z databáze rozhraní ODBC, jako je databázový stroj.|
|`dbAttachedODBC`|Označuje, že je tabulka připojené tabulky z databáze ODBC, jako je Microsoft SQL Server.|

Systémová tabulka je tabulka vytvořená databázovém stroji Microsoft Jet tak, aby obsahovala různých interních informací.

Skryté tabulky je vytvořený pro dočasné použití databázový stroj Microsoft Jet tabulku.

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="getconnect"></a>  CDaoTableDef::GetConnect

Voláním této členské funkce k získání připojovacího řetězce datového zdroje.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje typ cesty a databáze pro tabulku.

### <a name="remarks"></a>Poznámky

Pro `CDaoTableDef` objekt, který reprezentuje připojené tabulky `CString` objektu se skládá z jedné nebo dvou částí (specifikátor typu databáze a cestu k databázi).

Cesta, jak je znázorněno v následující tabulce je úplnou cestu k adresáři obsahujícímu soubory databáze a musí předcházet identifikátor "databáze =". V některých případech (jak s Microsoft Jet a Microsoft Excel databáze) konkrétní název souboru je zahrnuta v argumentu cesty databáze.

V tabulce v [CDaoTableDef::SetConnect](#setconnect) ukazuje databáze typy a jejich odpovídající specifikátory databáze a cesty:

Pro základní tabulky databáze Microsoft Jet specifikátor je prázdný řetězec ("").

Pokud heslo je vyžadována, ale není zadaný, zobrazí se ovladač ODBC čas přihlášení dialogového okna při prvním přístupu k tabulce znovu a pokud je připojení zavřít a znovu otevřít. Pokud má připojené tabulky `dbAttachSavePWD` atribut, výzva k přihlášení se nezobrazí, když znovu otevřete v tabulce.

Související informace naleznete v tématu "Připojit vlastnost" v nápovědě k DAO.

##  <a name="getdatecreated"></a>  CDaoTableDef::GetDateCreated

Voláním této funkce určete datum a čas podkladové tabulky `CDaoTableDef` objekt byl vytvořen.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

Hodnotu obsahující datum a čas vytvoření podkladové tabulky `CDaoTableDef` objektu.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozeny z počítače, na kterém byla vytvořena nebo poslední aktualizace základní tabulka. V prostředí uživatelé získají nastavení přímo ze souborového serveru, aby se zabránilo odchylky; To znamená všechny klienti měli používat jako zdroj času "standard", případně z jednoho serveru.

Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

##  <a name="getdatelastupdated"></a>  CDaoTableDef::GetDateLastUpdated

Voláním této funkce určete datum a čas podkladové tabulky `CDaoTableDef` byl objekt naposledy aktualizován.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která obsahuje datum a čas podkladové tabulky `CDaoTableDef` byl objekt naposledy aktualizován.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozeny z počítače, na kterém byla vytvořena nebo poslední aktualizace základní tabulka. V prostředí uživatelé získají nastavení přímo ze souborového serveru, aby se zabránilo odchylky; To znamená všechny klienti měli používat jako zdroj času "standard", případně z jednoho serveru.

Související informace naleznete v tématu "DateCreated LastUpdated vlastnosti" v nápovědě k DAO.

##  <a name="getfieldcount"></a>  CDaoTableDef::GetFieldCount

Voláním této členské funkce se načíst počet polí definovaných v tabulce.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v tabulce.

### <a name="remarks"></a>Poznámky

Pokud je jeho hodnota 0, nejsou žádné objekty v kolekci.

Související informace naleznete v tématu "Vlastnosti" v nápovědě k DAO.

##  <a name="getfieldinfo"></a>  CDaoTableDef::GetFieldInfo

Voláním této členské funkce získat různé druhy informací o pole definované v tabledef.

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
Index pole objektu v tabulky založený na nule kolekce pole pro vyhledávání podle indexu.

*FieldInfo*<br/>
Odkaz na [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o pole, které chcete načíst. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrátit:

- `AFX_DAO_PRIMARY_INFO` (Výchozí) Název, typ, velikosti, atributy. Tuto možnost použijte pro nejrychlejší výkon.

- `AFX_DAO_SECONDARY_INFO` Primární informace, a navíc: ordinální číslo pozice, povinné, umožňují nulovou délku, pořadí řazení cizí název pole zdroje, zdrojová tabulka

- `AFX_DAO_ALL_INFO` Informace o primární a sekundární, a navíc: ověřovací pravidlo, Text pro ověření, výchozí hodnota

*lpszName*<br/>
Ukazatel na název objektu pole pro vyhledávání podle názvu. Název je řetězec s až 64 znaků, který jednoznačně názvy pole.

### <a name="remarks"></a>Poznámky

Jednu verzi funkce umožňuje vyhledat pole podle indexu. Jiné verze umožňuje vyhledávání podle názvu pole.

Popis informací, najdete v tématu [cdaofieldinfo –](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, můžete získat informace o všech předchozích úrovní.

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="getindexcount"></a>  CDaoTableDef::GetIndexCount

Voláním této členské funkce získat počet indexů pro tabulku.

```
short GetIndexCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet indexů pro tabulku.

### <a name="remarks"></a>Poznámky

Pokud je jeho hodnota 0, nejsou žádné indexy v kolekci.

Související informace naleznete v tématu "Vlastnosti" v nápovědě k DAO.

##  <a name="getindexinfo"></a>  CDaoTableDef::GetIndexInfo

Voláním této členské funkce získat různé druhy informací o indexu definované v tabledef.

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
Číselný index objektu na Index v tabulce založený na nule indexů kolekce, pro vyhledávání podle jeho pozice v kolekci.

*indexinfo*<br/>
Odkaz na [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Možnosti, které určují, jaké informace o index k načtení. Tady jsou uvedené dostupné možnosti spolu s způsobí funkce vrátit:

- `AFX_DAO_PRIMARY_INFO` Pole se jménem, informace o poli. Tuto možnost použijte pro nejrychlejší výkon.

- `AFX_DAO_SECONDARY_INFO` Primární informace, a navíc: primární, jedinečné, clusteru, Ignorovat hodnoty Null, povinné, cizí

- `AFX_DAO_ALL_INFO` Primární a sekundární informace, a navíc: počet jedinečných položek

*lpszName*<br/>
Ukazatel na název objektu indexu pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jednu verzi funkce umožňuje vyhledat index podle jeho pozice v kolekci. Jiné verze umožňuje vyhledávání podle názvu indexu.

Popis informací, najdete v tématu [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Tato struktura obsahuje členy, které odpovídají položkám informací uvedených v popisu *dwInfoOptions*. Pokud budete požadovat informace na jedné úrovni, můžete získat informace o všech předchozích úrovní.

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="getname"></a>  CDaoTableDef::GetName

Voláním této členské funkce získat uživatelem definovaný název základní tabulky.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Uživatelem definovaný název tabulky.

### <a name="remarks"></a>Poznámky

Tento název začíná písmenem a může obsahovat až 64 znaků. Může obsahovat čísla a podtržítka znaků, ale nemůže obsahovat interpunkční znaménka nebo mezery.

Související informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

##  <a name="getrecordcount"></a>  CDaoTableDef::GetRecordCount

Voláním této členské funkce a zjistěte, kolik záznamů se v `CDaoTableDef` objektu.

```
long GetRecordCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů v objektu tabledef získat přístup.

### <a name="remarks"></a>Poznámky

Volání `GetRecordCount` pro typ tabulky `CDaoTableDef` objekt představuje přibližný počet záznamů v tabulce a má vliv okamžitě, jako jsou přidané a odstraněné záznamy tabulky. Vrátit zpět, dokud nezavoláte, bude se transakce zobrazují počet záznamů v rámci [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). A `CDaoTableDef` objektu se žádné záznamy je vlastnost počet záznamů je nastavena na hodnotu 0. Při práci s tabulkami v připojené nebo ODBC databází, `GetRecordCount` vždy vrátí hodnotu -1.

Související informace naleznete v tématu "PočetZáznamů vlastnost" v nápovědě k DAO.

##  <a name="getsourcetablename"></a>  CDaoTableDef::GetSourceTableName

Voláním této členské funkce načíst název připojené tabulky ve zdrojové databázi.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který určuje název zdroje připojené tabulky nebo prázdný řetězec, pokud má tabulka nativní data.

### <a name="remarks"></a>Poznámky

Připojené tabulky je tabulka v jiné databázi, které jsou propojeny s Microsoft Jet databáze. Data pro připojené tabulky zůstanou v externí databázi, ve kterém lze ovládat pomocí jiných aplikací.

Související informace naleznete v tématu "%{sourcetablename/ vlastnost" v nápovědě k DAO.

##  <a name="getvalidationrule"></a>  CDaoTableDef::GetValidationRule

Voláním této členské funkce k načtení ověřovacího pravidla pro tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který ověřuje data v poli jako ho se nezmění ani nepřidá do tabulky.

### <a name="remarks"></a>Poznámky

Ověřovací pravidla se používají v souvislosti s operace aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, musí aktualizace této tabledef předem kritériím neodpovídají, předtím, než se data změní. Pokud změna neodpovídá kritériím, výjimku, která obsahuje hodnotu [GetValidationText](#getvalidationtext) je vyvolána výjimka. Pro `CDaoTableDef` objektu, to `CString` je jen pro čtení pro připojené tabulky a čtení/zápisu pro základní tabulky.

Související informace naleznete v tématu "Ověřovací pravidlo vlastnost" v nápovědě k DAO.

##  <a name="getvalidationtext"></a>  CDaoTableDef::GetValidationText

Voláním této funkce se načíst řetězec, který se zobrazí, když uživatel zadá data, která se neshoduje s ověřovací pravidlo.

```
CString GetValidationText();
```

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který určuje text zobrazený v případě, že uživatel zadá data, která se neshoduje s ověřovací pravidlo.

### <a name="remarks"></a>Poznámky

Pro `CDaoTableDef` objektu, to `CString` je jen pro čtení pro připojené tabulky a čtení/zápisu pro základní tabulky.

Související informace naleznete v tématu "Ověřovací vlastnost" v nápovědě k DAO.

##  <a name="isopen"></a>  CDaoTableDef::IsOpen

Voláním této členské funkce k určení, zda `CDaoTableDef` objektu je momentálně otevřený.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulovou hodnotu, pokud `CDaoTableDef` objekt je otevřít; jinak 0.

### <a name="remarks"></a>Poznámky

##  <a name="m_pdatabase"></a>  CDaoTableDef::m_pDatabase

Obsahuje ukazatel [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objektu pro tuto tabulku.

### <a name="remarks"></a>Poznámky

##  <a name="m_pdaotabledef"></a>  CDaoTableDef::m_pDAOTableDef

Obsahuje ukazatel na rozhraní OLE pro základní objekt rozhraní DAO tabledef `CDaoTableDef` objektu.

### <a name="remarks"></a>Poznámky

Pokud je potřeba získat přímo přístup k rozhraní DAO, použijte tento ukazatel.

##  <a name="open"></a>  CDaoTableDef::Open

Tato členská funkce Otevřít tabledef dříve uložené v databázi volání vaší společnosti TableDef kolekce.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec, který určuje název tabulky.

### <a name="remarks"></a>Poznámky

##  <a name="refreshlink"></a>  CDaoTableDef::RefreshLink

Voláním této členské funkce k aktualizaci informací o připojení pro připojené tabulky.

```
void RefreshLink();
```

### <a name="remarks"></a>Poznámky

Změnit informace o připojení pro připojené tabulky voláním [SetConnect](#setconnect) u odpovídajícího `CDaoTableDef` objekt a potom pomocí `RefreshLink` členskou funkci k aktualizaci informací. Při volání `RefreshLink`, vlastnosti připojené tabulky se nezmění.

Chcete-li vynutit upravené připojení informace, které začnou platit, všechny otevřené [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekty podle této tabledef musí být uzavřeny.

Související informace naleznete v tématu "RefreshLink metodu" v nápovědě k DAO.

##  <a name="setattributes"></a>  CDaoTableDef::SetAttributes

Nastaví hodnotu, která určuje jeden nebo více vlastností `CDaoTableDef` objektu.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parametry

*lAttributes*<br/>
Vlastnosti tabulky reprezentována `CDaoTableDef` objekt a může být součet těchto konstanty:

|Konstanta|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|U databází, které používají databázovém stroji Microsoft Jet značí, že v tabulce je otevřen pro výhradní použití připojené tabulky.|
|`dbAttachSavePWD`|U databází, které používají databázovém stroji Microsoft Jet označuje, že se uloží ID uživatele a heslo pro připojené tabulku s informacemi o připojení.|
|`dbSystemObject`|Označuje, že systémová tabulka poskytuje databázový stroj Microsoft Jet je tabulka.|
|`dbHiddenObject`|Označuje, že tabulka se skryté tabulky, poskytovaných databázový stroj Microsoft Jet.|

### <a name="remarks"></a>Poznámky

Při nastavování více atributů, kombinovat sečtením odpovídající konstanty pomocí operátoru bitového operátoru OR. Nastavení `dbAttachExclusive` na samostatný tabulku vytváří výjimku. Kombinace těchto hodnot také vytvořit výjimku:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Související informace naleznete v tématu "Atributy vlastnosti" v nápovědě k DAO.

##  <a name="setconnect"></a>  CDaoTableDef::SetConnect

Pro `CDaoTableDef` objekt, který reprezentuje připojené tabulky, na objekt řetězce se skládá z jedné nebo dvou částí (specifikátor typu databáze a cestu k databázi).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Ukazatel na řetězcový výraz určující další parametry k předání do rozhraní ODBC nebo instalovat ovladače databází.

### <a name="remarks"></a>Poznámky

Cesta, jak je znázorněno v následující tabulce je úplnou cestu k adresáři obsahujícímu soubory databáze a musí předcházet identifikátor "databáze =". V některých případech (jak s Microsoft Jet a Microsoft Excel databáze) konkrétní název souboru je zahrnuta v argumentu cesty databáze.

> [!NOTE]
>  Nesmí obsahovat mezery kolem rovnítka cesta příkazy ve formě "databáze = jednotka:\\\path". To způsobí k vyvolání výjimky a neúspěšné připojení.

V následující tabulce jsou uvedeny typy databáze a jejich odpovídající specifikátory databáze a cesty:

|Typ databáze|Specifikátor|Cesta|
|-------------------|---------------|----------|
|Databáze s použitím databázový stroj|"[ `database`];"|" `drive`:\\\ *cesta*\\\ *filename*. MDB"|
|dBASE III|"dBASE III;"|" `drive`:\\\ *cesta*"|
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *cesta*"|
|dBASE 5|"dBASE 5.0."|" `drive`:\\\ *cesta*"|
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *cesta*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *cesta*"|
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *cesta*"|
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *cesta*\\\ *filename*. XLS"|
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *cesta*\\\ *filename*. XLS"|
|Excel 5.0 nebo 95 aplikace Excel|"Excel 5.0."|" `drive`:\\\ *cesta*\\\ *filename*. XLS"|
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *cesta*\ *filename*. XLS"|
|HTML Import|"HTML Import;"|" `drive`:\\\ *cesta*\ *filename*"|
|Export ve formátu HTML|"Export ve formátu HTML;"|" `drive`:\\\ *cesta*"|
|Text|"Text";|"jednotka:\\\path"|
|ODBC|"ODBC; DATABÁZE = `database`; UID = *uživatele*; PWD = *heslo*; Název zdroje dat = *datasourcename;* LOGINTIMEOUT = *sekund;*" (To nemusí být úplný připojovací řetězec pro všechny servery, je jenom pro příklad. Je velmi důležité, abyste adresní prostory mezi parametry.)|Žádné|
|Exchange|"Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 &AMP;#124; 1};]<br /><br /> [Profil = *profilu*;]<br /><br /> [PWD = *heslo*;]<br /><br /> [DATABÁZE = `database`;] "|*"jednotka*:\\\ *cesta*\\\ *filename*. MDB"|

> [!NOTE]
>  Btrieve je již nejsou podporovány od verze DAO 3.5.

Je třeba použít dvojité zpětné lomítko (\\\\) v připojovacích řetězcích. Pokud jste změnili vlastnosti existující připojení pomocí `SetConnect`, lze následně zavolat [RefreshLink](#refreshlink). Pokud se inicializace vlastností připojení pomocí `SetConnect`, budete potřebovat není volání `RefreshLink`, ale rozhodnete tak učinit, nejdřív připojit tabledef.

Pokud heslo je vyžadována, ale není zadaný, zobrazí se ovladač ODBC čas přihlášení dialogového okna při prvním přístupu k tabulce znovu a pokud je připojení zavřít a znovu otevřít.

Můžete nastavit připojovací řetězec pro `CDaoTableDef` objekt tím, že poskytuje zdroj argument `Create` členskou funkci. Můžete zkontrolovat nastavení k určení typu, cesta, ID uživatele, heslo nebo zdroje dat ODBC databáze. Další informace naleznete v dokumentaci pro určitý ovladač.

Související informace naleznete v tématu "Připojit vlastnost" v nápovědě k DAO.

##  <a name="setname"></a>  CDaoTableDef::SetName

Voláním této členské funkce pro nastavení uživatelem definovaný název pro tabulku.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Ukazatel na řetězec výraz, který určuje název tabulky.

### <a name="remarks"></a>Poznámky

Název musí začínat písmenem a může obsahovat až 64 znaků. Může obsahovat čísla a podtržítka znaků, ale nemůže obsahovat interpunkční znaménka nebo mezery.

Související informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

##  <a name="setsourcetablename"></a>  CDaoTableDef::SetSourceTableName

Voláním této členské funkce zadejte jméno připojené tabulky nebo název základní tabulky, na kterém `CDaoTableDef` podle objektu, protože existuje v původním zdroji dat.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parametry

*lpszSrcTableName*<br/>
Ukazatel na řetězec výraz, který určuje název tabulky v externí databázi. Základní tabulka, nastavení je prázdný řetězec ("").

### <a name="remarks"></a>Poznámky

Musíte pak zavolat [RefreshLink](#refreshlink). Nastavení této vlastnosti je pro čtení a zápisu pro připojené tabulky nebo objektu není připojen ke kolekci a základní tabulky prázdný.

Související informace naleznete v tématu "%{sourcetablename/ vlastnost" v nápovědě k DAO.

##  <a name="setvalidationrule"></a>  CDaoTableDef::SetValidationRule

Voláním této členské funkce, chcete-li nastavit ověřovací pravidlo pro tabledef.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parametry

*lpszValidationRule*<br/>
Ukazatel na výraz řetězce, která ověřuje operace.

### <a name="remarks"></a>Poznámky

Ověřovací pravidla se používají v souvislosti s operace aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, musí aktualizace této tabledef předem kritériím neodpovídají, předtím, než se data změní. Pokud změna neodpovídá kritériím, obsahující text výjimky [GetValidationText](#getvalidationtext) se zobrazí.

Ověření se podporuje jenom pro databáze, které používají databázový stroj Microsoft Jet. Výraz nemůže odkazovat na uživatelsky definovaných funkcí, domény agregační funkce, agregačních funkcí SQL nebo dotazy. Ověřovací pravidlo pro `CDaoTableDef` objektu mohou odkazovat na více polí v objektu.

Například pro pole s názvem *hire_date* a *termination_date*, může být ověřovacího pravidla:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Související informace naleznete v tématu "Ověřovací pravidlo vlastnost" v nápovědě k DAO.

##  <a name="setvalidationtext"></a>  CDaoTableDef::SetValidationText

Voláním této členské funkce, chcete-li nastavit text výjimky ověřovací pravidlo pro `CDaoTableDef` objekt s základní základní tabulka nepodporuje databázový stroj Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parametry

*lpszValidationText*<br/>
Ukazatel na řetězec výraz, který určuje text zobrazený v případě zadání dat je neplatný.

### <a name="remarks"></a>Poznámky

Nelze nastavit text pro ověření připojené tabulky.

Související informace naleznete v tématu "Ověřovací vlastnost" v nápovědě k DAO.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
