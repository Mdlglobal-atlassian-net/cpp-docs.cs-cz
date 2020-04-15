---
title: Module::GenericReleaseNotifier – třída
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371310"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier – třída

Vyvolá obslužnou rutinu události při uvolnění posledního objektu v aktuálním modulu. Obslužná rutina události je určena na lambda, functor nebo ukazatel na funkci.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ datového člena, který obsahuje umístění obslužné rutiny události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                                                                     | Popis
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Modul::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Inicializuje novou instanci třídy. `Module::GenericReleaseNotifier`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                                     | Popis
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Modul::GenericReleaseNotifier::Invoke Modul::GenericReleaseNotifier::Invoke Modul::GenericReleaseNotifier::Invoke Modul:](#genericreleasenotifier-invoke) | Zavolá obslužnou `Module::GenericReleaseNotifier` rutinu události přidruženou k aktuálnímu objektu.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                                                                          | Popis
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Modul::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | Obsahuje obslužnou rutinu události lambda, functor `Module::GenericReleaseNotifier` nebo ukazatel na funkci přidruženou k aktuálnímu objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Modul::GenericReleaseNotifier::callback_

Obsahuje obslužnou rutinu události lambda, functor `Module::GenericReleaseNotifier` nebo ukazatel na funkci přidruženou k aktuálnímu objektu.

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Modul::GenericReleaseNotifier::GenericReleaseNotifier

Inicializuje novou instanci třídy. `Module::GenericReleaseNotifier`

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parametry

*Zpětného volání*<br/>
Obslužná rutina události lambda, functor nebo pointer-to-function, kterou`()`lze vyvolat pomocí operátoru funkce závorek ( ).

*Vydání*<br/>
Zadejte, `true` chcete-li povolit volání základní metody [Module::ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) metody; v opačném `false`případě zadejte .

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Modul::GenericReleaseNotifier::Invoke Modul::GenericReleaseNotifier::Invoke Modul::GenericReleaseNotifier::Invoke Modul:

Zavolá obslužnou `Module::GenericReleaseNotifier` rutinu události přidruženou k aktuálnímu objektu.

```cpp
void Invoke();
```
