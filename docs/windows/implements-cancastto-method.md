---
title: Implements::cancastto – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 328691877a3b129c852460f8f68cdd3db4974e6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595296"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo – metoda

Získá ukazatel na rozhraní zadané.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*  
Odkaz na identifikátor rozhraní.

*ppv*  
Pokud úspěšná, ukazatel na rozhraní určené *riid*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu, například E_NOINTERFACE.

## <a name="remarks"></a>Poznámky

Toto je interní pomocné funkce, který provádí operace QueryInterface.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Implements – struktura](../windows/implements-structure.md)