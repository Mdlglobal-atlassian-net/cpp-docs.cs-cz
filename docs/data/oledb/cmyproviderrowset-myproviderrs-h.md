---
title: CMyProviderRowset (MyProviderRS.H) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c7c9830970f6e09d1993ac2fd78510b84068efaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021266"
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)

Průvodce vytvoří položku pro objektu sady řádků. V takovém případě se nazývá `CMyProviderRowset`. `CMyProviderRowset` Třída dědí ze třídy zprostředkovatele OLE DB volá `CRowsetImpl`, který implementuje všechna potřebná rozhraní objektu sady řádků. Následující kód ukazuje řetězec dědičnosti pro `CRowsetImpl`:  
  
```cpp  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T >>  
```  
  
`CRowsetImpl` také používá `IAccessor` a `IColumnsInfo` rozhraní. Tato rozhraní se používá pro výstupní pole tabulky. Třída rovněž poskytuje implementaci pro `IRowsetIdentity`, která umožňuje příjemci k určení, zda dva řádky jsou identické. `IRowsetInfo` Rozhraní implementuje vlastnosti objektu sady řádků. `IConvertType` Rozhraní umožňuje poskytovatelem a vyřešit rozdíly mezi datovými typy požadoval uživatel a používaných zprostředkovatelem.  
  
`IRowset` Rozhraní ve skutečnosti zpracovává data načítání. Příjemce nejprve volá metodu s názvem `GetNextRows` se vraťte na řádek, označované jako popisovač `HROW`. Pak zavolá příjemce `IRowset::GetData` s ním `HROW` načíst požadovaná data.  
  
`CRowsetImpl` také přijímá několik parametrů šablony. Tyto parametry umožňují určit, jak `CRowsetImpl` třída zpracovává data. `ArrayType` Argument umožňuje určit, jaký mechanismus úložiště se používá k ukládání dat řádku. *RowClass* parametr určuje, jaké třída obsahuje `HROW`.  
  
*RowsetInterface* parametr umožňuje použít také `IRowsetLocate` nebo `IRowsetScroll` rozhraní. `IRowsetLocate` a `IRowsetScroll` obě dědí z rozhraní `IRowset`. Šablony zprostředkovatele OLE DB proto musíte zadat speciální zpracování pro tato rozhraní. Pokud chcete použít některou z těchto rozhraní, budete muset použít tento parametr.  
  
## <a name="see-also"></a>Viz také  

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)