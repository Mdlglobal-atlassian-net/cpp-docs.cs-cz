---
title: bad_array_new_length – třída
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_array_new_length
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: c4f4f58f7b28960bbacf695a675fbe4f20a54192
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443702"
---
# <a name="bad_array_new_length-class"></a>bad_array_new_length – třída

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

**Záhlaví:** \<nové >

## <a name="see-also"></a>Viz také

\ [třídy výjimky](../standard-library/exception-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
