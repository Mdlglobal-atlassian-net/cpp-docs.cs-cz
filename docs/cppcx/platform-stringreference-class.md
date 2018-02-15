---
title: "Třída Platform::StringReference | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
dev_langs:
- C++
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c23960e392f39c44a57176e4afb81999783bad6c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformstringreference-class"></a>Platform::StringReference – třída
Typ optimalizace, které můžete použít k předávání dat řetězec z `Platform::String^` vstupní parametry pro jiné metody s minimální operace kopírování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class StringReference  
```  
  
### <a name="remarks"></a>Poznámky  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[StringReference::StringReference](#ctor)|Dva konstruktory pro vytvoření instancí `StringReference`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[StringReference::Data](#data)|Vrátí řetězec dat jako pole hodnot char16.|  
|[StringReference::Length](#length)|Vrátí počet znaků v řetězci.|  
|[StringReference::GetHSTRING](#gethstring)|Vrátí řetězec dat jako HSTRING.|  
|[StringReference::GetString](#getstring)|Vrátí řetězec dat jako `Platform::String^`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[StringReference::operator=](#operator-assign)|Přiřadí `StringReference` na nový `StringReference` instance.|  
|[StringReference::operator()](#operator-call)|Převede `StringReference` k `Platform::String^`.|  
  
### <a name="requirements"></a>Požadavky  
 **Minimální podporovaná klienta:** Windows 8  
  
 **Minimální podporovaná serveru:** systému Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Záhlaví:** vccorlib.h  

## <a name="data"></a>  StringReference::Data – metoda
Vrátí obsah tohoto `StringReference` jako pole hodnot char16.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
const ::default::char16 * Data() const  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pole char16 UNICODE textových znaků.  
  


## <a name="gethstring"></a>  StringReference::GetHSTRING – metoda
Vrátí obsah jako řetězec `__abi_HSTRING`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
__abi_HSTRING GetHSTRING() const  
  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `__abi_HSTRING` Obsahující dat řetězce.  
  
### <a name="remarks"></a>Poznámky  
  


## <a name="getstring"></a>  StringReference::GetString – metoda
Vrátí obsah jako řetězec `Platform::String^`.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
__declspec(no_release_return) __declspec(no_refcount)  
    ::Platform::String^ GetString() const  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `Platform::String^` obsahující dat řetězce.  

## <a name="length"></a>  StringReference::Length – metoda
Vrátí počet znaků v řetězci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
unsigned int Length() const  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo bez znaménka, která určuje počet znaků v řetězci.  
  
### <a name="remarks"></a>Poznámky  
  


## <a name="operator-assign"></a>  StringReference::operator = – operátor
Zadaný objekt přiřadí aktuální `StringReference` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
StringReference& operator=(const StringReference& __fstrArg);  
StringReference& operator=(const ::default::char16* __strArg);    
```  
  
### <a name="parameters"></a>Parametry  
 `__fstrArg`  
 Adresa `StringReference` objekt, který se používá k chybě při inicializaci aktuální `StringReference` objektu.  
  
 `__strArg`  
 Ukazatel na pole char16 hodnoty, které slouží k inicializaci aktuální `StringReference` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt typu `StringReference`.  
  
### <a name="remarks"></a>Poznámky  
 Protože `StringReference` je standardní C++ třídy a ne třídu ref, nezobrazí se v **Prohlížeč objektů**.  
  


## <a name="operator-call"></a>  StringReference::operator() – operátor
Převede `StringReference` do objektu `Platform::String^` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
__declspec(no_release_return) __declspec(no_refcount)  
         operator ::Platform::String^() const  
  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro objekt typu `Platform::String`.  

## <a name="ctor"></a>  StringReference::StringReference – konstruktor
Inicializuje novou instanci třídy `StringReference` třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
  
    StringReference();  
  
   StringReference(const StringReference& __fstrArg)  
  
StringReference(const ::default::char16* __strArg)  
  
StringReference(const ::default::char16* __strArg, size_t __lenArg)  
```  
  
### <a name="parameters"></a>Parametry  
 `__fstrArg`  
 `StringReference` Jejichž data se používají k inicializaci nové instance.  
  
 `__strArg`  
 Ukazatel na pole char16 hodnoty, které slouží k inicializaci nové instance.  
  
 `__lenArg`  
 Počet elementů v `__strArg`.  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti tento konstruktor je výchozí konstruktor. Druhá verze inicializuje novou `StringReference` instance třídy z objektu, která je zadána `__fstrArg` parametr. Přetížení třetí a čtvrtý inicializovat novou `StringReference` instanci char16 hodnoty z pole. char16 představuje 16bitové znak UNICODE text.  
  


  
## <a name="see-also"></a>Viz také  
 [Platform::StringReference – třída](../cppcx/platform-stringreference-class.md)