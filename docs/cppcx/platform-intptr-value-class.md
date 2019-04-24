---
title: Platform::IntPtr – hodnotová třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
ms.openlocfilehash: 8101fa2c82a0ac3e3b573384d14d9a7eff6ecf61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152733"
---
# <a name="platformintptr-value-class"></a>Platform::IntPtr – hodnotová třída

Představuje podepsaný ukazatel nebo popisovač a jejichž velikost se liší podle platformy (32bitová nebo 64bitová verze).

## <a name="syntax"></a>Syntaxe

```cpp
public value struct IntPtr
```

### <a name="members"></a>Členové

IntPtr má následující členy:

|Člen|Popis|
|------------|-----------------|
|[IntPtr::IntPtr](#ctor)|Inicializuje novou instanci třídy IntPtr.|
|[IntPtr::op_explicit – operátor](#op-explicit)|Převede zadaný parametr IntPtr nebo ukazatel na hodnotu IntPtr.|
|[IntPtr::ToInt32](#toint32)|Převede aktuální IntPtr na 32bitové celé číslo.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="ctor"> </a> IntPtr::IntPtr konstruktor

Inicializuje novou instanci třídy IntPtr se zadanou hodnotou.

### <a name="syntax"></a>Syntaxe

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>Parametry

*value*<br/>
64-bit popisovač nebo ukazatel nebo ukazatel 64 bitů hodnotu nebo hodnotu 32-bit, který lze převést na 64bitovou hodnotu.

## <a name="op-explicit"> </a> IntPtr::op_explicit – operátor

Převede zadaný parametr IntPtr nebo ukazatel na hodnotu IntPtr.

### <a name="syntax"></a>Syntaxe

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>Parametry

*value1*<br/>
Ukazatel na popisovač nebo IntPtr.

*value2*<br/>
Celé číslo 32-bit, který lze převést na IntPtr.

*value3*<br/>
An IntPtr.

### <a name="return-value"></a>Návratová hodnota

První a druhý operátory vrací IntPtr. Třetí operátor vrací ukazatel na hodnotu reprezentované aktuální IntPtr.

## <a name="toint32"> </a> IntPtr::ToInt32 – metoda

Převede aktuální hodnotu IntPtr na 32bitové celé číslo.

### <a name="syntax"></a>Syntaxe

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>Návratová hodnota

32bitové celé číslo.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
