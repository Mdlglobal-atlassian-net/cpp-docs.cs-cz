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
ms.openlocfilehash: 4525ee74bc63a9655e7f1142fb1b2b6812d82bb6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786644"
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

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](windows-foundation-namespace.md)