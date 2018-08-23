---
title: Comptr::comptr – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae03de851d7cf24d7322ff6f9e1f8610a584b376
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606213"
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr – konstruktor

Inicializuje novou instanci třídy **ComPtr** třídy. Přetížení poskytují výchozí, kopírovat, přesunout a převod konstruktory.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW ComPtr();
WRL_NOTHROW ComPtr(
   decltype(__nullptr)  
);
template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr(
   const ComPtr& other
);
template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>Parametry

*U*  
Typ *jiných* parametru.

*Ostatní*  
Objekt typu *U*.

## <a name="return-value"></a>Návratová hodnota

## <a name="remarks"></a>Poznámky

První konstruktor je výchozí konstruktor, který vkládacím vytvoří prázdný objekt. Druhý konstruktor Určuje [__nullptr](../windows/nullptr-cpp-component-extensions.md), které explicitně vytvoří prázdný objekt.

Třetí konstruktor vytvoří objekt v objektu určeném ukazatel.

Čtvrtý a pátý konstruktor je kopírovací konstruktory. Pátý konstruktor zkopíruje objekt je převést na typ aktuální.

Šestý a sedmý konstruktor jsou konstruktorů. Sedmý konstruktor přesune objekt je převést na typ aktuální.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)