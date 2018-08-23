---
title: Module::methodreleasenotifier – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cee634ab62e699b4de6af54a57b0fe3d6b5e9a40
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606605"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier – třída

Vyvolá obslužnou rutinu události po vydání poslední objekt v aktuálním modulu. Obslužná rutina události je zadaný objekt a jejího člena ukazatel na metodu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*  
Typ objektu, jehož členská funkce je obslužnou rutinu události.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Module::MethodReleaseNotifier::MethodReleaseNotifier – konstruktor](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicializuje novou instanci třídy **Module::MethodReleaseNotifier** třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Module::MethodReleaseNotifier::Invoke – metoda](../windows/module-methodreleasenotifier-invoke-method.md)|Volá obslužnou rutinu události spojené s aktuálním **Module::MethodReleaseNotifier** objektu.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[Module::MethodReleaseNotifier::method_ – datový člen](../windows/module-methodreleasenotifier-method-data-member.md)|Uchovává ukazatel na obslužnou rutinu události pro aktuální **Module::MethodReleaseNotifier** objektu.|
|[Module::MethodReleaseNotifier::object_ – datový člen](../windows/module-methodreleasenotifier-object-data-member.md)|Uchovává ukazatel na objekt, jehož členská funkce je obslužnou rutinu události pro aktuální **Module::MethodReleaseNotifier** objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
[Module – třída](../windows/module-class.md)