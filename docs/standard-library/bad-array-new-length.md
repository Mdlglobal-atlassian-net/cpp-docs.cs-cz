---
title: bad_array_new_length – třída
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459493"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length – třída

Třída popisuje vyvolanou výjimku, která označuje, že požadavek na přidělení nebyl úspěšný, protože velikost pole je menší než nula nebo větší než jeho limit.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená funkcí `what` je řetězec jazyka C definovaný implementací. Žádná z členských funkcí nevyvolá žádné výjimky.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<nový >

## <a name="see-also"></a>Viz také:

[Exception – třída](../standard-library/exception-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
