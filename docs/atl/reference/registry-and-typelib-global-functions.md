---
title: Globální funkce registru a TypeLib
ms.date: 03/27/2019
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
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: c5fdaceb47b6cd09dd9d66f26af1337a8dc6bbae
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417493"
---
# <a name="registry-and-typelib-global-functions"></a>Globální funkce registru a TypeLib

Tyto funkce poskytují podporu pro načítání a registraci knihovny typů.

> [!IMPORTANT]
>  Funkce uvedené v následujících tabulkách nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Vytvoří zadaný klíč registru.|
|[AfxRegDeleteKey](#afxregdeletekey)|Odstraní zadaný klíč registru.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Pomocný objekt pro registraci obslužné rutiny náhledu.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocný objekt pro zrušení registrace obslužné rutiny náhledu. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Voláním této funkce se zaregistruje knihovna typů.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Tato funkce se volá pro zrušení registrace knihovny typů.|
|[AfxRegOpenKey](#afxregopenkey)|Otevře zadaný klíč registru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otevře zadaný klíč registru.|
|[AtlLoadTypeLib](#atlloadtypelib)|Voláním této funkce se načte knihovna typů.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Voláním této funkce se registr aktualizuje ze zadaného prostředku.|
|[RegistryDataExchange](#registrydataexchange)|Voláním této funkce se provede čtení nebo zápis v systémovém registru. Volá se v [makrech výměny dat v registru](../../atl/reference/registry-data-exchange-macros.md).|

Tyto funkce řídí, který uzel v registru program používá k ukládání informací.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Načte, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** ( **HKCU**).|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Nastaví, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** ( **HKCU**).|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Pomocí této funkce lze určit, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parametry

*pEnabled*<br/>
mimo Hodnota TRUE označuje, že informace registru jsou směrovány na uzel **HKCU** ; Hodnota FALSE znamená, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Návratová hodnota

S_OK, zda je metoda úspěšná, jinak kód chyby HRESULT, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Přesměrování registru není ve výchozím nastavení povolené. Pokud povolíte tuto možnost, bude přístup k registru přesměrován na **HKEY_CURRENT_USER \software\classes**.

Přesměrování není globální. Toto přesměrování registru ovlivňuje pouze architektury MFC a ATL.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="afxregcreatekey"></a>AfxRegCreateKey

Vytvoří zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač pro otevřený klíč registru.

*lpSubKey*<br/>
Název klíče, který tato funkce otevře nebo vytvoří.

*phkResult*<br/>
Ukazatel na proměnnou, která přijímá popisovač pro otevřený nebo vytvořený klíč.

*pTM*<br/>
Ukazatel na objekt `CAtlTransactionManager`.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxregdeletekey"></a>AfxRegDeleteKey

Odstraní zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač pro otevřený klíč registru.

*lpSubKey*<br/>
Název klíče, který se má odstranit

*pTM*<br/>
Ukazatel na objekt `CAtlTransactionManager`.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxregisterpreviewhandler"></a>

Pomocný objekt pro registraci obslužné rutiny náhledu.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Určuje identifikátor CLSID obslužné rutiny.

*lpszShortTypeName*<br/>
Určuje identifikátor ProgID obslužné rutiny.

*lpszFilterExt*<br/>
Určuje příponu souboru zaregistrovanou v této obslužné rutině.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib

Voláním této funkce se zaregistruje knihovna typů.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Popisovač instance modulu.

*lpszIndex*<br/>
Řetězec ve formátu "\\\n", kde N je celočíselný index prostředku knihovny typů. Může mít hodnotu NULL, pokud není požadován index.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) a [CAtlComModule:: RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="afxregopenkey"></a>AfxRegOpenKey

Otevře zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač pro otevřený klíč registru.

*lpSubKey*<br/>
Název klíče, který tato funkce otevře nebo vytvoří.

*phkResult*<br/>
Ukazatel na proměnnou, která obdrží popisovač vytvořeného klíče.

*pTM*<br/>
Ukazatel na objekt `CAtlTransactionManager`.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Otevře zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Popisovač pro otevřený klíč registru.

*lpSubKey*<br/>
Název klíče, který tato funkce otevře nebo vytvoří.

*ulOptions*<br/>
Tento parametr je rezervovaný a musí být nula.

*samDesired*<br/>
Maska, která určuje požadovaná přístupová práva ke klíči.

*phkResult*<br/>
Ukazatel na proměnnou, která přijímá popisovač pro otevřený klíč.

*pTM*<br/>
Ukazatel na objekt `CAtlTransactionManager`.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, návratová hodnota je ERROR_SUCCESS. Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby definovaný v WinError. h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXPRIV. h

## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Pomocný objekt pro zrušení registrace obslužné rutiny náhledu.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Určuje identifikátor CLSID obslužné rutiny, která má být zrušena.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

Nastaví, zda aplikace přesměrovává přístup k registru do uzlu **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Hodnota TRUE označuje, že informace registru jsou směrovány na uzel **HKCU** ; Hodnota FALSE znamená, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Návratová hodnota

S_OK, zda je metoda úspěšná, jinak kód chyby HRESULT, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Přesměrování registru není ve výchozím nastavení povolené. Pokud povolíte tuto možnost, bude přístup k registru přesměrován na **HKEY_CURRENT_USER \software\classes**.

Přesměrování není globální. Toto přesměrování registru ovlivňuje pouze architektury MFC a ATL.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

Voláním této funkce se zruší registrace knihovny typů.

### <a name="syntax"></a>Syntaxe

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Popisovač instance modulu.

*lpszIndex*<br/>
Řetězec ve formátu "\\\n", kde N je celočíselný index prostředku knihovny typů. Může mít hodnotu NULL, pokud není požadován index.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [CAtlComModule:: UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) a [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

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

*hInstTypeLib*<br/>
Zpracujte modul přidružený k knihovně typů.

*lpszIndex*<br/>
Řetězec ve formátu "\\\n", kde N je celočíselný index prostředku knihovny typů. Může mít hodnotu NULL, pokud není požadován index.

*pbstrPath*<br/>
Po úspěšném návratu obsahuje úplnou cestu k modulu přidruženému k knihovně typů.

*ppTypeLib*<br/>
Po úspěšném vrácení obsahuje ukazatel na ukazatel na načtenou knihovnu typů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [AtlRegisterTypeLib](#atlregistertypelib) a [AtlUnRegisterTypeLib](#atlunregistertypelib).

##  <a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Tato funkce se v Visual Studio 2013 nepoužívá a je odebrána v aplikaci Visual Studio 2015.

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

*Bodů*<br/>
Ukazatel na aktuální objekt.

*rdxOp*<br/>
Hodnota výčtu, která určuje, která operace má funkce provádět. Povolené hodnoty najdete v tabulce v části poznámky.

*pItem*<br/>
Ukazatel na data, která se mají číst z registru nebo do něj zapisovat. Data mohou také představovat klíč, který se má odstranit z registru. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) a [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozbalí do funkce, která volá `RegistryDataExchange`.

Možné hodnoty výčtu, které určují, jakou operaci má funkce provádět, jsou uvedeny v následující tabulce:

|Hodnota výčtu|Operace|
|----------------|---------------|
|eReadFromReg|Načte data z registru.|
|eWriteToReg|Zapište data do registru.|
|eDeleteFromReg|Odstraňte klíč z registru.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="see-also"></a>Viz také

[Functions](atl-functions.md)<br/>
[Makra výměny dat registru](registry-data-exchange-macros.md)
