---
title: space_info – struktura
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: 2a9856746a8bbc796871663a81bd8911d34dcd4a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457559"
---
# <a name="spaceinfo-structure"></a>space_info – struktura

Uchovává informace o svazku.

## <a name="syntax"></a>Syntaxe

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|`unsigned long long capacity`|Představuje celkový počet bajtů, které může svazek reprezentovat.|
|`unsigned long long free`|Představuje počet bajtů, které se nepoužívají k reprezentaci dat na svazku.|
|`unsigned long long available`|Představuje počet bajtů, které jsou k dispozici pro reprezentaci dat na svazku.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> systému souborů

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<> systému souborů](../standard-library/filesystem.md)\
[Navigace v systému souborůC++()](../standard-library/file-system-navigation.md)
