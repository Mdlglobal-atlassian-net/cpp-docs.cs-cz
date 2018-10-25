---
title: Globální funkce registrace a TypeLib | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af2780c8b7fb332cd739416e5051a57a8bc7f765
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073529"
---
# <a name="registry-and-typelib-global-functions"></a>Globální funkce registrace a TypeLib

Tyto funkce poskytují podporu pro načítání a registraci knihovny typů.

> [!IMPORTANT]
>  Funkce uvedené v následujících tabulkách nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxrefcreatekey)|Vytvoří zadaného klíče registru.|
|[AfxRegDeleteKey](#afxrefdeletekey)|Odstraní zadaný klíč registru.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Pomocné rutiny zaregistrovat obslužnou rutinu ve verzi preview.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocné rutiny se zrušit registraci obslužné rutiny náhledu. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Voláním této funkce se zaregistruje knihovna typů.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Voláním této funkce se zrušit registraci knihovny typů|
|[AfxRegOpenKey](#afxregopenkey)|Otevře zadaný klíč registru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otevře zadaný klíč registru.|
|[AtlLoadTypeLib](#atlloadtypelib)|Voláním této funkce se načte knihovna typů.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Voláním této funkce se registr aktualizuje ze zadaného prostředku.|
|[RegistryDataExchange](#registrydataexchange)|Voláním této funkce se provede čtení nebo zápis v systémovém registru. Volá [makra výměny dat registru](../../atl/reference/registry-data-exchange-macros.md).|

Tyto funkce řízení uzel v registru, který program používá k ukládání informací.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Zjišťuje, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Nastaví, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration

Tato funkce slouží k určení, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** (**HKCU**) uzlu.

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parametry

*pEnabled*<br/>
[out] Hodnota TRUE označuje, že informace registru během směrována **HKCU** uzel. Hodnota FALSE označuje, že aplikace zapíše informace registru do uzlu výchozí. Je výchozí uzel **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je metoda úspěšná, jinak chyba HRESULT kódu pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení není povoleno přesměrování registru. Pokud tuto možnost povolíte, přístup k registru je přesměrován na **HKEY_CURRENT_USER\Software\Classes**.

Přesměrování není globální. Pouze rozhraní MFC a ATL se vztahuje toto přesměrování registru.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="afxregcreatekey"></a> AfxRegCreateKey

Vytvoří zadaného klíče registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*podstrom hKey*<br/>
Popisovač otevřít klíč registru.

*lpSubKey*<br/>
Název klíče, který tato funkce se otevře, nebo vytvoří.

*phkResult*<br/>
Ukazovat na proměnnou, která přijímá popisovač klíče otevřená nebo je vytvořený.

*Druh*<br/>
Ukazatel `CAtlTransactionManager` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxregdeletekey"></a> AfxRegDeleteKey

Odstraní zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*podstrom hKey*<br/>
Popisovač otevřít klíč registru.

*lpSubKey*<br/>
Název klíče, která se má odstranit.

*Druh*<br/>
Ukazatel `CAtlTransactionManager` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

Pomocné rutiny zaregistrovat obslužnou rutinu ve verzi preview.

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
Určuje, přípona souboru registrovaná s touto obslužnou rutinou.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib

Voláním této funkce se zaregistruje knihovna typů.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Popisovač instance modulu.

*lpszIndex*<br/>
Řetězec ve formátu "\\\N", kde N je celočíselný index zdroj knihovny typů. Může mít hodnotu NULL, pokud žádný index je povinný.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využíváno [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) a [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="afxregopenkey"></a> AfxRegOpenKey

Otevře zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*podstrom hKey*<br/>
Popisovač otevřít klíč registru.

*lpSubKey*<br/>
Název klíče, který tato funkce se otevře, nebo vytvoří.

*phkResult*<br/>
Ukazovat na proměnnou, která přijímá popisovač vytvořený klíč.

*Druh*<br/>
Ukazatel `CAtlTransactionManager` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx

Otevře zadaný klíč registru.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*podstrom hKey*<br/>
Popisovač otevřít klíč registru.

*lpSubKey*<br/>
Název klíče, který tato funkce se otevře, nebo vytvoří.

*ulOptions*<br/>
Tento parametr je vyhrazen a musí být nula.

*samDesired*<br/>
Maska, která určuje požadované přístupová práva ke klíči.

*phkResult*<br/>
Ukazovat na proměnnou, která přijímá popisovač otevřené klíč.

*Druh*<br/>
Ukazatel `CAtlTransactionManager` objektu.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je ERROR_SUCCESS. Pokud funkce selže, vrácená hodnota je nenulový chybový kód definovaný ve Winerror.h.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler

Pomocné rutiny se zrušit registraci obslužné rutiny náhledu.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Určuje identifikátor CLSID obslužné rutiny pro odstranění registrace.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration

Nastaví, zda aplikace přesměrovává přístup k registru do **HKEY_CURRENT_USER** (**HKCU**) uzlu.

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Hodnota TRUE označuje, že informace registru během směrována **HKCU** uzel. Hodnota FALSE označuje, že aplikace zapíše informace registru do uzlu výchozí. Je výchozí uzel **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Návratová hodnota

S_OK, pokud je metoda úspěšná, jinak chyba HRESULT kódu pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení není povoleno přesměrování registru. Pokud tuto možnost povolíte, přístup k registru je přesměrován na **HKEY_CURRENT_USER\Software\Classes**.

Přesměrování není globální. Pouze rozhraní MFC a ATL se vztahuje toto přesměrování registru.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib

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
Řetězec ve formátu "\\\N", kde N je celočíselný index zdroj knihovny typů. Může mít hodnotu NULL, pokud žádný index je povinný.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využíváno [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) a [AtlComModuleUnregisterServer](#atlcommoduleunregisterserver).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib

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
Zpracování do modulu přidružené ke knihovně typů.

*lpszIndex*<br/>
Řetězec ve formátu "\\\N", kde N je celočíselný index zdroj knihovny typů. Může mít hodnotu NULL, pokud žádný index je povinný.

*pbstrPath*<br/>
Při návratu úspěšné obsahuje úplnou cestu modulu přidružené ke knihovně typů.

*ppTypeLib*<br/>
Při návratu úspěšné obsahuje ukazatel na ukazatel na knihovnu typů načíst.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce je využíváno [AtlRegisterTypeLib](#atlregistertypelib) a [AtlUnRegisterTypeLib](#atlunregistertypelib).

##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD

Tato funkce se přestala nabízet v sadě Visual Studio 2013 a Odebereme v sadě Visual Studio 2015.

```
<removed>
```

##  <a name="registrydataexchange"></a>  RegistryDataExchange

Voláním této funkce se provede čtení nebo zápis v systémovém registru.

### <a name="syntax"></a>Syntaxe

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parametry

*PT*<br/>
Ukazatel na aktuální objekt.

*rdxOp*<br/>
Hodnotu výčtu, která označuje, které operace by měl provádět funkce. V tabulce v části poznámky povolených hodnot.

*pItem*<br/>
Ukazatel na data, která se má číst nebo zapsat do registru. Data můžete také představovat klíč k odstranění z registru. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) a [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozšířit na funkci, která volá `RegistryDataExchange`.

V následující tabulce jsou uvedeny možné výčtu hodnoty, které označují, že se že má provést operaci funkce:

|Hodnota výčtu|Operace|
|----------------|---------------|
|eReadFromReg|Čtení dat z registru.|
|eWriteToReg|Zápis dat do registru.|
|eDeleteFromReg|Odstranění klíče z registru.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Funkce](atl-functions.md)<br/>
[Makra výměny dat registru](registry-data-exchange-macros.md)
