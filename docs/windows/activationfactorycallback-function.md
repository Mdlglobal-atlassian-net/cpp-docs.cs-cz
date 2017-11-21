---
title: "Activationfactorycallback – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs: C++
helpviewer_keywords: ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: adf41c8a518b0ca57326da1dd71c1a8ddd6f0a27
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback – funkce
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `activationId`  
 Zpracování na řetězec, který určuje název třídy modulu runtime.  
  
 `ppFactory`  
 Po této operaci dokončení aktivace objekt factory, která odpovídá parametru `activationId`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT popisující selhání. Hodnoty HRESULT pravděpodobně selhání jsou CLASS_E_CLASSNOTAVAILABLE a E_INVALIDARG.  
  
## <a name="remarks"></a>Poznámky  
 Získá objekt factory aktivace pro ID zadaná aktivace.  
  
 Prostředí Windows Runtime volá tuto funkci zpětného volání k vyžádání objektu zadaného jeho název třídy modulu runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)