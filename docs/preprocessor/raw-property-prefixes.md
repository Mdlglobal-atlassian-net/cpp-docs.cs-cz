---
title: importovat atribut raw_property_prefixes
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216048"
---
# <a name="raw_property_prefixes-import-attribute"></a>importovat atribut raw_property_prefixes

**C++Konkrétní**

Určuje alternativní předpony pro tři metody vlastností.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **raw_property_prefixes (** "*getprefix*" **;** "*PutPrefix*" **;** "*PutRefPrefix*" **)**

### <a name="parameters"></a>Parametry

*Getprefix*\
Předpona, která se `propget` má použít pro metody

*PutPrefix*\
Předpona, která se `propput` má použít pro metody

*PutRefPrefix*\
Předpona, která se `propputref` má použít pro metody

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou metody nízké `propget`úrovně `propput`, a `propputref` vystavovány členskými funkcemi s názvem pomocí předpon `get_`, `put_`a `putref_`v uvedeném pořadí. Tyto předpony jsou kompatibilní s názvy používanými v souborech hlaviček generovaných jazykem MIDL.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
