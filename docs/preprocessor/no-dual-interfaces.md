---
title: importovat atribut no_dual_interfaces
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220759"
---
# <a name="no_dual_interfaces-import-attribute"></a>importovat atribut no_dual_interfaces

**C++Konkrétní**

Mění způsob, jakým kompilátor generuje obálkové funkce pro metody duálního rozhraní.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **no_dual_interfaces**

## <a name="remarks"></a>Poznámky

Obálka obvykle volá metodu prostřednictvím tabulky virtuálních funkcí pro rozhraní. Pomocí **no_dual_interfaces**obálka místo toho volá `IDispatch::Invoke` k vyvolání metody.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
