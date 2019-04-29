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
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403253"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier – třída

Vyvolá obslužnou rutinu události po vydání poslední objekt v modulu.

## <a name="syntax"></a>Syntaxe

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                                                | Popis
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module::ReleaseNotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Zruší inicializaci aktuální instance `Module::ReleaseNotifier` třídy.
[Module::releasenotifier:: releasenotifier –](#releasenotifier-releasenotifier)        | Inicializuje novou instanci třídy `Module::ReleaseNotifier` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                                         | Popis
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module::ReleaseNotifier:: Invoke](#releasenotifier-invoke)   | Při implementaci, volá obslužná rutina události po vydání poslední objekt v modulu.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Odstraní aktuální `Module::ReleaseNotifier` objektu, pokud byl objekt zkonstruován s parametrem **true**.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module::ReleaseNotifier:: ~ ReleaseNotifier

Zruší inicializaci aktuální instance `Module::ReleaseNotifier` třídy.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module::ReleaseNotifier:: Invoke

Při implementaci, volá obslužná rutina události po vydání poslední objekt v modulu.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

Odstraní aktuální `Module::ReleaseNotifier` objektu, pokud byl objekt zkonstruován s parametrem **true**.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module::releasenotifier:: releasenotifier –

Inicializuje novou instanci třídy `Module::ReleaseNotifier` třídy.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Vydání verze*<br/>
`true` odstranit toto instance, kdy `Release` metoda je volána; `false` k odstranění této instance.
