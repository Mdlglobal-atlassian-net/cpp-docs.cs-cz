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
ms.openlocfilehash: 8b679d4c8807a19c977cd7e59481dc1d78e67ba1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956515"
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
