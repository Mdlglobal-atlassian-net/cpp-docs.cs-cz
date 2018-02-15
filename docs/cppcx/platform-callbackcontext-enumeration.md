---
title: "Výčet Platform::CallbackContext | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9d34f7ef8a953ce60972c27b34e257ea66d62d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext – výčet
Určuje přístup z více vláken kontext, ve kterém se provádí funkce zpětného volání (obslužné rutiny události).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum class CallbackContext {};  
```  
  
### <a name="members"></a>Členové  
  
|Typ kódu|Popis|  
|---------------|-----------------|  
|všechny|Funkce zpětného volání můžete spustit na jakýkoli kontext přístup z více vláken.|  
|stejné|Funkce zpětného volání můžete provést pouze vlákno kontext, který spuštění asynchronní operaci.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd