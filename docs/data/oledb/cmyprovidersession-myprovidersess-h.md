---
title: CMyProviderSession (MyProviderSess.H) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ffb1a0ca8e9a2cd5b90d33c21423beb0969a4f4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H obsahuje prohlášení a implementací objektu session OLE DB. Objekt zdroje dat vytvoří objekt relace a představuje konverzaci mezi příjemcem a zprostředkovatelem. Několik souběžných relací může být otevřené pro jeden zdroj dat.. V seznamu dědičnosti `CMyProviderSession` následuje:  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
 Objekt relace dědí z **IGetdataaSource**, `IOpenRowset`, **ISessionProperties**, a **IDBCreateCommand**. **IGetdataaSource** rozhraní, které umožňuje relaci načíst zdroj dat, která ji vytvořila. To je užitečné, pokud potřebujete získat vlastnosti ze zdroje dat, který jste vytvořili nebo Další informace, které můžete zadat zdroj dat. **ISessionProperties** rozhraní zpracovává všechny vlastnosti v relaci. `IOpenRowset` a **IDBCreateCommand** rozhraní se používají k práci databáze. Pokud poskytovatel podporuje příkazy, implementuje **IDBCreateCommand** rozhraní. Slouží k vytvoření objektu command, která může spustit příkazy. Zprostředkovatel vždy implementuje `IOpenRowset` objektu. Slouží ke generování jednoduché sady řádků od zprostředkovatele. Je to výchozí sada řádků (například `"select * from mytable"`) od zprostředkovatele.  
  
 Průvodce vytvoří také tři třídy relace: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, a `CMyProviderSessionTRSchema`. Tyto relace se používají pro sady řádků schématu. Schéma sad řádků povolí zprostředkovateli vrátit metadata k příjemce, aniž by museli provést dotazu nebo načtení dat příjemce. Načítání metadat může být mnohem rychlejší než vyhledávání možností zprostředkovatelů.  
  
 Specifikace OLE DB vyžaduje, aby implementace zprostředkovatele **IDBSchemaRowset** typy sady řádků schématu podporu tři rozhraní: **DBSCHEMA_COLUMNS**, **DBSCHEMA_PROVIDER_TYPES **, a `DBSCHEMA_TABLES`. Průvodce generuje implementace pro každou sadu řádků schématu. Každá třída je vygenerovat průvodcem obsahuje `Execute` metoda. V tomto `Execute` metodu, můžete se vrátit data poskytovatele, o které tabulky, sloupce a typy dat, které podporujete. Tato data se obvykle označuje v době kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)