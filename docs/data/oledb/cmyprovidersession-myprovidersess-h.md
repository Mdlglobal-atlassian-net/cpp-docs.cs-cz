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
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079761"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Vlastní* Sess. H obsahuje deklaraci a implementaci objektu relace OLE DB. Objekt zdroje dat vytvoří objekt Session a představuje konverzaci mezi příjemcem a poskytovatelem. Pro jeden zdroj dat lze otevřít několik současných relací. Seznam dědičnosti pro `CCustomSession` následující:

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

Objekt Session dědí z `IGetDataSource`, `IOpenRowset`, `ISessionProperties`a `IDBCreateCommand`. Rozhraní `IGetDataSource` umožňuje relaci načíst zdroj dat, který ho vytvořil. To je užitečné v případě, že potřebujete získat vlastnosti ze zdroje dat, který jste vytvořili, nebo jiných informací, které může zdroj dat poskytnout. Rozhraní `ISessionProperties` zpracovává všechny vlastnosti relace. Rozhraní `IOpenRowset` a `IDBCreateCommand` slouží k tomu, aby databáze fungovala. Pokud zprostředkovatel podporuje příkazy, implementuje rozhraní `IDBCreateCommand`. Slouží k vytvoření objektu příkazu, který může spustit příkazy. Zprostředkovatel vždy implementuje objekt `IOpenRowset`. Používá se ke generování sady řádků od poskytovatele. Je to výchozí sada řádků (například `"select * from mytable"`) od poskytovatele.

Průvodce také generuje tři třídy relace: `CCustomSessionColSchema`, `CCustomSessionPTSchema`a `CCustomSessionTRSchema`. Tyto relace jsou používány pro sady řádků schématu. Sady řádků schématu umožňují poskytovateli vracet metadata příjemci bez nutnosti spustit dotaz nebo načíst data. Načítající metadata můžou být daleko rychlejší než nalezení schopností poskytovatele.

Specifikace OLE DB vyžaduje, aby poskytovatelé implementující rozhraní `IDBSchemaRowset` podporovaly tři typy sad řádků schématu: DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES a DBSCHEMA_TABLES. Průvodce generuje implementace pro každou sadu řádků schématu. Každá třída vygenerovaná průvodcem obsahuje metodu `Execute`. V této `Execute` metody můžete vrátit data zprostředkovateli, které tabulky, sloupce a datové typy, které podporujete. Tato data jsou známá v době kompilace.

## <a name="see-also"></a>Viz také

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)<br/>
