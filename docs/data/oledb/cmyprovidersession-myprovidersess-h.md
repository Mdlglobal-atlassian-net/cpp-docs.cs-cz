---
title: CMyProviderSession (MyProviderSess.H) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2d74c79535a97e8864ad55d3b0cfb35f98bb5ba4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106080"
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)

MyProviderSess.H obsahuje deklaraci a implementaci objektu relace technologie OLE DB. Objekt zdroje dat vytvoří objekt relace a představuje konverzaci mezi spotřebitele a zprostředkovatele. Několik souběžných relací může být otevřené pro jeden zdroj. V seznamu dědičnosti `CMyProviderSession` následující:  
  
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
  
Objekt relace dědí z `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, a `IDBCreateCommand`. `IGetDataSource` Rozhraní umožňuje relaci získání zdroje dat, která ho vytvořila. To je užitečné, pokud je potřeba získat vlastnosti ze zdroje dat, který jste vytvořili nebo Další informace, které zdroj dat může poskytovat. `ISessionProperties` Rozhraní zpracovává všechny vlastnosti v relaci. `IOpenRowset` a `IDBCreateCommand` rozhraní se používají k práci databáze. Pokud zprostředkovatel podporuje příkazy, implementuje `IDBCreateCommand` rozhraní. Používá se k vytvoření objektu příkazu, který můžete spouštět příkazy. Zprostředkovatel vždy implementuje `IOpenRowset` objektu. Používá se k vygenerování jednoduché sady řádků od poskytovatele. Je výchozí sada řádků (například `"select * from mytable"`) od poskytovatele.  
  
Průvodce také vytvoří tři třídy relace: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, a `CMyProviderSessionTRSchema`. Tyto relace se používají pro sad řádků schématu. Sady řádků schématu povolit zprostředkovatele vrátit metadata pro příjemce bez příjemce by bylo nutné provést dotaz nebo načíst data. Načítají se metadata může být mnohem rychlejší než vyhledávání možností zprostředkovatelů.  
  
Specifikaci OLE DB vyžaduje, aby implementace zprostředkovatele `IDBSchemaRowset` typy sada řádků schématu rozhraní podporu tři: DBSCHEMA_COLUMNS DBSCHEMA_PROVIDER_TYPES a DBSCHEMA_TABLES. Průvodce vytvoří implementacemi pro každý sada řádků schématu. Každá třída generované průvodcem knihovnou obsahuje `Execute` metody. V tomto `Execute` metoda může vrátit data poskytovatele, o které tabulky, sloupce a datové typy, které podporujete. Tato data se obvykle označuje v době kompilace.  
  
## <a name="see-also"></a>Viz také  

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)