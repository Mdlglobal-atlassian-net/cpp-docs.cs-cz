---
title: Module::ReleaseNotifier – třída
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: f314d09c443d0d284e3a821b5c879bfb74baf812
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371277"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier – třída

Vyvolá obslužnou rutinu události při uvolnění posledního objektu v modulu.

## <a name="syntax"></a>Syntaxe

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                                                | Popis
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Modul::ReleaseNotifier::~ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Deinitializes aktuální instance `Module::ReleaseNotifier` třídy.
[Modul::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | Inicializuje novou instanci třídy. `Module::ReleaseNotifier`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                         | Popis
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Modul::ReleaseNotifier::Invoke Modul::ReleaseNotifier::Invoke Modul::ReleaseNotifier::Invoke Modul:](#releasenotifier-invoke)   | Při implementaci volá obslužnou rutinu události při uvolnění posledního objektu v modulu.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Odstraní aktuální `Module::ReleaseNotifier` objekt, pokud byl objekt vytvořen s parametrem **true**.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>Modul::ReleaseNotifier::~ReleaseNotifier

Deinitializes aktuální instance `Module::ReleaseNotifier` třídy.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>Modul::ReleaseNotifier::Invoke Modul::ReleaseNotifier::Invoke Modul::ReleaseNotifier::Invoke Modul:

Při implementaci volá obslužnou rutinu události při uvolnění posledního objektu v modulu.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>Modul::ReleaseNotifier::Release

Odstraní aktuální `Module::ReleaseNotifier` objekt, pokud byl objekt vytvořen s parametrem **true**.

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>Modul::ReleaseNotifier::ReleaseNotifier

Inicializuje novou instanci třídy. `Module::ReleaseNotifier`

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Vydání*<br/>
`true`chcete-li odstranit `Release` tuto instanci při volání metody; `false` neodstraňujte tuto instanci.
