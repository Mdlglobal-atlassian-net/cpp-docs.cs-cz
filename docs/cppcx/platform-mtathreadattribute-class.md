---
title: "Třída Platform::MTAThreadAttribute | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs: C++
helpviewer_keywords: Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f99b8ab49579d949081af73e76d4bfcb167e2cb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute – třída
Označuje, že je modelu vláken pro aplikace Vícevláknová apartment (MTA).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
public ref class MTAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[1 konstruktor MTAThreadAttribute](#ctor) – konstruktor|Inicializuje novou instanci třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
 Atribut MTAThreadAttribute dědí z [Platform::Object třída](../cppcx/platform-object-class.md). MTAThreadAttribute také přetížení nebo má následující členy:  
  
|Název|Popis|  
|----------|-----------------|  
|[MTAThreadAttribute::Equals](#equals)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|  
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Vrátí kód hash této instance.|  
|[MTAThreadAttribute::ToString](#tostring)|Vrací řetězec, který představuje aktuální objekt.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Platform`  
  
### <a name="requirements"></a>Požadavky  
 **Metadata:** platform.winmd  
  
 **Namespace:** platformy  



## <a name="ctor"></a>MTAThreadAttribute – konstruktor
Inicializuje novou instanci třídy MTAThreadAttribute.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:MTAThreadAttribute()  
```  
  


## <a name="equals"></a>MTAThreadAttribute::Equals
Určuje, zda se zadaný objekt rovná aktuálnímu objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>Parametry  
 Obj  
 Objekt k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud jsou objekty stejné; v opačném `false`.  
  


## <a name="gethashcode"></a>MTAThreadAttribute::GetHashCode
Vrátí kód hash této instance.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kód hash této instance  
  


## <a name="tostring"></a>MTAThreadAttribute::ToString
Vrací řetězec, který představuje aktuální objekt.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který představuje aktuální objekt.  
    
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)