---
title: raw_native_types
ms.date: 11/04/2016
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: 32b77905ef7025334e5101e76864da9a15c50cf6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180476"
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

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)