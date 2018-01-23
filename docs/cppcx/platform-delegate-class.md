---
title: "Třída Platform::Delegate | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Delegate
dev_langs: C++
helpviewer_keywords: Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 661e96cd2455610e6a7f669928d49c915b7d7575
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2018
---
# <a name="platformdelegate-class"></a>Platform::Delegate – třída
Představuje objekt funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public delegate void delegate_name();  
```  
  
### <a name="members"></a>Členové  
 Má Equals(), GetHashCode(), delegát třídy a metody ToString() odvozen od [Platform::Object třída](../cppcx/platform-object-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Použít [delegovat](../windows/delegate-cpp-component-extensions.md) – klíčové slovo vytvořit delegáti; nepoužívejte Platform::Delegate explicitně. Další informace najdete v tématu [delegáti](../cppcx/delegates-c-cx.md). Příklad toho, jak vytvářet a využívat delegáta, naleznete v části [vytváření součásti systému Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)