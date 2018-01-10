---
title: "Třída Platform::AccessDeniedException | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs: C++
helpviewer_keywords: Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2e39acbd87dffc6bd0ffdeb483ada1eb1c6cc52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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