---
title: importovat atribut raw_dispinterfaces
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216222"
---
# <a name="raw_dispinterfaces-import-attribute"></a>importovat atribut raw_dispinterfaces

**C++Konkrétní**

Instruuje kompilátor, aby vygeneroval obálkové funkce nízké úrovně pro metody pro vyhlašování a vlastnosti `IDispatch::Invoke` , které volají, a vrátí kód chyby HRESULT.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **raw_dispinterfaces**

## <a name="remarks"></a>Poznámky

Pokud tento atribut není zadán, jsou vygenerovány pouze obálky vysoké úrovně, které vyvolávají C++ výjimky při selhání.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
