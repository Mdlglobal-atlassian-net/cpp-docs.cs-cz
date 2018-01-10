---
title: "Výčet Platform::CallbackContext | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::CallbackContext
dev_langs: C++
helpviewer_keywords: Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ede3cfecadbe87caf5182e0d3df9c25a481f3079
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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