---
title: "ActivationFactory – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory
dev_langs: C++
helpviewer_keywords: ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6876fb3d418a4dac8a68449da5d0eae855daa440
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Activationfactory::activationfactory – konstruktor](../windows/activationfactory-activationfactory-constructor.md)|Inicializuje ActivationFactory – třída.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Activationfactory::addref – metoda](../windows/activationfactory-addref-method.md)|Zvýší počet odkazů aktuální objekt ActivationFactory.|  
|[Activationfactory::getiids – metoda](../windows/activationfactory-getiids-method.md)|Načte pole ID implementovaných rozhraní.|  
|[Activationfactory::getruntimeclassname – metoda](../windows/activationfactory-getruntimeclassname-method.md)|Získá název modulu runtime třídy objektu, který vytvoří instanci aktuální ActivationFactory.|  
|[Activationfactory::gettrustlevel – metoda](../windows/activationfactory-gettrustlevel-method.md)|Získá objekt, který vytvoří instanci aktuální ActivationFactory úroveň důvěryhodnosti.|  
|[Activationfactory::QueryInterface – metoda](../windows/activationfactory-queryinterface-method.md)|Načte ukazatele k zadanému rozhraní.|  
|[Activationfactory::Release – metoda](../windows/activationfactory-release-method.md)|Snižuje počet odkaz na aktuální objekt ActivationFactory.|  
  
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
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)