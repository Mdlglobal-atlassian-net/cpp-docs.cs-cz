---
title: "Module::getactivationfactory – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GetActivationFactory
dev_langs: C++
helpviewer_keywords: GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d5c5ca4d470f52ff9dde862cc99b10a3459cd0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory – metoda
Získá objekt pro vytváření aktivace pro modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pActivatibleClassId`  
 Identifikátory IID třídu modulu runtime.  
  
 `ppIFactory`  
 IActivationFactory pro třídu zadaného modulu runtime.  
  
 `serverName`  
 Název podmnožinu objekty pro vytváření tříd v aktuální modulu. Zadejte název serveru, který je používán [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makro, nebo zadejte `nullptr` získat výchozí název serveru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT vrácený getactivationfactory –.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
[Module – třídy](../windows/module-class.md) [activatableclass – makra](../windows/activatableclass-macros.md)