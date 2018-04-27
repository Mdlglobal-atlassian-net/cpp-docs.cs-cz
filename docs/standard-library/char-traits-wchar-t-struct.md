---
title: char_traits –&lt;wchar_t&gt; struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f2b20b72bf92679395b19b2ad6b8ae68143bb6d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits –&lt;wchar_t&gt; – struktura

Třída, která je specializace šablony struktura **char_traits –\<CharType >** pro element typu `wchar_t`.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Poznámky

Specializace umožňuje struktura chcete využít výhod funkce knihovny, které pracují s objekty tohoto typu `wchar_t`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<řetězec >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[char_traits – struktura](../standard-library/char-traits-struct.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
