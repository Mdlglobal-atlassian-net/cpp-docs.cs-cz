---
title: "Norm – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs: C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 785c214ed904d1591c5d532ec9f09d42c93dc2ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="norm-class"></a>norm – třída
Představují norm číslo. Každý prvek je plovoucí bodu číslo v rozsahu [-1.0f, 1.0f].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class norm;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Norm – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor. Inicializace na 0, 0f.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|Norm::Operator-||  
|Norm::Operator--||  
|Norm::Operator float|Operátor převodu. Převést norm číslo na plovoucí bodu hodnotu.|  
|Norm::Operator * =||  
|/ Norm::Operator = – operátor||  
|Norm::Operator ++||  
|Norm::Operator +=||  
|Norm::Operator =||  
|Norm::Operator-=||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `norm`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a>Norm 

 Výchozí konstruktor. Inicializace na 0, 0f.  
  
```  
norm(
    void) restrict(amp,
    cpu);

 
explicit norm(
    float _V) restrict(amp,
    cpu);

 
explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit norm(
    int _V) restrict(amp,
    cpu);

 
explicit norm(
    double _V) restrict(amp,
    cpu);

 
norm(
    const norm& _Other) restrict(amp,
    cpu);

 
norm(
    const unorm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_V`  
 Hodnota určená k chybě při inicializaci.  
  
 `_Other`  
 Objekt použitý k chybě při inicializaci.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
