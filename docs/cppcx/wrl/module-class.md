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
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371320"
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

*modulTyp*<br/>
Kombinace jedné nebo více hodnot výčtu [ModuleType.](moduletype-enumeration.md)

## <a name="members"></a>Členové

### <a name="protected-classes"></a>Chráněné třídy

Name (Název)                                                                                | Popis
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Modul::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Vyvolá obslužnou rutinu události při uvolnění posledního objektu v aktuálním modulu. Obslužná rutina události je určena na lambda, functor nebo ukazatel na funkci.
[Modul::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Vyvolá obslužnou rutinu události při uvolnění posledního objektu v aktuálním modulu. Obslužná rutina události je určena objektem a jeho ukazatelem na člen metody.
[Modul::ReleaseNotifier](module-releasenotifier-class.md)               | Vyvolá obslužnou rutinu události při uvolnění posledního objektu v modulu.

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                             | Popis
-------------------------------- | -----------------------------------------------------------
[Modul::~Modul](#tilde-module) | Deinitializes aktuální instance `Module` třídy.

### <a name="protected-constructors"></a>Chráněné konstruktory

Name (Název)                      | Popis
------------------------- | ---------------------------------------------------
[Modul::Modul](#module) | Inicializuje novou instanci třídy. `Module`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                    | Popis
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Modul::Vytvořit](#create)                               | Vytvoří instanci modulu.
[Modul::DecrementObjectCount](#decrementobjectcount)   | Sníží počet objektů sledovaných modulem.
[Modul::GetActivationFactory](#getactivationfactory)   | Získá aktivační továrny pro modul.
[Modul::GetClassObject](#getclassobject)               | Načte mezipaměť třídy továren.
[Modul::GetModule](#getmodule)                         | Vytvoří instanci modulu.
[Modul::GetObjectCount](#getobjectcount)               | Načte počet objektů spravovaných tímto modulem.
[Modul::IncrementObjectCount](#incrementobjectcount)   | Zintáží počet objektů sledovaných modulem.
[Modul::RegisterCOMObject](#registercomobject)         | Zaregistruje jeden nebo více objektů MODELU COM, aby se k nim mohly připojit jiné aplikace.
[Modul::RegisterObjects](#registerobjects)             | Registruje objekty com nebo Windows Runtime, aby se k nim mohly připojit jiné aplikace.
[Modul::RegisterWinRTObject](#registerwinrtobject)     | Zaregistruje jeden nebo více objektů prostředí Windows Runtime, aby se k nim mohly připojit jiné aplikace.
[Modul::Ukončit](#terminate)                         | Způsobí, že všechny továrny instance modulu vypnout.
[Modul::Zrušit registraci objektu COMObject](#unregistercomobject)     | Zruší registrace jednoho nebo více objektů MODELU COM, což zabrání ostatním aplikacím v jejich připojení.
[Modul::Zrušit registraci objektů](#unregisterobjects)         | Zruší registrace objektů v zadaném modulu, aby se k nim nemohly připojit jiné aplikace.
[Modul::UnregisterWinRTObject](#unregisterwinrtobject) | Zruší registrace jednoho nebo více objektů prostředí Windows Runtime, aby se k nim nemohly připojit jiné aplikace.

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                      | Popis
------------------------- | --------------------------------
[Modul::Vytvořit](#create) | Vytvoří instanci modulu.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                                         | Popis
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Modul::objectCount_](#objectcount)         | Sleduje, kolik tříd bylo vytvořeno pomocí funkce [Vytvořit.](make-function.md)
[Modul::releaseNotifier_](#releasenotifier) | Podrží ukazatel `ReleaseNotifier` na objekt.

### <a name="macros"></a>Makra

Name (Název)                                                                   | Popis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Aktivovatelná třída](activatableclass-macros.md)              | Naplní vnitřní mezipaměť, která obsahuje továrnu, která může vytvořit instanci zadané třídy. Toto makro určuje výchozí parametry ID výroby a skupiny.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Naplní vnitřní mezipaměť, která obsahuje továrnu, která může vytvořit instanci zadané třídy. Toto makro umožňuje zadat konkrétní parametr výroby.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Naplní vnitřní mezipaměť, která obsahuje továrnu, která může vytvořit instanci zadané třídy. Toto makro umožňuje zadat konkrétní parametry ID výroby a skupiny.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Modul::~Modul

Deinitializes aktuální instance `Module` třídy.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Modul::Vytvořit

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

*Zpětného volání*<br/>
Nazývá se při uvolnění poslední instance objektu modulu.

*Objekt*<br/>
Parametry *objektu* a *metody* se používají v kombinaci. Odkazuje na poslední objekt instance při uvolnění posledního objektu instance v modulu.

*Metoda*<br/>
Parametry *objektu* a *metody* se používají v kombinaci. Odkazuje na metodu objektu poslední instance při uvolnění posledního objektu instance v modulu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na modul.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Modul::DecrementObjectCount

Sníží počet objektů sledovaných modulem.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet před operací snížení.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Modul::GetActivationFactory

Získá aktivační továrny pro modul.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*pActivatibleClassId*<br/>
IID třídy runtime.

*ppIFactory*<br/>
IActivationFactory pro zadanou třídu runtime.

*Název_serveru*<br/>
Název podmnožiny třídních továren v aktuálním modulu. Zadejte název serveru použitý v makru [ActivatableClassWithFactoryEx](activatableclass-macros.md) nebo zadejte `nullptr` výchozí název serveru.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT vrácena GetActivationFactory.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Modul::GetClassObject

Retreives cache třídy továren.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
ID třídy.

*riid řekl:*<br/>
ID rozhraní, které požadujete.

*Ppv*<br/>
Ukazatel na vrácený objekt.

*Název_serveru*<br/>
Název serveru zadaný v `ActivatableClassWithFactory`oblasti `ActivatableClassWithFactoryEx`, `ActivatableClass` nebo makra; nebo `nullptr` získat výchozí název serveru.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze pro com, nikoli prostředí Windows Runtime. Tato metoda zveřejňuje `IClassFactory` pouze metody.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Modul::GetModule

Vytvoří instanci modulu.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na modul.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Modul::GetObjectCount

Načte počet objektů spravovaných tímto modulem.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální počet objektů spravovaných tímto modulem.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Modul::IncrementObjectCount

Zintáží počet objektů sledovaných modulem.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet před operací přírůstek.

## <a name="modulemodule"></a><a name="module"></a>Modul::Modul

Inicializuje novou instanci třídy. `Module`

```cpp
Module();
```

### <a name="remarks"></a>Poznámky

Tento konstruktor je chráněn a `new` nelze jej volat pomocí klíčového slova. Místo toho volejte [modul::GetModule](#getmodule) nebo [Module::Create](#create).

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Modul::objectCount_

Sleduje, kolik tříd bylo vytvořeno pomocí funkce [Vytvořit.](make-function.md)

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Modul::RegisterCOMObject

Zaregistruje jeden nebo více objektů MODELU COM, aby se k nim mohly připojit jiné aplikace.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parametry

*Název_serveru*<br/>
Plně kvalifikovaný název serveru.

*Clsid*<br/>
Pole CLSIDs zaregistrovat.

*Továrny*<br/>
Pole IUnknown rozhraní třídy objektů, jejichž dostupnost je právě publikována.

*Soubory cookie*<br/>
Po dokončení operace pole ukazatelů na hodnoty, které identifikují objekty třídy, které byly registrovány. Tyto hodnoty jsou později použity odvolat registraci.

*Počet*<br/>
Počet CLSIDs zaregistrovat.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud successfu; jinak HRESULT, například CO_E_OBJISREG, který označuje důvod, proč se operace nezdařila.

### <a name="remarks"></a>Poznámky

Objekty COM jsou registrovány u CLSCTX_LOCAL_SERVER výčtu výčtu CLSCTX výčtu.

Typ připojení k registrovaným objektům je určen kombinací aktuálního parametru šablony *comflag* a REGCLS_SUSPENDED výčtu výčtu výčtu REGCLS.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Modul::RegisterObjects

Registruje objekty com nebo Windows Runtime, aby se k nim mohly připojit jiné aplikace.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*Modul*<br/>
Pole objektů com nebo Windows Runtime.

*Název_serveru*<br/>
Název serveru, který objekty vytvořil.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, který označuje důvod, proč se operace nezdařila.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Modul::RegisterWinRTObject

Zaregistruje jeden nebo více objektů prostředí Windows Runtime, aby se k nim mohly připojit jiné aplikace.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parametry

*Název_serveru*<br/>
Název, který určuje podmnožinu objektů ovlivněných touto operací.

*aktivovattřídidy*<br/>
Pole aktivovatelných CLSID s registrací.

*cookie*<br/>
Hodnota, která identifikuje objekty třídy, které byly registrovány. Tato hodnota se později používá k odvolání registrace.

*Počet*<br/>
Počet objektů, které mají být zapsány do registru.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chyba HRESULT, například CO_E_OBJISREG, která označuje důvod, proč se operace nezdařila.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Modul::releaseNotifier_

Podrží ukazatel `ReleaseNotifier` na objekt.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Modul::Ukončit

Způsobí, že všechny továrny instance modulu vypnout.

```cpp
void Terminate();
```

### <a name="remarks"></a>Poznámky

Uvolní továrny v mezipaměti.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Modul::Zrušit registraci objektu COMObject

Zruší registrace jednoho nebo více objektů MODELU COM, což zabrání ostatním aplikacím v jejich připojení.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parametry

*Název_serveru*<br/>
(Nepoužité)

*Soubory cookie*<br/>
Pole ukazatelů na hodnoty, které identifikují objekty třídy, které mají být neregistrované. Pole bylo vytvořeno metodou [RegisterCOMObject.](#registercomobject)

*Počet*<br/>
Počet tříd zrušit registraci.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je tato operace úspěšná; v opačném případě chyba HRESULT, která označuje důvod, proč se operace nezdařila.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Modul::Zrušit registraci objektů

Zruší registrace objektů v zadaném modulu, aby se k nim nemohly připojit jiné aplikace.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*Modul*<br/>
Ukazatel na modul.

*Název_serveru*<br/>
Opravňující název, který určuje podmnožinu objektů ovlivněných touto operací.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je tato operace úspěšná; v opačném případě chyba HRESULT, která označuje důvod, proč se tato operace nezdařila.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Modul::UnregisterWinRTObject

Zruší registrace jednoho nebo více objektů prostředí Windows Runtime, aby se k nim nemohly připojit jiné aplikace.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parametry

*cookie*<br/>
Ukazatel na hodnotu, která identifikuje objekt třídy, jehož registrace má být odvolána.
