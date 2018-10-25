---
title: raw_native_types – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4739b8664da21a86caa91398a7956eac77e22f3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072886"
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