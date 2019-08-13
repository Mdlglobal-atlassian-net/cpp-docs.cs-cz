---
title: bad_optional_access – třída
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: 043b0360c7e0be48267c8f406dbfea50eeb5a8e3
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957101"
---
# <a name="bad_optional_access-class"></a>bad_optional_access – třída

Definuje typ objektů vyvolaných jako výjimky, které nahlásí situaci, kdy se pokusí o přístup k hodnotě `optional` objektu, který neobsahuje hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>Viz také:

[\<volitelné >](optional.md)\
[Volitelná třída](optional-class.md)
