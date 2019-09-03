---
title: importovat atribut no_smart_pointers
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220700"
---
# <a name="no_smart_pointers-import-attribute"></a>importovat atribut no_smart_pointers

**C++Konkrétní**

Potlačí vytváření inteligentních ukazatelů pro všechna rozhraní v knihovně typů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **no_smart_pointers**

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, když použijete `#import`, získáte deklaraci inteligentního ukazatele pro všechna rozhraní v knihovně typů. Tyto inteligentní ukazatele jsou typu [_com_ptr_t](../cpp/com-ptr-t-class.md).

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
