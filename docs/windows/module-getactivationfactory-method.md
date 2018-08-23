---
title: Module::getactivationfactory – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e87ea3b0e44732d4271385073c48fd92e1aa114
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608924"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory – metoda

Získá objekt factory pro aktivaci pro modul.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*pActivatibleClassId*  
Identifikátor IID třídy modulu runtime.

*ppIFactory*  
IActivationFactory pro třídu zadaného modulu runtime.

*název_serveru*  
Název dílčí sady objekty pro vytváření tříd v aktuálním modulu. Zadejte název serveru používané [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) – makro, nebo zadejte **nullptr** získat výchozí název serveru.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT vrácený getactivationfactory –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)  
[ActivatableClass – makra](../windows/activatableclass-macros.md)