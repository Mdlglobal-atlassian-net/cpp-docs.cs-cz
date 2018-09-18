---
title: Referenční dokumentace šablony OLE DB poskytovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3bafe1aa7197ef037bdd54b7215173866e8c15d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039150"
---
# <a name="ole-db-provider-templates-reference"></a>Referenční dokumentace k šablonám zprostředkovatelů OLE DB

Třídy a rozhraní pro šablony zprostředkovatele technologie OLE DB mohou být seskupeny do následujících kategorií. Referenční materiál obsahuje také informace o [makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
Třídy používají následujícími zásadami vytváření názvů: třída s názvem se vzorem `IWidgetImpl` by poskytnout implementaci rozhraní `IWidget`.  
  
## <a name="session-classes"></a>Třídy relace  

[Idbcreatesessionimpl –](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní na nově vytvořené relace. Povinné rozhraní na objekty zdroje dat  
  
[Isessionpropertiesimpl –](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implementuje vlastnosti relace voláním statické funkce definované mapou sady vlastností. Mapa set vlastnosti musí být zadán v třídě relace. Povinné rozhraní na relace.  
  
## <a name="rowset-classes"></a>Třídy sady řádků  

[CRowsetImpl –](../../data/oledb/crowsetimpl-class.md)  
  
Poskytuje standardní implementace technologie OLE DB sady řádků bez nutnosti vícenásobná dědičnost mnoho implementace rozhraní. Jedinou metodou, pro kterou je nutné zadat implementace je `Execute`.  
  
[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Poskytuje výchozí implementaci pro popisovač řádku, který je používán `IRowsetImpl` třídy. Popisovač řádku jsou logicky jedinečný klíčová slova pro řádek výsledek. `IRowsetImpl` Vytvoří novou `CSimpleRow` pro každý řádek požaduje v `IRowsetImpl::GetNextRows`.  
  
[IAccessorImpl –](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB vyžaduje poskytovatele, jak implementovat `HACCESSOR`, což je značka na pole `DBBINDING` struktury. Poskytuje `HACCESSOR`, které jsou adresy `BindType` struktury. Povinné na příkazy a sady řádků.  
  
[Icolumnsinfoimpl –](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Delegáty pro statické funkce definované mapou sloupec zprostředkovatele. Povinné rozhraní sady řádků a příkazy.  
  
[Iconverttypeimpl –](../../data/oledb/iconverttypeimpl-class.md)<br/>
Poskytuje informace o dostupnosti převody typů příkazu nebo pro sadu řádků. Povinné na příkazy, sady řádků a index sady řádků. Implementuje `IConvertType` rozhraní delegováním převodu objektu poskytnutých OLE DB.  
  
[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implementuje `IDBSchemaRowset` rozhraní a funkce přepsaly creator `CreateSchemaRowset`.  
  
[Iopenrowsetimpl –](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Otevře se a vrátí sadu řádků, který obsahuje všechny řádky z jedné základní tabulky nebo indexu. Povinné rozhraní pro objekt relace.  
  
[IRowsetChangeImpl –](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implementuje rozhraní OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) rozhraní, která umožňuje aktualizaci hodnot sloupce v existující řádky, odstranění řádků a vložením nových řádků.  
  
[Irowsetcreatorimpl –](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Tato třída dědí z [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) a přepíše [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` provádí stejné funkce jako `IObjectWithSite` ale taky umožňuje vlastnosti OLE DB `DBPROPCANSCROLLBACKWARDS` a `DBPROPCANFETCHBACKWARDS`.  
  
[Irowsetidentityimpl –](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implementuje `IRowsetIdentity` rozhraní, které vám umožní porovnat, zda dva řádky dat jsou stejné, nebo ne.  
  
[IRowsetImpl –](../../data/oledb/irowsetimpl-class.md)<br/>
Poskytuje implementaci `IRowset` rozhraní, což je rozhraní základní sady řádků.  
  
[Irowsetinfoimpl –](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implementuje vlastnosti sady řádků pomocí vlastnosti nastavit mapování definované ve třídě příkazu. Povinné rozhraní na sady řádků.  
  
[IRowsetLocateImpl –](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implementuje rozhraní OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\)) rozhraní, která načte libovolné řádky ze sady řádků. Pro podporu technologie OLE DB záložky v sadě řádků, ujistěte se, v sadě řádků z této třídy dědit.  
  
[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implementuje vysílání funkce radit naslouchacích procesů najdete v bodě připojení `IID_IRowsetNotify` změny obsahu v sadě řádků. Implementovat příjemce, kteří zpracování oznámení [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\)) , zaregistrujte je v bodě připojení.  
  
[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implementuje rozhraní OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401\(v=vs.85\)) rozhraní, která umožňuje uživatelům zpoždění přenosu změn provedených s [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) do zdroje dat a vrátit zpět změny před samotným přenosem.  
  
## <a name="command-classes"></a>Třídy příkazů  

[Icommandimpl –](../../data/oledb/icommandimpl-class.md)<br/>
Poskytuje implementaci `ICommand` rozhraní. Toto rozhraní není viditelný, ale zařizuje služba `ICommandTextImpl`. Povinné rozhraní pro objekt příkazu.  
  
[Icommandpropertiesimpl –](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Tato implementace `ICommandProperties` rozhraní poskytuje statické funkce definované `BEGIN_PROPSET_MAP` – makro. Povinné na příkazy.  
  
[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Nastaví, ukládá a vrací text příkazu. Povinné na příkazy.  
  
[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Vytvoří nový příkaz z objektu relace a vrací požadovaná rozhraní na nově vytvořený příkaz. Volitelné rozhraní pro objekty relace.  
  
Další příkaz třídy jsou `IColumnsInfoImpl` a `IAccessorImpl`, které jsou popsány v části třídy sady řádků výše.  
  
## <a name="data-source-classes"></a>Třídy zdroje dat  

[Idbinitializeimpl –](../../data/oledb/idbinitializeimpl-class.md)<br/>
Vytvoří a odstraní připojení ke spotřebiteli. Povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory.  
  
[Idbpropertiesimpl –](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` je povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory. Nicméně pokud enumerátor zpřístupní `IDBInitialize`, musí vystavit `IDBProperties` (Vlastnosti zdroje dat).  
  
[Igetdatasourceimpl –](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Získá ukazatel na objekt zdroje dat rozhraní. Povinné rozhraní v relaci.  
  
## <a name="other-classes"></a>Jiné třídy  

[CUtlProps –](../../data/oledb/cutlprops-class.md)<br/>
Implementuje vlastnosti pro celou řadu vlastností rozhraní technologie OLE DB (například `IDBProperties`, `ISessionProperties`, a `IRowsetInfo`).  
  
[Ierrorrecordsimpl –](../../data/oledb/ierrorrecordsimpl-class.md)  
  
Implementuje rozhraní OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) rozhraní, přidání záznamů do a načtení záznamů z datového členu.  
  
## <a name="see-also"></a>Viz také  

[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Šablony OLE DB](../../data/oledb/ole-db-templates.md)