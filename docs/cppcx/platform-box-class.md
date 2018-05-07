---
title: Třída Platform::Box | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
dev_langs:
- C++
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59fcdf177f942dd598348654b366e0c0f42e916b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platformbox-class"></a>Platform::Box – třída
Typ hodnoty jako například umožňuje `Windows::Foundation::DateTime` nebo skalárního typu, jako `int` k uložení do `Platform::Object` typu. Obvykle není nutné používat `Box` explicitně, protože zabalení implicitně dochází, když přetypovat na typ hodnoty `Object^`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
ref class Box abstract;  
```  
  ### <a name="remarks"></a>Poznámky  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** vccorlib.h  
  
 **Namespace:** platformy
|Člen|Popis|  
|------------|-----------------|
|[Pole](#ctor)|Vytvoří `Box` který může zapouzdřit hodnotu zadaného typu.|
|[operátor pole&lt;const T&gt;^](#box-const-t)|Umožňuje zabalení převody z `const` třídy hodnoty `T` nebo `enum` třída `T` k `Box<T>`.|
|[operátor pole&lt;const volatile T&gt;^](#box-const-volatile-t)|Umožňuje zabalení převody z `const volatile` třídy hodnoty `T` nebo `enum` typ `T` k `Box<T>`. |
|[operátor pole&lt;T&gt;^](#box-t)|Umožňuje zabalení převody z – hodnotová třída `T` k `Box<T>`.|
|[operátor pole&lt;volatile T&gt;^](#box-volatile-t)|Umožňuje zabalení převody z `volatile` třídy hodnoty `T` nebo `enum` typ `T` k `Box<T>`.|
|[Box::Operator T](#t)|Umožňuje zabalení převody z – hodnotová třída `T` nebo `enum` třída `T` k `Box<T>`.| 
## <a name="ctor"></a> Box::Box – konstruktor
Vytvoří `Box` který může zapouzdřit hodnotu zadaného typu. | |[ Hodnota vlastnosti](#value)| Vrátí hodnotu, která je zapouzdřené v `Box` objektu. |  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Box(T valueArg);  
```  
  
### <a name="parameters"></a>Parametry  
 `valueArg`  
 Typ hodnoty zabaleny – například `int`, `bool`, `float64`, `DateTime`.  
  

## <a name="box-const-t"></a> Pole Box::Operator&lt;const T&gt;^ – operátor
Umožňuje zabalení převody z `const` třídy hodnoty `T` nebo `enum` třída `T` k `Box<T>`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Žádné – hodnotová třída, struktura hodnotu nebo výčtového typu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 A `Platform::Box<T>^` instance, který představuje původní hodnotu do pole v třídě ref.  
  
## <a name="box-const-volatile-t"></a> Pole Box::Operator&lt;const volatile T&gt;^ – operátor
Umožňuje zabalení převody z `const volatile` třídy hodnoty `T` nebo `enum` typ `T` k `Box<T>`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
operator Box<const volatile T>^(const volatile T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Všechny typ výčtu, hodnota třídě nebo struktuře hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 A `Platform::Box<T>^` instance, který představuje původní hodnotu do pole v třídě ref.  
  
## <a name="box-t"></a> Pole Box::Operator&lt;T&gt;^ – operátor
Umožňuje zabalení převody z – hodnotová třída `T` k `Box<T>`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Všechny typ výčtu, hodnota třídě nebo struktuře hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 A `Platform::Box<T>^` instance, který představuje původní hodnotu do pole v třídě ref.  
  
## <a name="box-volatile-t"></a> Pole Box::Operator&lt;volatile T&gt;^ – operátor
Umožňuje zabalení převody z `volatile` třídy hodnoty `T` nebo `enum` typ `T` k `Box<T>`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Všechny typ výčtu, hodnota třídě nebo struktuře hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 A `Platform::Box<T>^` instance, který představuje původní hodnotu do pole v třídě ref.  
  
## <a name="t"></a>  Operátor Box::Operator T
Umožňuje zabalení převody z – hodnotová třída `T` nebo `enum` třída `T` k `Box<T>`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
operator Box<T>^(T valueType);  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Všechny typ výčtu, hodnota třídě nebo struktuře hodnotu. Obsahuje vestavěné typy v [výchozí obor názvů](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 A `Platform::Box<T>^` instance, který představuje původní hodnotu do pole v třídě ref.  
  

## <a name="value"></a> Vlastnost Box::Value
Vrátí hodnotu, která je zapouzdřené v `Box` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí zabalené hodnoty stejného typu, protože byl původně před byl do pole.  
  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)   
 [Zabalení](../cppcx/boxing-c-cx.md)