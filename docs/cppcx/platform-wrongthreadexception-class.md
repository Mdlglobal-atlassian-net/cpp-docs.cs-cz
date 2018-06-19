---
title: Třída Platform::WrongThreadException | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
dev_langs:
- C++
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f01b52470f5c70c588c7905a2c46f7cae9b26d06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088255"
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