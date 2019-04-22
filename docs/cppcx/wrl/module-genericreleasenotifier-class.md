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
ms.openlocfilehash: 318415c9726426cbd60c205759a6ff8572cc555e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786739"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier – třída

Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný ve výrazu lambda, funktor nebo ukazatel na funkci.

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

Name                                                                                                     | Popis
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::genericreleasenotifier:: genericreleasenotifier –](#genericreleasenotifier-genericreleasenotifier) | Inicializuje novou instanci třídy `Module::GenericReleaseNotifier` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                                                     | Popis
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier:: Invoke](#genericreleasenotifier-invoke) | Volá obslužnou rutinu události spojené s aktuálním `Module::GenericReleaseNotifier` objektu.

### <a name="protected-data-members"></a>Chránění členové dat

Name                                                                          | Popis
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::genericreleasenotifier:: callback_ –](#genericreleasenotifier-callback) | Obsahuje výraz lambda, funktor nebo obslužná rutina události ukazatele na funkce přidružené k aktuální `Module::GenericReleaseNotifier` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="genericreleasenotifier-callback"></a>Module::genericreleasenotifier:: callback_ –

Obsahuje výraz lambda, funktor nebo obslužná rutina události ukazatele na funkce přidružené k aktuální `Module::GenericReleaseNotifier` objektu.

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Module::genericreleasenotifier:: genericreleasenotifier –

Inicializuje novou instanci třídy `Module::GenericReleaseNotifier` třídy.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parametry

*callback*<br/>
Výraz lambda, funktor nebo obslužná rutina události ukazatele na funkci, který lze vyvolat pomocí funkce operátoru závorky (`()`).

*Vydání verze*<br/>
Zadejte `true` povolit volání základní [modulu:: ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) metody; v opačném případě zadejte `false`.

## <a name="genericreleasenotifier-invoke"></a>Module::GenericReleaseNotifier:: Invoke

Volá obslužnou rutinu události spojené s aktuálním `Module::GenericReleaseNotifier` objektu.

```cpp
void Invoke();
```
