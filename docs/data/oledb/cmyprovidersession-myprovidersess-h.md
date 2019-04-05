---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 5cb462aba671e79450e9ee7b8447410252f8edc9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023461"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Vlastní*Sess.H obsahuje deklaraci a implementaci objektu relace technologie OLE DB. Objekt zdroje dat vytvoří objekt relace a představuje konverzaci mezi spotřebitele a zprostředkovatele. Několik souběžných relací může být otevřené pro jeden zdroj. V seznamu dědičnosti `CCustomSession` následující:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession : 
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

Objekt relace dědí z `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, a `IDBCreateCommand`. `IGetDataSource` Rozhraní umožňuje relaci získání zdroje dat, která ho vytvořila. To je užitečné, pokud je potřeba získat vlastnosti ze zdroje dat, který jste vytvořili nebo Další informace, které zdroj dat může poskytovat. `ISessionProperties` Rozhraní zpracovává všechny vlastnosti v relaci. `IOpenRowset` a `IDBCreateCommand` rozhraní se používají k práci databáze. Pokud zprostředkovatel podporuje příkazy, implementuje `IDBCreateCommand` rozhraní. Používá se k vytvoření objektu příkazu, který můžete spouštět příkazy. Zprostředkovatel vždy implementuje `IOpenRowset` objektu. Používá se k vygenerování sady řádků od poskytovatele. Je výchozí sada řádků (například `"select * from mytable"`) od poskytovatele.

Průvodce také vytvoří tři třídy relace: `CCustomSessionColSchema`, `CCustomSessionPTSchema`, a `CCustomSessionTRSchema`. Tyto relace se používají pro sad řádků schématu. Sady řádků schématu povolit zprostředkovatele vrátit metadata pro příjemce bez příjemce by bylo nutné provést dotaz nebo načíst data. Načítají se metadata může být mnohem rychlejší než hledání možnosti poskytovatele.

Specifikaci OLE DB vyžaduje, aby implementace zprostředkovatele `IDBSchemaRowset` typy sada řádků schématu rozhraní podporu tři: DBSCHEMA_COLUMNS DBSCHEMA_PROVIDER_TYPES a DBSCHEMA_TABLES. Průvodce vytvoří implementacemi pro každý sada řádků schématu. Každá třída generované průvodcem knihovnou obsahuje `Execute` metody. V tomto `Execute` metoda může vrátit data poskytovatele, o které tabulky, sloupce a datové typy, které podporujete. Tato data je známá v době kompilace.

## <a name="see-also"></a>Viz také:

[Poskytovatel souborů vytvořených průvodcem](../../data/oledb/provider-wizard-generated-files.md)<br/>
