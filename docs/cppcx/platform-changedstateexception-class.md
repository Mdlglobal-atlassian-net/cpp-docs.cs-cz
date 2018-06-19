---
title: Třída Platform::ChangedStateException | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
dev_langs:
- C++
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04daf6229ffa3f5ce41087a34ab53d92e3a1361c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087946"
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