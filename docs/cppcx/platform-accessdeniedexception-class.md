---
title: "Třída Platform::AccessDeniedException | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ccbadf13e7a4f4d82bce9c402a4816d31b0fdce6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException – třída
Vyvolána při přístupu k prostředku nebo funkci byl odepřen.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
### <a name="remarks"></a>Poznámky  
 Při dosažení této výjimky, ujistěte se, zda máte požadovaná příslušnou funkci a provádí požadované deklarace v manifest balíčku aplikace. Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md) třídy.  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  
  
## <a name="see-also"></a>Viz také  
 [Platform::COMException – třída](../cppcx/platform-comexception-class.md)