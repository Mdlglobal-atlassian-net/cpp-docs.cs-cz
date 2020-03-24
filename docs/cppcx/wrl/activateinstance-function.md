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
ms.openlocfilehash: d1109e769352d412df8348822e05b66063159ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214224"
---
# <a name="activateinstance-function"></a>ActivateInstance – funkce

Zaregistruje a načte instanci zadaného typu definovaného v zadaném ID třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ, který se má aktivovat

*activatableClassId*<br/>
Název ID třídy definující parametr *T*.

*případě*<br/>
Po dokončení této operace je odkaz na instanci *T*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě chyba HRESULT, která indikuje příčinu chyby.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Windows:: Foundation

## <a name="see-also"></a>Viz také

[Windows::Foundation – obor názvů](windows-foundation-namespace.md)
