---
title: "Třída CAtlBaseModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
dev_langs: C++
helpviewer_keywords: CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 88671ae94a1df10f3866dd2ae2e70092d1ca0c4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule – třída
Ve všech projektech ATL vytvoření instance této třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlBaseModule : public _ATL_BASE_MODULE
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Instance prostředků přidá do seznamu uložených popisovače.|  
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Vrátí popisovač do instance zadaný prostředek.|  
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Vrátí instanci modulu z `CAtlBaseModule` objektu.|  
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Vrátí instance prostředku z `CAtlBaseModule` objektu.|  
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Instance prostředků se odebere ze seznamu uložené popisovače.|  
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Nastaví instance prostředku `CAtlBaseModule` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Proměnná, která určuje, pokud modul inicializace se nezdařila.|  
  
## <a name="remarks"></a>Poznámky  
 Instance `CAtlBaseModule` s názvem _AtlBaseModule je k dispozici ve všech projektech ATL obsahující popisovač pro instanci modulu, popisovač pro modul, který obsahuje prostředky (což je ve výchozím nastavení, jsou téhož) a pole popisovače k poskytnutí primární moduly prostředky. `CAtlBaseModule`byla bezpečně přístupná z více vláken.  
  
 Nahradí tato třída zastaralá [CComModule](../../atl/reference/ccommodule-class.md) třída používaná v dřívějších verzích ATL.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)  
  
 `CAtlBaseModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance  
 Instance prostředků přidá do seznamu uložených popisovače.  
  
```
bool AddResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInst`  
 Instance prostředků pro přidání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud prostředek byl úspěšně přidán, false jinak.  
  
##  <a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule  
 Konstruktor  
  
```
CAtlBaseModule() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří `CAtlBaseModule`.  
  
##  <a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt  
 Vrátí popisovač do instance zadaný prostředek.  
  
```
HINSTANCE GetHInstanceAt(int i) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *i*  
 Počet instance prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač instance prostředku nebo hodnota NULL, pokud neexistuje žádný odpovídající instance prostředku.  
  
##  <a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance  
 Vrátí instanci modulu z `CAtlBaseModule` objektu.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací instanci modulu.  
  
##  <a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance  
 Vrátí instance prostředku.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí instance prostředku.  
  
##  <a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed  
 Proměnná, která určuje, pokud modul inicializace se nezdařila.  
  
```
static bool m_bInitFailed;
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota TRUE, pokud modul inicializována, false Pokud se nepodařilo inicializovat.  
  
##  <a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance  
 Instance prostředků se odebere ze seznamu uložené popisovače.  
  
```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInst`  
 Instance prostředků pro odebrání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud prostředek byl úspěšně odebrán, false jinak.  
  
##  <a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance  
 Nastaví instance prostředku `CAtlBaseModule` objektu.  
  
```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInst`  
 Nová instance prostředku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací instanci aktualizovaný prostředek.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
