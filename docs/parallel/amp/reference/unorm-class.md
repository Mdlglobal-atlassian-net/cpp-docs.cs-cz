---
title: unorm – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0769697dfbb0c43be9fb7326a5ad4361a2aecd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071221"
---
# <a name="unorm-class"></a>unorm – třída
Představují unorm číslo. Každý prvek je plovoucí bodu číslo v rozsahu [0,0 f, 1.0f].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class unorm;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[unorm – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor. Inicializujte na 0,0 f.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|unorm::Operator--||  
|unorm::Operator float|Operátor převodu. Převést unorm číslo plovoucí desetinnou čárkou.|  
|unorm::Operator * =||  
|unorm::Operator / =||  
|unorm::Operator ++||  
|unorm::Operator +=||  
|unorm::Operator =||  
|unorm::Operator-=||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `unorm`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a> unorm 

 Výchozí konstruktor. Inicializujte na 0,0 f.  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
*_V*<br/>
Hodnoty použité k inicializaci.  
  
*Ji_né*<br/>
Norm objekt použitý k inicializaci.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
