---
title: CCustomCommand (CustomRS.H) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d3f6b8775ab876834555e7c47e469c72d3a150b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807728"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand` Třída je implementace objektu command zprostředkovatel. Poskytuje implementaci pro `IAccessor`, `ICommandText`, a `ICommandProperties` rozhraní. `IAccessor` Rozhraní je stejný jako v dané sadě řádků. Objekt příkazu používá přistupující k určení vazby parametrů. Objektu sady řádků je používá k určení vazby pro výstupní sloupce. `ICommandText` Rozhraní je užitečný způsob, jak určit textový příkaz. V tomto příkladu `ICommandText` rozhraní později, když přidá vlastní kód; Potlačí také `ICommand::Execute` metody. `ICommandProperties` Rozhraní zpracovává všechny vlastnosti pro objekty příkazu a sady řádků.  
  
```cpp  
// CCustomCommand  
class ATL_NO_VTABLE CCustomCommand :   
class ATL_NO_VTABLE CCustomCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CCustomCommand>,  
   public ICommandTextImpl<CCustomCommand>,  
   public ICommandPropertiesImpl<CCustomCommand>,  
   public IObjectWithSiteImpl<CCustomCommand>,  
   public IConvertTypeImpl<CCustomCommand>,  
   public IColumnsInfoImpl<CCustomCommand>  
```  
  
`IAccessor` Rozhraní spravuje všechny vazby použité v příkazech a sady řádků. Příjemce volání `IAccessor::CreateAccessor` s polem `DBBINDING` struktury. Každý `DBBINDING` struktura obsahuje informace o tom, jak by měly být zpracovány vazeb sloupců (jako je například typ a délku). Zprostředkovatel přijímá struktury a určuje, jak by se měly převést data a zda jsou všechny převody potřebné. `IAccessor` Rozhraní se používá v objektu příkazu pro zpracování libovolných parametrů v příkazu.  
  
Objekt příkazu také poskytuje implementaci `IColumnsInfo`. OLE DB vyžaduje `IColumnsInfo` rozhraní. Rozhraní umožňuje příjemci k načtení informací o parametry příkazu. Pomocí objektu sady řádků `IColumnsInfo` rozhraní, který vrací informace o výstupní sloupce k poskytovateli.  
  
Zprostředkovatel také obsahuje rozhraní volá `IObjectWithSite`. `IObjectWithSite` Rozhraní bylo implementováno v knihovně ATL 2.0 a umožňuje implementátora k předávání informací o samotné do jeho podřízených. Objekt příkazu používá `IObjectWithSite` informace zjistit všechny generují rozhraní objektu sady řádků je vytvořil.  
  
## <a name="see-also"></a>Viz také  

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)