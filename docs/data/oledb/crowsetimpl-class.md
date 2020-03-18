---
title: CRowsetImpl – třída
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: 9c2e5923fe35287a7586cd4b52bc60e4a5b27b2d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441146"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl – třída

Poskytuje standardní OLE DB implementaci sady řádků bez nutnosti vícenásobné dědění mnoha implementačních rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl : 
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída uživatele, která je odvozena z `CRowsetImpl`.

*Storage*<br/>
Třída záznamu uživatele.

*CreatorClass*<br/>
Třída, která obsahuje vlastnosti pro sadu řádků; obvykle se jedná o příkaz.

*ArrayType*<br/>
Třída, která bude sloužit jako úložiště pro data sady řádků. Výchozí hodnota tohoto parametru je `CAtlArray`, ale může to být libovolná třída, která podporuje požadovanou funkci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[NameFromDBID](#namefromdbid)|Extrahuje řetězec z `DBID` a zkopíruje ho do předaného typu *BSTR* .|
|[SetCommandText](#setcommandtext)|Ověří a uloží `DBID`s v obou řetězcích ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|

### <a name="overridable-methods"></a>Přepsatelné metody

|||
|-|-|
|[GetColumnInfo –](#getcolumninfo)|Načte informace o sloupci pro konkrétní požadavek klienta.|
|[GetCommandFromID](#getcommandfromid)|Kontroluje, zda buď nebo oba parametry obsahují hodnoty řetězce, a pokud ano, zkopíruje řetězcové hodnoty do datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|
|[ValidateCommandID](#validatecommandid)|Kontroluje, zda buď nebo oba `DBID`s obsahují hodnoty řetězce, a pokud ano, zkopíruje je do datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_rgRowData](#rgrowdata)|Ve výchozím nastavení `CAtlArray`, který se templatizes na argumentu šablony záznamu uživatele `CRowsetImpl`. Jinou třídu typu pole lze použít změnou argumentu šablony `ArrayType` na `CRowsetImpl`.|
|[m_strCommandText](#strcommandtext)|Obsahuje počáteční příkaz sady řádků.|
|[m_strIndexText](#strindextext)|Obsahuje počáteční index sady řádků.|

## <a name="remarks"></a>Poznámky

`CRowsetImpl` poskytuje přepsání ve formě statických přetypování. Metody řídí způsob, jakým bude daná sada řádků ověřovat text příkazu. Můžete vytvořit vlastní třídu `CRowsetImpl`-Style tím, že implementujete rozhraní implementace s více děděnými možnostmi. Jedinou metodou, pro kterou je nutné zadat implementaci, je `Execute`. V závislosti na typu sady řádků, kterou vytváříte, budou metody autora očekávat různé signatury `Execute`. Například pokud používáte třídu odvozenou `CRowsetImpl`k implementaci sady řádků schématu, bude mít metoda `Execute` následující signaturu:

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

Pokud vytváříte třídu odvozenou od `CRowsetImpl`pro implementaci sady řádků příkazu nebo relace, bude mít metoda `Execute` následující signaturu:

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

Chcete-li implementovat některou z `CRowsetImpl`ch `Execute`ch metod, je nutné naplnit vnitřní vyrovnávací paměti pro data ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).

## <a name="namefromdbid"></a>CRowsetImpl:: NameFromDBID

Extrahuje řetězec z `DBID` a zkopíruje ho do předaného typu *BSTR* .

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>Parametry

*pDBID*<br/>
pro Ukazatel na `DBID`, ze kterého má být extrahován řetězec.

*BSTR*<br/>
pro [CComBSTR](../../atl/reference/ccombstr-class.md) odkaz na umístění kopie řetězce `DBID`.

*bIndex*<br/>
pro **true** , pokud `DBID`index; **false** , pokud `DBID`tabulky

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. V závislosti na tom, zda je `DBID` tabulka nebo index (označený *bIndex*), metoda vrátí hodnotu DB_E_NOINDEX nebo DB_E_NOTABLE.

### <a name="remarks"></a>Poznámky

Tato metoda je volána `CRowsetImpl` implementacemi rozhraní [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) a [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).

## <a name="setcommandtext"></a>CRowsetImpl:: SetCommandText

Ověří a uloží `DBID`s v obou řetězcích ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
pro Ukazatel na `DBID` reprezentující ID tabulky.

*pIndexID*<br/>
pro Ukazatel na `DBID` reprezentující ID indexu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Metoda `SetCommentText` je volána `CreateRowset`, statickou metodou založena `IOpenRowsetImpl`.

Tato metoda deleguje svou práci voláním [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) a [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) prostřednictvím přetypování ukazatele.

## <a name="getcolumninfo"></a>CRowsetImpl:: GetColumnInfo

Načte informace o sloupci pro konkrétní požadavek klienta.

### <a name="syntax"></a>Syntaxe

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>Parametry

*PV*<br/>
pro Ukazatel na odvozenou třídu uživatele `CRowsetImpl`.

*pcCols*<br/>
pro Ukazatel (výstup) na počet vrácených sloupců.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na statickou strukturu `ATLCOLUMNINFO`.

### <a name="remarks"></a>Poznámky

Tato metoda je pokročilé přepsání.

Tato metoda je volána několika základními třídami implementace pro načtení informací o sloupci pro konkrétní požadavek klienta. Obvykle by tato metoda byla volána `IColumnsInfoImpl`. Pokud přepíšete tuto metodu, je nutné umístit verzi metody do třídy odvozené od `CRowsetImpl`. Vzhledem k tomu, že metoda může být umístěna do třídy, která není založena, je nutné změnit *Souč_hod* na odpovídající třídu odvozenou od `CRowsetImpl`.

Následující příklad ukazuje použití `GetColumnInfo`. V tomto příkladu je `CMyRowset` odvozenou třídou `CRowsetImpl`. Chcete-li přepsat `GetColumnInfo` pro všechny instance této třídy, umístěte následující metodu do definice třídy `CMyRowset`:

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="getcommandfromid"></a>CRowsetImpl:: GetCommandFromID

Kontroluje, zda buď nebo oba parametry obsahují hodnoty řetězce, a pokud ano, zkopíruje řetězcové hodnoty do datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
pro Ukazatel na `DBID` reprezentující ID tabulky.

*pIndexID*<br/>
pro Ukazatel na `DBID` reprezentující ID indexu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda je volána prostřednictvím statického přetypování `CRowsetImpl` k naplnění datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Ve výchozím nastavení tato metoda kontroluje, zda buď oba parametry, nebo oba obsahují hodnoty v řetězci. Pokud obsahují hodnoty řetězce, tato metoda zkopíruje řetězcové hodnoty do datových členů. Vložením metody s tímto podpisem do vaší třídy odvozené od `CRowsetImpl`bude metoda volána místo základní implementace.

## <a name="validatecommandid"></a>CRowsetImpl:: ValidateCommandID

Kontroluje, zda buď nebo oba `DBID`s obsahují hodnoty řetězce, a pokud ano, zkopíruje je do datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>Parametry

*pTableID*<br/>
pro Ukazatel na `DBID` reprezentující ID tabulky.

*pIndexID*<br/>
pro Ukazatel na `DBID` reprezentující ID indexu.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato metoda je volána prostřednictvím statického přetypování `CRowsetImpl` k naplnění svých datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Ve výchozím nastavení tato metoda kontroluje, zda buď nebo obojí `DBID`s řetězcovými hodnotami, a pokud ano, zkopíruje je do svých datových členů. Vložením metody s tímto podpisem do vaší třídy odvozené od `CRowsetImpl`bude metoda volána místo základní implementace.

## <a name="rgrowdata"></a>CRowsetImpl:: m_rgRowData

Ve výchozím nastavení `CAtlArray`, který se templatizes na argumentu šablony záznamu uživatele `CRowsetImpl`.

### <a name="syntax"></a>Syntaxe

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>Poznámky

*ArrayType* je parametr šablony pro `CRowsetImpl`.

## <a name="strcommandtext"></a>CRowsetImpl:: m_strCommandText

Obsahuje počáteční příkaz sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="strindextext"></a>CRowsetImpl:: m_strIndexText

Obsahuje počáteční index sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```