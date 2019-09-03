---
title: importovat atribut no_registry
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220720"
---
# <a name="no_registry-import-attribute"></a>importovat atribut no_registry

**no_registry** instruuje kompilátor, aby nehledal v registru knihovny typů importované pomocí `#import`.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **no_registry**

### <a name="parameters"></a>Parametry

*typ – Knihovna*\
Knihovna typů.

## <a name="remarks"></a>Poznámky

Pokud se v adresářích include nenajde odkazovaná knihovna typů, kompilace se nezdařila i v případě, že se knihovna typů nachází v registru.  **no_registry** se šíří do jiných knihoven typů implicitně naimportovaných pomocí `auto_search`.

Kompilátor nikdy nehledá v registru knihovny typů, které jsou určeny názvem souboru a jsou předány přímo `#import`do.

Je `auto_search` -li parametr zadán, `#import` jsou další direktivy generovány pomocí nastavení **no_registry** počáteční `#import`. Pokud byla počáteční `#import` `auto_search`direktiva **no_registry**, vytvoří `#import` se také **no_registry**.

**no_registry** je užitečné, pokud chcete importovat knihovny typů s křížovými odkazy. Zachovává kompilátor hledáním starší verze souboru v registru. **no_registry** je užitečná také v případě, že není zaregistrována knihovna typů.

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
