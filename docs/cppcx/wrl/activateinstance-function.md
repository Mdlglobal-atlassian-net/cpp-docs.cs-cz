---
title: ActivateInstance – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 43aa34153f0e71dd665090243ff2288bff704404
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303967"
---
# <a name="activateinstance-function"></a>ActivateInstance – funkce

Zaregistruje a načte instanci zadaného typu definované v ID zadané třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ aktivace.

*activatableClassId*<br/>
Název ID třídy, která definuje parametr *T*.

*instance*<br/>
Když tato operace dokončí, odkaz na instanci *T*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chybu HRESULT určující příčinu chyby.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Viz také:

[Windows::Foundation – obor názvů](windows-foundation-namespace.md)