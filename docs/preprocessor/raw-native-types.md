---
title: importovat atribut raw_native_types
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: eb08a8e7cb081bd7a470c3c1ecf1492a7a65f833
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216067"
---
# <a name="raw_native_types-import-attribute"></a>importovat atribut raw_native_types

**C++Konkrétní**

Zakáže použití tříd podpory modelu COM v obálkových funkcích vysoké úrovně a vynutí místo toho použití datových typů na nízké úrovni.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **raw_native_types**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení používají metody zpracování chyb na vysoké úrovni třídy com support [_bstr_t](../cpp/bstr-t-class.md) a [_variant_t](../cpp/variant-t-class.md) `BSTR` namísto datových typů a `VARIANT` a nezpracovaných ukazatelů rozhraní modelu COM. Tyto třídy zapouzdřují podrobnosti přidělení a zrušení přidělení paměťového úložiště pro tyto datové typy a významně zjednodušují přetypování typů a operace převodu.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
