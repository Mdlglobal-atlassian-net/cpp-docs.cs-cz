---
title: "Třída Platform::WrongThreadException | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
dev_langs:
- C++
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 730c3039edfd4cc3773f61c7e81e0b7b933fbeac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformwrongthreadexception-class"></a>Platform::WrongThreadException – třída
Vyvolá, když vlákno volání mimo jiné ukazatele rozhraní pro objekt proxy serveru, který nepatří do objektu apartment vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md).  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  
  
## <a name="see-also"></a>Viz také  
 [Platform::COMException – třída](../cppcx/platform-comexception-class.md)