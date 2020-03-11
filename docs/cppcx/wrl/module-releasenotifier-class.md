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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865584"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier – třída

Vyvolá obslužnou rutinu události při uvolnění posledního objektu v modulu.

## <a name="syntax"></a>Syntaxe

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                                                | Popis
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Modul:: ReleaseNotifier –:: ~ ReleaseNotifier –](#releasenotifier-tilde-releasenotifier) | Deinicializuje aktuální instanci třídy `Module::ReleaseNotifier`.
[Modul:: ReleaseNotifier –:: ReleaseNotifier –](#releasenotifier-releasenotifier)        | Inicializuje novou instanci třídy `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Veřejné metody

Název                                                         | Popis
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: ReleaseNotifier –:: Invoke](#releasenotifier-invoke)   | Při implementaci zavolá obslužnou rutinu události, když se uvolní poslední objekt v modulu.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Odstraní aktuální objekt `Module::ReleaseNotifier`, pokud byl objekt vytvořen s parametrem **true**.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Modul:: ReleaseNotifier –:: ~ ReleaseNotifier –

Deinicializuje aktuální instanci třídy `Module::ReleaseNotifier`.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module:: ReleaseNotifier –:: Invoke

Při implementaci zavolá obslužnou rutinu události, když se uvolní poslední objekt v modulu.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Modul:: ReleaseNotifier –:: Release

Odstraní aktuální objekt `Module::ReleaseNotifier`, pokud byl objekt vytvořen s parametrem **true**.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Modul:: ReleaseNotifier –:: ReleaseNotifier –

Inicializuje novou instanci třídy `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*předběžné*<br/>
`true` odstranit tuto instanci při volání metody `Release`; tuto instanci `false` neodstraňujte.
