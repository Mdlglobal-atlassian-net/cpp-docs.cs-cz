---
title: Globální funkce registru a typu Lib
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
ms.openlocfilehash: 69df927ddd04c19d10703854aa8c8948894309d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326081"
---
# <a name="registry-and-typelib-global-functions"></a>Globální funkce registru a typu Lib

Tyto funkce poskytují podporu pro načítání a registraci knihovny typů.

> [!IMPORTANT]
> Funkce uvedené v následujících tabulkách nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Vytvoří zadaný klíč registru.|
|[AfxRegDeleteKey](#afxregdeletekey)|Odstraní zadaný klíč registru.|
|[AfxRegisterNáhledHandler](#afxregisterpreviewhandler)|Pomocník pro registraci obslužné rutiny náhledu.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocník pro zrušení registrace obslužné rutiny náhledu. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Voláním této funkce se zaregistruje knihovna typů.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Tato funkce je volána k zrušení registrace knihovny typů.|
|[AfxRegOpenKey](#afxregopenkey)|Otevře zadaný klíč registru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otevře zadaný klíč registru.|
|[AtlLoadTypeLib](#atlloadtypelib)|Voláním této funkce se načte knihovna typů.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Voláním této funkce se registr aktualizuje ze zadaného prostředku.|
|[RegistryDataExchange](#registrydataexchange)|Voláním této funkce se provede čtení nebo zápis v systémovém registru. Volat [makra výměny dat registru](../../atl/reference/registry-data-exchange-macros.md).|

Tyto funkce řídí, který uzel v registru program používá k ukládání informací.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Načte, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** ( **HKCU).**|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Nastaví, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** ( **HKCU**).|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Tato funkce slouží k určení, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parametry

*pPovoleno*<br/>
[out] True označuje, že informace o registru je směrována do uzlu **HKCU;** NEPRAVDA označuje, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná, jinak kód chyby HRESULT, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Přesměrování registru není ve výchozím nastavení povoleno. Pokud tuto možnost povolíte, bude přístup k registru přesměrován na **HKEY_CURRENT_USER\Software\Classes**.

Přesměrování není globální. Toto přesměrování registru ovlivňuje pouze architektury knihovny MFC a knihovny ATL.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a>AfxRegCreateKey

Vytvoří zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKlíč*<br/>
Popisovač otevřeného klíče registru.

*lpSubKey*<br/>
Název klíče, který tato funkce otevře nebo vytvoří.

*phkVýsledek*<br/>
Ukazatel na proměnnou, která přijímá popisovač otevřeného nebo vytvořeného klíče.

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a>AfxRegDeleteKey

Odstraní zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKlíč*<br/>
Popisovač otevřeného klíče registru.

*lpSubKey*<br/>
Název klíče, který má být odstraněn.

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

Pomocník pro registraci obslužné rutiny náhledu.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Určuje CLSID obslužné rutiny.

*lpszShortTypeName*<br/>
Určuje progID obslužné rutiny.

*lpszFilterExt*<br/>
Určuje příponu souboru registrovanou u této obslužné rutiny.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib

Voláním této funkce se zaregistruje knihovna typů.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Popisovač instance modulu.

*lpszIndex*<br/>
Řetězec ve formátu\\\N, kde N je index celéčíslo prostředku knihovny typů. Může být NULL, pokud není vyžadován žádný index.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) a [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a>AfxRegOpenKey

Otevře zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKlíč*<br/>
Popisovač otevřeného klíče registru.

*lpSubKey*<br/>
Název klíče, který tato funkce otevře nebo vytvoří.

*phkVýsledek*<br/>
Ukazatel na proměnnou, která obdrží popisovač vytvořeného klíče.

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Otevře zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKlíč*<br/>
Popisovač otevřeného klíče registru.

*lpSubKey*<br/>
Název klíče, který tato funkce otevře nebo vytvoří.

*ulMožnosti*<br/>
Tento parametr je vyhrazen a musí být nula.

*samDesired*<br/>
Maska, která určuje požadovaná přístupová práva ke klíči.

*phkVýsledek*<br/>
Ukazatel na proměnnou, která obdrží popisovač na otevřený klíč.

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný ve winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Pomocník pro zrušení registrace obslužné rutiny náhledu.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Určuje CLSID obslužné rutiny, která má být neregistrována.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

Nastaví, zda aplikace přesměruje přístup registru k uzlu **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] True označuje, že informace o registru je směrována do uzlu **HKCU;** NEPRAVDA označuje, že aplikace zapisuje informace registru do výchozího uzlu. Výchozí uzel je **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná, jinak kód chyby HRESULT, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Přesměrování registru není ve výchozím nastavení povoleno. Pokud tuto možnost povolíte, bude přístup k registru přesměrován na **HKEY_CURRENT_USER\Software\Classes**.

Přesměrování není globální. Toto přesměrování registru ovlivňuje pouze architektury knihovny MFC a knihovny ATL.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

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
Řetězec ve formátu\\\N, kde N je index celéčíslo prostředku knihovny typů. Může být NULL, pokud není vyžadován žádný index.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) a [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib

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
Zpracovat modul přidružený ke knihovně typů.

*lpszIndex*<br/>
Řetězec ve formátu\\\N, kde N je index celéčíslo prostředku knihovny typů. Může být NULL, pokud není vyžadován žádný index.

*cesta pbstrPath*<br/>
Při úspěšném návratu obsahuje úplnou cestu modulu přidruženého ke knihovně typů.

*ppTypeLib*<br/>
Při úspěšném návratu obsahuje ukazatel na ukazatel na načtenou knihovnu typů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využívána [AtlRegisterTypeLib](#atlregistertypelib) a [AtlUnRegisterTypeLib](#atlunregistertypelib).

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Tato funkce byla v sadě Visual Studio 2013 zastaralá a je odebrána v sadě Visual Studio 2015.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a>RegistryDataExchange

Voláním této funkce se provede čtení nebo zápis v systémovém registru.

### <a name="syntax"></a>Syntaxe

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Ukazatel na aktuální objekt.

*rdxOp*<br/>
Hodnota výčtu, která označuje, kterou operaci by měla funkce provést. Povolené hodnoty naleznete v tabulce v části Poznámky.

*pPoložka*<br/>
Ukazatel na data, která mají být přečtena z registru nebo do něj zapsána. Data mohou také představovat klíč, který má být odstraněn z registru. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) a [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozbalí `RegistryDataExchange`na funkci, která volá .

Možné výčtové hodnoty, které označují operaci, kterou by měla funkce provést, jsou uvedeny v následující tabulce:

|Hodnota výčtu|Operace|
|----------------|---------------|
|eReadFromReg|Čtení dat z registru.|
|eWriteToReg|Zapisovat data do registru.|
|eDeleteFromReg|Odstraňte klíč z registru.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Functions](atl-functions.md)<br/>
[Makra výměny dat registru](registry-data-exchange-macros.md)
