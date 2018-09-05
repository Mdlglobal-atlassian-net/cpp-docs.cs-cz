---
title: Platform::Array – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa689035a6e95db7f9471d4972063ec35486e0cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753214"
---
# <a name="platformarray-class"></a>Platform::Array – třída
Představuje jednorozměrné, upravitelná pole, která může být přijata a předané napříč binárním rozhraním aplikace (ABI).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp    
template <typename T>  
private ref class Array<TArg, 1> :   
    public WriteOnlyArray<TArg, 1>,  
    public IBoxArray<TArg>   
```  
  
### <a name="members"></a>Členové  
 Platform::Array dědí všechny metody z [Platform::writeonlyarray – třída](../cppcx/platform-writeonlyarray-class.md) a implementuje `Value` vlastnost [Platform::iboxarray – rozhraní](../cppcx/platform-iboxarray-interface.md).  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Pole konstruktory](#ctor)|Inicializuje jednorozměrné upravitelná pole s typy zadanými parametrem šablony třídy *T*.|  
  
### <a name="methods"></a>Metody  
 Zobrazit [Platform::writeonlyarray – třída](../cppcx/platform-writeonlyarray-class.md).  
  
### <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|[Array::Value](#value)|Načte popisovač pro daného pole.|  
  
### <a name="remarks"></a>Poznámky  
 Třídy pole je zapečetěná a nelze ji zdědit.  
  
 Systém typů prostředí Windows Runtime nepodporuje konceptu Vícenásobná pole a proto nelze předat IVector < Platform::Array\<T >> jako návratovou hodnotu nebo metoda parametr. Vícenásobné pole nebo sekvence sekvencí předejte ABI, použijte `IVector<IVector<T>^>`.  
  
 Další informace o kdy a jak používat Platform::Array najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
 Systém typů prostředí Windows Runtime nepodporuje konceptu Vícenásobná pole a proto nelze předat IVector < Platform::Array\<T >> jako návratovou hodnotu nebo metoda parametr. Vícenásobné pole nebo sekvence sekvencí předejte ABI, použijte `IVector<IVector<T>^>`.  
  
 Tato třída je definována v hlavičce vccorlib.h, který je automaticky zahrnut v kompilátoru. Je viditelný v technologii IntelliSense, ale ne v prohlížeči objektů, protože není veřejným typem definovaným v platform.winmd.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  

 
## <a name="ctor"></a>  Pole konstruktory
Inicializuje jednorozměrné upravitelná pole s typy zadanými parametrem šablony třídy *T*.  
  
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
 Ukazatel na pole datového typu `T` , který slouží k inicializaci objektu tohoto pole.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, jak vytvořit instance Platform::Array najdete v tématu [pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>  Array::Get – metoda
Získá odkaz na element pole na zadané umístění indexu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp    
T& get(unsigned int index)  const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Index založený na nule, který určuje element v poli. Minimální index 0 a maximální index hodnoty určené `size` parametr [konstruktor pole](#ctor).  
  
### <a name="return-value"></a>Návratová hodnota  
 Prvek pole, které jsou určené `index` parametru.  
  
## <a name="value"></a>  Vlastnost Array::Value
Načte popisovač pro daného pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp 
property Array^ Value;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač na aktuální pole.  

## <a name="see-also"></a>Viz také  
 [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)   
 [Pole a WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)