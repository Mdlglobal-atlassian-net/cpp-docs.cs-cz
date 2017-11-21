---
title: "Třída Platform::DisconnectedException | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
dev_langs: C++
helpviewer_keywords: Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0010f039db295f2efc9a8b920d685258a66878d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException – třída
Vyvolá, když objekt COM proxy pokusí odkazovat na server COM, která již existuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud třída A odkazy na jiné třídy (třídy B), která je v samostatném procesu, třídy A vyžaduje objekt proxy pro komunikaci se serverem COM mimo proces, obsahuje třídy B. V některých případech přejít server nedostatek paměti bez – třída zároveň budete vědět o něm. V takovém případě je vyvolána výjimka RPC_E_DISCONNECTED a získá převedeny na Platform::DisconnectedException. Jeden scénář, ve kterém se dojde k je při zdroje událostí vyvolá delegáta, který byl předán, ale delegát byl zničen v určitém okamžiku po jeho odběru události. V takovém případě zdroj události přidělíte odebere ze seznamu volání.  
  
 Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md) třídy.  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  
  
## <a name="see-also"></a>Viz také  
 [Platform::COMException – třída](../cppcx/platform-comexception-class.md)