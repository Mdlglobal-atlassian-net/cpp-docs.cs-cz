---
title: "Třída Platform::Box | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Box
dev_langs: C++
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac0940d9a7277b7b3f5b66e8d27750a593081471
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
## <a name="ctor"></a>Box::Box – konstruktor
Vytvoří `Box` který může zapouzdřit hodnotu zadaného typu. | |[ Hodnota vlastnosti](#value)| Vrátí hodnotu, která je zapouzdřené v `Box` objektu. |  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Box(T valueArg);  
```  
  
### <a name="parameters"></a>Parametry  
 `valueArg`  
 Typ hodnoty zabaleny – například `int`, `bool`, `float64`, `DateTime`.  
  

## <a name="box-const-t"></a>Pole Box::Operator&lt;const T&gt;^ – operátor
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
  
## <a name="box-const-volatile-t"></a>Pole Box::Operator&lt;const volatile T&gt;^ – operátor
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
  
## <a name="box-t"></a>Pole Box::Operator&lt;T&gt;^ – operátor
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
  
## <a name="box-volatile-t"></a>Pole Box::Operator&lt;volatile T&gt;^ – operátor
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
  
## <a name="t"></a>Operátor Box::Operator T
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
  

## <a name="value"></a>Vlastnost Box::Value
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