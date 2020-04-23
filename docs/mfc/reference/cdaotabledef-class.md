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
ms.openlocfilehash: adc31ccbf2be34aa1df1fa56111d1990701a6329
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754686"
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
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Vytvoří `CDaoTableDef` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef::Připojit](#append)|Přidá do databáze novou tabulku.|
|[CDaoTableDef::CanUpdate](#canupdate)|Vrátí nenulovou hodnotu, pokud lze tabulku aktualizovat (můžete upravit definici polí nebo vlastnosti tabulky).|
|[CDaoTableDef::Zavřít](#close)|Zavře otevřenou tabulkovou def.|
|[CDaoTableDef::Vytvořit](#create)|Vytvoří tabulku, kterou lze přidat do databáze pomocí [funkce Připojit](#append).|
|[CDaoTableDef::CreateField](#createfield)|Nazývá se vytvoření pole pro tabulku.|
|[CDaoTableDef::Vytvořitindex](#createindex)|Nazývá se vytvoření indexu pro tabulku.|
|[CDaoTableDef::DeleteField](#deletefield)|Nazývá se odstranění pole z tabulky.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Nazývá se odstranění indexu z tabulky.|
|[CDaoTableDef::Atributy GetAttributes](#getattributes)|Vrátí hodnotu, která označuje jednu nebo více vlastností objektu. `CDaoTableDef`|
|[CDaoTableDef::GetConnect](#getconnect)|Vrátí hodnotu, která poskytuje informace o zdroji tabulky.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Vrátí datum a čas vytvoření `CDaoTableDef` základní tabulky, která je podkladem objektu.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Vrátí datum a čas poslední změny provedené v návrhu základní tabulky.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Vrátí hodnotu, která představuje počet polí v tabulce.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Vrátí určité druhy informací o polích v tabulce.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Vrátí počet indexů pro tabulku.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Vrátí určité druhy informací o indexech pro tabulku.|
|[CDaoTableDef::GetName](#getname)|Vrátí uživatelem definovaný název tabulky.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Vrátí počet záznamů v tabulce.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Vrátí hodnotu, která určuje název připojené tabulky ve zdrojové databázi.|
|[CDaoTableDef::Pravidlo ověření pravosti](#getvalidationrule)|Vrátí hodnotu, která ověřuje data v poli při změně nebo přidání do tabulky.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Vrátí hodnotu, která určuje text zprávy, kterou aplikace zobrazí, pokud hodnota objektu Field nesplňuje zadané ověřovací pravidlo.|
|[CDaoTableDef::Jeotevřeno](#isopen)|Vrátí nenulovou, pokud je tabulka otevřená.|
|[CDaoTableDef::Otevřít](#open)|Otevře existující tabledef uložené v databázi TableDef kolekce.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informace o připojení připojené tabulky.|
|[CDaoTableDef::Atributy set](#setattributes)|Nastaví hodnotu, která označuje `CDaoTableDef` jednu nebo více vlastností objektu.|
|[CDaoTableDef::SetConnect](#setconnect)|Nastaví hodnotu, která poskytuje informace o zdroji tabulky.|
|[CDaoTableDef::SetName](#setname)|Nastaví název tabulky.|
|[CDaoTableDef::Název_tabulky SetSourceTableName](#setsourcetablename)|Nastaví hodnotu, která určuje název připojené tabulky ve zdrojové databázi.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Nastaví hodnotu, která ověřuje data v poli při změně nebo přidání do tabulky.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Nastaví hodnotu, která určuje text zprávy, kterou aplikace zobrazí, pokud hodnota objektu Field nesplňuje zadané ověřovací pravidlo.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Ukazatel na rozhraní DAO, které je základem objektu tabledef.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Zdrojová databáze pro tuto tabulku.|

## <a name="remarks"></a>Poznámky

Každý databázový objekt DAO udržuje kolekci nazvanou TableDefs, která obsahuje všechny uložené objekty DAO tabledef.

Definice tabulky se manipuluje `CDaoTableDef` pomocí objektu. Můžete například provést následující věci:

- Zkontrolujte strukturu polí a indexu libovolné místní, připojené nebo externí tabulky v databázi.

- Volání `SetConnect` a `SetSourceTableName` členské funkce pro připojené tabulky `RefreshLink` a pomocí členské funkce aktualizovat připojení k připojeným tabulkám.

- Volání `CanUpdate` členské funkce k určení, zda můžete upravovat definice polí v tabulce.

- Získejte nebo nastavte `GetValidationRule` podmínky `SetValidationRule`ověření `GetValidationText` pomocí `SetValidationText` funkcí a a a a.

- Pomocí `Open` členské funkce vytvořte objekt typu `CDaoRecordset` tabulka, dynaset nebo snímek.

    > [!NOTE]
    >  Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Stále můžete přistupovat ke zdrojům dat ODBC pomocí tříd DAO; Třídy DAO obecně nabízejí vynikající funkce, protože jsou specifické pro databázový stroj Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Použití objektů tabledef buď pro práci s existující tabulkou, nebo k vytvoření nové tabulky

1. Ve všech případech nejprve vytvořte `CDaoTableDef` objekt, který poskytuje ukazatel na objekt [CDaoDatabase,](../../mfc/reference/cdaodatabase-class.md) ke kterému tabulka patří.

1. Pak udělejte následující, v závislosti na tom, co chcete:

   - Chcete-li použít existující uloženou tabulku, zavolejte členská funkci [Open](#open) objektu tabledef a zadejnázev uloženou tabulku.

   - Chcete-li vytvořit novou tabulku, zavolejte členovou funkci [Create](#create) objektu tabledef a zadejte název tabulky. Volání [CreateField](#createfield) a [CreateIndex](#createindex) přidat pole a indexy do tabulky.

   - Volání [Append](#append) uložit tabulku připojením do databáze TableDefs kolekce. `Create`vloží tabledef do otevřeného stavu, `Create` takže po `Open`volání nevolejte .

        > [!TIP]
        >  Nejjednodušší způsob, jak vytvořit uložené tabulky, je vytvořit je a uložit je do databáze pomocí aplikace Microsoft Access. Pak je můžete otevřít a použít v kódu knihovny MFC.

Chcete-li použít objekt tabledef, který jste `CDaoRecordset` otevřeli nebo vytvořili, vytvořte `dbOpenTable` a otevřete objekt a zadejte název tabledef s hodnotou v parametru *nOpenType.*

Chcete-li použít objekt tabledef k vytvoření objektu, `CDaoRecordset` obvykle vytvoříte nebo otevřete tabledef, jak je popsáno výše, pak vytvořte objekt sady záznamů a při volání sady [CDaoRecordset ::Open](../../mfc/reference/cdaorecordset-class.md#open)předáte ukazatel objektu tabledef. Tabledef, které předáte, musí být v otevřeném stavu. Další informace naleznete v tématu třída [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Po dokončení pomocí tabledef objektu, volání jeho [Zavřít](../../mfc/reference/cdaorecordset-class.md#close) členská funkce; pak zničit tabledef objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef::Připojit

Volání této členské funkce po volání [Create](#create) vytvořit nový objekt tabledef uložit tabledef v databázi.

```
virtual void Append();
```

### <a name="remarks"></a>Poznámky

Funkce připojí objekt do kolekce TableDefs databáze. Tabledef můžete použít jako dočasný objekt při definování tím, že není připojení, ale pokud chcete `Append`uložit a použít, musíte volat .

> [!NOTE]
> Pokud se pokusíte připojit nepojmenované tabledef (obsahující null nebo prázdný řetězec), mfc vyvolá výjimku.

Související informace naleznete v tématu "Append Method" v nápovědě DAO.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef::CanUpdate

Volání této členské funkce k určení, zda `CDaoTableDef` lze změnit definici tabulky základní objekt.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze změnit strukturu tabulky (schéma) (přidat nebo odstranit pole a indexy), jinak 0.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení lze aktualizovat `CDaoTableDef` nově vytvořenou tabulku, na níž `CDaoTableDef` je objekt založen, a připojenou tabulku, na níž je objekt založen, nelze aktualizovat. Objekt `CDaoTableDef` může být aktualizovatelný, i když výsledná sada záznamů není aktualizovatelná.

Související informace naleznete v tématu "Aktualizovatelná vlastnost" v nápovědě dao.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Vytvoří `CDaoTableDef` objekt.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabáze*<br/>
Ukazatel na objekt [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Poznámky

Po vytvoření objektu je nutné volat [členská](#create) funkci Vytvořit nebo [Otevřít.](#open) Po dokončení s objektem, musíte [Close](#close) volat jeho Zavřít `CDaoTableDef` členské funkce a zničit objekt.

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef::Zavřít

Volání této členské funkce zavřete a uvolněte objekt tabledef.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Obvykle po `Close`volání odstraňte objekt tabledef, pokud byl přidělen s **novým**.

Po volání [Open](#open) můžete znovu `Close`zavolat Open . To umožňuje znovu použít objekt tabledef.

Související informace naleznete v tématu "Close Method" v nápovědě dao.

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef::Vytvořit

Voláním této členské funkce vytvořte novou uloženou tabulku.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězec obsahující název tabulky.

*lAtributy*<br/>
Hodnota odpovídající charakteristikám tabulky reprezentované objektem tabledef. Bitové nebo lze použít ke kombinaci některé z následujících konstant:

|Trvalé|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|Pro databáze, které používají databázový stroj Microsoft Jet, označuje, že tabulka je připojená tabulka otevřená pro výhradní použití.|
|`dbAttachSavePWD`|Pro databáze, které používají databázový stroj Microsoft Jet, označuje, že ID uživatele a heslo pro připojenou tabulku jsou uloženy s informacemi o připojení.|
|`dbSystemObject`|Označuje, že tabulka je systémová tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbHiddenObject`|Označuje, že tabulka je skrytá tabulka poskytovaná databázovým strojem Microsoft Jet.|

*lpszSrcTabulka*<br/>
Ukazatel na řetězec obsahující název zdrojové tabulky. Ve výchozím nastavení je tato hodnota inicializována jako null.

*lpszPřipojit*<br/>
Ukazatel na řetězec obsahující výchozí připojovací řetězec. Ve výchozím nastavení je tato hodnota inicializována jako null.

### <a name="remarks"></a>Poznámky

Jakmile jste pojmenovali tabledef, potom můžete volat [Append](#append) uložit tabledef v databázi TableDefs kolekce. Po `Append`volání je tabledef v otevřeném stavu a můžete jej použít k vytvoření objektu [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

Související informace naleznete v tématu "Metoda CreateTableDef" v nápovědě dao.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef::CreateField

Volání této členské funkce pro přidání pole do tabulky.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězcový výraz určující název tohoto pole.

*nTyp*<br/>
Hodnota označující datový typ pole. Nastavení může být jedna z těchto hodnot:

|Typ|Velikost (bajty)|Popis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Bool|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Měna ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Datum a čas ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Dlouhý binární (objekt OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) nebo [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Poznámka ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lVelikost*<br/>
Hodnota, která označuje maximální velikost pole obsahujícího text v bajtech nebo pevnou velikost pole obsahujícího textové nebo číselné hodnoty. Parametr *lSize* je ignorován pro všechna kromě textových polí.

*lAtributy*<br/>
Hodnota odpovídající charakteristikám pole, kterou lze kombinovat pomocí bitového nebo.

|Trvalé|Popis|
|--------------|-----------------|
|`dbFixedField`|Velikost pole je pevná (výchozí pro číselná pole).|
|`dbVariableField`|Velikost pole je proměnná (pouze textová pole).|
|`dbAutoIncrField`|Hodnota pole pro nové záznamy se automaticky zintáží na jedinečné dlouhé celé číslo, které nelze změnit. Podporováno pouze pro databázové tabulky Microsoft Jet.|
|`dbUpdatableField`|Hodnotu pole lze změnit.|
|`dbDescending`|Pole je seřazeno v sestupném pořadí (Z - A nebo 100 - 0) (vztahuje se pouze na objekt Pole v kolekci Polí objektu Index). Pokud tuto konstantu vynechete, pole seřadí vzestupně (A - Z nebo 0 - 100) (výchozí).|

*Fieldinfo*<br/>
Odkaz na strukturu [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

### <a name="remarks"></a>Poznámky

A `DAOField` (OLE) objekt je vytvořen a připojen `DAOTableDef` k Fields kolekce (OLE) objektu. Kromě jeho použití pro zkoumání vlastností `CDaoFieldInfo` objektu můžete také vytvořit vstupní parametr pro vytváření nových polí v tabledef. První verze `CreateField` aplikace je jednodušší, ale pokud chcete jemnější řízení, můžete `CreateField`použít druhou `CDaoFieldInfo` verzi aplikace , která přebírá parametr.

Pokud použijete `CreateField` verzi, která `CDaoFieldInfo` přebírá parametr, musíte pečlivě nastavit každý `CDaoFieldInfo` z následujících členů struktury:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Zbývající členy `CDaoFieldInfo` by měla být nastavena na **0**, FALSE nebo prázdný řetězec, podle potřeby pro člena, nebo `CDaoException` může dojít.

Související informace naleznete v tématu "Metoda CreateField" v nápovědě dao.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef::Vytvořitindex

Volání této funkce přidat index do tabulky.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parametry

*informace o indexech*<br/>
Odkaz na strukturu [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

### <a name="remarks"></a>Poznámky

Indexy určují pořadí záznamů, ke které se přistupuje z databázových tabulek, a zda jsou duplicitní záznamy přijaty. Indexy také poskytují efektivní přístup k datům.

Není třeba vytvářet indexy pro tabulky, ale ve velkých, neindexovaných tabulkách může přístup k určitému záznamu nebo vytvoření sady záznamů trvat dlouho. Na druhou stranu vytváření příliš mnoho indexů zpomaluje aktualizace, připojit a odstranit operace jako všechny indexy jsou automaticky aktualizovány. Zvažte tyto faktory při rozhodování, které indexy chcete vytvořit.

Musí být nastaveny `CDaoIndexInfo` tyto členy konstrukce:

- `m_strName`Musí být zadán název.

- `m_pFieldInfos`Musí přejděte na `CDaoIndexFieldInfo` pole struktur.

- `m_nFields`Je nutné zadat počet polí `CDaoFieldInfo` v poli struktur.

Zbývající členové budou ignorováni, pokud je nastavena na FALSE. Kromě toho `m_lDistinctCount` člen je ignorována při vytváření indexu.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField

Volání této členské funkce odebrat pole a znepřístupní jej.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězcový výraz, který je názvem existujícího pole.

*nIndex*<br/>
Index pole v kolekci polí založených na nule v tabulce pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Tuto člennou funkci můžete použít u nového objektu, který nebyl připojen k databázi, nebo když [CanUpdate](#canupdate) vrátí nenulovou hodnotu.

Související informace naleznete v tématu "Delete Method" v nápovědě dao.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex

Volání této členské funkce odstranit index v podkladové tabulce.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězcový výraz, který je názvem existujícího indexu.

*nIndex*<br/>
Index pole objektu indexu v databázi TableDefs založené na nule, pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Tuto člennou funkci můžete použít u nového objektu, který nebyl připojen k databázi, nebo když [CanUpdate](#canupdate) vrátí nenulovou hodnotu.

Související informace naleznete v tématu "Delete Method" v nápovědě dao.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef::Atributy GetAttributes

Pro `CDaoTableDef` objekt určuje vrácená hodnota charakteristiky tabulky `CDaoTableDef` reprezentované objektem a může být součtem těchto konstant:

```
long GetAttributes();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která označuje jednu nebo více vlastností objektu. `CDaoTableDef`

### <a name="remarks"></a>Poznámky

|Trvalé|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|Pro databáze, které používají databázový stroj Microsoft Jet, označuje, že tabulka je připojená tabulka otevřená pro výhradní použití.|
|`dbAttachSavePWD`|Pro databáze, které používají databázový stroj Microsoft Jet, označuje, že ID uživatele a heslo pro připojenou tabulku jsou uloženy s informacemi o připojení.|
|`dbSystemObject`|Označuje, že tabulka je systémová tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbHiddenObject`|Označuje, že tabulka je skrytá tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbAttachedTable`|Označuje, že tabulka je připojená tabulka z databáze mimo ODBC, například databáze Paradox.|
|`dbAttachedODBC`|Označuje, že tabulka je připojená tabulka z databáze ODBC, například Microsoft SQL Server.|

Systémová tabulka je tabulka vytvořená databázovým strojem Microsoft Jet, která obsahuje různé interní informace.

Skrytá tabulka je tabulka vytvořená pro dočasné použití databázovým strojem Microsoft Jet.

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef::GetConnect

Volání této členské funkce získat připojovací řetězec pro zdroj dat.

```
CString GetConnect();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CString` obsahující cestu a typ databáze pro tabulku.

### <a name="remarks"></a>Poznámky

Pro `CDaoTableDef` objekt, který představuje připojenou `CString` tabulku, se objekt skládá z jedné nebo dvou částí (specifikátor typu databáze a cesta k databázi).

Cesta, jak je znázorněno v následující tabulce, je úplná cesta pro adresář obsahující databázové soubory a musí předcházet identifikátor "DATABASE=". V některých případech (stejně jako u databází Microsoft Jet a Microsoft Excel) je do argumentu cesty k databázi zahrnut konkrétní název souboru.

Tabulka v [CDaoTableDef::SetConnect](#setconnect) zobrazuje možné typy databází a jejich odpovídající specifikátory databáze a cesty:

Pro základní tabulky databáze Microsoft Jet je specifikátor prázdný řetězec ("").

Pokud je heslo vyžadováno, ale není k dispozici, ovladač ODBC zobrazí přihlašovací dialogové okno při prvním přístupu k tabulce a znovu, pokud je připojení uzavřeno a znovu otevřeno. Pokud připojená tabulka `dbAttachSavePWD` obsahuje atribut, výzva k přihlášení se při opětovném otevření tabulky nezobrazí.

Související informace naleznete v tématu "Connect Property" v nápovědě dao.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

Volání této funkce k určení data a `CDaoTableDef` času tabulky, která je základem objektu byla vytvořena.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota obsahující datum a čas vytvoření tabulky, která `CDaoTableDef` je základem objektu.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena od počítače, ve kterém byla základní tabulka vytvořena nebo naposledy aktualizována. Ve víceuživatelském prostředí by uživatelé měli získat tato nastavení přímo ze souborového serveru, aby se zabránilo nesrovnalostem; to znamená, že všichni klienti by měli používat "standardní" zdroj času - možná z jednoho serveru.

Související informace naleznete v tématu DateCreated, LastUpdated Properties v nápovědě dao.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Volání této funkce k určení data a `CDaoTableDef` času tabulky, která je základem objektu, byla naposledy aktualizována.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která obsahuje datum a čas, kdy byla tabulka, na níž objekt založen, `CDaoTableDef` naposledy aktualizována.

### <a name="remarks"></a>Poznámky

Nastavení data a času jsou odvozena od počítače, ve kterém byla základní tabulka vytvořena nebo naposledy aktualizována. Ve víceuživatelském prostředí by uživatelé měli získat tato nastavení přímo ze souborového serveru, aby se zabránilo nesrovnalostem; to znamená, že všichni klienti by měli používat "standardní" zdroj času - možná z jednoho serveru.

Související informace naleznete v tématu DateCreated, LastUpdated Properties v nápovědě dao.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Volánítéto členské funkce načíst počet polí definovaných v tabulce.

```
short GetFieldCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet polí v tabulce.

### <a name="remarks"></a>Poznámky

Pokud je jeho hodnota 0, neexistují žádné objekty v kolekci.

Související informace naleznete v tématu "Count Property" v nápovědě dao.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo

Volání této členské funkce získat různé druhy informací o pole definované v tabledef.

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
Index objektu pole v kolekci polí založených na nule v tabulce pro vyhledávání podle indexu.

*Fieldinfo*<br/>
Odkaz na strukturu [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o poli mají být načteny. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit:

- `AFX_DAO_PRIMARY_INFO`(Výchozí) Název, Typ, Velikost, Atributy. Tuto možnost použijte pro nejrychlejší výkon.

- `AFX_DAO_SECONDARY_INFO`Primární informace plus: Ordinální pozice, Povinné, Povolit nulovou délku, Řazení objednávky, Cizí jméno, Zdrojové pole, Zdrojová tabulka

- `AFX_DAO_ALL_INFO`Primární a sekundární informace plus: Ověřovací pravidlo, ověřovací text, výchozí hodnota

*název lpsz*<br/>
Ukazatel na název objektu pole pro vyhledávání podle názvu. Název je řetězec s až 64 znaky, který jedinečně pojmenuje pole.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat pole podle indexu. Druhá verze umožňuje vyhledat pole podle názvu.

Popis vrácených informací naleznete ve struktuře [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Když požadujete informace na jedné úrovni, získáte také informace pro všechny předchozí úrovně.

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Volání této členské funkce získat počet indexů pro tabulku.

```
short GetIndexCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet indexů pro tabulku.

### <a name="remarks"></a>Poznámky

Pokud je jeho hodnota 0, neexistují žádné indexy v kolekci.

Související informace naleznete v tématu "Count Property" v nápovědě dao.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Volání této členské funkce získat různé druhy informací o indexu definované v tabledef.

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
Číselný index Index objektu v tabulce indexy založené na nule kolekce, pro vyhledávání podle jeho pozice v kolekci.

*informace o indexech*<br/>
Odkaz na strukturu [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoMožnosti*<br/>
Možnosti, které určují, které informace o indexu načíst. Dostupné možnosti jsou uvedeny zde spolu s tím, co způsobí, že funkce vrátit:

- `AFX_DAO_PRIMARY_INFO`Jméno, informace o poli, pole. Tuto možnost použijte pro nejrychlejší výkon.

- `AFX_DAO_SECONDARY_INFO`Primární informace plus: Primární, Jedinečný, Clustered, Ignorovat nulls, Povinné, Cizí

- `AFX_DAO_ALL_INFO`Primární a sekundární informace plus: Odlišný počet

*název lpsz*<br/>
Ukazatel na název objektu indexu pro vyhledávání podle názvu.

### <a name="remarks"></a>Poznámky

Jedna verze funkce umožňuje vyhledat index podle jeho umístění v kolekci. Druhá verze umožňuje vyhledat index podle názvu.

Popis vrácených informací naleznete ve struktuře [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md) Tato struktura má členy, které odpovídají výše uvedeným položkám informací v popisu *dwInfoOptions*. Když požadujete informace na jedné úrovni, získáte také informace pro všechny předchozí úrovně.

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef::GetName

Volání této členské funkce získat uživatelem definovaný název podkladové tabulky.

```
CString GetName();
```

### <a name="return-value"></a>Návratová hodnota

Uživatelem definovaný název tabulky.

### <a name="remarks"></a>Poznámky

Tento název začíná písmenem a může obsahovat maximálně 64 znaků. Může obsahovat čísla a znaky podtržítka, ale nemůže obsahovat interpunkci nebo mezery.

Související informace naleznete v tématu "Name Property" v nápovědě dao.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Volání této členské funkce zjistit, kolik `CDaoTableDef` záznamů jsou v objektu.

```
long GetRecordCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet záznamů přístupných v objektu tabledef.

### <a name="remarks"></a>Poznámky

Volání `GetRecordCount` objektu typu `CDaoTableDef` tabulky odráží přibližný počet záznamů v tabulce a je ovlivněno okamžitě při přidávání a odstraňování záznamů tabulky. Vrácené transakce se zobrazí jako součást počtu záznamů, dokud nezavoláte [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Objekt `CDaoTableDef` bez záznamů má nastavení vlastnosti počet záznamů 0. Při práci s připojenými tabulkami `GetRecordCount` nebo databázemi ODBC vždy vrátí -1.

Související informace naleznete v tématu "RecordCount Property" v nápovědě DAO.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Volání této členské funkce načíst název připojené tabulky ve zdrojové databázi.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CString` který určuje zdrojový název připojené tabulky nebo prázdný řetězec, pokud je nativní tabulka dat.

### <a name="remarks"></a>Poznámky

Připojená tabulka je tabulka v jiné databázi propojené s databází Microsoft Jet. Data pro připojené tabulky zůstávají v externí databázi, kde s nimi mohou manipulovat jiné aplikace.

Související informace naleznete v tématu "SourceTableName Property" v nápovědě DAO.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::Pravidlo ověření pravosti

Volání této členské funkce načíst ověřovací pravidlo pro tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CString` který ověřuje data v poli při změně nebo přidání do tabulky.

### <a name="remarks"></a>Poznámky

Ověřovací pravidla se používají ve spojení s operacemi aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, aktualizace tohoto tabledef musí odpovídat předem určeným kritériím před změnou dat. Pokud změna neodpovídá kritériím, je vyvolána výjimka obsahující hodnotu [GetValidationText.](#getvalidationtext) Pro `CDaoTableDef` objekt je `CString` to jen pro čtení pro připojené tabulky a čtení a zápis pro základní tabulku.

Související informace naleznete v tématu "ValidationRule Property" v nápovědě dao.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Volání této funkce načíst řetězec zobrazí, když uživatel zadá data, která neodpovídá ověřovací pravidlo.

```
CString GetValidationText();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CString` který určuje text zobrazený, pokud uživatel zadá data, která neodpovídají ověřovacímu pravidlu.

### <a name="remarks"></a>Poznámky

Pro `CDaoTableDef` objekt je `CString` to jen pro čtení pro připojené tabulky a čtení a zápis pro základní tabulku.

Související informace naleznete v tématu "Vlastnost ValidationText" v nápovědě dao.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef::Jeotevřeno

Volání této členské funkce `CDaoTableDef` k určení, zda je objekt aktuálně otevřen.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, `CDaoTableDef` pokud je objekt otevřený; jinak 0.

### <a name="remarks"></a>Poznámky

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase

Obsahuje ukazatel na objekt [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) pro tuto tabulku.

### <a name="remarks"></a>Poznámky

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef

Obsahuje ukazatel na rozhraní OLE pro objekt DAO `CDaoTableDef` tabledef, který je základem objektu.

### <a name="remarks"></a>Poznámky

Tento ukazatel použijte, pokud potřebujete přímý přístup k rozhraní DAO.

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::Otevřít

Volání této členské funkce otevřete tabledef dříve uložené v databázi TableDef kolekce.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězec, který určuje název tabulky.

### <a name="remarks"></a>Poznámky

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

Volání této členské funkce aktualizovat informace o připojení pro připojené tabulky.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>Poznámky

Informace o připojení připojené tabulky změníte voláním [Funkce SetConnect](#setconnect) na odpovídajícím `CDaoTableDef` objektu a následným `RefreshLink` použitím členské funkce k aktualizaci informací. Při volání `RefreshLink`se vlastnosti připojené tabulky nezmění.

Chcete-li vynutit, aby se změněné informace o připojení projevily, musí být uzavřeny všechny otevřené objekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) založené na této tabulkové def.

Související informace naleznete v tématu "RefreshLink Method" v nápovědě DAO.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef::Atributy set

Nastaví hodnotu, která označuje `CDaoTableDef` jednu nebo více vlastností objektu.

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parametry

*lAtributy*<br/>
Charakteristiky tabulky reprezentované objektem `CDaoTableDef` a mohou být součtem těchto konstant:

|Trvalé|Popis|
|--------------|-----------------|
|`dbAttachExclusive`|Pro databáze, které používají databázový stroj Microsoft Jet, označuje, že tabulka je připojená tabulka otevřená pro výhradní použití.|
|`dbAttachSavePWD`|Pro databáze, které používají databázový stroj Microsoft Jet, označuje, že ID uživatele a heslo pro připojenou tabulku jsou uloženy s informacemi o připojení.|
|`dbSystemObject`|Označuje, že tabulka je systémová tabulka poskytovaná databázovým strojem Microsoft Jet.|
|`dbHiddenObject`|Označuje, že tabulka je skrytá tabulka poskytovaná databázovým strojem Microsoft Jet.|

### <a name="remarks"></a>Poznámky

Při nastavování více atributů je můžete kombinovat sečtením příslušných konstant pomocí operátoru Bitwise-OR. Nastavení `dbAttachExclusive` na nepřipojené tabulce vytváří výjimku. Kombinace následujících hodnot také vytvořit výjimku:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Související informace naleznete v tématu "Vlastnost atributů" v nápovědě dao.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect

Pro `CDaoTableDef` objekt, který představuje připojenou tabulku, objekt řetězce se skládá z jedné nebo dvou částí (specifikátor typu databáze a cesta k databázi).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszPřipojit*<br/>
Ukazatel na řetězcový výraz, který určuje další parametry, které mají být předávány ovladačům ODBC nebo instalovatelným ovladačům ISAM.

### <a name="remarks"></a>Poznámky

Cesta, jak je znázorněno v následující tabulce, je úplná cesta pro adresář obsahující databázové soubory a musí předcházet identifikátor "DATABASE=". V některých případech (stejně jako u databází Microsoft Jet a Microsoft Excel) je do argumentu cesty k databázi zahrnut konkrétní název souboru.

> [!NOTE]
> Nezahrnujte mezery kolem rovnítko v příkazy\\cesty formuláře "DATABASE=drive: \path". To bude mít za následek výjimku je vyvolána a připojení se lhem.

V následující tabulce jsou uvedeny možné typy databází a jejich odpovídající specifikátory databáze a cesty:

|Typ databáze|Specifikátor|Cesta|
|-------------------|---------------|----------|
|Databáze pomocí databázového stroje Jet|"[ `database`];"|" `drive`\\\ :*název souboru**cesty*\\\ . MDB"|
|dBASE III|"dBASE III;"|" `drive`\\\ :*cesta*"|
|dBASE IV|"dBASE IV;"|" `drive`\\\ :*cesta*"|
|dBASE 5|"dBASE 5.0;"|" `drive`\\\ :*cesta*"|
|Paradox 3.x|"Paradox 3.x;"|" `drive`\\\ :*cesta*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive`\\\ :*cesta*"|
|Paradox 5.x|"Paradox 5.x;"|" `drive`\\\ :*cesta*"|
|Aplikace Excel 3.0|"Excel 3.0;"|" `drive`\\\ :*název souboru**cesty*\\\ . XLS"|
|Aplikace Excel 4.0|"Excel 4.0;"|" `drive`\\\ :*název souboru**cesty*\\\ . XLS"|
|Excel 5.0 nebo Excel 95|"Excel 5.0;"|" `drive`\\\ :*název souboru**cesty*\\\ . XLS"|
|Aplikace Excel 97|"Excel 8.0;"|" `drive`\\\ :*název souboru**cesty*\ . XLS"|
|HTML Import|"Import HTML;"|" `drive`\\\ :*název souboru**cesty*\ "|
|HTML Export|"Export HTML;"|" `drive`\\\ :*cesta*"|
|Text|"Text;"|"jednotka:\\\cesta"|
|ODBC|"ODBC; DATABÁZE `database`= ; UID = *uživatel*; PWD = *heslo*; DSN = *název zdroje dat;* LOGINTIMEOUT = *sekundy;*" (To to nemusí být kompletní připojovací řetězec pro všechny servery; je to jen příklad. Je velmi důležité, aby mezery mezi parametry.)|Žádná|
|Výměna|"Výměna;<br /><br /> MAPILEVEL = *cesta ke složce*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [PROFIL = *profil*;]<br /><br /> [PWD= *heslo*;]<br /><br /> [DATABÁZE= `database`;]"|*"drive*\\\ :*path*\\\ *filename*. MDB"|

> [!NOTE]
> Btrieve již není podporován a DAO 3.5.

V připojovacích\\\\řetězcích je nutné použít dvojité zpětné lomítko ( ). Pokud jste změnili vlastnosti existujícího připojení pomocí `SetConnect`, musíte následně zavolat [RefreshLink](#refreshlink). Pokud inicializujete vlastnosti připojení `SetConnect`pomocí `RefreshLink`aplikace , nemusíte volat , ale pokud se rozhodnete tak učinit, nejprve připojte tabledef.

Pokud je heslo vyžadováno, ale není k dispozici, ovladač ODBC zobrazí přihlašovací dialogové okno při prvním přístupu k tabulce a znovu, pokud je připojení uzavřeno a znovu otevřeno.

Připojovací řetězec pro `CDaoTableDef` objekt můžete nastavit poskytnutím zdrojového argumentu pro člennou `Create` funkci. V nastavení můžete zkontrolovat a určit typ, cestu, ID uživatele, heslo nebo zdroj dat ODBC databáze. Další informace naleznete v dokumentaci k konkrétnímu ovladači.

Související informace naleznete v tématu "Connect Property" v nápovědě dao.

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef::SetName

Volánítéto členské funkce nastavit uživatelem definovaný název tabulky.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
Ukazatel na řetězcový výraz, který určuje název tabulky.

### <a name="remarks"></a>Poznámky

Název musí začínat písmenem a může obsahovat maximálně 64 znaků. Může obsahovat čísla a znaky podtržítka, ale nemůže obsahovat interpunkci nebo mezery.

Související informace naleznete v tématu "Name Property" v nápovědě dao.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::Název_tabulky SetSourceTableName

Volání této členské funkce určit název připojené tabulky nebo název základní tabulky, na kterém je `CDaoTableDef` objekt založen, protože existuje v původním zdroji dat.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parametry

*lpszSrcTableName*<br/>
Ukazatel na řetězcový výraz, který určuje název tabulky v externí databázi. Pro základní tabulku je nastavení prázdný řetězec ("").

### <a name="remarks"></a>Poznámky

Potom je nutné zavolat [RefreshLink](#refreshlink). Toto nastavení vlastnosti je prázdné pro základní tabulku a čtení a zápis pro připojenou tabulku nebo objekt, který není připojen ke kolekci.

Související informace naleznete v tématu "SourceTableName Property" v nápovědě DAO.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

Volání této členské funkce nastavit ověřovací pravidlo pro tabledef.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parametry

*lpszValidationRule*<br/>
Ukazatel na řetězcový výraz, který ověřuje operaci.

### <a name="remarks"></a>Poznámky

Ověřovací pravidla se používají ve spojení s operacemi aktualizace. Pokud tabledef obsahuje ověřovací pravidlo, aktualizace tohoto tabledef musí odpovídat předem určeným kritériím před změnou dat. Pokud změna neodpovídá kritériím, zobrazí se výjimka obsahující text [GetValidationText.](#getvalidationtext)

Ověření je podporováno pouze pro databáze, které používají databázový stroj Microsoft Jet. Výraz nemůže odkazovat na uživatelem definované funkce, funkce agregace domény, agregační funkce SQL nebo dotazy. Ověřovací pravidlo pro `CDaoTableDef` objekt může odkazovat na více polí v tomto objektu.

Například pro pole s názvem *hire_date* a *termination_date*může být ověřovací pravidlo:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Související informace naleznete v tématu "ValidationRule Property" v nápovědě dao.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Volání této členské funkce nastavit text výjimky `CDaoTableDef` ověřovacípravidlo pro objekt s základní tabulky podporované databázového stroje Microsoft Jet.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parametry

*lpszValidationText*<br/>
Ukazatel na řetězcový výraz, který určuje text zobrazený v případě, že zadaná data jsou neplatná.

### <a name="remarks"></a>Poznámky

Ověřovací text připojené tabulky nelze nastavit.

Související informace naleznete v tématu "Vlastnost ValidationText" v nápovědě dao.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)
