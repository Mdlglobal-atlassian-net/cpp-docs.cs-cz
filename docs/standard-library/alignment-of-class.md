---
title: alignment_of – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb492c1c804aacd79f1552afb5293b8b40a8b648
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42466200"
---
# <a name="alignmentof-class"></a>alignment_of – třída

Získá zarovnání zadaného typu. Tato struktura je implementován z hlediska [alignof](../cpp/alignof-and-alignas-cpp.md). Použití `alignof` přímo kdy stačí jednoduše k dotazování na zarovnání hodnotu. Alignment_of – použijte v případě potřebujete integrální konstantou, například při odbavení značky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Ty* typ dotazu.

## <a name="remarks"></a>Poznámky

Dotaz typu obsahuje hodnotu zarovnání typu *Ty*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage – třída](../standard-library/aligned-storage-class.md)<br/>
