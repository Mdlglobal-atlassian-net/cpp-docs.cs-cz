---
title: CRowsetImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- GetColumnInfo
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1583a5cb6ff67943bde8af530593dff94986d551
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340472"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl – třída
Poskytuje standardní implementace technologie OLE DB sady řádků bez nutnosti vícenásobná dědičnost mnoho implementace rozhraní.  
  
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
 *T*  
 Třída odvozená z uživatele `CRowsetImpl`.  
  
 *Úložiště*  
 Třída uživatelského záznamu.  
  
 *CreatorClass*  
 Třídy, která obsahuje vlastnosti pro sadu řádků; obvykle příkaz.  
  
 *ArrayType*  
 Třída, která bude sloužit jako úložiště pro data v sadě řádků. Výchozí hodnota tohoto parametru `CAtlArray`, ale může být jakékoli třídy, které podporuje požadovanou funkci.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[NameFromDBID](#namefromdbid)|Extrahuje řetězce ze `DBID` a zkopíruje je do *bstr* předán.|  
|[SetCommandText](#setcommandtext)|Ověří a ukládá `DBID`ve dvou řetězců ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|  
  
### <a name="overridable-methods"></a>Přepisovatelné metody  
  
|||  
|-|-|  
|[GetColumnInfo –](#getcolumninfo)|Načte informace o sloupci pro žádost o konkrétního klienta.|  
|[Getcommandfromid –](#getcommandfromid)|Kontroluje, zda nebo oba parametry obsahovat řetězcové hodnoty a pokud ano, zkopíruje řetězcové hodnoty na datové členy [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID –](#validatecommandid)|Zkontroluje, zda je buď nebo obojí `DBID`s obsahovat řetězcové hodnoty a pokud ano, zkopíruje je do svých datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_rgRowData](#rgrowdata)|Ve výchozím nastavení `CAtlArray` , který templatizes na argumentu šablony záznamu uživatele `CRowsetImpl`. Jiné pole typu třídy je možné tak, že změníte `ArrayType` argument šablony pro `CRowsetImpl`.|  
|[m_strCommandText](#strcommandtext)|Obsahuje počáteční příkaz v sadě řádků.|  
|[m_strIndexText](#strindextext)|Obsahuje počáteční index v sadě řádků.|  
  
## <a name="remarks"></a>Poznámky  
 `CRowsetImpl` poskytuje přepsání ve formě upcasts statické. Metody řízení způsobu, ve kterém se ověří dané sadě řádků text příkazu. Můžete vytvořit svoje vlastní `CRowsetImpl`– styl tím, že vaše implementace rozhraní více zděděné třídy. Jedinou metodou, pro kterou je nutné zadat implementace je `Execute`. V závislosti na tom, jaký typ sady řádků vytváříte, bude očekávat metod creator různé podpisy pro `Execute`. Například, pokud používáte `CRowsetImpl`-odvozené třídy k implementaci sady řádků schématu `Execute` metoda bude mít následující podpis:  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Pokud vytváříte `CRowsetImpl`-odvozené třídy k implementaci příkazu nebo sady řádků relace, `Execute` metoda bude mít následující podpis:  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 K implementaci všech `CRowsetImpl`-odvozené `Execute` metod, musí naplnit vaše interní datové vyrovnávací paměti ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).  

## <a name="namefromdbid"></a> CRowsetImpl::NameFromDBID
Extrahuje řetězce ze `DBID` a zkopíruje je do *bstr* předán.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pDBID*  
 [in] Ukazatel `DBID` ze kterého budou extrahovány řetězec.  
  
 *BSTR*  
 [in] A [CComBSTR](../../atl/reference/ccombstr-class.md) odkaz na umístěte kopii `DBID` řetězec.  
  
 *bIndex*  
 [in] **true** Pokud indexu `DBID`; **false** Pokud má tabulka `DBID`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT. V závislosti na tom, zda `DBID` tabulky nebo indexu (udávají *bIndex*), metoda vrátí buď DB_E_NOINDEX nebo DB_E_NOTABLE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána metodou `CRowsetImpl` implementace [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) a [getcommandfromid –](../../data/oledb/crowsetimpl-getcommandfromid.md). 
  
## <a name="setcommandtext"></a> CRowsetImpl::SetCommandText
Ověří a ukládá `DBID`ve dvou řetězců ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pTableID*  
 [in] Ukazatel `DBID` představující ID tabulky.  
  
 *pIndexID*  
 [in] Ukazatel `DBID` představující ID indexu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 `SetCommentText` Metoda je volána metodou `CreateRowset`, šablona statickou metodu `IOpenRowsetImpl`.  
  
 Tato metoda deleguje svou práci voláním [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) a [getcommandfromid –](../../data/oledb/crowsetimpl-getcommandfromid.md) prostřednictvím upcasted ukazatele. 

## <a name="getcolumninfo"></a> CRowsetImpl::GetColumnInfo
Načte informace o sloupci pro žádost o konkrétního klienta.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>Parametry  
 *PV*  
 [in] Ukazatel na uživatele `CRowsetImpl` odvozené třídy.  
  
 *pcCols*  
 [in] Ukazatel (výstup) na číslo vrácených sloupců.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na statickou `ATLCOLUMNINFO` struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je pokročilá přepsání.  
  
 Tato metoda je volána v několika základní implementace tříd se načíst informace o sloupci pro žádost o konkrétního klienta. Obvykle by být tato metoda volána `IColumnsInfoImpl`. Pokud tuto metodu přepíšete, je nutné umístit verzi metoda ve vaší `CRowsetImpl`-odvozené třídy. Protože metoda můžete umístit v třídě šablona, je nutné změnit *pv* na příslušné `CRowsetImpl`-odvozené třídy.  
  
 Následující příklad ukazuje `GetColumnInfo` využití. V tomto příkladu `CMyRowset` je `CRowsetImpl`-odvozené třídy. Aby bylo možné přepsat `GetColumnInfo` pro všechny instance této třídy, umístěte následující metodu v `CMyRowset` definici třídy:  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  

## <a name="getcommandfromid"></a> CRowsetImpl::GetCommandFromID
Kontroluje, zda nebo oba parametry obsahovat řetězcové hodnoty a pokud ano, zkopíruje řetězcové hodnoty na datové členy [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pTableID*  
 [in] Ukazatel `DBID` představující ID tabulky.  
  
 *pIndexID*  
 [in] Ukazatel `DBID` představující ID indexu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána pomocí statické přetypování nahoru podle `CRowsetImpl` k naplnění datové členy [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Ve výchozím nastavení zkontroluje tato metoda, pokud nebo oba parametry obsahovat řetězcové hodnoty. Pokud obsahují řetězcové hodnoty, tato metoda zkopíruje řetězcové hodnoty na datové členy. Tak, že metoda s tímto podpisem ve vaší `CRowsetImpl`-odvozené třídy, vaše metoda bude volána místo základní implementaci. 

## <a name="validatecommandid"></a> CRowsetImpl::ValidateCommandID
Zkontroluje, zda je buď nebo obojí `DBID`s obsahovat řetězcové hodnoty a pokud ano, zkopíruje je do svých datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pTableID*  
 [in] Ukazatel `DBID` představující ID tabulky.  
  
 *pIndexID*  
 [in] Ukazatel `DBID` představující ID indexu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána pomocí statické přetypování nahoru podle `CRowsetImpl` k naplnění svých datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Ve výchozím nastavení, tato metoda zkontroluje, zda je buď nebo obojí `DBID`s obsahovat řetězcové hodnoty a pokud ano, zkopíruje je do svých datových členů. Tak, že metoda s tímto podpisem ve vaší `CRowsetImpl`-odvozené třídy, vaše metoda bude volána místo základní implementaci.  

## <a name="rgrowdata"></a> CRowsetImpl::m_rgRowData
Ve výchozím nastavení `CAtlArray` , který templatizes na argumentu šablony záznamu uživatele `CRowsetImpl`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;  
```  
  
### <a name="remarks"></a>Poznámky  
 *ArrayType* je parametr šablony `CRowsetImpl`.  

## <a name="strcommandtext"></a> CRowsetImpl::m_strCommandText
Obsahuje počáteční příkaz v sadě řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;  
```  

## <a name="strindextext"></a> CRowsetImpl::m_strIndexText
Obsahuje počáteční index v sadě řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;  
``` 