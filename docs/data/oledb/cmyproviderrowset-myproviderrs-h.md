---
title: CMyProviderRowset (MyProviderRS.H) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a4a786a5980763a0588456004efafc02978365e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
Průvodce generuje položku pro objektu sady řádků. V takovém případě se nazývá `CMyProviderRowset`. `CMyProviderRowset` Třída dědí z třídy zprostředkovatele OLE DB názvem `CRowsetImpl`, který implementuje všechna rozhraní, které jsou nezbytné pro objektu sady řádků. Následující kód ukazuje řetězec dědičnosti pro `CRowsetImpl`:  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T >>  
```  
  
 `CRowsetImpl` používá také `IAccessor` a `IColumnsInfo` rozhraní. Používá tato rozhraní pro výstup pole v tabulkách. Třída také poskytuje implementaci pro **IRowsetIdentity**, což umožňuje příjemci zjistit, zda jsou dva řádky identické. `IRowsetInfo` Rozhraní implementuje vlastnosti objektu sady řádků. **IConvertType** rozhraní umožňuje poskytovateli vyřešte rozdíly mezi datovými typy požadoval příjemce a používaných zprostředkovatelem.  
  
 `IRowset` Rozhraní ve skutečnosti zpracovává načítání data. Příjemce nejprve volá metodu s názvem `GetNextRows` pro vrácení popisovače na řádek, označuje jako **HROW**. Příjemce potom volá **IRowset::GetData** s třídou **HROW** načíst požadovaná data.  
  
 `CRowsetImpl` také trvá několik parametrů šablony. Tyto parametry umožňují určit, jak `CRowsetImpl` třída zpracovává data. `ArrayType` Argument umožňuje určit, jaký mechanismus úložiště se používá k ukládání dat řádku. **RowClass** parametr určuje, jaké třída obsahuje **HROW**.  
  
 **RowsetInterface** parametr můžete také použít `IRowsetLocate` nebo `IRowsetScroll` rozhraní. `IRowsetLocate` a `IRowsetScroll` rozhraní obě dědí z `IRowset`. Šablony zprostředkovatele technologie OLE DB tedy musí zadat zvláštní zpracování těchto rozhraní. Pokud chcete použít některou z těchto rozhraní, budete muset použít tento parametr.  
  
## <a name="see-also"></a>Viz také  
 [Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)