---
title: Výčet Platform::CallbackContext | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 757de5f686bb809a5d2fb159a3ee547a20edc982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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