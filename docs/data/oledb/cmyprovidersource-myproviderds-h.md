---
title: CMyProviderSource (MyProviderDS.H) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f141ad7565a78ff4e7a02b3847287879b81ccd6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098651"
---
# <a name="cmyprovidersource-myproviderdsh"></a>CMyProviderSource (MyProviderDS.H)
Třídy zprostředkovatele použití vícenásobné dědičnosti. Následující kód ukazuje řetězec dědičnosti pro objekt zdroje dat:  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSource  
class ATL_NO_VTABLE CMyProviderSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CMyProviderSource, &CLSID_MyProvider>,  
   public IDBCreateSessionImpl<CMyProviderSource, CMyProviderSession>,  
   public IDBInitializeImpl<CMyProviderSource>,  
   public IDBPropertiesImpl<CMyProviderSource>,  
   public IPersistImpl<CMyProviderSource>,  
   public IInternalConnectionImpl<CMyProviderSource>  
```  
  
 Všechny komponenty modelu COM odvozena od `CComObjectRootEx` a `CComCoClass`. `CComObjectRootEx` poskytuje implementaci pro **IUnknown** rozhraní. Ho může zpracovávat všechny model vláken. `CComCoClass` zpracovává všechny podporu chyby. Pokud chcete odeslat klientovi bohatší informace o chybě, můžete některé chybové rozhraní API v `CComCoClass`.  
  
 Objekt zdroje dat se také dědí z několika 'Impl' tříd. Každá třída poskytuje implementaci pro rozhraní. Implementuje objekt zdroje dat `IPersist`, `IDBProperties`, **IDBInitialize**, a **IDBCreateSession** rozhraní. Každé rozhraní je vyžadují k implementaci objekt zdroje dat OLE DB. Můžete podporovat nebo není dědění nebo není dědění z jedné z těchto tříd 'Impl' konkrétní funkce. Pokud chcete zajistit podporu **IDBDataSourceAdmin** rozhraní dědit z **IDBDataSourceAdminImpl** třídy pro získání požadované funkce.  
  
## <a name="com-map"></a>Mapu modelu COM  
 Vždy, když klient volá `QueryInterface` pro rozhraní ve zdroji dat, prochází následující mapa COM:  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 Makra COM_INTERFACE_ENTRY jsou z knihovny ATL a oznamují implementace `QueryInterface` v `CComObjectRootEx` navrácení odpovídající rozhraní.  
  
## <a name="property-map"></a>Mapy vlastností  
 Mapa vlastností určuje všechny vlastnosti, které jsou určeny zprostředkovatelem:  
  
```  
BEGIN_PROPSET_MAP(CMyProviderSource)  
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
   CHAIN_PROPERTY_SET(CMyProviderSession)  
END_PROPSET_MAP()  
```  
  
 Vlastnosti v OLE DB jsou seskupené. Objekt zdroje dat obsahuje dvě skupiny vlastností: jeden pro **DBPROPSET_DATASOURCEINFO** sadu a jeden pro **DBPROPSET_DBINIT** nastavit. **DBPROPSET_DATASOURCEINFO** sada odpovídá vlastnosti o poskytovateli a zdrojem dat. **DBPROPSET_DBINIT** sada odpovídá vlastnosti použitých při inicializaci. Šablony zprostředkovatele technologie OLE DB zpracovávat tyto sady s makry PROPERTY_SET. Makra vytvořit blok, který obsahuje pole vlastností. Vždy, když klient volá `IDBProperties` rozhraní poskytovatele používá mapa vlastností.  
  
 Není nutné k implementaci všech vlastností ve specifikaci. Však musí podporovat požadované vlastnosti; v tématu specifikace shody úrovně 0 pro další informace. Pokud nechcete podporovat vlastnost, můžete jej odebrat z mapování. Pokud chcete podporovat vlastnost, přidejte ji do mapy pomocí PROPERTY_INFO_ENTRY makra. Makro odpovídá **UPROPINFO** struktury, jak je znázorněno v následujícím kódu:  
  
```  
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
  
 Každý prvek ve struktuře představuje informace ke zpracování vlastnosti. Obsahuje **DBPROPID** k určení GUID a ID pro vlastnost. Obsahuje taky položky k určení typu a hodnoty vlastnosti.  
  
 Pokud chcete změnit výchozí hodnotu vlastnosti (Všimněte si, že příjemce může kdykoli změnit hodnotu zapisovatelné vlastnosti), můžete buď PROPERTY_INFO_ENTRY_VALUE nebo PROPERTY_INFO_ENTRY_EX – makro. Tyto makra umožňují zadat hodnotu pro odpovídající vlastnost. Makro PROPERTY_INFO_ENTRY_VALUE je zjednodušený zápis, který vám umožní změnit hodnotu. Makro PROPERTY_INFO_ENTRY_VALUE volá makro PROPERTY_INFO_ENTRY_EX. Toto makro umožňuje přidat nebo změnit všechny atributy v **UPROPINFO** struktura.  
  
 Pokud chcete definovat vlastní sadu vlastností, můžete přidat tak, že další kombinaci BEGIN_PROPSET_MAP/END_PROPSET_MAP. Budete muset definovat identifikátor GUID pro sadu vlastností a potom vlastní vlastnosti. Pokud máte vlastnosti specifické pro zprostředkovatele, můžete je přidáte do nové místo použití existující sady vlastností. Tím předejdete potížím v novějších verzích technologie OLE DB.  
  
## <a name="user-defined-property-sets"></a>Uživatelem definované vlastnosti sady  
 Visual C++ podporuje uživatelem definované vlastnosti sady. Není nutné přepsat **GetProperties** nebo `GetPropertyInfo`. Místo toho šablony zjistit žádné uživatelem definované vlastnosti sadě a přidat ji do příslušného objektu.  
  
 Pokud máte sadu vlastností definovaný uživatelem, který musí být k dispozici v době inicializace (to znamená, než příjemce volá **IDBInitialize::Initialize**), můžete toto určíte pomocí **UPROPSET_USERINIT** příznak ve spojení s BEGIN_PROPERTY_SET_EX makro. Sada vlastností musí být v objekt zdroje dat pro tento postup (jako je specifikace OLE DB vyžaduje). Příklad:  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>Viz také  
 [Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)