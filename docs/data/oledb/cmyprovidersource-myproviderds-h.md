---
title: CMyProviderSource (MyProviderDS.H) | Dokumentace Microsoftu
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
ms.openlocfilehash: 848f940c9aa974c838a4600235ab97d099bcbd06
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340147"
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
  
 Všechny komponenty modelu COM jsou odvozeny z `CComObjectRootEx` a `CComCoClass`. `CComObjectRootEx` poskytuje implementaci pro `IUnknown` rozhraní. Dokáže zpracovat všechny modelu vláken. `CComCoClass` je vyžadována podpora všechny chyby zpracovává. Pokud chcete odeslat klientovi bohatší informace o chybě, můžete použít některé chyby rozhraní API v `CComCoClass`.  
  
 Objekt zdroje dat také dědí z třídy několik 'Impl'. Každá třída poskytuje implementaci pro rozhraní. Zdroje dat objektu implementuje `IPersist`, `IDBProperties`, `IDBInitialize`, a `IDBCreateSession` rozhraní. Implementace objektu zdroje dat OLE DB každé rozhraní vyžaduje. Můžete se na podporu nebo děděním nebo není dědění z jedné z těchto tříd 'Impl' nepodporuje konkrétní funkce. Pokud chcete zajistit podporu `IDBDataSourceAdmin` rozhraní, abyste dědili z `IDBDataSourceAdminImpl` třídy pro získání funkce vyžaduje.  
  
## <a name="com-map"></a>Mapy modelu COM.  
 Vždy, když klient volá `QueryInterface` pro rozhraní na zdroj dat, prochází následující mapy modelu COM:  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 COM_INTERFACE_ENTRY – makra jsou z knihovny ATL a že se provádění `QueryInterface` v `CComObjectRootEx` navrácení odpovídající rozhraní.  
  
## <a name="property-map"></a>Mapy vlastností  
 Mapy vlastností určuje všechny vlastnosti určené zprostředkovatele:  
  
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
  
 Vlastnosti v OLE DB jsou seskupeny. Objekt zdroje dat má dvě vlastnosti skupiny: jednu pro DBPROPSET_DATASOURCEINFO nastavit a jeden pro DBPROPSET_DBINIT nastavit. Sada DBPROPSET_DATASOURCEINFO odpovídá vlastnosti o poskytovateli a zdrojem dat. Sada DBPROPSET_DBINIT odpovídá vlastnosti používané při inicializaci. Šablony zprostředkovatele technologie OLE DB zpracování těchto sad s makry PROPERTY_SET. Makra vytvořit blok, který obsahuje pole vlastností. Vždy, když klient volá `IDBProperties` rozhraní, poskytovatel použije mapy vlastností.  
  
 Nemusíte implementovat každé vlastnosti ve specifikaci. Však musí podporovat požadované vlastnosti; v tématu specifikace shody úroveň 0 pro další informace. Pokud nechcete podporu vlastnost, můžete ho odebrat z mapy. Pokud chcete zajistit podporu vlastnost, přidejte ho do objektu map s použitím PROPERTY_INFO_ENTRY – makro. Makro odpovídá `UPROPINFO` struktury, jak je znázorněno v následujícím kódu:  
  
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
  
 Každý prvek ve struktuře představuje informace, které zpracovávají vlastnost. Obsahuje `DBPROPID` určit identifikátor GUID a ID pro vlastnost. Také obsahuje položky, které určují typ a hodnotu vlastnosti.  
  
 Pokud chcete změnit výchozí hodnotu vlastnosti (Všimněte si, že příjemce může kdykoli změnit hodnotu zapisovatelnou vlastnost), můžete použít buď PROPERTY_INFO_ENTRY_VALUE nebo PROPERTY_INFO_ENTRY_EX – makro. Tato makra umožňují zadat hodnotu pro odpovídající vlastnost. PROPERTY_INFO_ENTRY_VALUE – makro je zjednodušenou notaci, který vám umožní změnit hodnotu. PROPERTY_INFO_ENTRY_VALUE – makro volá PROPERTY_INFO_ENTRY_EX – makro. Toto makro umožňuje přidat nebo změnit všechny atributy v `UPROPINFO` struktury.  
  
 Pokud chcete definovat vlastní sadu vlastností, můžete přidat jednu tím, že další kombinace BEGIN_PROPSET_MAP/END_PROPSET_MAP. Budete muset definovat identifikátor GUID pro sadu vlastností a pak definovat vlastní vlastnosti. Pokud máte vlastnosti specifické pro zprostředkovatele, můžete je přidáte do nové místo použití existující sady vlastností. Tím předejdete potížím v novějších verzích technologie OLE DB.  
  
## <a name="user-defined-property-sets"></a>Uživatelem definované vlastnosti sady  
 Jazyk Visual C++ podporuje uživatelem definované vlastnosti sady. Není nutné přepsat `GetProperties` nebo `GetPropertyInfo`. Místo toho šablony zjistit žádné uživatelem definované vlastnosti sadu a přidat ho do příslušného objektu.  
  
 Pokud budete mít nastavenou vlastnost definovaný uživatelem, který má být k dispozici v době inicializace (to znamená, než příjemce volá `IDBInitialize::Initialize`), můžete toto určíte pomocí příznaku UPROPSET_USERINIT ve spojení s BEGIN_PROPERTY_SET_EX – makro. Sada vlastností musí být v objektu zdroje dat, aby to fungovalo (jak vyžaduje specifikaci OLE DB). Příklad:  
  
```cpp  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>Viz také  
 [Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)