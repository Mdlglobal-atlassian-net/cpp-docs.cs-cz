---
title: "Třída CAtlModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
dev_langs: C++
helpviewer_keywords: CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c969341656d0861224cf0835d08e31907328b5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catlmodule-class"></a>CAtlModule – třída
Tato třída poskytuje metody používané v několika ATL – třídy modulů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](#catlmodule)|Konstruktor|  
|[CAtlModule:: ~ CAtlModule](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Potlačí tuto metodu za účelem přidání parametrů do mapy nahrazení komponenta knihovny ATL registru (Registrar).|  
|[CAtlModule::AddTermFunc](#addtermfunc)|Přidá nové funkce, která se má volat při modul ukončí.|  
|[CAtlModule::GetGITPtr](#getgitptr)|Vrátí ukazatel globální rozhraní.|  
|[CAtlModule::GetLockCount](#getlockcount)|Vrátí počet zámků.|  
|[CAtlModule::Lock](#lock)|Zvětší počet zámku.|  
|[CAtlModule::Term](#term)|Uvolní všechny datové členy.|  
|[CAtlModule::Unlock](#unlock)|Snižuje počet zámek.|  
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript obsažené v zadaný prostředek k registraci nebo zrušení registrace objektu.|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Tato metoda je volána `UpdateRegistryFromResourceD` provést aktualizaci registru.|  
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Spustí skript obsažené v zadaný prostředek k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na komponentu ATL registru.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|Obsahuje identifikátor GUID modulu aktuální.|  
|[CAtlModule::m_pGIT](#m_pgit)|Ukazatel na globální rozhraní tabulky.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída se používá ve [CAtlDllModuleT třída](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT třída](../../atl/reference/catlexemodulet-class.md), a [CAtlServiceModuleT třída](../../atl/reference/catlservicemodulet-class.md) poskytuje podporu pro aplikace, knihovny DLL, EXE aplikace, a Windows služby v uvedeném pořadí.  
  
 Další informace o modulech v ATL najdete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md).  
  
 Nahradí tato třída zastaralá [CComModule – třída](../../atl/reference/ccommodule-class.md) použitého v předchozích verzích ATL.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 `CAtlModule`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements  
 Potlačí tuto metodu za účelem přidání parametrů do mapy nahrazení komponenta knihovny ATL registru (Registrar).  
  
```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```  
  
### <a name="parameters"></a>Parametry  
 *pRegistrar*  
 Vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Nahraditelné parametry Povolit klientům doménového registrátora zadejte data pro spuštění. K tomuto účelu udržuje registrátora nahrazení mapy, do kterého přejde hodnoty přidružené k nahraditelné parametry ve vašem skriptu. Registrátora umožňuje tyto položky v době běhu.  
  
 Podívejte se na téma [pomocí nahraditelné parametry (registrátora Preprocessor)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) další podrobnosti.  
  
##  <a name="addtermfunc"></a>CAtlModule::AddTermFunc  
 Přidá nové funkce, která se má volat při modul ukončí.  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pFunc*  
 Ukazatel na funkci přidat.  
  
 `dw`  
 Uživatelem definované datové předaný funkci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="catlmodule"></a>CAtlModule::CAtlModule  
 Konstruktor  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje datových členů a zahájí kritická sekce kolem modulu přístup z více vláken.  
  
##  <a name="dtor"></a>CAtlModule:: ~ CAtlModule  
 Destruktor.  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny datové členy.  
  
##  <a name="getgitptr"></a>CAtlModule::GetGITPtr  
 Načte ukazatel na globální rozhraní tabulky.  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ppGIT`  
 Ukazatel na proměnnou, která se zobrazí ukazatel na globální rozhraní tabulky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo kód chyby při selhání. E_POINTER je vrácena v případě `ppGIT` rovná hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Pokud objekt globální rozhraní tabulka neexistuje, je vytvořen a jeho adresy je uložen v členské proměnné [CAtlModule::m_pGIT](#m_pgit).  
  
 V sestavení pro ladění, dojde k chybě assertion Pokud `ppGIT` rovná NULL, nebo pokud ukazatele globální rozhraní tabulky nelze získat.  
  
 V tématu [IGlobalInterfaceTable](http://msdn.microsoft.com/library/windows/desktop/ms678517) informace o tabulce globální rozhraní.  
  
##  <a name="getlockcount"></a>CAtlModule::GetLockCount  
 Vrátí počet zámků.  
  
```
virtual LONG GetLockCount() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet zámků. Tato hodnota může být užitečné pro diagnostiku a ladění.  
  
##  <a name="lock"></a>CAtlModule::Lock  
 Zvětší počet zámku.  
  
```
virtual LONG Lock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Zvětší počet zámku a vrátí aktualizované hodnoty. Tato hodnota může být užitečné pro diagnostiku a ladění.  
  
##  <a name="m_libid"></a>CAtlModule::m_libid  
 Obsahuje identifikátor GUID modulu aktuální.  
  
```
static GUID m_libid;
```  
  
##  <a name="m_pgit"></a>CAtlModule::m_pGIT  
 Ukazatel na globální rozhraní tabulky.  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="term"></a>CAtlModule::Term  
 Uvolní všechny datové členy.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny datové členy. Tato metoda je volána destruktoru.  
  
##  <a name="unlock"></a>CAtlModule::Unlock  
 Snižuje počet zámek.  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Snižuje počet zámek a vrátí aktualizované hodnoty. Tato hodnota může být užitečné pro diagnostiku a ladění.  
  
##  <a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD  
 Spustí skript obsažené v zadaný prostředek k registraci nebo zrušení registrace objektu.  
  
```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszRes`  
 Název prostředku.  
  
 `nResID`  
 ID prostředku.  
  
 `bRegister`  
 **Hodnota TRUE,** Pokud objekt by měl být zapsány; **FALSE** jinak.  
  
 `pMapEntries`  
 Ukazatel na mapě nahrazení ukládání hodnot přidružený ke skriptu nahraditelné parametry. ATL automaticky používá modul %. Chcete-li použít další nahraditelné parametry, přečtěte si téma [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Jinak použijte **NULL** výchozí hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Spustí skript obsažené v prostředku zadaného parametrem *lpszRes nebo nResID*. Pokud `bRegister` je **TRUE**, tato metoda registruje objekt v registru systému; v opačném případě odebere objekt z registru.  
  
 Staticky odkaz na komponentu ATL registru (Registrar), najdete v tématu [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Tato metoda volá [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) a [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).  
  
##  <a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper  
 Tato metoda je volána `UpdateRegistryFromResourceD` provést aktualizaci registru.  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszRes`  
 Název prostředku.  
  
 `bRegister`  
 Označuje, zda by měl být registrován objekt.  
  
 `pMapEntries`  
 Ukazatel na mapě nahrazení ukládání hodnot přidružený ke skriptu nahraditelné parametry. ATL automaticky používá modul %. Chcete-li použít další nahraditelné parametry, přečtěte si téma [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Jinak použijte **NULL** výchozí hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje implementace [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).  
  
##  <a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS  
 Spustí skript obsažené v zadaný prostředek k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na komponentu ATL registru.  
  
```
HRESULT WINAPI UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nResID`  
 ID prostředku.  
  
 `lpszRes`  
 Název prostředku.  
  
 `bRegister`  
 Určuje, jestli by měl být zaregistrované skriptu prostředků.  
  
 `pMapEntries`  
 Ukazatel na mapě nahrazení ukládání hodnot přidružený ke skriptu nahraditelné parametry. ATL automaticky používá modul %. Chcete-li použít další nahraditelné parametry, přečtěte si téma [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Jinak použijte **NULL** výchozí hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) s výjimkou `CAtlModule::UpdateRegistryFromResourceS` vytvoří statický odkaz na komponentu ATL registru (Registrar).  
  
## <a name="see-also"></a>Viz také  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)   
 [Komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md)  
