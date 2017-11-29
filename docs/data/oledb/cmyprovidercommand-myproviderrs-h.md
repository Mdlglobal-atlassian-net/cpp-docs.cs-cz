---
title: CMyProviderCommand (MyProviderRS.H) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68846352d3e6b407a4ec7ef6b7993969371a89de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
`CMyProviderCommand` Třída je implementace pro objekt příkazu zprostředkovatele. Poskytuje implementaci pro `IAccessor`, `ICommandText`, a **ICommandProperties** rozhraní. `IAccessor` Rozhraní je stejný jako ten, který v dané sadě řádků. Objekt příkazu používá přistupující objekt k určení vazby parametrů. Objekt sady řádků je používá k určení vazby pro výstupní sloupce. `ICommandText` Rozhraní je užitečný způsob, jak určit textový příkaz. Tento příklad používá `ICommandText` rozhraní později, když přidá vlastní kód; Potlačí také `ICommand::Execute` metoda. **ICommandProperties** rozhraní zpracovává všechny vlastnosti pro objekty příkazu a sady řádků.  
  
```  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
 `IAccessor` Rozhraní spravuje všechny vazby používané v příkazech a sady řádků. Volání příjemce **IAccessor::CreateAccessor** s pole **DBBINDING** struktury. Každý **DBBINDING** struktura obsahuje informace o tom, jak by měly být zpracovány vazeb sloupců (například typ a délku). Zprostředkovatel obdrží struktury a určuje, jak by se měly převést data a zda jsou nutné převody. `IAccessor` Rozhraní v objektu command slouží ke zpracování všech parametrů v příkazu.  
  
 Také poskytuje implementaci pro objekt příkazu `IColumnsInfo`. OLE DB vyžaduje `IColumnsInfo` rozhraní. Rozhraní umožňuje příjemci získat informace o parametrech z příkazu. Objekt sady řádků používá `IColumnsInfo` rozhraní k vrácení informací o výstupních sloupcích ke zprostředkovateli.  
  
 Zprostředkovatel také obsahuje rozhraní nazvané `IObjectWithSite`. `IObjectWithSite` Rozhraní je implementováno v knihovně ATL 2.0 a umožňuje implementátorovi předání informace o samotné a jeho podřízené. Objekt příkazu používá `IObjectWithSite` informace říct všechny generují objektu sady řádků je vytvořil.  
  
## <a name="see-also"></a>Viz také  
 [Poskytovatel souborů vytvořených průvodcem](../../data/oledb/provider-wizard-generated-files.md)