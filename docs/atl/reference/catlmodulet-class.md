---
title: "Třída CAtlModuleT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
dev_langs: C++
helpviewer_keywords: CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4f1ba8d59e85a480af38e5b9778fee0c714a0db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlmodulet-class"></a>CAtlModuleT – třída
Tato třída implementuje modul ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CAtlModuleT`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](#initlibid)|Inicializuje datový člen obsahující identifikátor GUID modulu aktuální.|  
|[CAtlModuleT::RegisterAppId](#registerappid)|EXE se přidá do registru.|  
|[CAtlModuleT::RegisterServer](#registerserver)|Přidá službu do registru.|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|EXE se odebere z registru.|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Odebere službu z registru.|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informace o EXE v registru.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlModuleT`, odvozené od [CAtlModule](../../atl/reference/catlmodule-class.md), implementuje modul ATL služby (EXE) nebo spustitelný soubor (EXE). Modul spustitelný soubor je serveru místní, mimo proces, zatímco modul služby je aplikace Windows, která běží na pozadí při spuštění systému Windows.  
  
 `CAtlModuleT`poskytuje podporu pro inicializaci registrace a zrušení registrace modulu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT  
 Konstruktor  
  
```
CAtlModuleT() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlModuleT::InitLibId](#initlibid).  
  
##  <a name="initlibid"></a>CAtlModuleT::InitLibId  
 Inicializuje datový člen obsahující identifikátor GUID modulu aktuální.  
  
```
static void InitLibId() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volá konstruktor [CAtlModuleT::CAtlModuleT](#catlmodulet).  
  
##  <a name="registerappid"></a>CAtlModuleT::RegisterAppId  
 EXE se přidá do registru.  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="registerserver"></a>CAtlModuleT::RegisterServer  
 Přidá službu do registru.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 TRUE, pokud je typ knihovna k registraci. Výchozí hodnota je FALSE.  
  
 `pCLSID`  
 Body CLSID objekt, který má být zaregistrován. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapování objektu bude zaregistrována.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId  
 EXE se odebere z registru.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="unregisterserver"></a>CAtlModuleT::UnregisterServer  
 Odebere službu z registru.  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bUnRegTypeLib`  
 TRUE, pokud knihovny typů je také možné odregistrovat.  
  
 `pCLSID`  
 Body CLSID objekt, který má neregistrované. Pokud hodnotu NULL (výchozí hodnota), všechny objekty v mapování objektu bude zrušena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId  
 Aktualizuje informace o EXE v registru.  
  
```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegister`  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
## <a name="see-also"></a>Viz také  
 [CAtlModule – třída](../../atl/reference/catlmodule-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
