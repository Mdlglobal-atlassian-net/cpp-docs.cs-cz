---
title: IID_PPV_ARGS_Helper – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: cae29c70c551701a351cdcf404342ed1634a0e3b
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334691"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper – funkce

Ověřuje, že typ zadaného argumentu je odvozen od `IUnknown` rozhraní.

> [!IMPORTANT]
> Tato specializace šablony podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo v kódu. Použití [IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) místo.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ argumentu *pp*.

*pp*<br/>
Dvakrát nepřímé ukazatel.

## <a name="return-value"></a>Návratová hodnota

Argument *pp* přetypovat na ukazatel na ukazatel na **void**.

## <a name="remarks"></a>Poznámky

Pokud je vygenerována chyba kompilace parametr šablony *T* není odvozen od `IUnknown`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

