---
title: "Třída CAtlWinModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcaf3d6573432b7f6f16826b2551a7e9330abed9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlwinmodule-class"></a>CAtlWinModule – třída
Tato třída poskytuje podporu pro knihovny ATL oddílová součásti.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlWinModule : public _ATL_WIN_MODULE
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Konstruktor|  
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Přidá na datový objekt.|  
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Vrací ukazatel na datový objekt okno modulu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje podporu pro všechny třídy ATL, které vyžadují oddílová funkce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)  
  
 `CAtlWinModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData  
 Tato metoda inicializuje a přidá `_AtlCreateWndData` struktura.  
  
```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Ukazatel `_AtlCreateWndData` struktura inicializovat a přidat je do aktuální modulu.  
  
 `pObject`  
 Ukazatele na objekt **to** ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) které inicializuje [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury. Tato struktura uloží **to** ukazatele, použije k získání instance třídy v procedury oken.  
  
##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule  
 Konstruktor  
  
```
CAtlWinModule();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud se inicializace nezdaří, **EXCEPTION_NONCONTINUABLE** došlo k výjimce.  
  
##  <a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule  
 Destruktor.  
  
```
~CAtlWinModule();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData  
 Tato metoda vrátí ukazatel na `_AtlCreateWndData` struktura.  
  
```
void* ExtractCreateWndData();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel `_AtlCreateWndData` struktura dříve přidány s [CAtlWinModule::AddCreateWndData](#addcreatewnddata), nebo hodnota NULL, pokud je k dispozici žádný objekt.  
  
## <a name="see-also"></a>Viz také  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
