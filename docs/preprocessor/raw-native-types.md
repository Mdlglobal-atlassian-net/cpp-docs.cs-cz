---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: e48aa2ca1469d38b67dcb06a3377713141a158e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620438"
---
# <a name="rawnativetypes"></a>raw_native_types
**Specifické pro C++**

Zakáže použití tlačítek třídy pro podporu modelu COM v funkce obálky vysoké úrovně a místo toho vynutí použití nižší úrovně datových typů.

## <a name="syntax"></a>Syntaxe

```
raw_native_types
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, použijte základní metody zpracování chyb třídy COM support [_bstr_t](../cpp/bstr-t-class.md) a [_variant_t](../cpp/variant-t-class.md) místo `BSTR` a `VARIANT` datových typů a raw COM rozhraní ukazatele. Tyto třídy zapouzdřit podrobnosti o přidělování a rušení přidělení paměti úložiště pro tyto typy dat a výrazně zjednodušit operace přetypování a převodu typu.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)