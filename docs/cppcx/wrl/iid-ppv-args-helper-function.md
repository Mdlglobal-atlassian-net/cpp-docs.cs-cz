---
title: IID_PPV_ARGS_Helper – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 68dbd0b5b2e9d4fc04821a7e7e0193840b55e312
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077131"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper – funkce

Ověřuje, že typ zadaného argumentu je odvozen z rozhraní `IUnknown`.

> [!IMPORTANT]
> Tato specializace šablony podporuje infrastrukturu WRL a není určena pro použití přímo v kódu. Místo toho použijte [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) .

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ argumentu *PP*.

*str*<br/>
Dvakrát nepřímý ukazatel.

## <a name="return-value"></a>Návratová hodnota

Argument *PP* se přetypování na ukazatel na ukazatel na **typ void**.

## <a name="remarks"></a>Poznámky

Pokud se parametr šablony *T* neodvozuje z `IUnknown`, vygeneruje se chyba při kompilaci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h
