---
title: "Globální funkce registru a TypeLib | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dbb919cb2fe4d91f5665fbea3dcfd2140d178341
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="registry-and-typelib-global-functions"></a>Globální funkce registru a knihovny typů
Tyto funkce poskytuje podporu pro načítání a registraci knihovny typů.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulky nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AfxRegCreateKey](#afxrefcreatekey)|Vytvoří zadaný klíč registru.|
|[AfxRegDeleteKey](#afxrefdeletekey)|Odstraní určený klíč registrů.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Pomocné rutiny zaregistrovat obslužnou rutinu preview.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocné rutiny se zrušit registraci obslužnou rutinu preview. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Voláním této funkce se zaregistruje knihovna typů.|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Tato funkce je volána se zrušit registraci knihovny typů|  
|[AfxRegOpenKey](#afxregopenkey)|Otevře určený klíč registrů.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otevře určený klíč registrů.|
|[AtlLoadTypeLib](#atlloadtypelib)|Voláním této funkce se načte knihovna typů.|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Voláním této funkce se registr aktualizuje ze zadaného prostředku.|  
|[RegistryDataExchange](#registrydataexchange)|Voláním této funkce se provede čtení nebo zápis v systémovém registru. Volá [výměny dat registru makra](../../atl/reference/registry-data-exchange-macros.md).|  
  
 Tyto funkce řízení uzel v registru, který program používá k ukládání informací.  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Načte zda přesměruje registru přístup k aplikaci **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Nastaví, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration
Tato funkce slouží k určení, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** (**HKCU**) uzlu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`pEnabled`  
 `TRUE`Označuje, že se přesměruje informace o registru **HKCU** uzlu; `FALSE` označuje, že aplikace do uzlu výchozí zapisuje informace registru. Je výchozí uzel **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud je metoda úspěšné, jinak `HRESULT` kód chyby, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení není povoleno přesměrování registru. Pokud povolíte tuto možnost, přístup k registru je přesměrován na **HKEY_CURRENT_USER\Software\Classes**.  
  
 Přesměrování není globální. Pouze rozhraní MFC a knihovna ATL se vztahuje toto registru přesměrování.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  

 ## <a name="afxregcreatekey"></a>AfxRegCreateKey
 Vytvoří zadaný klíč registru.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač otevřít klíč registru.  
  
 `lpSubKey`  
 Název klíče, který tuto funkci otevře nebo vytvoří.  
  
 `phkResult`  
 Ukazatel na proměnnou, která přijímá popisovač pro otevřenou nebo vytvořený klíč.  
  
 `pTM`  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpriv.h  

## <a name="afxregdeletekey"></a>AfxRegDeleteKey
Odstraní určený klíč registrů.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač otevřít klíč registru.  
  
 `lpSubKey`  
 Název klíče, který se odstranit.  
  
 `pTM`  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>
Pomocné rutiny zaregistrovat obslužnou rutinu preview.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszCLSID`  
 Určuje identifikátor CLSID obslužné rutiny.  
  
 `lpszShortTypeName`  
 Určuje identifikátor ProgID obslužné rutiny.  
  
 `lpszFilterExt`  
 Určuje příponu souboru zaregistrována této obslužné rutiny.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h   

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib  
 Voláním této funkce se zaregistruje knihovna typů.  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `hInstTypeLib`  
 Popisovač instancí modulu.  
  
 `lpszIndex`  
 Řetězec ve formátu "\\\N", kde N je celé číslo indexu prostředek knihovny bude typu. Může mít hodnotu NULL, pokud je potřeba žádný index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná funkce je využíváno [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) a [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h

 ## <a name="afxregopenkey"></a>AfxRegOpenKey
 Otevře určený klíč registrů.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač otevřít klíč registru.  
  
 `lpSubKey`  
 Název klíče, který tuto funkci otevře nebo vytvoří.  
  
 `phkResult`  
 Ukazatel na proměnnou, která přijímá popisovač pro vytvořený klíč.  
  
 `pTM`  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpriv.h  

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx
Otevře určený klíč registrů. 

### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Popisovač otevřít klíč registru.  
  
 `lpSubKey`  
 Název klíče, který tuto funkci otevře nebo vytvoří.  
  
 `ulOptions`  
 Tento parametr je vyhrazen a musí být nula.  
  
 `samDesired`  
 Maska, která určuje požadovanou přístupová práva ke klíči.  
  
 `phkResult`  
 Ukazatel na proměnnou, která přijímá popisovač pro otevřenou klíč.  
  
 `pTM`  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu ERROR_SUCCESS. V případě selhání funkce vrácená hodnota je definovaný v Winerror.h kód nenulové hodnoty v chybě.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpriv.h  

 ## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler
 Pomocné rutiny se zrušit registraci obslužnou rutinu preview.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszCLSID`  
 Určuje identifikátor CLSID obslužné rutiny pro zrušení registrace.  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdisp.h  

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration
Nastaví, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** (**HKCU**) uzlu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Označuje, že se přesměruje informace o registru **HKCU** uzlu; `FALSE` označuje, že aplikace do uzlu výchozí zapisuje informace registru. Je výchozí uzel **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud je metoda úspěšné, jinak `HRESULT` kód chyby, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení není povoleno přesměrování registru. Pokud povolíte tuto možnost, přístup k registru je přesměrován na **HKEY_CURRENT_USER\Software\Classes**.  
  
 Přesměrování není globální. Pouze rozhraní MFC a knihovna ATL se vztahuje toto registru přesměrování.  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib  
 Voláním této funkce se zruší registrace knihovny typů.  
  
### <a name="syntax"></a>Syntaxe  
```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `hInstTypeLib`  
 Popisovač instancí modulu.  
  
 `lpszIndex`  
 Řetězec ve formátu "\\\N", kde N je celé číslo indexu prostředek knihovny bude typu. Může mít hodnotu NULL, pokud je potřeba žádný index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná funkce je využíváno [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) a [AtlComModuleUnregisterServer](#atlcommoduleunregisterserver).  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h

##  <a name="atlloadtypelib"></a>AtlLoadTypeLib  
 Voláním této funkce se načte knihovna typů.  
  
### <a name="syntax"></a>Syntaxe  
```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```  
  
### <a name="parameters"></a>Parametry  
 `hInstTypeLib`  
 Zpracování v modulu přidružené ke knihovně typů.  
  
 `lpszIndex`  
 Řetězec ve formátu "\\\N", kde N je celé číslo indexu prostředek knihovny bude typu. Může mít hodnotu NULL, pokud je potřeba žádný index.  
  
 *pbstrPath*  
 Na úspěšné vrátí obsahuje úplnou cestu modul přidružené ke knihovně typů.  
  
 `ppTypeLib`  
 Na úspěšné vrátí obsahuje ukazatel na ukazatel na načíst typ knihovny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato pomocná funkce je využíváno [AtlRegisterTypeLib](#atlregistertypelib) a [AtlUnRegisterTypeLib](#atlunregistertypelib).  
  
##  <a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD  
 Tato funkce byla v sadě Visual Studio 2013 nepoužívá a je odebrán v sadě Visual Studio 2015.  
  
```
<removed>
```  
  

  
##  <a name="registrydataexchange"></a>RegistryDataExchange  
 Voláním této funkce se provede čtení nebo zápis v systémovém registru.  

### <a name="syntax"></a>Syntaxe  
```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 Ukazatel na aktuální objekt.  
  
 *rdxOp*  
 Hodnotu výčtu, která určuje, které operace se musí provést funkce. Najdete v tabulce v části poznámky pro povolené hodnoty.  
  
 `pItem`  
 Ukazatel na data, která má číst nebo zapisovat do registru. Data můžete také představovat klíč k odstranění z registru. Výchozí hodnota je NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) a [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozšířit na funkci, která volá `RegistryDataExchange`.  
  
 V následující tabulce jsou uvedeny možné výčtu hodnoty, které indikovat, že se že má provést operaci funkce:  
  
|Hodnota výčtu|Operace|  
|----------------|---------------|  
|eReadFromReg|Čtení dat z registru.|  
|eWriteToReg|Zápis dat do registru.|  
|eDeleteFromReg|Odstraňte klíč z registru.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také  
 [Funkce](atl-functions.md) [výměny dat registru makra](registry-data-exchange-macros.md)





