---
title: bad_array_new_length třídy
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 823da1555119735e9aa1c46aa4db2e3a47affdec
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267961"
---
# <a name="badarraynewlength-class"></a>bad_array_new_length třídy

Tato třída popisuje výjimku vyvolanou k označení, že požadavek na přidělení nebylo úspěšné kvůli velikost pole menší než nula nebo větší než limit.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená `what` je řetězec C definované implementací. Žádná z členské funkce generovat žádné výjimky.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

## <a name="see-also"></a>Viz také:

[exception – třída](../standard-library/exception-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
