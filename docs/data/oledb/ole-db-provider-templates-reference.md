---
title: "Referenční dokumentace šablony zprostředkovatele OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.templates.ole
dev_langs: C++
helpviewer_keywords: OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4b8271e7a5a69c91612a3bda13ad4b1cc817f012
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-provider-templates-reference"></a>Referenční dokumentace k šablonám zprostředkovatelů OLE DB
Třídy a rozhraní pro šablony zprostředkovatele technologie OLE DB, je možné seskupit do následujících kategorií. Referenční materiál také obsahuje informace o [makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
 Třídy používají následující konvence: třídy s názvem se vzorkem **IWidgetImpl** by poskytnout implementaci rozhraní **IWidget**.  
  
## <a name="session-classes"></a>Třídy relace  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 Vytvoří novou relaci z objekt zdroje dat a vrátí požadované rozhraní v nově vytvořené relace. Povinné rozhraní na objekty zdroje dat.  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 Implementuje vlastnosti relace voláním statickou funkci definované mapy sady vlastností. Mapy sady vlastností musí být zadán v třídě relace. Povinné rozhraní na relací.  
  
## <a name="rowset-classes"></a>Třídy sady řádků  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 Poskytuje standardní implementace sady řádků OLE DB bez nutnosti vícenásobná dědičnost mnoho implementaci rozhraní. Jedinou metodou, pro které je nutné zadat, je implementace **Execute**.  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 Poskytuje výchozí implementaci pro popisovač řádku, který je používán `IRowsetImpl` třídy. Popisovač řádku je logicky jedinečný kód pro řádek, výsledek. `IRowsetImpl`Vytvoří novou `CSimpleRow` pro každý řádek požadované v `IRowsetImpl::GetNextRows`.  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB vyžaduje poskytovatelům implementovat **HACCESSOR**, což je značka na pole **DBBINDING** struktury. Poskytuje **HACCESSOR**s, které jsou adresy **BindType** struktury. Povinné na příkazy a sady řádků.  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 Delegáti statické funkce definované mapu sloupců poskytovatele. Povinné rozhraní na příkazy a sady řádků.  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 Poskytuje informace o dostupnosti převody typů v příkazu nebo pro sadu řádků. Povinné na příkazy, sady řádků a sady řádků index. Implementuje **IConvertType** rozhraní delegováním k objektu převod poskytl OLE DB.  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 Implementuje **IDBSchemaRowset** rozhraní a funkce šablonou creator `CreateSchemaRowset`.  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 Otevře a vrací sadu řádků, který zahrnuje všechny řádky z jedné základní tabulky nebo indexu. Povinné rozhraní pro objekt relace.  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 Implementuje OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) rozhraní, která umožňuje aktualizaci hodnot sloupců v existujících řádků, odstranění řádků a vkládání nových řádků.  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 Tato třída dědí z [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) a přepíše [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). `IRowsetCreatorImpl`provádí stejné funkce jako `IObjectWithSite` , ale taky umožňuje vlastnosti OLE DB **DBPROPCANSCROLLBACKWARDS** a **DBPROPCANFETCHBACKWARDS**.  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 Implementuje **IRowsetIdentity** rozhraní, což vám umožní porovnat, zda jsou dva řádky dat identické nebo ne.  
  
 [IRowsetImpl –](../../data/oledb/irowsetimpl-class.md)  
 Představuje implementaci objektu `IRowset` rozhraní, což je rozhraní pro základní sady řádků.  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 Implementuje vlastnosti sady řádků pomocí vlastnosti nastavit mapy definovaný ve třídě příkaz. Povinné rozhraní na sady řádků.  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 Implementuje OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) rozhraní, která načte libovolný řádky ze sady řádků. Pro podporu technologie OLE DB záložky v sadě řádků, zkontrolujte řádků z této třídy dědit.  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 Implementuje vysílání funkce pro navedení naslouchací procesy ve spojovacím bodě **IID_IRowsetNotify** změny obsah sady řádků. Příjemci, které zpracovávají oznámení implementovat [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) a zaregistrovat ho v tomto bodě připojení.  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 Implementuje OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) rozhraní, která umožňuje příjemci sdělovat změny provedené s [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) do zdroje dat a vrátit zpět změny před samotným přenosem.  
  
## <a name="command-classes"></a>Třídy příkazů  
 [Icommandimpl –](../../data/oledb/icommandimpl-class.md)  
 Představuje implementaci objektu `ICommand` rozhraní. Toto rozhraní není viditelný, ale jsou zpracována **ICommandTextImpl**. Povinné rozhraní pro objekt příkazu.  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 Tato implementace **ICommandProperties** rozhraní poskytuje statické funkce definované `BEGIN_PROPSET_MAP` makro. Povinné na příkazy.  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 Nastaví, ukládá a vrátí text příkazu. Povinné na příkazy.  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 Vytvoří nový příkaz z objektu session a vrátí požadované rozhraní na nově vytvořený příkaz. Volitelné rozhraní na objekty relace.  
  
 Další příkaz třídy jsou `IColumnsInfoImpl` a `IAccessorImpl`, které jsou popsány v části třídy sady řádků výše.  
  
## <a name="data-source-classes"></a>Třídy zdroje dat  
 [Idbinitializeimpl –](../../data/oledb/idbinitializeimpl-class.md)  
 Vytvoří nebo odstraní připojení k příjemce. Povinné rozhraní na objekty zdroje dat a volitelné rozhraní na výčty.  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties`je povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro výčty. Ale pokud enumerátor zpřístupní **IDBInitialize**, musí vystavit `IDBProperties` (Vlastnosti zdroje dat).  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 Získá ukazatele rozhraní pro objekt zdroje dat. Povinné rozhraní v relaci.  
  
## <a name="other-classes"></a>Ostatní třídy  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 Implementuje vlastnosti pro celou řadu vlastností rozhraní OLE DB (například `IDBProperties`, **ISessionProperties**, a `IRowsetInfo`).  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 Implementuje OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) rozhraní, přidání záznamů do a načítání záznamů ze člena.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Šablony technologie OLE DB](../../data/oledb/ole-db-templates.md)