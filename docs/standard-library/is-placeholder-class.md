---
title: is_placeholder – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1dd65d50dd2a4b42b949c7ce649c2dcca71f4d72
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="isplaceholder-class"></a>is_placeholder – třída

Testy, pokud je typ zástupný symbol.

## <a name="syntax"></a>Syntaxe

Struktura is_placeholder {statické const int hodnoty;};

## <a name="remarks"></a>Poznámky

Hodnota konstanty `value` je 0, pokud typ `Ty` není zástupný symbol; jinak, jeho hodnota může být pozici argument volání funkce, která se váže k. Můžete použít k určení hodnoty `N` n-tou zástupného textu `_N`.

## <a name="example"></a>Příklad

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[_1 – objekt](../standard-library/1-object.md)<br/>
