---
title: Platform::IntPtr – hodnotová třída | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
dev_langs:
- C++
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b54facc94be3f43b500e38371e0eba9e00d130a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr – hodnotová třída
Představuje podepsaný ukazatel nebo popisovač a jehož velikost se liší podle platformy (32bitová nebo 64bitová verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public value struct IntPtr  
```  
  
### <a name="members"></a>Členové  
 IntPtr má následující členy:  
  
|Člen|Popis|  
|------------|-----------------|  
|[IntPtr::IntPtr](#ctor)|Inicializuje novou instanci třídy IntPtr.|  
|[IntPtr::op_Explicit – operátor](#op-explicit)|Převede zadaný parametr IntPtr nebo ukazatel na hodnotu IntPtr.|  
|[IntPtr::ToInt32](#toint32)|Převede aktuální IntPtr 32bitové celé číslo.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadata:** platform.winmd  

## <a name="ctor"> </a> IntPtr::IntPtr – konstruktor
Inicializuje novou instanci třídy IntPtr se zadanou hodnotou.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );  
```  
  
### <a name="parameters"></a>Parametry  
 value  
 Popisovač 64-bit nebo ukazatel nebo ukazatel na hodnotu 64-bit nebo 32bitovou hodnotu, která lze převést na hodnotu 64-bit.  
  


## <a name="op-explicit"> </a> IntPtr::op_Explicit – operátor
Převede zadaný parametr IntPtr nebo ukazatel na hodnotu IntPtr.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
### <a name="parameters"></a>Parametry  
 value1  
 Ukazatel na popisovač nebo IntPtr.  
  
 Value2  
 Celé 32bitové číslo, které lze převést na IntPtr.  
  
 hodnota3  
 IntPtr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Operátory první a druhý vrátit IntPtr. Vrátí třetí operátor ukazatel na hodnotu reprezentována aktuální IntPtr.  
  


## <a name="toint32"> </a> IntPtr::ToInt32 – metoda
Převede aktuální hodnotu IntPtr 32bitové celé číslo.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
int32 IntPtr::ToInt32();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 32bitové celé číslo.  
  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)