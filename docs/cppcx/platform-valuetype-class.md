---
title: Platform::ValueType – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12766e81ddd90b257830b6bf5adefd2562781d9e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611044"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType – třída
Základní třída pro instance typů hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class ValueType : Object  
```  
  
## <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|[ValueType::ToString](#tostring)|Vrátí řetězcovou reprezentaci objektu. Zděděno z [Platform::Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Poznámky  
 ValueType třída se používá k vytvoření typů hodnot. Typ hodnoty je odvozen od objektu, jehož členové se základním členstvím. Kompilátor však odpojí tyto členy základní úrovně z typů hodnot, které jsou odvozeny z třídy ValueType. Kompilátor znovu tyto členy základní úrovně, když je typ hodnoty v poli.  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serverem:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

## <a name="tostring"></a> ValueType::ToString – metoda
Vrátí řetězcovou reprezentaci objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::String ToString();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Platform::String, který představuje hodnotu.  
    
## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)