---
title: IID_PPV_ARGS_Helper – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: e7733ae6084b64c20dff5a2c35d7a31c614d6e44
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500509"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper – funkce

Ověřuje, že typ zadaného argumentu je odvozen z `IUnknown` rozhraní.

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

*T*<br/>
Typ argumentu *PP*.

*pp*<br/>
Dvakrát nepřímý ukazatel.

## <a name="return-value"></a>Návratová hodnota

Argument *PP* se přetypování na ukazatel na ukazatel na **typ void**.

## <a name="remarks"></a>Poznámky

Pokud parametr šablony *T* neodvozuje z `IUnknown`, vygeneruje se chyba při kompilaci.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

