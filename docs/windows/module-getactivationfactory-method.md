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
ms.openlocfilehash: e41b90ea56f65665ccdaff0fe4dceff292d1cdcf
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608102"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory – metoda
Získá objekt factory pro aktivaci pro modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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