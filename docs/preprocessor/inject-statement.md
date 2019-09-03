---
title: importovat atribut inject_statement
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220989"
---
# <a name="inject_statement-import-attribute"></a>importovat atribut inject_statement

**C++Konkrétní**

Vloží svůj argument jako zdrojový text do hlavičky knihovny typů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **inject_statement (** "*zdrojový-text*" **)**

### <a name="parameters"></a>Parametry

*zdrojový text*\
Zdrojový text, který má být vložen do souboru hlaviček knihovny typů.

## <a name="remarks"></a>Poznámky

Text je umístěn na začátku deklarace oboru názvů, která zabalí obsah *knihovny typů* v hlavičkovém souboru.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
