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
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371292"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier – třída

Vyvolá obslužnou rutinu události při uvolnění posledního objektu v aktuálním modulu. Obslužná rutina události je určena objektem a jeho ukazatelem na člen metody.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, jehož členská funkce je obslužná rutina události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                                                                 | Popis
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Modul::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Inicializuje novou instanci třídy. `Module::MethodReleaseNotifier`

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                                   | Popis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Modul::MethodReleaseNotifier::Invoke](#methodreleasenotifier-invoke) | Zavolá obslužnou `Module::MethodReleaseNotifier` rutinu události přidruženou k aktuálnímu objektu.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                                                                    | Popis
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Modul::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Podrží ukazatel na obslužnou rutinu události pro aktuální `Module::MethodReleaseNotifier` objekt.
[Modul::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Obsahuje ukazatel na objekt, jehož členská funkce `Module::MethodReleaseNotifier` je obslužná rutina události pro aktuální objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Obor názvů:** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Modul::MethodReleaseNotifier::Invoke

Zavolá obslužnou `Module::MethodReleaseNotifier` rutinu události přidruženou k aktuálnímu objektu.

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Modul::MethodReleaseNotifier::method_

Podrží ukazatel na obslužnou rutinu události pro aktuální `Module::MethodReleaseNotifier` objekt.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Modul::MethodReleaseNotifier::MethodReleaseNotifier

Inicializuje novou instanci třídy. `Module::MethodReleaseNotifier`

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parametry

*Objekt*<br/>
Objekt, jehož členská funkce je obslužná rutina události.

*Metoda*<br/>
Členská funkce *parametru objektu,* který je obslužnou rutinou události.

*Vydání*<br/>
Zadejte, `true` chcete-li povolit volání základní metody [Module::ReleaseNotifier::Release()](module-releasenotifier-class.md#releasenotifier-release) metody; v opačném `false`případě zadejte .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Modul::MethodReleaseNotifier::object_

Obsahuje ukazatel na objekt, jehož členská funkce `Module::MethodReleaseNotifier` je obslužná rutina události pro aktuální objekt.

```cpp
T* object_;
```
