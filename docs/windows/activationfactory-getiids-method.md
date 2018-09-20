---
title: Activationfactory::getiids – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89cebd5c6fdfa3ee523a3ab2730ba11c1e2b68ab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407618"
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids – metoda

Načte pole ID implementovaného rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Když tato operace dokončí, počet ID uživatelského rozhraní v *IID* pole.

*IID*<br/>
Po dokončení této operace implementované pole ID rozhraní.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby. E_OUTOFMEMORY je možné selhání hodnoty HRESULT.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ActivationFactory – třída](../windows/activationfactory-class.md)