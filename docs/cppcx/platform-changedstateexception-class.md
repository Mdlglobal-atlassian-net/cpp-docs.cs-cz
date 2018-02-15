---
title: "Třída Platform::ChangedStateException | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
dev_langs:
- C++
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0910500c24a4e7ca574ac2eebc6264148d14a410
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException – třída
Vyvolá, když vnitřní stav objektu se změnil, a tím zneplatnění výsledky metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Poznámky  
 Příkladem, kde je vyvolána výjimka je, pokud jsou volány metody iterator kolekce nebo kolekce zobrazení po změně její nadřazená kolekce, zneplatnění výsledky metody.  
  
 Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md) třídy.  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  
  
## <a name="see-also"></a>Viz také  
 [Platform::COMException – třída](../cppcx/platform-comexception-class.md)