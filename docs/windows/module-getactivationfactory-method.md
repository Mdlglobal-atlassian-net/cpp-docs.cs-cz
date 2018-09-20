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
ms.openlocfilehash: 995594ee48e6ca408e88d9ab14968d88b536d309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403504"
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

*pActivatibleClassId*<br/>
Identifikátor IID třídy modulu runtime.

*ppIFactory*<br/>
IActivationFactory pro třídu zadaného modulu runtime.

*název_serveru*<br/>
Název dílčí sady objekty pro vytváření tříd v aktuálním modulu. Zadejte název serveru používané [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) – makro, nebo zadejte **nullptr** získat výchozí název serveru.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT vrácený getactivationfactory –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Module – třída](../windows/module-class.md)<br/>
[ActivatableClass – makra](../windows/activatableclass-macros.md)