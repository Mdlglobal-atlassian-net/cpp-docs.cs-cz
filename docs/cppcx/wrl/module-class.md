---
title: Modul – třída
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: db3eb123382ac70f6198d094c5eb3fe44d3bbcd9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786879"
---
# <a name="module-class"></a>Modul – třída

Představuje kolekci souvisejících objektů.

## <a name="syntax"></a>Syntaxe

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Parametry

*moduleType*<br/>
Kombinace jedné nebo více [ModuleType](moduletype-enumeration.md) hodnot výčtu.

## <a name="members"></a>Členové

### <a name="protected-classes"></a>Chráněné třídy

Name                                                                                | Popis
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module::genericreleasenotifier –](module-genericreleasenotifier-class.md) | Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný ve výrazu lambda, funktor nebo ukazatel na funkci.
[Module::methodreleasenotifier –](module-methodreleasenotifier-class.md)   | Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.
[Module::ReleaseNotifier](module-releasenotifier-class.md)               | Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.

### <a name="public-constructors"></a>Veřejné konstruktory

Name                             | Popis
-------------------------------- | -----------------------------------------------------------
[Module::~Module](#tilde-module) | Zruší inicializaci aktuální instance `Module` třídy.

### <a name="protected-constructors"></a>Chráněné konstruktory

Name                      | Popis
------------------------- | ---------------------------------------------------
[Module::module –](#module) | Inicializuje novou instanci třídy `Module` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                                    | Popis
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module::Create –](#create)                               | Vytvoří instanci modulu.
[Module::decrementobjectcount –](#decrementobjectcount)   | Sníží počet objektů, které sledují modulem.
[Module::getactivationfactory –](#getactivationfactory)   | Získá objekt factory pro aktivaci pro modul.
[Module::GetClassObject –](#getclassobject)               | Načte mezipaměť objekty pro vytváření tříd.
[Module::getmodule –](#getmodule)                         | Vytvoří instanci modulu.
[Module::getobjectcount –](#getobjectcount)               | Získá počet objektů, které spravuje tento modul.
[Module::incrementobjectcount –](#incrementobjectcount)   | Zvýší počet objektů, které jsou sledovány v rámci modulu.
[Module::registercomobject –](#registercomobject)         | Zaregistruje jeden nebo více objektů modelu COM, takže k nim mohli připojit další aplikace.
[Module::registerobjects –](#registerobjects)             | Zaregistruje objekty COM nebo prostředí Windows Runtime, takže k nim mohli připojit další aplikace.
[Module::RegisterWinRTObject](#registerwinrtobject)     | Zaregistruje jeden nebo více objektů prostředí Windows Runtime, takže k nim mohli připojit další aplikace.
[Module::terminate –](#terminate)                         | Způsobí, že všechny objekty pro vytváření vytvořit instanci modulu pro vypnutí.
[Module::unregistercomobject –](#unregistercomobject)     | Zruší jeden nebo více objektů modelu COM, registraci což zabrání aplikacím bránily v připojení k nim.
[Module::unregisterobjects –](#unregisterobjects)         | Zruší registraci objekty v zadaném modulu tak, aby k nim nelze připojit další aplikace.
[Module::UnregisterWinRTObject](#unregisterwinrtobject) | Zruší registraci jeden nebo více objektů prostředí Windows Runtime, tak, aby k nim nelze připojit další aplikace.

### <a name="protected-methods"></a>Chráněné metody

Name                      | Popis
------------------------- | --------------------------------
[Module::Create –](#create) | Vytvoří instanci modulu.

### <a name="protected-data-members"></a>Chránění členové dat

Name                                         | Popis
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module::objectcount_ –](#objectcount)         | Uchovává informace o tom, kolik třídy byly vytvořeny s [zkontrolujte](make-function.md) funkce.
[Module::releasenotifier_ –](#releasenotifier) | Uchovává ukazatel `ReleaseNotifier` objektu.

### <a name="macros"></a>Makra

Název | Popis------| --- [Activatableclass –](activatableclass-macros.md) |  Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy. Toto makro Určuje výchozí objekt pro vytváření a skupiny ID parametry.
[ActivatableClassWithFactory](activatableclass-macros.md) | Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy. Toto makro umožňuje zadat parametr konkrétní objekt pro vytváření.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Naplní interní mezipaměť, která obsahuje objekt factory, který můžete vytvořit instanci dané třídy. Toto makro umožňuje určit konkrétní objekt pro vytváření a parametry ID skupiny.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="tilde-module"></a>Module::~Module

Zruší inicializaci aktuální instance `Module` třídy.

```cpp
virtual ~Module();
```

## <a name="create"></a>Module::Create –

Vytvoří instanci modulu.

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ modulu.

*callback*<br/>
Volá se, když se uvolní objekt poslední instance modulu.

*object*<br/>
*Objekt* a *metoda* v kombinaci se používají parametry. Když se uvolní objekt poslední instance v modulu odkazuje na poslední instance objektu.

*– Metoda*<br/>
*Objekt* a *metoda* v kombinaci se používají parametry. Odkazuje na metodu poslední instance objektu poslední objekt instance v modulu se při uvolnění.

### <a name="return-value"></a>Návratová hodnota

Odkaz na modul.

## <a name="decrementobjectcount"></a>Module::decrementobjectcount –

Sníží počet objektů, které sledují modulem.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet před provedením operace dekrementace.

## <a name="getactivationfactory"></a>Module::getactivationfactory –

Získá objekt factory pro aktivaci pro modul.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*pActivatibleClassId*<br/>
Identifikátor IID třídy modulu runtime.

*ppIFactory*<br/>
IActivationFactory pro třídu zadaného modulu runtime.

*serverName*<br/>
Název dílčí sady objekty pro vytváření tříd v aktuálním modulu. Zadejte název serveru používané [ActivatableClassWithFactoryEx](activatableclass-macros.md) – makro, nebo zadejte `nullptr` získat výchozí název serveru.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT vrácený getactivationfactory –.

## <a name="getclassobject"></a>Module::GetClassObject –

Načte mezipaměť objekty pro vytváření tříd.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*clsid*<br/>
ID třídy.

*riid*<br/>
ID rozhraní, které požadujete.

*ppv*<br/>
Ukazatel na vráceného objektu.

*serverName*<br/>
Název serveru, který je zadán buď `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, nebo `ActivatableClass` – makro; nebo `nullptr` získat výchozí název serveru.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze pro model COM, nikoliv modul Windows Runtime. Tato metoda poskytuje pouze `IClassFactory` metody.

## <a name="getmodule"></a>Module::getmodule –

Vytvoří instanci modulu.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na modul.

## <a name="getobjectcount"></a>Module::getobjectcount –

Získá počet objektů, které spravuje tento modul.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet objektů, které spravuje tento modul.

## <a name="incrementobjectcount"></a>Module::incrementobjectcount –

Zvýší počet objektů, které jsou sledovány v rámci modulu.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet před provedením operace Inkrementace.

## <a name="module"></a>Module::module –

Inicializuje novou instanci třídy `Module` třídy.

```cpp
Module();
```

### <a name="remarks"></a>Poznámky

Tento konstruktor je chráněn a nelze volat pomocí `new` – klíčové slovo. Namísto toho zavolejte metodu buď [Module::getmodule –](#getmodule) nebo [Module::Create –](#create).

## <a name="objectcount"></a>Module::objectcount_ –

Uchovává informace o tom, kolik třídy byly vytvořeny s [zkontrolujte](make-function.md) funkce.

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module::registercomobject –

Zaregistruje jeden nebo více objektů modelu COM, takže k nim mohli připojit další aplikace.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
Plně kvalifikovaný název serveru.

*CLSID*<br/>
Pole CLSID k registraci.

*objekty pro vytváření*<br/>
Pole rozhraní IUnknown objektů tříd, jejichž dostupnost je publikován.

*cookies*<br/>
Po dokončení operace, pole ukazatelů na hodnoty, které identifikují třídu objektů, které jste zaregistrovali. Tyto hodnoty se později použijí zrušit registraci.

*Počet*<br/>
Počet CLSID k registraci.

### <a name="return-value"></a>Návratová hodnota

S_OK Pokud úspěšné; v opačném případě HRESULT jako je například CO_E_OBJISREG, který označuje důvod operace se nezdařila.

### <a name="remarks"></a>Poznámky

Objekty modelu COM jsou registrovány CLSCTX_LOCAL_SERVER enumerátor výčtu CLSCTX.

Typ připojení k registrované objekty je určená kombinací aktuální *comflag* parametr šablony a REGCLS_SUSPENDED enumerátor výčtu REGCLS.

## <a name="registerobjects"></a>Module::registerobjects –

Zaregistruje objekty COM nebo prostředí Windows Runtime, takže k nim mohli připojit další aplikace.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*module*<br/>
Pole objektů COM nebo prostředí Windows Runtime.

*serverName*<br/>
Název serveru, který vytvořil objekty.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, který označuje důvod operace se nezdařila.

## <a name="registerwinrtobject"></a>Module::RegisterWinRTObject

Zaregistruje jeden nebo více objektů prostředí Windows Runtime, takže k nim mohli připojit další aplikace.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
Název, který určuje podmnožinu objekty ovlivněné touto operací.

*activatableClassIds*<br/>
Pole aktivovatelné CLSID k registraci.

*cookie*<br/>
Hodnota, která označuje, které jste zaregistrovali objekty třídy. Tato hodnota se používá později zrušení registrace.

*Počet*<br/>
Počet objektů, které chcete zaregistrovat.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chybu HRESULT jako je například CO_E_OBJISREG, který označuje důvod operace se nezdařila.

## <a name="releasenotifier"></a>Module::releasenotifier_ –

Uchovává ukazatel `ReleaseNotifier` objektu.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module::terminate –

Způsobí, že všechny objekty pro vytváření vytvořit instanci modulu pro vypnutí.

```cpp
void Terminate();
```

### <a name="remarks"></a>Poznámky

Uvolní továren v mezipaměti.

## <a name="unregistercomobject"></a>Module::unregistercomobject –

Zruší jeden nebo více objektů modelu COM, registraci což zabrání aplikacím bránily v připojení k nim.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
(Nepoužívané)

*cookies*<br/>
Pole ukazatelů na hodnoty, které identifikují objekty třídy pro odstranění registrace. Pole byl vytvořen [registercomobject –](#registercomobject) metody.

*Počet*<br/>
Počet tříd se zrušit registraci.

### <a name="return-value"></a>Návratová hodnota

Pokud je tato operace úspěšná; S_OK v opačném případě chybu HRESULT, který označuje důvod operace se nezdařila.

## <a name="unregisterobjects"></a>Module::unregisterobjects –

Zruší registraci objekty v zadaném modulu tak, aby k nim nelze připojit další aplikace.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*module*<br/>
Ukazatel na modul.

*serverName*<br/>
Kvalifikovaný název, který určuje podmnožinu objekty ovlivněné touto operací.

### <a name="return-value"></a>Návratová hodnota

Pokud je tato operace úspěšná; S_OK v opačném případě chybu HRESULT, který označuje důvod tato operace se nezdařila.

## <a name="unregisterwinrtobject"></a>Module::UnregisterWinRTObject

Zruší registraci jeden nebo více objektů prostředí Windows Runtime, tak, aby k nim nelze připojit další aplikace.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parametry

*cookie*<br/>
Ukazatel na hodnotu, která identifikuje objektu třídy, jehož registrace je zrušené.
