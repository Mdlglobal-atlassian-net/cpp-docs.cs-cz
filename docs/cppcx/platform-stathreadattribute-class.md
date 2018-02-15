---
title: "Třída Platform::STAThreadAttribute | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db66ba0775ad3b38be1b43fd5781be611ca2f333
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute – třída
Označuje, že modelu vláken pro aplikaci je single-threaded apartment (STA).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
public ref class STAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Konstruktor STAThreadAttribute 1](#ctor)|Inicializuje novou instanci třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
 Atribut STAThreadAttribute dědí z [Platform::Object třída](../cppcx/platform-object-class.md). STAThreadAttribute také přetížení nebo má následující členy:  
  
|Název|Popis|  
|----------|-----------------|  
|[STAThreadAttribute::Equals](#equals)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|  
|[STAThreadAttribute::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|  
|[STAThreadAttribute::ToString](#tostring)|Vrací řetězec, který představuje aktuální objekt.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Platform`  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** collection.h  
  
 **Namespace:** platformy  



## <a name="ctor"></a> STAThreadAttribute – konstruktor
Inicializuje novou instanci třídy STAThreadAttribute.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:STAThreadAttribute()  
```  
  


## <a name="equals">STAThreadAttribute::Equals</a>
Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>Parametry  
 obj  
 Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud jsou objekty stejné; v opačném `false`.  
  


## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode
Vrátí kód hash této instance.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kód hash této instance  
  


## <a name="tostring">STAThreadAttribute::ToString</a>
Vrací řetězec, který představuje aktuální objekt.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který představuje aktuální objekt.  
  

  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)