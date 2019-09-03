---
title: importovat atribut high_property_prefixes
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219002"
---
# <a name="high_property_prefixes-import-attribute"></a>importovat atribut high_property_prefixes

**C++Konkrétní**

Určuje alternativní předpony pro tři metody vlastností.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **high_property_prefixes (** "*getprefix*" **;** "*PutPrefix*" **;** "*PutRefPrefix*" **)**

### <a name="parameters"></a>Parametry

*Getprefix*\
Předpona, která se má `propget` použít pro metody.

*PutPrefix*\
Předpona, která se má `propput` použít pro metody.

*PutRefPrefix*\
Předpona, která se má `propputref` použít pro metody.

## <a name="remarks"></a>Poznámky

Ve výchozím `propget`nastavení jsou metody zpracování chyb na vysoké úrovni, `propput`a `propputref` `Get`vystavovány členskými funkcemi s názvem s předponami `Put`, a `PutRef`v uvedeném pořadí.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
