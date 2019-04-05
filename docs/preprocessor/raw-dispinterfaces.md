---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: ef8ed3992c77df0f1d551e923ddc90c2d1bb9b0b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027920"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Specifické pro C++**

Instruuje kompilátor, aby generovat funkce nízké úrovně obálky pro dispinterface metody a vlastnosti, které volají `IDispatch::Invoke` a vrátí kód chyby: HRESULT.

## <a name="syntax"></a>Syntaxe

```
raw_dispinterfaces
```

## <a name="remarks"></a>Poznámky

Pokud tento atribut není zadaný, pouze vysoké úrovně jsou generovány obálky, které vyvolají výjimky C++ v případě selhání.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[#import – atributy](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)