---
title: "Runtimeclass::getruntimeclassname – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
dev_langs: C++
helpviewer_keywords: GetRuntimeClassName method
ms.assetid: f6388163-fe65-4948-a4bc-ae6826f480e7
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9987c539bb67e3989af851c3e4088e25b67f9136
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassgetruntimeclassname-method"></a>RuntimeClass::GetRuntimeClassName – metoda

Získá název třídy runtime aktuálního objektu RuntimeClass.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*  
Po dokončení této operace, název modulu runtime třídy.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.

## <a name="remarks"></a>Poznámky

Chybu assert je emitovaného Pokud &#95; &#95; WRL_STRICT &#95; &#95; nebo &#95; &#95; WRL_FORCE_INSPECTABLE_CLASS_MACRO &#95; &#95; není definován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[RuntimeClass – třída](../windows/runtimeclass-class.md)