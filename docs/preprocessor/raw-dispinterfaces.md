---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 8a6c335c7afe2cc56613f06abf5c181f05f6bfec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585390"
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

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)