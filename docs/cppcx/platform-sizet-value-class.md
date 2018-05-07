---
title: Platform::SizeT – hodnotová třída | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c69bf34a7965c098f6a656907071e0899b785b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformsizet-value-class"></a>Platform::SizeT – hodnotová třída
Představuje velikost objektu. SizeT je typ nepodepsaná data.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class SizeT sealed : ValueType  
```  
  
### <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[SizeT::SizeT – konstruktor](#ctor)|Inicializuje novou instanci třídy se zadanou hodnotou.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

 ## <a name="ctor"></a>  SizeT::SizeT – konstruktor
Inicializuje novou instanci třídy SizeT se zadanou hodnotou.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
### <a name="parameters"></a>Parametry  
 value1  
 Nepodepsané 32bitovou hodnotu.  
  
 Value2  
 Ukazatel na hodnotu 32-bit bez znaménka.  
  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)