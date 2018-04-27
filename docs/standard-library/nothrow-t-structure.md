---
title: nothrow_t – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28ed3502c60b53ac0f4f3f532eadad6f4ef61d17
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="nothrowt-structure"></a>nothrow_t – struktura

Struct slouží jako parametr funkce operátor nové indikující, že funkce by měla vrátit ukazatele null do sestavy došlo k chybě přidělení, nikoli výjimku.

## <a name="syntax"></a>Syntaxe

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>Poznámky

Struct pomáhá kompilátoru a vyberte správnou verzi konstruktoru. [nothrow](../standard-library/new-functions.md#nothrow) je synonymum pro objekty typu `std::nothrow_t`.

## <a name="example"></a>Příklad

V tématu [new – operátor](../standard-library/new-operators.md#op_new) a [new – operátor&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) příklady `std::nothrow_t` slouží jako parametr funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
