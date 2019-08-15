---
title: CAtlModule – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 798e94aed3bbd98108866ce0a1810485bd68699b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497751"
---
# <a name="catlmodule-class"></a>CAtlModule – třída

Tato třída poskytuje metody používané několika třídami modulů ATL.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Konstruktor|
|[CAtlModule::~CAtlModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Tuto metodu přepište, pokud chcete přidat parametry do náhradní mapy komponenty registru ATL (registrátor).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Přidá novou funkci, která bude volána, když se modul ukončí.|
|[CAtlModule::GetGITPtr](#getgitptr)|Vrátí ukazatel globálního rozhraní.|
|[CAtlModule::GetLockCount](#getlockcount)|Vrátí počet zámků.|
|[CAtlModule:: Lock](#lock)|Zvýší počet zámků.|
|[CAtlModule:: Term](#term)|Uvolní všechny datové členy.|
|[CAtlModule:: Unlock](#unlock)|Sníží počet zámků.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Tato metoda je volána nástrojem `UpdateRegistryFromResourceD` k provedení aktualizace registru.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na komponentu registru ATL.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Obsahuje identifikátor GUID aktuálního modulu.|
|[CAtlModule::m_pGIT](#m_pgit)|Ukazatel na tabulku globálních rozhraní.|

## <a name="remarks"></a>Poznámky

Tato třída je používána třídou [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)třídy, třídy [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)a [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) pro poskytování podpory pro aplikace knihoven DLL, aplikace exe a služby systému Windows v uvedeném pořadí.

Další informace o modulech v knihovně ATL naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md).

Tato třída nahrazuje zastaralou [třídu CComModule](../../atl/reference/ccommodule-class.md) , která se používá v dřívějších verzích knihovny ATL.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

Tuto metodu přepište, pokud chcete přidat parametry do náhradní mapy komponenty registru ATL (registrátor).

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parametry

*pRegistrar*<br/>
Rezervovaný.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Nahraditelný parametr umožňuje klientovi registrátora zadat data za běhu. V tomto případě registrátor udržuje náhradní mapu, do které vstoupí do hodnot přidružených k nahraditelným parametrům ve vašem skriptu. Registrátor provede tyto položky v době běhu.

Další podrobnosti najdete v tématu [Použití nahraditelných parametrů (preprocesor registrátora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) .

##  <a name="addtermfunc"></a>CAtlModule::AddTermFunc

Přidá novou funkci, která bude volána, když se modul ukončí.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parametry

*pFunc*<br/>
Ukazatel na funkci, kterou chcete přidat.

*dw*<br/>
Data definovaná uživatelem, která jsou předána do funkce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

##  <a name="catlmodule"></a>CAtlModule::CAtlModule

Konstruktor

```
CAtlModule() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a inicializuje kritickou část kolem vlákna modulu.

##  <a name="dtor"></a>CAtlModule:: ~ CAtlModule

Destruktor.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy.

##  <a name="getgitptr"></a>CAtlModule::GetGITPtr

Načte ukazatel na globální tabulku rozhraní.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parametry

*ppGIT*<br/>
Ukazatel na proměnnou, která získá ukazatel na globální tabulku rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybový kód při selhání. E_POINTER se vrátí, pokud je *ppGIT* rovno null.

### <a name="remarks"></a>Poznámky

Pokud objekt tabulky globálního rozhraní neexistuje, je vytvořen a jeho adresa je uložena v členské proměnné [CAtlModule:: m_pGIT](#m_pgit).

V ladicích sestaveních dojde k chybě kontrolního výrazu, pokud je *ppGIT* ROVNO hodnotě null nebo pokud nelze získat ukazatel globální tabulky rozhraní.

Informace o globální tabulce rozhraní naleznete v tématu [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) .

##  <a name="getlockcount"></a>CAtlModule::GetLockCount

Vrátí počet zámků.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet zámků. Tato hodnota může být užitečná pro diagnostiku a ladění.

##  <a name="lock"></a>CAtlModule:: Lock

Zvýší počet zámků.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Zvýší počet zámků a vrátí aktualizovanou hodnotu. Tato hodnota může být užitečná pro diagnostiku a ladění.

##  <a name="m_libid"></a>CAtlModule::m_libid

Obsahuje identifikátor GUID aktuálního modulu.

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>CAtlModule::m_pGIT

Ukazatel na tabulku globálních rozhraní.

```
IGlobalInterfaceTable* m_pGIT;
```

##  <a name="term"></a>CAtlModule:: Term

Uvolní všechny datové členy.

```
void Term() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy. Tato metoda je volána destruktorem.

##  <a name="unlock"></a>CAtlModule:: Unlock

Sníží počet zámků.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Sníží počet zámků a vrátí aktualizovanou hodnotu. Tato hodnota může být užitečná pro diagnostiku a ladění.

##  <a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.

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
TRUE, pokud by měl být objekt zaregistrován; V opačném případě NEPRAVDA.

*pMapEntries*<br/>
Ukazatel na náhradní mapu ukládá hodnoty přidružené k nahraditelným parametrům skriptu. ATL automaticky používá% MODULE%. Chcete-li použít další nahraditelný parametr, přečtěte si téma [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Spustí skript obsažený v prostředku určeném parametrem *lpszRes nebo nResID*. Pokud má *bRegister* hodnotu true, tato metoda registruje objekt v registru systému. v opačném případě Odebere objekt z registru.

Chcete-li staticky propojit komponentu registru knihovny ATL (registrátor), přečtěte si téma [CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources).

Tato metoda volá [CAtlModule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) a [IRegistrar:: ResourceUnregister](iregistrar-class.md#resourceunregister).

##  <a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

Tato metoda je volána nástrojem `UpdateRegistryFromResourceD` k provedení aktualizace registru.

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
Určuje, zda má být objekt zaregistrován.

*pMapEntries*<br/>
Ukazatel na náhradní mapu ukládá hodnoty přidružené k nahraditelným parametrům skriptu. ATL automaticky používá% MODULE%. Chcete-li použít další nahraditelný parametr, přečtěte si téma [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda poskytuje implementaci [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced).

##  <a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na komponentu registru ATL.

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
Určuje, zda má být zaregistrován skript prostředků.

*pMapEntries*<br/>
Ukazatel na náhradní mapu ukládá hodnoty přidružené k nahraditelným parametrům skriptu. ATL automaticky používá% MODULE%. Chcete-li použít další nahraditelný parametr, přečtěte si téma [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Podobně jako [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced) s `CAtlModule::UpdateRegistryFromResourceS` tím rozdílem, že vytvoří statický odkaz na komponentu registru ATL (registrátor).

## <a name="see-also"></a>Viz také:

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)<br/>
[Součást registru (registrátor)](../../atl/atl-registry-component-registrar.md)
