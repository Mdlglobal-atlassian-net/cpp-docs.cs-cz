---
title: nothrow_t – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a34d9b4e87e2a9036afe7dc12b85fa6d4354209
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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
