---
title: "RuntimeClass – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass
dev_langs: C++
helpviewer_keywords: RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e757712b360ff3ed4de12d8236c75a691a1f0c7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass – třída
Představuje instancí třídu, která dědí zadaný počet rozhraní a obsahuje zadané prostředí Windows Runtime, classic COM a slabé odkaz na podporu.  
  
 Obvykle jsou odvozeny vaší knihovny WRL typů z `RuntimeClass` vzhledem k tomu, že tato třída implementuje `AddRef`, `Release`, a `QueryInterface`, a pomáhá spravovat celkový počet odkazů modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
class RuntimeClass : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT, RuntimeClassFlags<WinRt>>;  
  
template <  
   unsigned int classFlags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
class RuntimeClass<RuntimeClassFlags<classFlags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT, RuntimeClassFlags<classFlags> >;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 ID zeroth rozhraní. (Povinné)  
  
 `I1`  
 První rozhraní ID. (Volitelné)  
  
 `I2`  
 Druhý ID rozhraní. (Volitelné)  
  
 `I3`  
 Třetí ID rozhraní. (Volitelné)  
  
 `I4`  
 Čtvrtý ID rozhraní. (Volitelné)  
  
 `I5`  
 Páté ID rozhraní. (Volitelné)  
  
 `I6`  
 Šesté ID rozhraní. (Volitelné)  
  
 `I7`  
 Sedmého ID rozhraní. (Volitelné)  
  
 `I8`  
 ID nakrmeni rozhraní. (Volitelné)  
  
 `I9`  
 Deváté ID rozhraní. (Volitelné)  
  
 `classFlags`  
 Kombinace jednoho nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnot výčtu.  `__WRL_CONFIGURATION_LEGACY__` Makro lze definovat za účelem změnit výchozí hodnotu classFlags pro všechny třídy za běhu v projektu. -Li definována, jsou instance RuntimeClass – agilní dy výchozí. Pokud není definované, RuntimeClass instance jsou agilní ve výchozím nastavení. Aby se zabránilo nejednoznačnosti vždycky zadat RuntimeClassType::FtmBase nebo RuntimeClassType::InhibitFtmBase.
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Runtimeclass::runtimeclass – konstruktor](../windows/runtimeclass-runtimeclass-constructor.md)|Inicializuje aktuální instanci RuntimeClass – třída.|  
|[RuntimeClass:: ~ runtimeclass – destruktor](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Deinitializes aktuální instance třídy RuntimeClass.|  
  
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
  
 `RuntimeClass`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)
