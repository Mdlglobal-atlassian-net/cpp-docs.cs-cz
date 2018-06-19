---
title: Třída Platform::ValueType | Microsoft Docs
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1994aa6445c67bae138a51f1d3eebb2a54f9b17d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088203"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType – třída
Základní třída pro typy hodnot instancí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class ValueType : Object  
```  
  
## <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|[ValueType::ToString](#tostring)|Vrátí řetězcovou reprezentaci objektu. Zděděno z [Platform::Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Poznámky  
 Typ hodnoty třída se používá k vytvoření typů hodnot. Typ hodnoty je odvozený od objektu, který má členové se základním členstvím. Kompilátor však umožňuje odpojit tyto základní členy z typů hodnot, které jsou odvozeny od třídy typ hodnoty. Kompilátor reattaches základní členů, když je do pole Typ hodnoty.  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
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
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)