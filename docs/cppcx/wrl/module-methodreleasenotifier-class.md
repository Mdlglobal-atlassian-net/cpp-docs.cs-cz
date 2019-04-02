---
title: Module::MethodReleaseNotifier – třída
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: 41b7cfb2601cd2023e895dbcf1a56e85fe65b35d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786553"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier – třída

Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, jehož členská funkce je obslužnou rutinu události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                                                                 | Popis
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::methodreleasenotifier:: methodreleasenotifier –](#methodreleasenotifier-methodreleasenotifier) | Inicializuje novou instanci třídy `Module::MethodReleaseNotifier` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                                                   | Popis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier:: Invoke](#methodreleasenotifier-invoke) | Volá obslužnou rutinu události spojené s aktuálním `Module::MethodReleaseNotifier` objektu.

### <a name="protected-data-members"></a>Chránění členové dat

Název                                                                    | Popis
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::methodreleasenotifier:: method_ –](#methodreleasenotifier-method) | Uchovává ukazatel na obslužnou rutinu události pro aktuální `Module::MethodReleaseNotifier` objektu.
[Module::methodreleasenotifier:: object_ –](#methodreleasenotifier-object) | Uchovává ukazatel na objekt, jehož členská funkce je obslužnou rutinu události pro aktuální `Module::MethodReleaseNotifier` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier:: Invoke

Volá obslužnou rutinu události spojené s aktuálním `Module::MethodReleaseNotifier` objektu.

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::methodreleasenotifier:: method_ –

Uchovává ukazatel na obslužnou rutinu události pro aktuální `Module::MethodReleaseNotifier` objektu.

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::methodreleasenotifier:: methodreleasenotifier –

Inicializuje novou instanci třídy `Module::MethodReleaseNotifier` třídy.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parametry

*object*<br/>
Objekt, jehož členská funkce je obslužnou rutinu události.

*– Metoda*<br/>
Členská funkce parametru *objekt* , který je obslužnou rutinu události.

*Vydání verze*<br/>
Zadejte `true` povolit volání základní [modulu:: ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) metody; v opačném případě zadejte `false`.

## <a name="methodreleasenotifier-object"></a>Module::methodreleasenotifier:: object_ –

Uchovává ukazatel na objekt, jehož členská funkce je obslužnou rutinu události pro aktuální `Module::MethodReleaseNotifier` objektu.

```cpp
T* object_;
```
