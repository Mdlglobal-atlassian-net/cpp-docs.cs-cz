---
title: Třída CAtlModule
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
ms.openlocfilehash: cfc11a95a8d5d9354279f4c71698a6bc35c7aca7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748616"
---
# <a name="catlmodule-class"></a>Třída CAtlModule

Tato třída poskytuje metody používané několika třídami modulů ATL.

## <a name="syntax"></a>Syntaxe

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Konstruktor|
|[CAtlModule::~CAtlModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Přepsat tuto metodu přidat parametry atl registru součásti (registrátor) náhradní mapy.|
|[CAtlModule::AddTermFunc](#addtermfunc)|Přidá novou funkci, která má být volána při ukončení modulu.|
|[CAtlModule::GetGITPtr](#getgitptr)|Vrátí ukazatel globálního rozhraní.|
|[CAtlModule::GetLockCount](#getlockcount)|Vrátí počet zámků.|
|[CAtlModule::Zámek](#lock)|Zvýšení počet zámků.|
|[CAtlModule::Termín](#term)|Uvolní všechny datové členy.|
|[CAtlModule::Odemknout](#unlock)|Sníží počet zámků.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Tato metoda je `UpdateRegistryFromResourceD` volána k provedení aktualizace registru.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na součást registru ATL.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAtlModul::m_libid](#m_libid)|Obsahuje identifikátor GUID aktuálního modulu.|
|[CAtlModul::m_pGIT](#m_pgit)|Ukazatel na tabulku globálního rozhraní.|

## <a name="remarks"></a>Poznámky

Tato třída je používána [třídou CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), [třídou CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)a [třídou CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) k poskytování podpory aplikací DLL, aplikací EXE a služeb systému Windows.

Další informace o modulech v atl naleznete v tématu [ATL Module Classes](../../atl/atl-module-classes.md).

Tato třída nahrazuje zastaralou [třídu CComModule používanou](../../atl/reference/ccommodule-class.md) v dřívějších verzích atl.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

Přepsat tuto metodu přidat parametry atl registru součásti (registrátor) náhradní mapy.

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parametry

*pRegistrar*<br/>
Vyhrazeno.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Nahraditelné parametry umožňují klientovi registrátora určit data za běhu. Za tímto účelem registrátor udržuje náhradní mapu, do které zadá hodnoty spojené s nahraditelnými parametry ve skriptu. Registrátor provádí tyto položky za běhu.

Další podrobnosti najdete v tématu [Using Replaceable Parameters (Preprocessor registrátora).](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

Přidá novou funkci, která má být volána při ukončení modulu.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parametry

*pFunc*<br/>
Ukazatel na funkci, kterou chcete přidat.

*Dw*<br/>
Uživatelem definovaná data, předaná funkci.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

Konstruktor

```
CAtlModule() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a iniciuje kritickou část kolem vlákna modulu.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule::~CAtlModule

Destruktor.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

Načte ukazatel na tabulku globálního rozhraní.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parametry

*ppGIT*<br/>
Ukazatel na proměnnou, která obdrží ukazatel na tabulku globálního rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo kód chyby při selhání. E_POINTER je vrácena, pokud *ppGIT* se rovná NULL.

### <a name="remarks"></a>Poznámky

Pokud objekt Tabulka globálního rozhraní neexistuje, je vytvořen a jeho adresa je uložena v členské proměnné [CAtlModule::m_pGIT](#m_pgit).

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud je *ppGIT* rovna hodnotě NULL nebo pokud nelze získat ukazatel tabulky globálního rozhraní.

Informace v tabulce globálního rozhraní naleznete v tématu [IGlobalInterfaceTable.](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

Vrátí počet zámků.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet zámků. Tato hodnota může být užitečné pro diagnostiku a ladění.

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule::Zámek

Zvýšení počet zámků.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Zintáží počet zámků a vrátí aktualizovanou hodnotu. Tato hodnota může být užitečné pro diagnostiku a ladění.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModul::m_libid

Obsahuje identifikátor GUID aktuálního modulu.

```
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModul::m_pGIT

Ukazatel na tabulku globálního rozhraní.

```
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule::Termín

Uvolní všechny datové členy.

```cpp
void Term() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny datové členy. Tato metoda je volána destruktorem.

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule::Odemknout

Sníží počet zámků.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Návratová hodnota

Sníží počet zámků a vrátí aktualizovanou hodnotu. Tato hodnota může být užitečné pro diagnostiku a ladění.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

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

*bRegistrovat*<br/>
TRUE, pokud by měl být objekt registrován; FALSE jinak.

*pMapEntries*<br/>
Ukazatel na náhradní mapu ukládající hodnoty přidružené k nahraditelným parametrům skriptu. Atl automaticky používá %MODULE%. Další nahraditelné parametry naleznete [v tématu CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Spustí skript obsažený v prostředku určeném *lpszRes nebo nResID*. Pokud *bRegister* je PRAVDA, tato metoda zaregistruje objekt v systémovém registru; v opačném případě odebere objekt z registru.

Chcete-li staticky propojit součást registru ATL (registrátor), přečtěte si článek [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).

Tato metoda volá [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) a [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

Tato metoda je `UpdateRegistryFromResourceD` volána k provedení aktualizace registru.

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
Název prostředku.

*bRegistrovat*<br/>
Označuje, zda má být objekt registrován.

*pMapEntries*<br/>
Ukazatel na náhradní mapu ukládající hodnoty přidružené k nahraditelným parametrům skriptu. Atl automaticky používá %MODULE%. Další nahraditelné parametry naleznete [v tématu CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Tato metoda poskytuje implementaci [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

Spustí skript obsažený v zadaném prostředku k registraci nebo zrušení registrace objektu. Tato metoda staticky odkazuje na součást registru ATL.

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

*bRegistrovat*<br/>
Označuje, zda má být skript prostředku zaregistrován.

*pMapEntries*<br/>
Ukazatel na náhradní mapu ukládající hodnoty přidružené k nahraditelným parametrům skriptu. Atl automaticky používá %MODULE%. Další nahraditelné parametry naleznete [v tématu CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). V opačném případě použijte výchozí hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Podobně jako [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) s výjimkou `CAtlModule::UpdateRegistryFromResourceS` vytvoří statické propojení s součástí registru ATL (registrátor).

## <a name="see-also"></a>Viz také

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)<br/>
[Součást registru (registrátor)](../../atl/atl-registry-component-registrar.md)
