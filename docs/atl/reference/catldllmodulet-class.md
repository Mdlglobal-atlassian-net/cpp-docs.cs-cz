---
title: Třída CAtlDllModuleT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b1ea8b5922454d32961f0e7d87eda16f55fe52c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT – třída
Tato třída představuje modul pro knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CAtlDllModuleT`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor|  
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Testy, pokud nelze uvolnit knihovnu DLL.|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Vrátí objekt pro vytváření tříd.|  
|[CAtlDllModuleT::DllMain](#dllmain)|Volitelné vstupní bod do dynamická knihovna (DLL).|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Přidá položky systémového registru pro objekty v knihovně DLL.|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Odebere položky systémového registru pro objekty v knihovně DLL.|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Vrátí objekt pro vytváření tříd. Vyvolá se podle [DllGetClassObject](#dllgetclassobject).|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlDllModuleT` představuje modul pro dynamická knihovna (DLL) a poskytuje funkce, které jsou používány ve všech projektech knihovny DLL. Tato specializace [CAtlModuleT](../../atl/reference/catlmodulet-class.md) třída zahrnuje podporu pro registraci.  
  
 Další informace o modulech v ATL najdete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT  
 Konstruktor  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>  CAtlDllModuleT:: ~ CAtlDllModuleT  
 Destruktor.  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow  
 Testy, pokud nelze uvolnit knihovnu DLL.  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, zda knihovnu DLL může být odpojen nebo S_FALSE, pokud ji nelze.  
  
##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject  
 Vrátí objekt pro vytváření tříd.  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rclsid`  
 CLSID objektu, který se má vytvořit.  
  
 `riid`  
 Identifikátory IID požadované rozhraní.  
  
 `ppv`  
 Ukazatel na ukazatel rozhraní identifikovaný `riid`. Pokud objekt nepodporuje toto rozhraní `ppv` je nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain  
 Volitelné vstupní bod do dynamická knihovna (DLL).  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwReason`  
 Pokud je nastaven na DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH a DLL_THREAD_DETACH případně volání oznámení jsou zakázány.  
  
 *lpReserved*  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Zakázání DLL_THREAD_ATTACH a DLL_THREAD_DETACH případně oznámení volání může být užitečné optimalizace pro vícevláknové aplikace, které mají mnoho knihoven DLL, která často vytvářet a odstraňovat vláken, a jehož knihovny DLL nepotřebují tyto úrovni vlákna oznámení o připojení nebo odpojení.  
  
##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer  
 Přidá položky systémového registru pro objekty v knihovně DLL.  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 TRUE, pokud je typ knihovna k registraci. Výchozí hodnota je TRUE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer  
 Odebere položky systémového registru pro objekty v knihovně DLL.  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bUnRegTypeLib`  
 TRUE, pokud je typ knihovna odeberou z registru. Výchozí hodnota je TRUE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject  
 Vytvoří objekt zadaného CLSID.  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rclsid`  
 CLSID objektu, který se má vytvořit.  
  
 `riid`  
 Identifikátory IID požadované rozhraní.  
  
 `ppv`  
 Ukazatel na ukazatel rozhraní identifikovaný `riid`. Pokud objekt nepodporuje toto rozhraní `ppv` je nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) a je zahrnuté pro zpětné kompatibility.  
  
## <a name="see-also"></a>Viz také  
 [CAtlModuleT – třída](../../atl/reference/catlmodulet-class.md)   
 [CAtlExeModuleT – třída](../../atl/reference/catlexemodulet-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
