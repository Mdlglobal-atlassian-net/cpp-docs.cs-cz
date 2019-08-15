---
title: Referenční dokumentace k šablonám zprostředkovatelů OLE DB
ms.date: 11/04/2016
f1_keywords:
- vc.templates.ole
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: 4c89d22cc66937ef9e10636bec79e2cf8b7de43c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501332"
---
# <a name="ole-db-provider-templates-reference"></a>Referenční dokumentace k šablonám zprostředkovatelů OLE DB

Třídy a rozhraní pro šablony poskytovatele OLE DB mohou být seskupeny do následujících kategorií. Referenční materiál obsahuje také informace o makrech [pro šablony zprostředkovatele OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).

Třídy používají následující konvence pojmenování: třída s názvem se vzorem `IWidgetImpl` by poskytovala implementaci rozhraní. `IWidget`

## <a name="session-classes"></a>Třídy relací

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Vytvoří novou relaci z objektu zdroje dat a vrátí požadované rozhraní v nově vytvořené relaci. Povinné rozhraní pro objekty zdroje dat

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implementuje vlastnosti relace voláním statické funkce definované mapou sady vlastností. V třídě relace by měla být zadána mapa sady vlastností. Povinné rozhraní v relacích

## <a name="rowset-classes"></a>Třídy sady řádků

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Poskytuje standardní OLE DB implementaci sady řádků bez nutnosti vícenásobné dědění mnoha implementačních rozhraní. Jedinou metodou, pro kterou je nutné zadat implementaci, `Execute`je.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Poskytuje výchozí implementaci pro popisovač řádku, který se používá ve `IRowsetImpl` třídě. Popisovač řádku je logicky jedinečný tag pro řádek výsledku. `IRowsetImpl`Vytvoří nový `CSimpleRow` pro každý požadovaný řádek v `IRowsetImpl::GetNextRows`.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB vyžaduje `HACCESSOR`, aby poskytovatelé implementovali, což je značka pro `DBBINDING` pole struktur. Poskytuje `HACCESSOR`adresy pro tyto `BindType` struktury. Povinné pro sady řádků a příkazy.

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Deleguje delegáty statické funkce definované mapou sloupce zprostředkovatele. Povinné rozhraní pro sady řádků a příkazy.

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
Poskytuje informace o dostupnosti převodů typů pro příkaz nebo sadu řádků. Povinné pro příkazy, sady řádků a indexové sady řádků. `IConvertType` Implementuje rozhraní delegováním do objektu převodu dodaného OLE DB.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implementuje rozhraní a funkci `CreateSchemaRowset`založena Creator. `IDBSchemaRowset`

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Otevře a vrátí sadu řádků, která obsahuje všechny řádky z jedné základní tabulky nebo indexu. Povinné rozhraní pro objekt relace.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implementuje rozhraní OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) , které umožňuje aktualizovat hodnoty sloupců ve stávajících řádcích, odstraňovat řádky a vkládat nové řádky.

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Tato třída dědí z [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) a Přepisuje [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl`provádí stejné funkce jako `IObjectWithSite` , ale také umožňuje OLE DB vlastnosti `DBPROPCANSCROLLBACKWARDS` a `DBPROPCANFETCHBACKWARDS`.

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
`IRowsetIdentity` Implementuje rozhraní, které umožňuje porovnat, zda jsou dva řádky dat identické.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Poskytuje implementaci `IRowset` rozhraní, což je základní rozhraní sady řádků.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implementuje vlastnosti sady řádků pomocí mapy sady vlastností definované ve vaší třídě příkazu. Povinné rozhraní pro sady řádků.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implementuje rozhraní OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , které načte libovolné řádky ze sady řádků. Chcete-li podporovat OLE DB záložky v sadě řádků, nastavte sadu řádků z této třídy jako děděnou.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implementuje všesměrové funkce pro poradenství naslouchací procesy v `IID_IRowsetNotify` bodu připojení změny obsahu sady řádků. Příjemci, kteří zpracovávají oznámení, implementují rozhraní [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) a zaregistrují ho v tomto spojovacím bodě.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implementuje rozhraní OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) , které umožňuje uživatelům zpozdit přenos změn provedených s [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) na zdroj dat a vrátit zpět změny před přenosem.

## <a name="command-classes"></a>Třídy příkazů

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Poskytuje implementaci `ICommand` rozhraní. Toto rozhraní není viditelné, ale je zpracováváno `ICommandTextImpl`. Povinné rozhraní objektu Command.

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Tato implementace `ICommandProperties` rozhraní je poskytována statickou funkcí definovanou `BEGIN_PROPSET_MAP` makrem. Povinné příkazy.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Nastaví, uloží a vrátí text příkazu. Povinné příkazy.

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Vytvoří nový příkaz z objektu Session a vrátí požadované rozhraní u nově vytvořeného příkazu. Volitelné rozhraní objektů relací.

Jiné třídy příkazů jsou `IColumnsInfoImpl` a `IAccessorImpl`, popsané v části třídy sady řádků výše.

## <a name="data-source-classes"></a>Třídy zdroje dat

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Vytvoří a odstraní připojení k příjemci. Povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory.

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties`je povinné rozhraní pro objekty zdroje dat a volitelné rozhraní pro enumerátory. Nicméně pokud enumerátor zveřejňuje `IDBInitialize`, musí vystavit `IDBProperties` (vlastnosti ve zdroji dat).

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Získá ukazatel rozhraní objektu zdroje dat. Povinné rozhraní v relaci

## <a name="other-classes"></a>Jiné třídy

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implementuje vlastnosti pro celou řadu OLE DBch vlastností rozhraní (například `IDBProperties` `ISessionProperties`,, a `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implementuje rozhraní OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , přidávání záznamů do a načítání záznamů z datového členu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Šablony OLE DB](../../data/oledb/ole-db-templates.md)