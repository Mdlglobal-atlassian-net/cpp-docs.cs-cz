---
title: "Třída Platform::Array | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
dev_langs: C++
helpviewer_keywords: Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7aa3a29615f6c744a3c790dd7b223225bc31f87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="platformarray-class"></a>Platform::Array – třída
Představuje jednorozměrné, upravitelnými pole, které mohou být přijata a předán přes rozhraní binární aplikace (ABI).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp    
template <typename T>  
private ref class Array<TArg, 1> :   
    public WriteOnlyArray<TArg, 1>,  
    public IBoxArray<TArg>   
```  
  
### <a name="members"></a>Členové  
 Platform::Array dědí všechny její metody z [Platform::WriteOnlyArray třída](../cppcx/platform-writeonlyarray-class.md) a implementuje `Value` vlastnost [Platform::IBoxArray rozhraní](../cppcx/platform-iboxarray-interface.md).  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Pole konstruktory](#ctor)|Inicializuje jednorozměrné, upravitelnými pole typů určeného parametr šablony třídy *T*.|  
  
### <a name="methods"></a>Metody  
 V tématu [Platform::WriteOnlyArray třída](../cppcx/platform-writeonlyarray-class.md).  
  
### <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|[Array::Value](#value)|Načte popisovač pro aktuální pole.|  
  
### <a name="remarks"></a>Poznámky  
 Array – třída je zapečetěná a nelze ji zdědit.  
  
 Systém typů prostředí Windows Runtime nepodporuje koncept Vícenásobná pole a proto nemůžete předat IVector < Platform::Array\<T >> jako návratový parametr hodnotu nebo metoda. Chcete-li předat Vícenásobná pole nebo posloupnost pořadí napříč ABI, použijte `IVector<IVector<T>^>`.  
  
 Další informace o kdy a jak používat Platform::Array najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
 Systém typů prostředí Windows Runtime nepodporuje koncept Vícenásobná pole a proto nemůžete předat IVector < Platform::Array\<T >> jako návratový parametr hodnotu nebo metoda. Chcete-li předat Vícenásobná pole nebo posloupnost pořadí napříč ABI, použijte `IVector<IVector<T>^>`.  
  
 Tato třída je definována v hlavičce vccorlib.h, která je automaticky součástí kompilátorem. Viditelné v technologii Intellisense, ale není v prohlížeči objektu je vzhledem k tomu, že se nejedná o veřejné typem definovaným v platform.winmd.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  

 
## <a name="ctor"></a>Pole konstruktory
Inicializuje jednorozměrné, upravitelnými pole typů určeného parametr šablony třídy *T*.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Array(unsigned int size);  
Array(T* data, unsigned int size);    
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr šablony třídy.  
  
 `size`  
 Počet prvků v poli.  
  
 `data`  
 Ukazatel na pole data typu `T` sloužící k inicializaci objektu Toto pole.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, jak vytvořit instance Platform::Array najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>Array::Get – metoda
Získá odkaz na element pole na zadané umístění indexu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp    
T& get(unsigned int index)  const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Index založený na nule identifikuje element v poli. Minimální index je 0 a maximální index je hodnotu zadanou pomocí `size` parametr ve [Array – konstruktor](#ctor).  
  
### <a name="return-value"></a>Návratová hodnota  
 Element pole určeného `index` parametr.  
  
## <a name="value"></a>Vlastnost Array::Value
Načte popisovač pro aktuální pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp 
property Array^ Value;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro aktuální pole.  

## <a name="see-also"></a>Viz také  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)   
 [Pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)