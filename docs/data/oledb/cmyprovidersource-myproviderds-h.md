---
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 60324ae914c9490144a715e06323ee6d184ce201
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079726"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS. h)

Třídy poskytovatele používají vícenásobnou dědičnost. Následující kód ukazuje řetěz dědičnosti pro objekt zdroje dat:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

Všechny komponenty modelu COM jsou odvozeny z `CComObjectRootEx` a `CComCoClass`. `CComObjectRootEx` poskytuje veškerou implementaci rozhraní `IUnknown`. Může zpracovat jakýkoliv model vláken. `CComCoClass` zpracovává jakoukoli povinnou podporu. Pokud chcete klientovi odesílat rozsáhlejší informace o chybách, můžete použít některé z rozhraní API pro chyby v `CComCoClass`.

Objekt zdroje dat také dědí z několika tříd ' Impl '. Každá třída poskytuje implementaci pro rozhraní. Objekt zdroje dat implementuje rozhraní `IPersist`, `IDBProperties`, `IDBInitialize`a `IDBCreateSession`. Každé rozhraní je vyžadováno OLE DB k implementaci objektu zdroje dat. Můžete zvolit podporu nebo nepodporovat konkrétní funkce děděním nebo neděděním z jedné z těchto tříd ' Impl '. Pokud chcete podporovat rozhraní `IDBDataSourceAdmin`, převezmete od `IDBDataSourceAdminImpl` třídy, abyste získali požadovanou funkcionalitu.

## <a name="com-map"></a>Mapa modelu COM

Pokaždé, když klient volá `QueryInterface` pro rozhraní na zdroji dat, projde následující mapu modelu COM:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

Všechny komponenty modelu COM jsou odvozeny z `CComObjectRootEx` a `CComCoClass`. `CComObjectRootEx` poskytuje veškerou implementaci rozhraní `IUnknown`. Může zpracovat jakýkoliv model vláken. `CComCoClass` zpracovává jakoukoli povinnou podporu. Pokud chcete klientovi odesílat rozsáhlejší informace o chybách, můžete použít některé z rozhraní API pro chyby v `CComCoClass`.

Objekt zdroje dat také dědí z několika tříd ' Impl '. Každá třída poskytuje implementaci pro rozhraní. Objekt zdroje dat implementuje rozhraní `IPersist`, `IDBProperties`, `IDBInitialize`a `IDBCreateSession`. Každé rozhraní je vyžadováno OLE DB k implementaci objektu zdroje dat. Můžete zvolit podporu nebo nepodporovat konkrétní funkce děděním nebo neděděním z jedné z těchto tříd ' Impl '. Pokud chcete podporovat rozhraní `IDBDataSourceAdmin`, převezmete od `IDBDataSourceAdminImpl` třídy, abyste získali požadovanou funkcionalitu.

## <a name="com-map"></a>Mapa modelu COM

Pokaždé, když klient volá `QueryInterface` pro rozhraní na zdroji dat, projde následující mapu modelu COM:

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

Makra COM_INTERFACE_ENTRY jsou z knihovny ATL a oznamují implementaci `QueryInterface` v `CComObjectRootEx`, aby vrátila odpovídající rozhraní.

## <a name="property-map"></a>Mapování vlastností

Mapa vlastností určuje všechny vlastnosti přiřazené zprostředkovatelem:

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

Vlastnosti v OLE DB jsou seskupeny. Objekt zdroje dat má dvě skupiny vlastností: jeden pro DBPROPSET_DATASOURCEINFO sadu a jednu pro DBPROPSET_DBINIT sadu. DBPROPSET_DATASOURCEINFO sada odpovídá vlastnostem poskytovatele a jeho zdroje dat. Sada DBPROPSET_DBINIT odpovídá vlastnostem použitým při inicializaci. Šablony poskytovatele OLE DB tyto sady zpracovávají pomocí maker PROPERTY_SET. Makra vytvoří blok, který obsahuje pole vlastností. Pokaždé, když klient zavolá rozhraní `IDBProperties`, zprostředkovatel použije mapu vlastností.

Ve specifikaci nemusíte implementovat každou vlastnost. Je však nutné podporovat požadované vlastnosti. Další informace najdete v tématu Specifikace shody úrovně 0. Pokud nechcete, aby vlastnost podporovala, můžete ji odebrat z mapy. Pokud chcete vlastnost podporovat, přidejte ji do mapy pomocí PROPERTY_INFO_ENTRYho makra. Makro odpovídá struktuře `UPROPINFO`, jak je znázorněno v následujícím kódu:

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

Každý prvek ve struktuře představuje informace pro zpracování vlastnosti. Obsahuje `DBPROPID` k určení identifikátoru GUID a ID pro vlastnost. Obsahuje také položky pro určení typu a hodnoty vlastnosti.

Pokud chcete změnit výchozí hodnotu vlastnosti (Všimněte si, že příjemce může kdykoli změnit hodnotu vlastnosti s možností zápisu), můžete použít makro PROPERTY_INFO_ENTRY_VALUE nebo PROPERTY_INFO_ENTRY_EX. Tato makra umožňují zadat hodnotu pro odpovídající vlastnost. Makro PROPERTY_INFO_ENTRY_VALUE je zkrácený zápis, který umožňuje změnit hodnotu. Makro PROPERTY_INFO_ENTRY_VALUE volá makro PROPERTY_INFO_ENTRY_EX. Toto makro umožňuje přidat nebo změnit všechny atributy ve struktuře `UPROPINFO`.

Pokud chcete definovat vlastní sadu vlastností, můžete ji přidat tak, že vytvoříte další kombinaci BEGIN_PROPSET_MAP/END_PROPSET_MAP. Definujte identifikátor GUID pro sadu vlastností a pak definujte vlastní vlastnosti. Pokud máte vlastnosti specifické pro poskytovatele, přidejte je do nové sady vlastností namísto použití existující. Tím se vyhnete problémům v novějších verzích OLE DB.

## <a name="user-defined-property-sets"></a>Uživatelsky definované sady vlastností

Vizuál C++ podporuje uživatelsky definované sady vlastností. Nemusíte přepisovat `GetProperties` ani `GetPropertyInfo`. Místo toho šablony zjišťují všechny uživatelsky definované sady vlastností a přidají je do příslušného objektu.

Máte-li sadu vlastností definovanou uživatelem, která musí být k dispozici při inicializaci (tj. před voláním příjemce `IDBInitialize::Initialize`), můžete to určit pomocí příznaku UPROPSET_USERINIT spolu s BEGIN_PROPERTY_SET_EXm makrem. Aby tato vlastnost fungovala (OLE DB specifikace vyžaduje), musí být sada vlastností v objektu zdroje dat. Příklad:

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>Viz také

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)<br/>
