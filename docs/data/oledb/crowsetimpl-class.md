---
title: CRowsetImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- CRowsetImpl class
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eece641adacd6ce918929366c4fc6dc78105e71a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetimpl-class"></a>CRowsetImpl – třída
Poskytuje standardní implementace sady řádků OLE DB bez nutnosti vícenásobná dědičnost mnoho implementaci rozhraní.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Uživatele třída odvozená z `CRowsetImpl`.  
  
 `Storage`  
 Třída záznamu uživatele.  
  
 `CreatorClass`  
 Třídu, která obsahuje vlastnosti pro sadu řádků; obvykle příkaz.  
  
 `ArrayType`  
 Třída, která bude sloužit jako úložiště pro data sady řádků. Použije se výchozí hodnota tohoto parametru `CAtlArray`, ale může být jakákoli třída, která podporuje požadovanou funkci.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|Extrahuje řetězec z **DBID** a zkopíruje je do `bstr` předaná.|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|Ověří a ukládá **DBID**s v dva řetězce ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).|  
  
### <a name="overridable-methods"></a>Přepisovatelné metody  
  
|||  
|-|-|  
|[GetColumnInfo –](../../data/oledb/crowsetimpl-getcolumninfo.md)|Načte informace o sloupci pro požadavek na konkrétní klienta.|  
|[Getcommandfromid –](../../data/oledb/crowsetimpl-getcommandfromid.md)|Kontroluje, zda nebo oba parametry obsahovat řetězcové hodnoty, a pokud ano, zkopíruje řetězcové hodnoty datových členů [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
|[ValidateCommandID –](../../data/oledb/crowsetimpl-validatecommandid.md)|Zkontroluje, zda buď nebo obojí **DBID**s obsahovat řetězcové hodnoty a pokud ano, kopíruje je do svých členů dat [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) a [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|Ve výchozím nastavení `CAtlArray` , templatizes na argument šablony záznamů uživatele `CRowsetImpl`. Jiné třídy typu pole lze změnou `ArrayType` šablony argument `CRowsetImpl`.|  
|[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|Obsahuje sadu řádků počáteční příkaz.|  
|[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|Obsahuje sadu řádků počáteční index.|  
  
## <a name="remarks"></a>Poznámky  
 `CRowsetImpl` poskytuje přepsání ve formě statické upcasts. Metody určit způsob, ve kterém bude dané sadě řádků ověření text příkazu. Můžete vytvořit vlastní `CRowsetImpl`– styl třídy tím, že vaše implementace rozhraní zděděná více. Jedinou metodou, pro které je nutné zadat, je implementace **Execute**. V závislosti na tom, jaký typ řádků vytváříte, bude metody creator očekávat různé podpisy pro **Execute**. Například, pokud používáte `CRowsetImpl`-odvozené třídy k implementaci sadu řádků schématu **Execute** metoda bude mít následující podpis:  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 Pokud vytváříte `CRowsetImpl`-odvozené třídy k implementaci příkazu nebo sady řádků relace, **Execute** metoda bude mít následující podpis:  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 K implementaci některé z `CRowsetImpl`-odvozené **Execute** metod, musí naplnit vaše interní datové vyrovnávací paměti ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h