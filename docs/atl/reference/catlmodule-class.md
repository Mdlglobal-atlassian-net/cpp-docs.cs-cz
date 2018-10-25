---
title: Catlmodule – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3211f87e2c692c587ee2df82497fc56662e4974d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077280"
---
# <a name="catlmodule-class"></a>Catlmodule – třída

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
|[Catlmodule –:: ~ catlmodule –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Potlačí tuto metodu za účelem přidání parametrů do mapy nahrazení komponenta knihovny ATL registru (Registrar).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Přidá novou funkci, která se má volat při ukončení modulu.|
|[CAtlModule::GetGITPtr](#getgitptr)|Vrátí ukazatel rozhraní globální.|
|[CAtlModule::GetLockCount](#getlockcount)|Vrací počet zámků.|
|[CAtlModule::Lock](#lock)|Zvýší počet zámků.|
|[CAtlModule::Term](#term)|Uvolní všechny datové členy.|
|[CAtlModule::Unlock](#unlock)|Dekrementuje počet zámků.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript, které jsou obsaženy v určený prostředek k registraci nebo zrušení registrace objektu.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Tato metoda je volána metodou `UpdateRegistryFromResourceD` a proveďte aktualizaci registru.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Spustí skript, které jsou obsaženy v určený prostředek k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na komponentu ATL registru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Obsahuje identifikátor GUID aktuálního modulu.|
|[CAtlModule::m_pGIT](#m_pgit)|Ukazatel na tabulky globálního rozhraní.|

## <a name="remarks"></a>Poznámky

Tato třída používá [catldllmodulet – třída](../../atl/reference/catldllmodulet-class.md), [catlexemodulet – třída](../../atl/reference/catlexemodulet-class.md), a [catlservicemodulet – třída](../../atl/reference/catlservicemodulet-class.md) a poskytuje podporu pro aplikace, knihovny DLL, EXE aplikace, a Windows services, v uvedeném pořadí.

Další informace o modulech v ATL naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md).

Nahradí tato třída zastaralá [ccommodule – třída](../../atl/reference/ccommodule-class.md) použité v dřívějších verzích ATL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements

Potlačí tuto metodu za účelem přidání parametrů do mapy nahrazení komponenta knihovny ATL registru (Registrar).

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parametry

*pRegistrar*<br/>
Vyhrazená.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Nahraditelné parametry umožňují klienta vašeho registrátora zadání dat za běhu. K tomuto účelu udržuje doménový Registrátor nahrazení mapování, do kterého se zadá hodnoty přidružené k nahraditelné parametry ve skriptu. Doménový Registrátor provede tyto položky v době běhu.

Naleznete v tématu [použití nahraditelných parametrů (preprocesor The registrátoru)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) další podrobnosti.

##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc

Přidá novou funkci, která se má volat při ukončení modulu.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parametry

*pFunc*<br/>
Ukazatel na funkci přidat.

*datový sklad*<br/>
Uživatelem definované datové předána funkci.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="catlmodule"></a>  CAtlModule::CAtlModule

Konstruktor

```
CAtlModule() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a zahájí kritický oddíl kolem vlákna modulu.

##  <a name="dtor"></a>  Catlmodule –:: ~ catlmodule –

Destruktor.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy.

##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr

Načte ukazatel na Global Interface Table.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parametry

*ppGIT*<br/>
Ukazatel na proměnnou, která se zobrazí ukazatel na Global Interface Table.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo při selhání kód chyby. E_POINTER je vrácena, jestliže *ppGIT* je rovna hodnotě NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt Global Interface Table neexistuje, je vytvořen a její adresa je uložen v proměnné člena [CAtlModule::m_pGIT](#m_pgit).

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *ppGIT* je rovna hodnotě NULL, nebo pokud ukazatel Global Interface Table nelze získat.

Zobrazit [IGlobalInterfaceTable](/windows/desktop/api/objidl/nn-objidl-iglobalinterfacetable) informace o globální tabulku rozhraní.

##  <a name="getlockcount"></a>  CAtlModule::GetLockCount

Vrací počet zámků.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací počet zámků. Tato hodnota může být užitečné pro diagnostiku a ladění.

##  <a name="lock"></a>  CAtlModule::Lock

Zvýší počet zámků.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Zvýší počet zámků a vrátí aktualizovanou hodnotu. Tato hodnota může být užitečné pro diagnostiku a ladění.

##  <a name="m_libid"></a>  CAtlModule::m_libid

Obsahuje identifikátor GUID aktuálního modulu.

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>  CAtlModule::m_pGIT

Ukazatel na tabulky globálního rozhraní.

```
IGlobalInterfaceTable* m_pGIT;
```

##  <a name="term"></a>  CAtlModule::Term

Uvolní všechny datové členy.

```
void Term() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy. Tato metoda je volán destruktor.

##  <a name="unlock"></a>  CAtlModule::Unlock

Dekrementuje počet zámků.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Dekrementuje počet zámků a vrátí aktualizovanou hodnotu. Tato hodnota může být užitečné pro diagnostiku a ladění.

##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD

Spustí skript, které jsou obsaženy v určený prostředek k registraci nebo zrušení registrace objektu.

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

*lpszRes*<br/>
Název prostředku.

*nResID*<br/>
ID prostředku.

*bRegister*<br/>
Hodnota TRUE, pokud by měl být zaregistrován objekt; FALSE v opačném případě.

*pMapEntries*<br/>
Ukazatel na náhradní mapy ukládání hodnot, které jsou přidružené k nahraditelné parametry skriptu. ATL – automaticky používá modul %. Použití dalších nahraditelných parametrů naleznete v části [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Jinak použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Spustí skript obsažené v prostředku zadaného parametrem *lpszRes nebo nResID*. Pokud *bRegister* má hodnotu TRUE, tato metoda registruje v systémovém registru objektu; v opačném případě se odebere objekt z registru.

Staticky propojit komponenta knihovny ATL registru (Registrar), najdete v článku [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).

Tato metoda volá [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) a [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).

##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper

Tato metoda je volána metodou `UpdateRegistryFromResourceD` a proveďte aktualizaci registru.

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
Název prostředku.

*bRegister*<br/>
Určuje, zda by měly být zaregistrovány objektu.

*pMapEntries*<br/>
Ukazatel na náhradní mapy ukládání hodnot, které jsou přidružené k nahraditelné parametry skriptu. ATL – automaticky používá modul %. Použití dalších nahraditelných parametrů naleznete v části [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Jinak použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda poskytuje implementaci [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).

##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS

Spustí skript, které jsou obsaženy v určený prostředek k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na komponentu ATL registru.

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

*nResID*<br/>
ID prostředku.

*lpszRes*<br/>
Název prostředku.

*bRegister*<br/>
Určuje, zda by měly být zaregistrovány skript prostředků.

*pMapEntries*<br/>
Ukazatel na náhradní mapy ukládání hodnot, které jsou přidružené k nahraditelné parametry skriptu. ATL – automaticky používá modul %. Použití dalších nahraditelných parametrů naleznete v části [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Jinak použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Podobně jako [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) s výjimkou `CAtlModule::UpdateRegistryFromResourceS` vytvoří statický odkaz na komponentu ATL registru (Registrar).

## <a name="see-also"></a>Viz také

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)<br/>
[Komponenta registru (Registrar)](../../atl/atl-registry-component-registrar.md)
