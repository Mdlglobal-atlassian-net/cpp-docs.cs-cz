---
title: "ActivationFactory – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73690603b1be1dd74b7ae7626372e3ab6ff9101e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactory-class"></a>ActivationFactory – třída
Umožňuje jednu nebo více tříd, které chcete aktivovat pomocí prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Rozhraní zeroth.  
  
 `I1`  
 První rozhraní.  
  
 `I2`  
 Druhý rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 ActivationFactory poskytuje metody registrace a základních funkcí pro rozhraní IActivationFactory. ActivationFactory také umožňuje zadat vlastní objekt pro vytváření implementace.  
  
 Následující fragment kódu symbolicky znázorňuje, jak používat ActivationFactory.  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 Následující fragment kódu ukazuje způsob použití [implementuje](../windows/implements-structure.md) struktura zadat více než tří rozhraní ID.  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory – konstruktor](../windows/activationfactory-activationfactory-constructor.md)|Inicializuje ActivationFactory – třída.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ActivationFactory::AddRef – metoda](../windows/activationfactory-addref-method.md)|Zvýší počet odkazů aktuální objekt ActivationFactory.|  
|[ActivationFactory::GetIids – metoda](../windows/activationfactory-getiids-method.md)|Načte pole ID implementovaných rozhraní.|  
|[ActivationFactory::GetRuntimeClassName – metoda](../windows/activationfactory-getruntimeclassname-method.md)|Získá název modulu runtime třídy objektu, který vytvoří instanci aktuální ActivationFactory.|  
|[ActivationFactory::GetTrustLevel – metoda](../windows/activationfactory-gettrustlevel-method.md)|Získá objekt, který vytvoří instanci aktuální ActivationFactory úroveň důvěryhodnosti.|  
|[ActivationFactory::QueryInterface – metoda](../windows/activationfactory-queryinterface-method.md)|Načte ukazatele k zadanému rozhraní.|  
|[ActivationFactory::Release – metoda](../windows/activationfactory-release-method.md)|Snižuje počet odkaz na aktuální objekt ActivationFactory.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ActivationFactory`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)