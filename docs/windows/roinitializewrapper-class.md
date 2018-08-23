---
title: Roinitializewrapper – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f5c47ac34d8b159e75acf672ba57ca8c1ebac1e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592826"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída

Inicializuje modul Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class RoInitializeWrapper
```

## <a name="remarks"></a>Poznámky

**RoInitializeWrapper** je usnadnění práce, která inicializuje modul Windows Runtime a vrátí HRESULT, která určuje, zda operace byla úspěšná. Vzhledem k tomu volá destruktor třídy `::Windows::Foundation::Uninitialize`, výskyty **RoInitializeWrapper** musí být deklarovány v oboru globálním správcem nebo nejvyšší úrovně.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[RoInitializeWrapper::RoInitializeWrapper – konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializuje novou instanci třídy **RoInitializeWrapper** třídy.|
|[RoInitializeWrapper::~RoInitializeWrapper – destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Odstraní aktuální instanci aplikace **RoInitializeWrapper** třídy.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[RoInitializeWrapper::HRESULT() – operátor](../windows/roinitializewrapper-hresult-parens-operator.md)|Načte hodnotu HRESULT vytvořené metodou **RoInitializeWrapper** konstruktoru.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RoInitializeWrapper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)